# 00.3 Decision / ADR Register

**Project:** KHOJ BHET  

**Document:** Decision / ADR Register  

**Document ID:** KB-DOC-003  

**Status:** Active  

**Version:** 1.1  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-10-15  

**Parent:** 00. DOCUMENTATION FOUNDATION  

**Related:** 00. Project Documentation Guide, 00.1 Documentation & SDLC Framework, 00.2 Terminology & Glossary  

**Next work:** Complete the project-wide documentation consistency audit before creating Document 29.

---

# Purpose

This page is the **authoritative master register for Architecture Decision Records (ADRs) in KHOJ BHET**.

It answers:

> **What important architectural decisions have been made, why were they made, what is their current status, and where is the detailed decision record?**
> 

This register is an index and governance page. Individual ADRs should contain the detailed context, alternatives, decision, rationale, consequences, and follow-up information.

# 1. What Is an ADR?

**ADR (Architecture Decision Record)** is a durable record of an important technical or architectural decision.

An ADR should capture:

- the problem or context
- the decision that was considered necessary
- important alternatives considered
- the selected approach
- the reasons for the decision
- consequences and trade-offs
- affected areas
- status
- date
- related decisions and documentation

The purpose is to preserve **decision history**, not merely the final technical configuration.

# 2. Role of This Register

The register is the **single source of truth for the ADR index**.

It must:

1. provide a unique ADR identifier;
2. show every active, superseded, deprecated, or rejected architectural decision;
3. link each ADR to its detailed record;
4. show the current status of each decision;
5. identify relationships between decisions;
6. prevent duplicate or conflicting ADR records;
7. make architectural history understandable to future developers.

The register does **not** replace the individual ADR documents.

# 3. ADR Scope

An ADR is appropriate when a decision has meaningful long-term consequences for one or more of:

- system architecture
- application architecture
- technology selection
- data architecture
- API architecture
- authentication and authorization
- security architecture
- infrastructure
- deployment
- storage
- search
- messaging or notifications
- external integrations
- scalability
- reliability
- major development practices
- major platform decisions

# 4. What Does Not Usually Need an ADR?

Do not create ADRs for ordinary implementation details such as:

- variable naming
- normal UI styling
- routine bug fixes
- ordinary refactoring
- individual function implementation
- temporary debugging
- ordinary CRUD implementation
- isolated code-level choices with no meaningful architectural impact

These belong in code, technical documentation, issues, pull requests, or development notes as appropriate.

# 5. ADR Lifecycle

ADR status uses the following lifecycle:

**Proposed → Accepted → Superseded / Deprecated / Rejected**

### Proposed

A decision is being evaluated and has not yet become an approved project decision.

### Accepted

The project has adopted the decision and implementation may proceed according to it.

### Superseded

A newer ADR replaces the decision. The old ADR remains part of the historical record.

### Deprecated

The decision is no longer recommended or applicable, but has not necessarily been replaced by another ADR.

### Rejected

The proposed decision was explicitly considered and not adopted. Rejected ADRs may be useful when the same question is revisited later.

# 6. ADR Numbering

ADR identifiers are sequential and permanent.

Format:

`ADR-001`

`ADR-002`

`ADR-003`

Once assigned, an ADR number must not be reused.

If an ADR is superseded, its identifier remains unchanged. The replacement receives the next available ADR number.

# 7. ADR Naming Convention

Recommended title format:

`ADR-XXX — <Decision Title>`

Examples:

- ADR-001 — Application Architecture
- ADR-002 — Authentication Architecture
- ADR-003 — Mobile Application Framework
- ADR-004 — Search Engine Strategy

The title should describe the **decision**, not merely the technology name.

# 8. Required ADR Content

Every accepted or rejected ADR should contain, at minimum:

### Metadata

- ADR ID
- Title
- Status
- Date
- Decision owner
- Related ADRs

### Context

Explain the problem, constraints, requirements, and circumstances that created the need for a decision.

### Decision Drivers

Identify the factors that materially affected the decision, such as cost, maintainability, scalability, security, developer capability, ecosystem maturity, operational complexity, performance, availability, and vendor dependency.

### Alternatives Considered

Document the meaningful alternatives considered.

### Decision

State the adopted approach precisely.

### Rationale

Explain why the decision was made.

### Consequences

Document benefits, trade-offs, risks, operational implications, and future constraints.

### Related Documentation

Link affected requirements, architecture documents, specifications, or implementation guidance.

# 9. Decision States vs Implementation States

An ADR status describes the **decision**, not whether every implementation task is complete.

For example:

- ADR status: **Accepted**
- Implementation status: **Partially implemented**

Implementation progress belongs in project/task tracking and relevant technical documentation.

# 10. ADR Register

| ADR ID | Decision | Status | Area | Date | Replaces | Replaced By | Detailed ADR |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ADR-001 | Application Architecture | Accepted | Architecture | 2026-09-28 | — | — | Child ADR page |
| ADR-002 | Authentication Architecture | Accepted | Security / Identity | 2026-09-28 | — | — | Child ADR page |
| ADR-003 | Mobile Application Framework | Accepted | Mobile | 2026-09-28 | — | — | Child ADR page |
| ADR-004 | Search Engine Strategy | Accepted | Search | 2026-09-28 | — | — | Child ADR page |
| ADR-005 | File Storage Strategy | Accepted | Infrastructure / Media | 2026-09-28 | — | — | Child ADR page |
| ADR-006 | Payment Architecture | Accepted | Payments | 2026-09-28 | — | — | Child ADR page |
| ADR-007 | Notification Architecture | Accepted | Notifications | 2026-09-28 | — | — | Child ADR page |
| ADR-008 | Database Search Strategy | Accepted | Data / Search | 2026-09-28 | — | — | Child ADR page |

**Register status rule:** The table above reflects the current status of the individual ADR pages. All eight current ADRs (ADR-001 through ADR-008) are Accepted as of the current project baseline. Their detailed pages remain the authoritative records of the individual decisions and rationale.

# 11. Initial ADR Topics

## ADR-001 — Application Architecture

**Accepted decision:** Use a modular monolith with explicit business-module boundaries for the initial product. Keep domain modules cohesive and testable; consider service extraction only when measurable scale, team, isolation, or operational needs justify the added distributed-system complexity. Implementation status remains tracked separately in the ADR and delivery evidence.

## ADR-002 — Authentication Architecture

**Accepted decision:** Normal marketplace clients use Firebase Authentication ID tokens in the Bearer Authorization header; Laravel verifies tokens and applies authoritative MySQL account and authorization rules. The marketplace API does not require Laravel session cookies or CSRF tokens. Administrative authentication is separate through the Laravel/Filament admin identity store and guard, with MFA required for privileged access.

## ADR-003 — Mobile Application Framework

**Accepted decision:** React Native + Expo is the current mobile application baseline for Android and future iOS support. Flutter is not the active baseline choice. Reconsideration requires a new decision record and a documented reason.

## ADR-004 — Search Engine Strategy

**Accepted decision:** Begin with MySQL-based search and filtering for V1, using appropriate relational indexes and full-text search where validated. Do not make a dedicated search service a V1 dependency. Evaluate a dedicated engine only against measurable relevance, language, latency, scale, and operational thresholds.

## ADR-005 — File Storage Strategy

**Accepted decision:** Keep media behind a provider-agnostic storage abstraction and use local application/server storage as the V1 baseline. A CDN is not required for V1. V1 video is limited to one MP4 (H.264/AAC) video per listing, up to 50 MB and 60 seconds, processed asynchronously. The schema compatibility and end-to-end media-processing gates remain open; acceptance of the storage strategy does not prove implementation.

## ADR-006 — Payment Architecture

**Accepted decision:** Use a provider-agnostic payment abstraction with a provider-neutral relational core. V1 uses manual payment submission and administrator review; online gateway redirects, callbacks, webhooks, automated reconciliation, and refunds are future-phase capabilities, not V1 implementation requirements.

## ADR-007 — Notification Architecture

**Accepted decision:** V1 focuses on transactional, security, and account notifications, with in-app read state, preferences, and approved native FCM push. Campaigns, quiet hours, browser push, WhatsApp, and promotional bulk messaging are deferred unless separately approved. Schema and provider implementation gates remain subject to their owning documents.

## ADR-008 — Database Search Strategy

**Accepted decision:** MySQL remains the authoritative source of marketplace records and the V1 search implementation. Any future dedicated index is derived/read-optimized data, must be rebuildable from MySQL, and must not become the authority for core transactional records. This decision complements ADR-004 by defining data ownership and migration boundaries.

# 12. ADR Decision Rules

### Rule 1 — Decisions must be explicit

Do not allow important architectural decisions to exist only in chat messages, meetings, or developer memory.

### Rule 2 — Decisions must be traceable

An accepted ADR should be traceable to the documentation and implementation affected by it.

### Rule 3 — Do not backfill decisions as if they were historical facts

If a decision has not actually been made, its ADR must remain **Proposed** or **Decision Pending**.

### Rule 4 — Do not duplicate ADRs

If a decision already exists, update or supersede the existing ADR instead of creating a duplicate decision record.

### Rule 5 — Supersede; do not erase

When architecture changes, preserve the previous ADR and create a new ADR describing the replacement decision.

### Rule 6 — ADRs do not replace requirements

Requirements define what the system needs. ADRs explain important decisions about how the system will be designed or operated.

### Rule 7 — ADRs do not replace implementation documentation

An ADR records the decision and rationale. Detailed implementation instructions belong in the relevant architecture, API, database, infrastructure, or engineering documentation.

# 13. ADR Review

An ADR should be reviewed when a significant architectural change is proposed, a major dependency becomes unavailable, a technology reaches end-of-life, project scale changes materially, security or regulatory requirements change, original decision drivers are no longer valid, or implementation reveals an important architectural problem.

A review does not automatically mean the ADR should change. If the decision remains valid, retain the ADR and record any relevant implementation guidance elsewhere.

# 14. ADR Relationships

ADRs may have relationships such as:

- Supersedes
- Superseded By
- Depends On
- Related To
- Constrains
- Enables

These relationships should be explicit when they materially affect understanding.

# 15. Source of Authority

For architectural decisions:

**ADR Register → Individual ADR → Relevant Technical Documentation → Implementation**

If these sources conflict:

1. determine which document is authoritative;
2. correct the lower-level documentation;
3. create or update an ADR if the architectural decision itself has changed;
4. keep implementation aligned with the accepted decision.

# 16. Relationship to Phase 0

This page completes the Phase 0 documentation foundation:

1. **00. Project Documentation Guide** — how project documentation is organized.
2. **00.1 Documentation & SDLC Framework** — how documentation and SDLC governance operate.
3. **00.2 Terminology & Glossary** — common language and definitions.
4. **00.3 Decision / ADR Register** — how important architectural decisions are recorded and tracked.

ADRs remain **cross-cutting records** throughout the SDLC. They are not a later sequential development phase.

# 17. Relationship to Later Documentation

ADR decisions may affect Product Scope, Requirements Specification, Software Architecture, Technology Stack, Database Architecture, API Specification, Frontend Architecture, Backend Architecture, Mobile Application Architecture, Authentication & Authorization, Security Architecture, Media & File Storage, Search Architecture, Notification System, DevOps & CI/CD, and Infrastructure & Deployment.

When an ADR changes, affected authoritative documents must be reviewed.

# 18. Governance

The KHOJ BHET project team owns the ADR register.

Before accepting a significant architectural decision:

1. identify the problem;
2. document meaningful alternatives;
3. evaluate decision drivers;
4. record the decision;
5. record consequences;
6. identify affected documentation;
7. obtain appropriate project review;
8. mark the ADR Accepted;
9. update implementation and technical documentation.

# 19. Current Status

**Phase:** 0 — Documentation Foundation and cross-cutting governance

**Document status:** Active

**Version:** 1.1

**Current ADR state:** ADR-001 through ADR-008 are **Accepted** as architectural decisions. Their implementation status is tracked separately; acceptance does not prove implementation or runtime validation. Detailed category/attribute seed catalogue work remains a product-definition artifact rather than a new ADR.

**Next work:** Complete the project-wide documentation consistency audit before creating Document 29. Developer Onboarding Guide.

# 20. Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-DOC-003 |
| Document | Decision / ADR Register |
| Status | Active |
| Version | 1.1 |
| Owner | KHOJ BHET Project Team |
| Last Reviewed | 2026-10-15 |
| Parent | 00. DOCUMENTATION FOUNDATION |
| Related | 00. Project Documentation Guide |
| Related | 00.1 Documentation & SDLC Framework |
| Related | 00.2 Terminology & Glossary |
| Next | 01. Product Vision & Mission |

[ADR-001 — Application Architecture](00%203%20Decision%20ADR%20Register/ADR-001%20%E2%80%94%20Application%20Architecture%203e19628c857d81a09106e3bf9821eb63.md)

[ADR-002 — Authentication Architecture](00%203%20Decision%20ADR%20Register/ADR-002%20%E2%80%94%20Authentication%20Architecture%203e19628c857d8117b2afc2289644cc1a.md)

[ADR-003 — Mobile Application Framework](00%203%20Decision%20ADR%20Register/ADR-003%20%E2%80%94%20Mobile%20Application%20Framework%203e19628c857d81808a3ec947cfd3854b.md)

[ADR-004 — Search Engine Strategy](00%203%20Decision%20ADR%20Register/ADR-004%20%E2%80%94%20Search%20Engine%20Strategy%203e19628c857d8116a049ea2ff9bae266.md)

[ADR-005 — File Storage Strategy](00%203%20Decision%20ADR%20Register/ADR-005%20%E2%80%94%20File%20Storage%20Strategy%203e19628c857d81399b76d453d304fdcd.md)

[ADR-006 — Payment Architecture](00%203%20Decision%20ADR%20Register/ADR-006%20%E2%80%94%20Payment%20Architecture%203e19628c857d81e293fdc952955531e2.md)

[ADR-007 — Notification Architecture](00%203%20Decision%20ADR%20Register/ADR-007%20%E2%80%94%20Notification%20Architecture%203e19628c857d8187be47eef7028f176c.md)

[ADR-008 — Database Search Strategy](00%203%20Decision%20ADR%20Register/ADR-008%20%E2%80%94%20Database%20Search%20Strategy%203e19628c857d81aab5dacc88621103b2.md)

## Revision History

- **v1.1 — 2026-10-15:** Updated ADR-001–ADR-008 summaries to reflect their accepted decisions, separated decision acceptance from implementation readiness, and updated current next-work guidance to the documentation audit gate.

## Approved Product Scope Decisions — 2026-10-18

### PD-01 — Defer paid monetization from Marketplace MVP

**Status:** Approved. **Authority:** Document 02 and the 2026-10-18 V1 scope addenda. Paid subscriptions, paid entitlement activation, paid contact/location unlocks, paid-plan payment submission, recurring billing and gateway checkout are Stage 4/future-phase scope, not MVP acceptance criteria. Reopening requires product change control and reconciliation of roadmap, business rules, API, schema, UX and tests.

### PD-02 — Visitor contact and protected information

**Status:** Approved. Visitors may browse eligible public listings but must authenticate before starting an in-app conversation. Authenticated conversation creation remains subject to listing/account eligibility, seller in-app-contact preference, blocks, moderation and safety rules. V1 does not disclose protected phone/email or exact residential location to non-owners through platform API or public web/SEO surfaces. Consent to in-app messaging is not consent to disclose direct contact details or exact location.

### PD-03 — V1 search normalization boundary

**Status:** Contract approved; validation open. Normalize Unicode to NFC, trim/collapse whitespace, match Latin text case-insensitively, preserve Devanagari, and defer automatic Romanized Nepali transliteration. MySQL remains the V1-first search approach, but actual short-query and Devanagari behavior must be tested on the supported configuration before DOC-09 can close.

These product decisions do not certify runtime behavior or close the database, OpenAPI, security implementation, visual diagram, or operational evidence gates.