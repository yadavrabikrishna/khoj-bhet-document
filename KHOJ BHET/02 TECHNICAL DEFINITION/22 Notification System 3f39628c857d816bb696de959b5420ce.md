# 22. Notification System

> **Implementation status clarification — 2026-10-15:** “Active” means this is the current authoritative design baseline, not that implementation is release-ready. Implementation sign-off remains gated by the final OpenAPI 3.1 contract, successful clean-MySQL migration/runtime validation, and the relevant component tests. Component-specific schema or provider gates documented below remain independently binding.
> 

> ## Notification Schema Compatibility Gate — 2026-10-09
> 

> Document 13 currently models notifications with id, user_id, optional listing_id, notification_type, payload, read_at and timestamps; notification_deliveries records channel, status, provider reference, attempts, delivery timestamps and error state. The current schema does not establish dedicated notification dedupe key, classification, expiry, or locale fields, nor a notification_templates table.
> 

> 
> 

> Do not assume these columns/tables exist. For V1, templates may be versioned code/config assets and deduplication may use a durable outbox event identity plus idempotent worker logic only if that guarantees one logical notification under retries. If a durable database-level dedupe invariant, per-notification locale, classification or expiry is required, add it through an approved Document 13 schema gate before implementation. Choose and document the V1 notification locale policy; do not infer notification-template language from the API Accept-Language header. The final endpoint and response shapes remain governed by Document 14.
> 

## Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-TECH-022 |
| Status | Active — Notification System Baseline |
| Version | 1.0 |
| Owner | KHOJ BHET Engineering |
| Last Reviewed | 2026-10-08 |
| Parent | 02. TECHNICAL DEFINITION |
| Previous | 21. Search Architecture |
| Next | 23. SEO Architecture |
| Related | 08 Product & Business Rules; 09 Software Architecture; 10 Technology Stack; 12 Engineering Standards; 13 Database Architecture & Data Model; 14 API Specification; 15 Frontend Architecture; 16 Backend Architecture; 17 Mobile Application Architecture; 18 Authentication & Authorization; 19 Security Architecture; 20 Media & File Storage; 21 Search Architecture |

## 1. Purpose

This document defines the authoritative notification architecture for KHOJ BHET.

It covers:

- in-app notifications;
- push notifications;
- email notifications where enabled;
- Approved transactional SMS notifications; marketplace sign-in/recovery OTP is handled exclusively by Firebase Authentication under ADR-002.
- future WhatsApp or other approved channels;
- notification preferences;
- notification templates;
- delivery states;
- device-token management;
- event-driven notification generation;
- queue processing;
- retries;
- deduplication and idempotency;
- user privacy;
- transactional versus promotional notifications;
- notification scheduling;
- deep links;
- read/unread state;
- provider abstraction;
- delivery observability;
- failure handling;
- abuse prevention;
- security and authorization.

The architecture is designed around a **provider-agnostic Notification Service** with Firebase Cloud Messaging (FCM) as the primary push-delivery mechanism for V1 mobile applications.

## 2. Core Architectural Decision

KHOJ BHET separates:

**Domain Event → Notification Decision → Notification Record → Delivery Job → Channel Provider → Delivery Result**

The flow is:

**Laravel Domain Event → Notification Service → MySQL Notification Record → Queue/Worker → Channel Adapter → Provider**

The notification provider is never the source of truth for whether a notification should exist.

MySQL remains authoritative for:

- notification identity;
- recipient;
- notification type;
- preference evaluation;
- read state;
- delivery state;
- retry state;
- scheduling;
- deduplication/idempotency metadata.

## 2.1 V1 Scope Boundary

V1 notification scope is limited to transactional marketplace events, required security/account notices, in-app notifications/read state, user notification preferences, and approved FCM native-device push. Each externally observable read/mutation endpoint must be defined in Document 14 before clients implement it. Do not assume mark-all-read, bulk/multi-read, or unread-count endpoints exist unless Document 14 explicitly defines them.

The following are deferred unless separately approved: campaigns/promotional blasts, user-configurable quiet hours, browser push, WhatsApp Business API, and any provider-specific push token service beyond FCM native device tokens. Email/SMS are adapters only for approved transactional/security use cases. Define the V1 locale fallback explicitly; do not imply all templates are localized when only one locale is available.

## 3. Notification Principles

1. Notifications are generated from authoritative application events.
2. Clients never create authoritative notifications directly.
3. Delivery providers are replaceable adapters.
4. Transactional notifications are separated from promotional notifications.
5. User preferences must be respected unless a legally/business-required transactional exception applies.
6. Notification delivery must be asynchronous for non-critical request paths.
7. Notification operations must be idempotent.
8. A failed push must not corrupt the underlying business operation.
9. Notification content must respect authorization and privacy.
10. Notification payloads must contain the minimum required data.
11. Push-device registration grants no application permissions.
12. Delivery success does not prove that a user read the notification.
13. Read state belongs to KHOJ BHET, not the provider.
14. Provider outages must not cause fail-open behavior.
15. Web and mobile notification semantics must remain consistent.

## 4. Notification Channels

The architecture supports channel adapters.

| Channel | V1 Role | Primary Use |
| --- | --- | --- |
| In-App | Required | Persistent user notification center |
| Push / FCM | Required | Mobile real-time alerts |
| Email | Optional/approved | Account and important communications |
| SMS | Required where business flow needs it | OTP and selected transactional messages |
| WhatsApp | Future | Approved transactional/communication workflows |
| Other providers | Future | Added through adapters |

A channel may be disabled without changing the underlying notification event model.

## 5. In-App Notifications

In-app notifications are persistent records associated with a recipient.

They may include:

- title;
- body;
- notification type;
- related resource;
- deep-link target;
- read/unread state;
- created time;
- expiry where applicable.

The in-app notification is the canonical user-facing record even when push delivery fails.

## 6. Push Notifications

FCM is the primary V1 push provider.

The application sends push notifications through a provider adapter rather than embedding FCM-specific logic throughout business services.

Push delivery may target:

- one device;
- all eligible devices for a user;
- a controlled subset of a user's devices.

A push payload should normally contain a notification identifier and minimal routing metadata rather than sensitive business data.

## 7. Device Token Architecture

Device tokens are associated with authenticated marketplace users.

A device registration should maintain, where applicable:

- device registration ID;
- user ID;
- push provider;
- push token;
- platform;
- application/version information;
- device metadata needed for delivery diagnostics;
- active/inactive state;
- last-seen timestamp;
- token creation/update timestamps.

The exact schema remains aligned with Document 13.

## 8. Push Device Security

Push registration requires authenticated ownership.

Requirements:

- user may manage only their own device registrations;
- a push token does not grant account access;
- a token cannot be used as authentication;
- token rotation is supported;
- invalid tokens are deactivated;
- logout/account changes must be handled safely;
- sensitive notification data is not placed in long-lived push payloads.

These rules reinforce Document 18 and Document 19.

## 9. Notification Types

Notification types must be canonical identifiers.

Examples include:

### Account

- account security event;
- email/phone verification;
- account status change;
- password/authentication event where applicable.

### Listing

- listing submitted;
- listing approved;
- listing rejected;
- listing published;
- listing paused;
- listing resumed;
- listing expired;
- listing moderation update.

### Marketplace

- inquiry/message;
- favorite-related event;
- saved-search match;
- price/update alert where approved.

### Business

- business invitation;
- membership change;
- role change;
- business listing event.

### Payment/Subscription

- payment initiated;
- payment confirmed;
- payment failed;
- subscription activated;
- subscription expiring;
- subscription changed.

### Safety

- security alert;
- suspicious account activity;
- moderation/safety action.

Exact public notification enum values remain governed by Document 14 and the final enum registry.

## 10. Transactional vs Promotional Notifications

Every notification must have a communication classification.

### Transactional

Required to complete, secure, or materially operate an account/service.

Examples:

- OTP;
- security alert;
- critical account status;
- payment result;
- required moderation decision.

### Service/Operational

Important product events that may be preference-controlled depending on business rules.

Examples:

- listing approval;
- inquiry;
- business membership event;
- saved-search result.

### Promotional

Marketing, advertising, campaigns, recommendations, and promotional offers.

Promotional communication requires explicit preference/consent handling where applicable.

A user opting out of promotional notifications must not automatically disable required transactional security notifications.

## 11. Notification Preferences

Preferences are user-controlled settings subject to mandatory communication rules.

Preference dimensions may include:

- push;
- email;
- SMS;
- in-app;
- promotional;
- listing activity;
- inquiry/message;
- saved searches;
- business activity;
- payment/subscription;
- security/account.

Preferences must be evaluated server-side.

Client settings are not authoritative.

## 12. Preference Evaluation

Before delivery, the Notification Service evaluates:

1. notification classification;
2. recipient account state;
3. channel;
4. user preference;
5. legal/business mandatory status;
6. resource visibility;
7. current authorization;
8. rate/quiet-hour policy where applicable.

A disabled channel should suppress that delivery without deleting the underlying in-app notification when the product semantics require persistence.

## 13. Quiet Hours

Quiet hours may suppress non-critical push notifications.

Critical security or legally required transactional notifications may bypass quiet hours when defined by policy.

Queued notifications should not be silently lost because of quiet hours.

The system should retain enough state to determine whether to:

- delay;
- suppress;
- deliver immediately;
- convert to in-app only.

## 14. Notification Templates

Notification content must be template-driven rather than scattered through business services.

A template should define:

- notification type;
- channel;
- title/body structure;
- locale;
- version;
- required variables;
- classification;
- enabled/disabled status.

Business events provide data; templates provide presentation.

## 15. Localization

Notifications should support localized content.

V1 should be designed for at least:

- Nepali;
- English.

Locale selection may consider:

1. user preference;
2. application locale;
3. supported locale fallback.

Original event data must remain language-neutral.

## 16. Template Variables

Template variables must be explicitly defined and validated.

Examples:

- user display name;
- listing title;
- listing identifier;
- business name;
- payment amount;
- status label.

Templates must not receive unrestricted database objects.

Only approved fields may enter notification rendering.

## 17. Privacy of Notification Content

Notification content may appear on a locked device screen.

Therefore:

- avoid unnecessary sensitive information;
- do not include passwords, OTPs, tokens, secrets, or payment credentials;
- avoid exposing exact protected locations;
- avoid unnecessary contact details;
- avoid private document content;
- use generic wording where necessary.

Sensitive detail should be retrieved through an authorized application flow after the user opens the notification.

## 18. Deep Links

Notifications may contain an application deep-link target.

A deep link is a navigation instruction, not an authorization grant.

Example conceptual target:

**khojbhet://listing/{public-id}**

When opening a public web URL, use the canonical `/listing/{slug}-{public-id}` route. App-native deep links may use the stable public ID without the slug; never embed the sequential BIGINT database ID in an externally visible deep link.

When opened, the destination must perform normal authentication, authorization, lifecycle, and privacy checks.

A notification for a resource that later becomes private must not bypass those checks.

## 19. Web Links

Web notifications may use HTTPS application routes.

The URL must not contain secrets or long-lived access tokens.

The destination page remains responsible for authorization and current resource state.

## 20. Event-Driven Architecture

Domain events should trigger notification decisions.

Examples:

- ListingPublished;
- ListingApproved;
- ListingRejected;
- ListingPaused;
- InquiryCreated;
- BusinessMemberInvited;
- BusinessRoleChanged;
- PaymentCompleted;
- PaymentFailed;
- SubscriptionChanged;
- SecurityEventDetected.

The exact event registry remains aligned with the backend architecture and ADR decisions.

## 21. Transaction Boundary

Business transactions must not depend on successful notification delivery.

Required V1 sequence (transactional outbox, see section 22):

1. Perform the authoritative business transaction and write the `outbox_events` row in the same MySQL transaction.
2. Commit.
3. The outbox relay publishes the committed event.
4. An idempotent consumer creates the notification record.
5. Deliver asynchronously.
6. Record the delivery result.

If the notification is generated transactionally, the notification record and event publication must use a reliable mechanism such as an outbox pattern where necessary.

## 22. Outbox Pattern

For transactional events that trigger notifications or other durable side effects, the transactional outbox is required: the business mutation and `outbox_events` row are committed in the same MySQL transaction. A relay worker publishes committed events and retries failures; consumers must be idempotent. This is not merely an optional recommendation.

Conceptual flow:

**Business Transaction → Database Commit + Outbox Event → Worker → Notification Service**

This prevents the failure mode where:

- the business transaction succeeds;
- the API response succeeds;
- notification dispatch is lost because the application process fails before enqueueing.

The exact outbox implementation belongs to Document 16 and the database architecture.

## 23. Queue Architecture

Notification delivery should use queues/workers.

Separate queues may be used for:

- push;
- email;
- SMS;
- low-priority promotional communication;
- retry/dead-letter processing.

High-priority security notifications must not be blocked indefinitely behind bulk promotional traffic.

## 24. Retry Policy

Retries must be classified by failure type.

### Retryable

- provider timeout;
- transient network error;
- temporary provider failure;
- temporary queue/worker failure.

### Non-Retryable

- invalid recipient;
- permanently invalid token;
- invalid template;
- unauthorized target;
- unsupported channel;
- provider permanent rejection.

Retries must use bounded attempts and controlled backoff.

## 25. Exponential Backoff

Retryable delivery failures should use bounded exponential backoff with jitter.

The system must avoid retry storms.

After maximum retries, the notification enters a terminal failure/dead-letter state where appropriate.

## 26. Idempotency

Every notification operation that can be retried must be idempotent.

A notification event should have a stable identity or deduplication key.

Examples:

- event ID;
- recipient ID;
- notification type;
- resource ID;
- logical event version.

The same business event must not generate unlimited duplicate notifications because of worker retries.

## 27. Duplicate Prevention

Duplicate prevention must be designed per notification type.

For example:

- one listing approval event → one logical approval notification;
- one membership invitation → one active invitation notification;
- repeated provider retry → no additional logical notification record.

Legitimate repeated events must remain distinguishable from accidental retries.

## 28. Notification Delivery States

Internal delivery state may include:

- pending;
- queued;
- sending;
- sent;
- delivered where provider supports confirmation;
- failed;
- suppressed;
- expired;
- cancelled.

Provider delivery states must be normalized into application-level internal states.

Public API enum values remain governed by Document 14.

## 29. Read State

Read/unread is an application state.

The system may maintain:

- unread;
- read;
- read timestamp.

Provider delivery does not change read state.

Opening the target resource may optionally mark the notification as read according to product rules.

## 30. Notification Expiry

Some notifications may expire.

Examples:

- temporary invitation;
- time-sensitive promotion;
- expiring saved-search alert.

Expiry must not delete mandatory audit/history where retention is required.

An expired notification may remain in history but no longer trigger active delivery.

## 31. Notification Center

The V1 API supports only what Document 14 defines (see section 2.1): list notifications, pagination and mark one as read. Unread count, mark-multiple-as-read, mark-all-as-read and notification detail are future options and must not be implemented until Document 14 defines them.

The notification center is user-scoped.

## 32. Notification Ordering

Default ordering should be deterministic, normally newest first.

Tie-breaking must use a stable identifier or timestamp/identifier combination.

Pagination should use the API's canonical cursor strategy where appropriate.

## 33. Unread Count

Unread counts must be calculated from authoritative notification records.

Cached counts may be used for performance but must not permanently diverge from MySQL.

Security-sensitive account events should not be hidden merely because an unread-count cache is stale.

## 34. Channel Fan-Out

One logical notification may produce multiple delivery records.

Example:

**PaymentCompleted → In-App + Push + Email**

The logical notification and channel delivery attempts must remain conceptually separate.

Failure of one channel must not automatically mean failure of the logical notification.

## 35. Provider Abstraction

Each external delivery mechanism must be behind an adapter.

Conceptual adapters:

- FCM adapter;
- SMS provider adapter;
- email provider adapter;
- future WhatsApp adapter.

Business services must not directly call provider SDKs.

Provider replacement should not require rewriting notification business rules.

## 36. FCM-Specific Rules

FCM is a delivery mechanism, not an authorization system.

Requirements:

- store tokens server-side;
- send only to authorized user devices;
- deactivate invalid tokens;
- handle token rotation;
- avoid sensitive payloads;
- use provider message identifiers for diagnostics where available;
- handle provider errors through the adapter;
- never expose server-side FCM credentials to clients.

## 37. SMS and OTP Boundary

SMS is appropriate for selected transactional messages. Marketplace sign-in/recovery OTP delivery and verification are owned exclusively by Firebase Authentication under ADR-002; the Notification System SMS adapter must not send or verify those OTPs.

OTP delivery has stricter security controls:

- short expiration;
- attempt limits;
- resend throttling;
- abuse/rate limiting;
- no OTP logging;
- no OTP persistence in notification history;
- provider failure handling.

OTP architecture remains governed by Authentication & Authorization.

## 38. Email Boundary

Email may be used for account, transactional, and approved communication.

Email content must follow the same privacy rules.

Unsubscribe/preference behavior must distinguish promotional communication from mandatory transactional communication.

## 39. Future WhatsApp Integration

WhatsApp or other messaging channels may be introduced through a provider adapter.

The core notification event, preference, template, authorization, and audit architecture must remain unchanged.

Provider-specific compliance and template requirements remain isolated to the adapter.

## 40. Notification and Authorization

Before generating or delivering a notification, the system must verify that the recipient is entitled to receive information about the event.

Examples:

- business membership must still be valid;
- listing relationship must still permit disclosure;
- private conversation notification must target authorized participants;
- administrative notifications must never be sent to ordinary users.

Notification generation is not exempt from authorization.

## 41. Notification and Listing Privacy

A notification may refer to a listing without exposing restricted details.

For example, a push may state that a listing has changed without including exact location or protected seller information.

When opened, the application retrieves current authorized data.

## 42. Notification and Subscription

Subscription events may generate notifications, but entitlement itself does not authorize notification access to unrelated data.

Subscription expiration may trigger operational reminders subject to preference rules.

Promotional notifications remain separately classified.

## 43. Notification and Search

Saved-search notifications may be generated when a newly eligible listing matches a saved search.

The matching system must use current search eligibility.

A notification must not reveal a listing that the recipient could not currently discover under applicable visibility rules.

## 44. Notification and Media

Notification payloads should use media references only when necessary.

Do not embed sensitive media directly in push payloads.

If an image is used for a notification preview, it must be public or accessed through a controlled mechanism appropriate to the provider.

## 45. Rate Limiting and Anti-Spam

Notification generation and delivery require abuse controls.

Controls include:

- per-user notification frequency;
- per-event deduplication;
- channel-specific rate limits;
- promotional campaign limits;
- provider throughput limits;
- SMS abuse controls;
- push burst controls.

Security notifications must remain deliverable despite ordinary promotional limits.

## 46. Campaign Notifications

Promotional campaigns must be separated from transactional notification processing.

Campaign infrastructure should support:

- audience eligibility;
- consent/preferences;
- scheduling;
- frequency caps;
- unsubscribe behavior;
- provider throttling;
- campaign auditability.

A campaign must never bypass account suspension or communication preferences.

## 47. Scheduled Notifications

Scheduled notifications may support:

- subscription expiry reminders;
- listing expiry reminders;
- saved-search alerts;
- appointment/reminder features if introduced.

Scheduled jobs must be idempotent.

The scheduler must revalidate eligibility at execution time rather than assuming the state from scheduling time remains valid.

## 48. Time Zones

The backend's canonical application/storage timezone is **UTC**, consistent with Documents 13 and 14. Configure `APP_TIMEZONE=UTC`; persist and compare timestamps in UTC. Use `Asia/Kathmandu` only when interpreting Nepal-local schedules, quiet-hour windows, user-facing display, and calendar boundaries. Convert to UTC at scheduling/persistence boundaries and make the intended timezone explicit in every scheduled job.

## 49. Notification Analytics

Operational analytics may include:

- generated notifications;
- queued notifications;
- delivery attempts;
- delivery success/failure;
- provider latency;
- invalid token rate;
- read rate;
- click/open rate where available;
- unsubscribe/preference changes;
- retry volume;
- dead-letter volume.

Analytics must avoid storing unnecessary sensitive content.

## 50. Observability

Monitor:

- queue depth;
- worker health;
- notification generation latency;
- delivery latency;
- provider failure rate;
- retry rate;
- invalid device-token rate;
- email/SMS bounce or rejection;
- unread-count consistency;
- notification duplication;
- dead-letter queue size.

Alerts should be configured for sustained provider or worker failures.

## 51. Failure Handling

Notification failures must be isolated from core marketplace transactions.

If FCM is unavailable:

- in-app notification may still be created;
- retry may occur;
- user can see the notification later.

If SMS fails:

- authentication flow applies its own failure/retry rules;
- the business transaction must not assume SMS delivery unless that flow explicitly requires confirmation.

If email fails:

- the in-app record remains where applicable;
- retry/dead-letter behavior applies.

## 52. Dead-Letter Handling

Terminal failures may enter a dead-letter queue or failure table.

Dead-letter processing must support:

- inspection;
- safe retry;
- cancellation;
- provider-error classification;
- operational metrics.

Dead-letter records must not contain secrets or unnecessary sensitive content.

## 53. Data Retention

Notification retention depends on classification.

The system should distinguish:

- user-facing history;
- security/audit records;
- delivery diagnostics;
- promotional campaign records.

Retention must follow the project's privacy/data-lifecycle policy.

Expired notification content should not be retained indefinitely without purpose.

## 54. Security Controls

Notification architecture must follow Document 19.

Required controls include:

- least privilege;
- provider credential isolation;
- server-side authorization;
- secure queue access;
- secret protection;
- input/template validation;
- payload minimization;
- auditability;
- rate limiting;
- safe logging.

Provider credentials never appear in client applications.

## 55. Notification Template Security

Template rendering must be protected against:

- template injection;
- unsafe HTML;
- malicious URLs;
- untrusted markup;
- oversized content;
- invalid variables.

User-controlled values must be escaped according to the target channel.

## 56. Deep-Link Security

Deep links must contain only safe identifiers/routing information.

They must never contain:

- access tokens;
- passwords;
- OTPs;
- signed storage credentials;
- long-lived session credentials.

The destination rechecks authorization.

## 57. Notification API

Public notification APIs in V1 are limited to Document 14 (unread count and bulk-read are future options):

- list notifications;
- mark notification read;
- register/update push device;
- remove push device;
- retrieve/update notification preferences.

Exact endpoint paths, request/response envelopes, and public enums remain governed by Document 14.

## 58. Backend Implementation Boundary

The Laravel backend should separate:

- Notification Domain Service;
- Preference Service;
- Template Renderer;
- Delivery Dispatcher;
- Channel Adapters;
- Notification Repository;
- Device Token Service;
- Notification Jobs;
- Provider Webhook/Delivery Status Handler where supported.

Controllers should not contain provider-specific delivery logic.

## 59. Mobile Implementation Boundary

The React Native/Expo application should handle:

- permission prompts;
- push-token acquisition;
- token refresh;
- notification reception;
- notification tap handling;
- deep-link routing;
- local notification presentation where applicable;
- unread/notification-center synchronization.

The mobile client must never assume that a notification itself grants access to its target resource.

## 60. Web Implementation Boundary

The web application may provide:

- notification center;
- unread indicator;
- browser push where explicitly enabled;
- notification preferences;
- deep-link navigation.

Web notification permission is separate from application authorization.

## 61. Browser Push

If browser push is implemented:

- use the approved web push/provider architecture;
- bind subscriptions to authenticated users;
- expire invalid subscriptions;
- keep browser tokens/subscriptions server-side;
- avoid sensitive payloads;
- apply the same preference and authorization rules as mobile push.

## 62. Notification Security Invariants

1. Notification delivery never grants authorization.
2. Push tokens are never authentication credentials.
3. Provider delivery is never the source of truth for notification existence.
4. Read state is controlled by KHOJ BHET.
5. Transactional and promotional communications are separated.
6. User preferences are enforced server-side.
7. Security notifications cannot be disabled through ordinary promotional settings.
8. Notification payloads contain only necessary information.
9. Exact location and protected contact information are never unnecessarily pushed.
10. Deep links never contain secrets.
11. Provider credentials never reach clients.
12. Notification retries are idempotent.
13. Provider failure never corrupts the underlying business transaction.
14. Search/listing notifications respect current visibility rules.
15. Private resources are notified only to authorized recipients.
16. Background jobs revalidate sensitive state.
17. Client notification state never overrides server authority.

## 63. Cross-Document Contracts

| Document | Notification Contract |
| --- | --- |
| 08 Product & Business Rules | Defines notification-triggering business events and communication rules |
| 09 Software Architecture | Defines event/service boundaries |
| 10 Technology Stack | Defines FCM and channel/provider technology |
| 12 Engineering Standards | Defines implementation, queue, and testing standards |
| 13 Database Architecture & Data Model | Defines notification, device-token, preference, and outbox persistence |
| 14 API Specification | Defines notification APIs, errors, pagination, and enums |
| 15 Frontend Architecture | Defines web notification UI and browser-push behavior |
| 16 Backend Architecture | Defines event, queue, worker, and Notification Service implementation |
| 17 Mobile Application Architecture | Defines push-token, receipt, tap, and deep-link behavior |
| 18 Authentication & Authorization | Defines recipient identity and authorization |
| 19 Security Architecture | Defines notification security and privacy controls |
| 20 Media & File Storage | Defines media references used in notifications |
| 21 Search Architecture | Defines saved-search and visibility interaction |
| 22 Notification System | Defines end-to-end notification architecture |

## 64. Implementation Rules

1. Use a provider-agnostic Notification Service.
2. Store authoritative notification records in MySQL.
3. Use FCM through an adapter for V1 mobile push.
4. Keep device-token registration separate from authentication.
5. Generate notifications from authoritative domain events.
6. Use asynchronous queues for delivery.
7. Use an outbox pattern for high-value transactional events where required.
8. Make notification creation and delivery idempotent.
9. Use bounded exponential retry with jitter.
10. Separate transactional, operational, and promotional communication.
11. Enforce preferences server-side.
12. Keep sensitive payloads minimal.
13. Use deep links only as navigation instructions.
14. Revalidate authorization when notifications reference private resources.
15. Keep provider credentials server-side.
16. Handle invalid device tokens automatically.
17. Keep campaign traffic separate from critical notifications.
18. Keep web and mobile semantics consistent.
19. Add provider-failure and duplicate-delivery tests.
20. Record material notification architecture changes through an ADR.

## 65. Acceptance Checklist

- [ ]  Notification Service abstraction exists.
- [ ]  MySQL is authoritative for notification records.
- [ ]  In-app notifications are persistent.
- [ ]  FCM adapter exists for V1 push.
- [ ]  Device tokens are user-scoped.
- [ ]  Push tokens never grant authentication.
- [ ]  Canonical notification types are defined.
- [ ]  Transactional and promotional notifications are separated.
- [ ]  Notification preferences are server-enforced.
- [ ]  Quiet-hour behavior is defined.
- [ ]  Templates are versioned and localized.
- [ ]  Nepali and English notification content is supported.
- [ ]  Sensitive payload data is minimized.
- [ ]  Deep links contain no secrets.
- [ ]  Domain events trigger notification decisions.
- [ ]  High-value events use reliable event publication/outbox where required.
- [ ]  Queue workers process delivery asynchronously.
- [ ]  Retry/backoff is bounded.
- [ ]  Delivery is idempotent.
- [ ]  Duplicate notifications are controlled.
- [ ]  Delivery states are tracked.
- [ ]  Read/unread state is authoritative.
- [ ]  Channel fan-out is supported.
- [ ]  Provider adapters isolate external services.
- [ ]  Invalid device tokens are deactivated.
- [ ]  SMS/OTP handling remains under authentication rules.
- [ ]  Search-triggered notifications respect current visibility.
- [ ]  Rate limits and anti-spam controls exist.
- [ ]  Scheduled notifications revalidate eligibility.
- [ ]  Observability and alerts exist.
- [ ]  Dead-letter handling exists.
- [ ]  Retention policy is defined.
- [ ]  Notification APIs match Document 14.
- [ ]  Security regression tests exist.
- [ ]  Provider replacement does not require business-logic rewrites.

## 66. Status

**Active — Notification System Baseline**

This document is the authoritative architectural baseline for KHOJ BHET notifications. Implementation details may evolve, but provider abstraction, MySQL authority, authorization boundaries, preference enforcement, event-driven generation, idempotency, privacy, and notification security invariants must remain intact unless changed through the appropriate architecture or ADR process.

## Authentication OTP Boundary Clarification — 2026-10-18

Marketplace sign-in and recovery OTP delivery and verification belong exclusively to Firebase Authentication under ADR-002. The Notification System's SMS adapter may send approved transactional/application SMS only; it must not send or verify marketplace authentication OTPs or create a second OTP-verification path. Any older generic references to “SMS/OTP notifications” must be interpreted subject to this boundary.

## V1 Monetization Boundary — Notification Events (2026-10-18)

Paid subscriptions, paid entitlement activation/expiry and payment-to-entitlement automation are deferred beyond the Marketplace MVP under Documents 02 and 08. Do not treat subscription-expiring, paid-plan renewal, payment-submitted-for-plan, or entitlement-upgrade events as required MVP notification types. Account, security, listing moderation/lifecycle and in-app contact notifications remain in scope only where their corresponding V1 feature is approved. If monetization is approved in a later phase, add its event types and templates through the notification change-control process.

## TV-08 V1 Notification Policy — 2026-10-18

Supported notification locales are Nepali (`ne-NP`) and English (`en`). Use a validated persisted user preference when available; otherwise use configured `ne-NP` default. Do not infer template language from an unrelated request's `Accept-Language`; keep locale stable across retries. Current schema has no `expires_at`, so V1 must not invent automatic expiry. Templates may remain versioned code/config. Map `notification_type` to a version-controlled classification policy. The current schema has no unique notification deduplication key: before production generation, approve durable per-recipient event deduplication linked to stable outbox identity, or prove an equivalent atomic design. Status remains BLOCKED pending this decision and runtime tests.