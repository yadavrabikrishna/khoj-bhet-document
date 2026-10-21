# 16. Backend Architecture

> ## ORM, Module and Contract Baseline Addendum — 2026-10-09
> 

> **Module structure:** follow Document 09's module-first organization. Each bounded module owns its application/domain/infrastructure/API layers; shared code is limited to stable cross-cutting abstractions. The transactional outbox is mandatory for durable post-commit events: write the outbox_events row in the same MySQL transaction as the business mutation, then relay/retry with idempotent consumers.
> 

> 
> 

> **Contract strategy:** contract-first OpenAPI 3.1 is the approved API strategy. The final artifact remains blocked until the Document 13 schema artifacts are regenerated and clean-MySQL runtime validation passes.
> 

> 
> 

> **Eloquent identifiers:** physical entities retain BIGINT internal primary keys where defined and separate unique CHAR(26) public_id identifiers. Generate public_id explicitly or with a verified custom trait; do not let a ULID trait silently change the internal primary-key type or incrementing behavior. External route binding must resolve public_id where the API exposes public IDs. Add model tests for creation, route binding, uniqueness and serialization before implementation sign-off.
> 

> 
> 

> **V1 concurrency/idempotency:** If-Match remains optional; a supplied stale ETag is rejected, while omission follows documented last-write-wins behavior. MySQL api_idempotency_keys is authoritative; Redis is only a lock/cache accelerator. V1 payment is manual submission/admin review only; gateway callbacks and webhooks are future-phase work.
> 

> **Implementation status clarification — 2026-10-09:** “Active” means this is the current architecture design baseline, not that implementation is release-ready. Implementation remains gated by Document 14's regenerated OpenAPI 3.1 contract and successful clean-MySQL runtime validation.
> 

Document ID: KB-TECH-016

Status: Active — Backend Architecture Baseline

Version: 1.0

Owner: KHOJ BHET Engineering

Last Reviewed: 2026-10-04

Parent: 02. TECHNICAL DEFINITION

Previous: 15. Frontend Architecture

Next: 17. Mobile Application Architecture

Related: 08. Product & Business Rules, 09. Software Architecture, 10. Technology Stack, 12. Engineering Standards, 13. Database Architecture & Data Model, 14. API Specification, 15. Frontend Architecture, 18. Authentication & Authorization, 19. Security Architecture, 20. Media & File Storage, 21. Search Architecture, 22. Notification System, 23. SEO Architecture

# 1. Document Purpose

This document defines the production backend architecture for KHOJ BHET.

The backend is the authoritative application and domain boundary between clients and persistent infrastructure. It implements the approved business rules, API contract, authorization, validation, listing lifecycle, catalogue rules, entitlement enforcement, persistence, media workflows, messaging, notifications, reporting, payments, and operational safeguards.

The backend must implement Document 14. API Specification rather than inventing a second API contract.

Core rule: clients request actions; the backend decides whether those actions are valid and performs them atomically according to the domain rules.

# 2. Architectural Baseline

KHOJ BHET uses a Laravel modular-monolith architecture.

Web / Mobile Clients

→ Laravel REST API /api/v1

→ Authentication + Authorization

→ Application Services / Use Cases

→ Domain Rules

→ Repositories / Query Services

→ MySQL

→ Redis / Queue Workers

→ External Provider Adapters

The modular monolith is the V1 boundary. Microservices are not required.

# 3. Technology Baseline

| Area | Baseline |
| --- | --- |
| Framework | Laravel 13 |
| Language | PHP 8.5.x (pinned to Document 10) |
| API | REST / JSON, /api/v1 |
| Database | MySQL 9.7.x LTS-compatible baseline (pinned to Documents 10 and 13) |
| Cache / Queue | Redis |
| Authentication | Firebase Authentication token verification |
| Admin | FilamentPHP 5 |
| Web client | Next.js |
| Mobile client | React Native + Expo |
| Search V1 | MySQL |
| Media | Provider abstraction |
| Realtime | Optional secondary transport; MySQL remains authoritative |
| Payments | Provider adapters |
| Notifications | FCM/SMS/provider adapters |
| API contract | OpenAPI 3.1 |

Exact versions are controlled by lockfiles and deployment manifests.

# 4. Core Backend Principles

BE-PR-001 — API authority: all marketplace business operations pass through the backend.

BE-PR-002 — Domain authority: business rules are implemented server-side.

BE-PR-003 — Contract first: implementation follows Document 14 and OpenAPI 3.1.

BE-PR-004 — Modular monolith: bounded feature modules inside one Laravel application.

BE-PR-005 — Transactional integrity: related writes occur in explicit database transactions.

BE-PR-006 — Least privilege: authorization is checked at the resource/action boundary.

BE-PR-007 — Provider isolation: external services are accessed through adapters.

BE-PR-008 — Idempotent writes: retry-sensitive operations use documented idempotency semantics.

BE-PR-009 — Observable operations: important operations carry request/correlation context.

BE-PR-010 — Database authority: MySQL is the primary V1 source of truth.

# 5. Module Boundaries

Recommended modules:

1. Identity & Accounts
2. Users / Profiles
3. Catalogue
4. Locations
5. Listings
6. Listing Attributes
7. Media
8. Search
9. Favorites
10. Conversations
11. Messages
12. Notifications
13. Reports / Moderation
14. Subscriptions / Entitlements
15. Payments
16. Admin / Operations
17. SEO / Public Content
18. Audit / Observability

Modules communicate through explicit application services, domain objects, events, or well-defined query interfaces.

Avoid uncontrolled cross-module model manipulation.

# 6. Request Lifecycle

HTTP Request

→ Middleware

→ Authentication

→ Request ID / Correlation

→ Rate Limiting

→ Controller

→ Form Request / DTO

→ Application Service

→ Domain Rules / Policies

→ Repository / Query Service

→ Transaction

→ Persistence

→ Domain/Event dispatch

→ API Resource

→ JSON Response

Controllers remain thin.

# 7. Controller Responsibilities

Controllers should:

- receive HTTP requests;
- invoke validation;
- authorize;
- call an application service/query;
- return an API Resource/response.

Controllers must not contain:

- complex pricing rules;
- listing lifecycle logic;
- catalogue applicability rules;
- payment verification logic;
- multi-step persistence;
- provider-specific implementation.

# 8. Form Requests and DTOs

Use Form Requests for HTTP-level validation.

Use DTOs/command objects for application-layer input where useful.

Validation is divided into:

- transport validation;
- domain validation;
- persistence constraints.

The backend must revalidate all values received from clients.

# 9. Application Services / Use Cases

Application services represent meaningful actions.

Examples:

- CreateListing
- UpdateListing
- SubmitListing
- PublishListing
- PauseListing
- ResumeListing
- RenewListing
- ArchiveListing
- DeleteListing (authorized DELETE/moderation workflow; not a client-assignable lifecycle state)
- FavoriteListing
- UnfavoriteListing
- StartConversation
- SendMessage
- MarkNotificationRead
- CreateReport
- StartSubscription
- InitiatePayment
- RequestAccountDeletion
- ReactivateAccount

Services orchestrate domain behavior; they should not become giant generic service classes.

# 10. Domain Rules

Domain rules determine:

- who may perform an action;
- whether listing state permits an action;
- category/attribute applicability;
- required attributes;
- allowed values;
- listing type;
- ownership/member authority;
- entitlement;
- location visibility;
- payment state;
- report permissions.

These rules must not be implemented only in controllers or frontend code.

# 11. Authorization

Use policy/action authorization.

Authorization sequence:

Authenticated identity

→ User/account state

→ Resource relationship

→ Role/membership

→ Entitlement

→ Action policy

→ Domain rule

The frontend may hide controls, but the backend must always enforce the operation.

# 12. Identity and Firebase

Firebase Authentication is the user authentication provider.

Backend flow:

1. Receive Firebase ID token.
2. Verify token using Firebase Admin/server-side credentials.
3. Resolve Firebase UID.
4. Resolve local user/account.
5. Evaluate account state.
6. Establish authenticated application context.

Firebase Admin credentials never enter frontend or mobile bundles.

# 13. Local User Record

Firebase identity and local marketplace user identity are separate concerns.

Local users hold marketplace-specific:

- profile;
- account state;
- preferences;
- roles/memberships;
- subscription/entitlement references;
- audit references.

Firebase UID is an external identity key, not a substitute for internal domain identity.

# 14. Roles and Memberships

The backend supports the approved ownership/business-member/admin model.

For business-owned listings:

- owner remains authoritative according to business rules;
- permitted business members can perform approved operations;
- admin has elevated moderation/operational authority.

Membership must be checked server-side on every protected action.

# 15. Catalogue Architecture

Catalogue is authoritative for:

- categories;
- subcategories;
- attribute definitions;
- applicability;
- option definitions;
- units;
- validation behavior;
- filter/search flags;
- public display metadata.

Do not duplicate the catalogue as independent hard-coded backend arrays.

Seed data and database registries are the authoritative operational representation.

# 16. Dynamic Attribute Validation

Listing submission:

1. Resolve category/subcategory.
2. Load applicable attribute definitions.
3. Validate attribute keys.
4. Validate data types.
5. Validate required fields.
6. Validate allowed options.
7. Validate multi-value behavior.
8. Validate numeric ranges/units where defined.
9. Reject unknown/inapplicable attributes.
10. Persist normalized values.

The API must reject client-created attributes not present in the authoritative catalogue.

# 17. Listing Aggregate

A listing is treated as a domain aggregate composed of:

- identity;
- ownership;
- category;
- listing type;
- attributes;
- price;
- location;
- media;
- lifecycle;
- visibility;
- timestamps.

Cross-resource operations should use explicit application services. Critical state changes must write an `outbox_events` record in the same MySQL transaction as the business mutation. A relay worker publishes committed outbox events to queue consumers (search projection, notifications, media processing, and other durable side effects), with retries, idempotent consumers, observability, and safe replay. Dispatch-after-commit alone is not a substitute for the transactional outbox because a process can fail after commit and before dispatch.

Eloquent models use the database primary key as the internal BIGINT identity and `public_id` ULID as the external route key. Configure route binding explicitly (for example, `getRouteKeyName()` returning `public_id`); do not assume Laravel's `HasUlids` automatically changes a separate `public_id` column while the primary key remains BIGINT. Add model-level tests for ULID generation, uniqueness, binding, and serialization.

# 18. Listing Lifecycle

The backend owns lifecycle transitions.

Conceptual transitions:

draft → review → published

published → paused

paused → published

published → expired

expired → renewed/published where allowed

draft/review → archived where permitted

published → archived only through an explicitly authorized domain action; deletion/removal follows the separate API DELETE/moderation contract and is not a public lifecycle enum

The exact public enum values and transitions follow Document 14 and final enum registry.

Invalid transitions return documented API errors.

# 19. Listing Creation Transaction

Creation should validate and persist all required core data consistently.

Typical transaction:

- create listing;
- persist category/listing type;
- validate/persist attributes;
- persist location;
- persist media references;
- write audit information;
- commit.

External side effects should be dispatched after successful commit where possible.

# 20. Database Architecture

MySQL is the V1 authoritative database.

The backend uses:

- Eloquent for ordinary persistence;
- query builders/raw SQL only where justified;
- repositories/query services where useful;
- database transactions;
- foreign keys;
- unique constraints;
- indexes;
- check constraints where supported/appropriate.

The generated migration/schema artifacts from the database gate are authoritative.

# 21. Transactions

Use transactions for multi-record domain mutations.

Examples:

- listing creation;
- listing lifecycle change;
- favorite creation/removal where multiple records/events are involved;
- subscription state change;
- payment state update;
- account deletion request;
- business membership changes.

Do not wrap long external network operations unnecessarily inside database transactions.

# 22. Concurrency

For concurrent mutations:

- use database row locking where necessary;
- use version/ETag semantics;
- reject stale If-Match values;
- return conflict responses;
- when `If-Match` is supplied, reject stale values. In V1 the header is optional: if omitted, the documented last-write-wins behavior applies. The client must not claim conflict detection for a mutation that omitted `If-Match`.

# 23. Idempotency

Document 14 defines idempotency requirements.

For supported unsafe operations:

- accept Idempotency-Key;
- scope key appropriately;
- persist the authoritative key, request hash, and result/status in MySQL `api_idempotency_keys`;
- Redis may be used only as a lock/cache accelerator, never as the authoritative idempotency record;
- return the same logical result for retries;
- reject key reuse for a different request payload.

Particularly important for payments and externally visible creation operations.

# 24. API Response Architecture

API responses use stable resource representations.

Use:

- API Resources / serializers;
- consistent error envelope;
- pagination representation;
- metadata where defined;
- request/correlation ID.

Never expose Eloquent models directly as uncontrolled JSON.

# 25. API Error Architecture

Errors must map to documented API semantics.

Categories include:

- validation;
- authentication;
- authorization;
- not found;
- conflict;
- rate limited;
- business rule violation;
- dependency/provider failure;
- internal error.

Internal exceptions are logged; clients receive safe documented responses.

# 26. OpenAPI Contract

Document 14 and its final OpenAPI 3.1 contract are the external API authority.

Required workflow:

OpenAPI

→ generated/requested contract types

→ Laravel route/controller/resource implementation

→ contract tests.

Undocumented endpoints must not be added casually.

# 27. API Versioning

V1 base:

/api/v1

Breaking changes require a deliberate versioning strategy and migration plan.

Non-breaking additions should follow compatibility rules.

Deprecated fields/endpoints must follow the contract's deprecation/sunset metadata.

# 28. Search Architecture

V1:

Laravel Search Application Service

→ MySQL query/index strategy.

Search must remain behind an abstraction so a future search engine can replace MySQL without changing clients.

Do not introduce Meilisearch/OpenSearch as a V1 dependency unless approved by an ADR.

# 29. Location Architecture

Canonical hierarchy:

Country → Province → District → Municipality → Ward → Locality/Tole → Chowk/Landmark.

Location data must support:

- human-readable addresses;
- postal code;
- optional coordinates;
- approximate location;
- exact location;
- privacy/entitlement-aware presentation.

The backend decides what representation a caller may receive.

# 30. Exact Location Protection

Exact coordinates/address information is protected domain data.

The backend must:

1. identify requester;
2. evaluate ownership/role;
3. evaluate entitlement;
4. determine allowed precision;
5. return only the permitted representation.

Do not rely on frontend masking.

# 31. Media Architecture

Media uses a provider abstraction, with local application/server storage and direct multipart uploads through Laravel for V1 (Document 14 AD-API-03 / ADR-005). Backend responsibilities include validating file signature and detected MIME, authorizing actor and target, enforcing the approved count/byte/duration limits, persisting media records, tracking processing, validating ownership, managing ordering/primary media, and exposing approved derivatives. Do not implement upload-intent/complete endpoints or direct-to-provider upload for V1 unless Document 14 is formally amended. V1 supports up to 20 images (JPEG/PNG/WebP, 10 MB each) and at most one MP4 H.264/AAC listing video (50 MB, 60 seconds), processed asynchronously with poster/playback output and byte-range delivery.

# 32. Media Lifecycle

V1 lifecycle: multipart request accepted → uploaded/recorded → validating/processing → ready or failed; only ready and approved media may be exposed. A separate initiated/upload-intent state is future-only and must not be represented as an active V1 API flow. Deletion/replacement must validate ownership and listing state. Orphan cleanup should be handled asynchronously through the queue/outbox workflow.

# 33. Favorites

Favorite mutation:

- authenticate;
- authorize;
- validate listing visibility;
- enforce uniqueness;
- persist;
- return authoritative state.

Unique database constraint prevents duplicates.

# 34. Messaging

MySQL is authoritative for:

- conversations;
- participants;
- messages;
- message state.

Optional realtime technology may project/update client experience but must not become an ungoverned second source of truth.

Conversation authorization is checked for every message operation.

# 35. Notifications

Notification creation should occur through backend services/events.

Channels may include:

- in-app;
- FCM;
- SMS;
- future WhatsApp Business API.

Notification delivery failure must not invalidate the underlying business transaction unless the business rule explicitly requires it.

# 36. Event Architecture

Use domain/application events for decoupled side effects.

Examples:

ListingPublished

ListingExpired

FavoriteCreated

MessageSent

PaymentSucceeded

SubscriptionActivated

ReportCreated

Events should contain stable identifiers and required metadata, not unnecessarily large domain objects.

# 37. Queue Architecture

Use Redis-backed queues for:

- notifications;
- media processing;
- cleanup;
- search/index refresh;
- provider retries;
- non-critical post-commit work;
- analytics/telemetry where appropriate.

Queue jobs must be idempotent where retries are possible.

# 38. Payment Architecture

**V1 payment processing is manual-submission and admin-review only.** The client creates a payment intent, submits `manual-submission` with the payment reference and required proof media, and the backend places it into pending review. An authorized admin records the decision and audit reason; only the approved server-side transition may update subscription/entitlement state.

V1 flow:

Client

→ Laravel payment-intent API

→ Manual submission + proof media/reference

→ MySQL transaction + audit record

→ Admin review in Filament

→ Approved/rejected payment state

→ Entitlement update only after approval

Automated eSewa/Khalti/connectIPS/Fonepay/card redirects, provider callbacks, webhooks, and automated reconciliation are deferred. Keep provider adapters as future extension points, but do not ship gateway initiation/callback routes as active V1 behavior.

→ Notification

Never trust a client success redirect as proof of payment.

Provider callbacks/webhooks require signature/authentication verification and replay protection where supported.

# 39. Subscription and Entitlement

Separate:

- subscription record;
- payment transaction;
- entitlement state.

Entitlement is the backend authorization decision for premium capabilities.

Payment success and entitlement activation are related but not identical concepts.

# 40. Reports and Moderation

Reports are authoritative backend records.

Backend validates:

- reporter;
- target type;
- target existence;
- duplicate/report constraints;
- allowed reasons;
- lifecycle/status.

Moderation actions require appropriate admin/authorized permissions and auditability.

# 41. Audit Logging

Audit significant security/domain events:

- authentication/account changes;
- listing lifecycle;
- ownership/membership changes;
- moderation;
- subscription/payment state;
- entitlement changes;
- sensitive access;
- deletion/reactivation.

Audit logs must avoid unnecessary sensitive payloads.

# 42. Account Deletion and Reactivation

Account deletion is a controlled workflow.

Backend must:

- validate requester;
- record request/state;
- enforce retention requirements;
- protect required audit/payment records;
- revoke appropriate access;
- process asynchronous cleanup where necessary;
- support approved reactivation semantics.

Never hard-delete records simply because a frontend requests deletion.

# 43. Caching

Redis caching is an optimization.

Suitable:

- stable catalogue data;
- location reference data;
- selected public resources;
- rate limiting;
- Redis may provide locks or short-lived acceleration only; `api_idempotency_keys` in MySQL is authoritative.

Do not cache authorization-sensitive representations globally.

Cache invalidation must follow domain changes.

# 44. Rate Limiting

Rate-limit by endpoint/risk class.

Higher protection for:

- authentication;
- OTP-related flows where applicable;
- listing creation;
- messaging;
- reports;
- payment initiation;
- media operations;
- search abuse patterns.

Return documented rate-limit metadata and Retry-After where appropriate.

# 45. Security Architecture Boundary

Backend security includes:

- token verification;
- authorization;
- validation;
- input normalization;
- SQL parameterization;
- mass-assignment protection;
- CSRF considerations where applicable;
- secure headers through deployment;
- secret management;
- encryption in transit;
- sensitive logging controls;
- webhook verification;
- abuse prevention.

Detailed security controls belong to Document 19.

# 46. SEO Backend Responsibilities

The backend must support the SEO architecture rather than treating SEO as only a Next.js concern.

The backend/public API should provide authoritative data needed for:

- canonical listing URL;
- indexability state;
- listing lifecycle;
- public title/description;
- public category/location metadata;
- structured-data source fields;
- published/expired/deletion behavior, keeping internal removal/deletion distinct from the public lifecycle enum;
- sitemap eligibility;
- robots policy inputs.

The frontend renders these values into HTML/metadata.

# 47. Robots.txt Integration

Robots policy is a cross-layer concern.

The backend must expose/maintain the authoritative rules or configuration required by the public web application.

Recommended architecture:

Next.js /robots.txt

→ approved SEO configuration/service

→ backend/public configuration where dynamic policy is required.

Rules must prevent crawling of:

- authenticated/account routes;
- admin routes;
- internal API routes;
- private user resources;
- query combinations that create uncontrolled crawl spaces.

Robots.txt is NOT an authorization mechanism and must never be used to protect private data.

# 48. Sitemap Integration

The backend provides sitemap-eligible public resource information.

Sitemap architecture may be:

Next.js sitemap generation

→ paginated public API queries

→ canonical listing/category/location URLs.

Only indexable resources should enter sitemaps.

Removed/private/restricted resources must not remain indefinitely in sitemap output.

# 49. llms.txt / AI Crawler Integration

KHOJ BHET will support an explicit machine-readable public-information policy.

Recommended public endpoints/files:

- /llms.txt
- optionally /llms-full.txt when the content strategy justifies it.

The backend/public-content layer supplies the authoritative public site sections, descriptions, documentation links, and policy references consumed by these files.

Important distinction:

- llms.txt is a discoverability/documentation convention.
- robots.txt controls crawler access policy.
- neither is an authorization boundary.
- private listing data, exact restricted locations, contact details, messages, account data, and admin content must never be exposed merely because a crawler requests a URL.

AI crawler policy must remain consistent with privacy, robots, canonical URL, and public-content rules.

# 50. AI/LLM Metadata Boundary

Public content may include:

- site description;
- category descriptions;
- public listing summaries;
- public location descriptions;
- documentation/policy pages.

Do not publish:

- private user information;
- exact restricted location;
- contact details protected by entitlement;
- private messages;
- internal moderation notes;
- payment information.

# 51. SEO Metadata API Fields

Where appropriate, public resources should expose normalized metadata:

- canonical URL;
- title;
- description;
- robots/indexability state;
- published timestamp;
- updated timestamp;
- primary image;
- category;
- location;
- public structured-data attributes.

The frontend decides how these fields are rendered according to the SEO document.

# 52. Structured Data

The backend provides trustworthy source values for:

- Product/Offer-like listing structured data where applicable;
- BreadcrumbList;
- Organization;
- WebSite;
- other approved schema types.

The frontend owns final JSON-LD rendering.

Never generate structured data from untrusted hidden/client-only fields.

# 53. Public vs Private API Representation

API resources must deliberately separate:

- public listing representation;
- owner/member representation;
- premium/entitled representation;
- admin representation.

Do not return a superset resource and rely on frontend hiding.

# 54. ETag / Conditional Requests

For resources supporting conditional requests:

- generate stable ETags;
- honor If-None-Match for reads;
- honor If-Match for supported writes;
- return documented 304/412 behavior.

ETag strategy must not leak sensitive information.

# 55. Request Correlation

Every significant API request should have a request/correlation ID.

Backend:

- accept valid client request ID where policy allows;
- otherwise generate one;
- include it in responses;
- include it in logs.

This ID must not be used as an authorization credential.

# 56. Logging

Logs should support:

- request ID;
- route/action;
- status;
- latency;
- authenticated user ID where appropriate;
- provider outcome;
- error class.

Never log:

- passwords;
- Firebase private credentials;
- access tokens;
- payment secrets;
- private message bodies unless explicitly approved;
- unnecessary personal data.

# 57. Observability

Measure:

- request latency;
- error rate;
- database latency;
- queue failures;
- provider failures;
- payment callback failures;
- media processing;
- search latency;
- authentication failures;
- rate-limit activity.

Health checks should distinguish application health from dependency health.

# 58. Scheduled Jobs

Scheduled backend tasks may include:

- listing expiry;
- renewal reminders;
- notification cleanup;
- media orphan cleanup;
- stale payment reconciliation;
- subscription reconciliation;
- sitemap/public-index refresh;
- audit/retention processing.

Jobs must be safe to rerun.

# 59. Provider Adapter Pattern

External services must be hidden behind interfaces/adapters.

Examples:

- PaymentProvider;
- SmsProvider;
- PushProvider;
- MediaStorageProvider;
- GeocodingProvider;
- Map/Tile provider;
- optional RealtimeProvider.

Application services should not contain provider-specific SDK calls.

# 60. Testing Architecture

Unit:

- domain rules;
- policies;
- validators;
- attribute rules;
- price/unit logic;
- lifecycle transitions.

Feature/API:

- endpoints;
- auth;
- authorization;
- validation;
- transactions;
- resource representations.

Integration:

- MySQL;
- Redis;
- Firebase token verification;
- provider adapters;
- queues.

Contract:

- OpenAPI 3.1 compatibility.

E2E:

- web/mobile critical journeys against realistic backend behavior.

# 61. Database Runtime Validation

Before implementation is considered stable:

- clean MySQL schema must migrate successfully;
- foreign keys must succeed;
- unique constraints must behave as designed;
- seed catalogue must load;
- option/unit registries must validate;
- validation SQL must pass;
- representative listing lifecycle operations must execute;
- API integration must run against the clean schema.

This gate precedes final production API implementation.

# 62. CI/CD Backend Gate

Minimum:

1. composer install;
2. static analysis;
3. code style;
4. unit tests;
5. feature/API tests;
6. migration test;
7. seed/fixture validation;
8. OpenAPI contract validation;
9. security/dependency scan;
10. queue/job tests;
11. production build/config validation.

# 63. Deployment Topology

Recommended V1:

Internet

→ TLS / Reverse Proxy

→ Next.js Web

→ Laravel API

→ MySQL

→ Redis

→ Queue Workers / Scheduler

Admin:

Authorized Admin

→ FilamentPHP

→ Laravel Application

External providers:

Laravel Adapter Layer

→ Firebase / Payments / SMS / FCM / Media / Geocoding

# 64. Admin Architecture

FilamentPHP is an administrative interface over the same authoritative Laravel domain.

Admin UI must use policies and application/domain rules rather than bypassing them.

Admin-only capabilities:

- moderation;
- catalogue administration;
- user/account operations;
- business membership;
- reports;
- subscriptions/payment reconciliation;
- operational settings;
- audit inspection.

Admin routes and resources are never part of the public API.

# 65. Backend Module Structure

Follow the module-first structure defined in Document 09: each bounded module owns its application, domain, infrastructure, and presentation/API layers. Avoid a single shared layer-first Application/Services area that creates cross-module coupling. Shared code is limited to small, stable cross-cutting abstractions with explicit ownership.

Example conceptual structure:

app/

├── Modules/

│   ├── Identity/

│   │   ├── Application/

│   │   ├── Domain/

│   │   ├── Infrastructure/

│   │   └── Presentation/

│   ├── Catalogue/

│   ├── Locations/

│   ├── Listings/

│   ├── Businesses/ (business profiles and member permissions)

│   ├── Verification/

│   ├── Media/

│   ├── Search/

│   ├── Favorites/

│   ├── Messaging/ (conversation read cursor and message state)

│   ├── ContactReveal/

│   ├── UserSafety/ (blocking and reports)

│   ├── Notifications/ (preferences and read state)

│   ├── AccountLifecycle/ (deactivate/reactivate/delete/cancel deletion)

│   ├── Reports/

│   ├── Subscriptions/

│   ├── Payments/

│   └── Audit/

├── Shared/

└── Providers/

Exact Laravel physical structure may evolve without changing module boundaries.

# 66. Anti-Patterns

Do not:

- place domain logic in controllers;
- expose Eloquent models directly;
- call external SDKs from controllers;
- query MySQL from frontend;
- create generic BaseService abstractions without purpose;
- duplicate catalogue definitions;
- use Firestore as V1 business authority;
- trust payment redirects;
- use robots.txt for security;
- publish private data through llms.txt;
- use frontend entitlement flags as authorization;
- perform non-idempotent retries blindly;
- create microservices prematurely.

# 67. Traceability Examples

Create Listing:

Use Case → API → Controller → Request/DTO → CreateListing Service → Catalogue Validation → Listing Domain Rules → Transaction → MySQL → Resource.

Protected Contact:

Request → Auth → Policy → Entitlement → Public/Entitled Resource → Response.

Payment V1:

Request → Auth → Idempotency → Payment Intent → Manual Submission + Proof Media → Admin Review/Audit → Transaction → Entitlement only after approval → Outbox Event → Notification.

Future gateway callbacks/webhooks are deferred and must not be implemented as active V1 flows.

SEO:

Listing State → Public Resource → Canonical/Indexability Metadata → Next.js Metadata/Sitemap/JSON-LD.

AI crawler:

Public Content Registry → llms.txt generation → public web root.

# 68. Definition of Done

Backend feature is complete only when:

- business rule identified;
- API contract updated if necessary;
- authorization implemented;
- validation implemented;
- transaction/concurrency requirements handled;
- persistence constraints correct;
- provider calls abstracted;
- errors documented;
- logging/observability appropriate;
- tests added;
- OpenAPI contract aligned;
- security reviewed;
- SEO/privacy implications considered for public resources.

# 69. Recommended Implementation Order

1. Clean MySQL runtime validation.
2. Laravel 13 bootstrap.
3. Authentication/token verification.
4. Base API infrastructure and error model.
5. Catalogue.
6. Locations.
7. Listings and dynamic attributes.
8. Listing lifecycle.
9. Media.
10. Search.
11. Favorites.
12. Conversations/messages.
13. Notifications.
14. Reports/moderation.
15. Subscriptions/entitlements.
16. Payments.
17. Account lifecycle.
18. SEO/public-content services.
19. Admin/Filament integration.
20. Observability/hardening.
21. Contract/E2E validation.
22. Production readiness.

# 70. Final Architectural Baseline

Laravel 13 module-first modular monolith

- 

PHP 8.5.x (pinned by Document 10)

- 

REST API /api/v1; contract-first OpenAPI 3.1

- 

Firebase Authentication Bearer-token verification for marketplace users

- 

Separate Laravel/Filament admin guard with required MFA

- 

Bounded modules, each owning application/domain/infrastructure/presentation layers

- 

MySQL 9.7.x LTS-compatible baseline (pinned by Documents 10 and 13)

- 

Transactional business writes + outbox_events in the same transaction

- 

Redis cache/queue/locks; never authoritative for business data or idempotency

- 

MySQL api_idempotency_keys as the durable idempotency authority

- 

Manual payment submission + admin review for V1; gateway adapters deferred

- 

FilamentPHP 5

↓

Next.js Web + React Native/Expo Mobile

SEO integration is explicitly cross-layer:

Backend authoritative public-resource metadata

→ Next.js canonical/metadata/robots/sitemap rendering

→ public llms.txt / optional llms-full.txt generation

→ search-engine and AI-crawler discoverability

without exposing private or entitlement-protected data.

# 71. Document Control

Document: 16. Backend Architecture

Document ID: KB-TECH-016

Status: Active — Backend Architecture Baseline

Version: 1.0

Owner: KHOJ BHET Engineering

Last Reviewed: 2026-10-04

Previous: 15. Frontend Architecture

Next: 17. Mobile Application Architecture

Architecture conclusion: The backend is the authoritative modular-monolith domain/API boundary. It implements the approved OpenAPI contract, database model, business rules, authorization, lifecycle, entitlement, provider integrations, and public-content/SEO support. Runtime implementation should proceed only after the clean-MySQL validation gate and final API contract audit are satisfied.