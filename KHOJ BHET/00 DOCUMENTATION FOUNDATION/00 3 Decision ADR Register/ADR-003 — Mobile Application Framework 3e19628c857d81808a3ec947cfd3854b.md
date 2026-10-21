# ADR-003 — Mobile Application Framework

# ADR Metadata

- **ADR ID:** ADR-003
- **Status:** Accepted
- **Date:** 2026-09-20
- **Decision Owner:** KHOJ BHET Project Team
- **Area:** Mobile
- **Related ADRs:** ADR-001, ADR-002
- **Implementation Status:** Not started

# 1. Context

KHOJ BHET is planned as a web-first marketplace with Android as an important future client. The mobile application will need authentication, media upload, location, push notifications, deep links, search, listing creation, messaging, and potentially payments.

# 2. Decision Drivers

- Android requirements
- Future iOS requirements
- Developer capability
- Existing project experience
- Native API access
- Performance
- UI consistency
- Package ecosystem
- Long-term maintenance
- Build and release complexity
- Testing
- Cost

# 3. Alternatives

## Flutter

Cross-platform framework using Dart.

## React Native

Cross-platform framework using JavaScript/TypeScript with native platform integration.

## Native Android

Kotlin-based Android application.

Other frameworks may be evaluated only if they materially satisfy project requirements.

# 4. Decision

**Accepted decision:** React Native + Expo is the selected mobile application stack for the current project baseline. Flutter is no longer the active baseline choice. The architecture remains capable of reconsideration through a new ADR if requirements materially change.

# 5. Evaluation Requirements

Evaluate authentication, camera/image upload, video upload, location/GPS, push notifications, deep links, API integration, offline behavior, background processing, payment SDK integration, release process, crash reporting, automated testing, and developer onboarding.

# 6. Consequences

Cross-platform development can reduce duplicated implementation but introduces framework and plugin dependencies. Native development provides direct platform access but requires more platform-specific work when multiple mobile platforms are supported.

# 7. Acceptance Criteria

The decision can be Accepted after requirements are finalized, critical features are prototyped, developer capability is evaluated, native integrations are validated, and long-term maintenance implications are documented.

# 8. Related Documentation

1. Technology Stack
2. Mobile Application Architecture
3. Requirements Specification
- ADR-001 — Application Architecture
- ADR-002 — Authentication Architecture

# 9. Status History

- 2026-09-20 — Created as Decision Pending.
- 2026-09-28 — Accepted; React Native + Expo selected for the mobile application baseline.