# ADR-007 — Notification Architecture

# ADR Metadata

- **ADR ID:** ADR-007
- **Status:** Accepted
- **Date:** 2026-09-20
- **Decision Owner:** KHOJ BHET Project Team
- **Area:** Notifications
- **Related ADRs:** ADR-002, ADR-006
- **Implementation Status:** Not started

# 1. Context

KHOJ BHET may need notifications for new messages, listing approval/rejection, listing expiry, favorites, saved-search matches, subscriptions, payments, security alerts, and administrative actions.

Potential channels include web, Android push, email, SMS, and other future channels.

# 2. Decision Drivers

- Reliability
- Delivery speed
- User preferences
- Cost
- Provider dependency
- Retry handling
- Queueing
- Rate limiting
- Transactional vs promotional messaging
- Auditability
- Mobile/web support

# 3. Alternatives

## Direct Channel Delivery

Business code sends notifications directly through each provider.

## Central Notification Module

Application events become notification jobs and are routed to one or more channels through a central module.

## External Notification Platform

A third-party platform manages delivery orchestration.

# 4. Decision

**Accepted decision:** KHOJ BHET will use a **central notification module** that separates notification events from delivery channels and provider adapters:

`Business Event → Notification Event → User Preferences → Channel Delivery → Provider Adapter`

The supported channel architecture covers **in-app, push, email, SMS, and WhatsApp**. Not every channel must be enabled for every event or every user.

- **Push:** Firebase Cloud Messaging (FCM) is the initial push provider.
- **SMS:** a separate SMS-provider adapter may be used for approved transactional/application notifications when required; the vendor remains provider-agnostic until selected. **Marketplace authentication OTP is sent and verified only by Firebase Authentication** under ADR-002. The notification SMS adapter must not send or verify marketplace sign-in/recovery OTPs or create a second authentication-verification path.
- **WhatsApp:** WhatsApp Business API is a later-phase channel, not an initial dependency.
- **Email:** provider remains abstracted behind the notification channel adapter.

Business modules must not call individual notification providers directly.

# 5. Notification Model

The eventual architecture should distinguish event, notification, channel, template, recipient, preference, delivery attempt, delivery status, retry, and provider response.

# 6. Notification Categories

### Transactional

Important system events such as security, moderation, and payment status.

### User-Controlled

Notifications that users may enable or disable.

### Promotional

Marketing or promotional communication subject to applicable consent and communication rules.

These categories should not be treated identically.

# 7. Reliability Requirements

Address queueing, retries, duplicate prevention, idempotency, provider failures, delivery logging, preferences, rate limits, and failed-job handling.

# 8. Acceptance Criteria

Define initial events, required channels, provider choices, queue architecture, preference model, retry strategy, retention, and promotional communication rules.

# 9. Related Documentation

- 
    1. Notification System
- 
    1. Authentication & Authorization
- 
    1. Testing & QA
- 
    1. Infrastructure & Deployment
- ADR-002 — Authentication Architecture

# 10. Status History

- 2026-09-20 — Created as Decision Pending.
- 2026-09-28 — Accepted: central notification module with in-app, push, email, SMS, and future WhatsApp channels; FCM selected for push; Firebase Authentication owns marketplace OTP, while a separate SMS adapter may support approved transactional notifications; WhatsApp Business API deferred. Clarification recorded 2026-10-18.

## Clarification — Marketplace Authentication OTP Boundary (2026-10-18)

Marketplace sign-in and recovery OTP delivery/verification are owned exclusively by Firebase Authentication under ADR-002. The separate SMS adapter in this notification architecture is for approved transactional/application notifications only; it must not send or verify marketplace authentication OTPs or create a second OTP-verification path. This clarification supersedes any ambiguous earlier wording that grouped a separate SMS-provider path with OTP.