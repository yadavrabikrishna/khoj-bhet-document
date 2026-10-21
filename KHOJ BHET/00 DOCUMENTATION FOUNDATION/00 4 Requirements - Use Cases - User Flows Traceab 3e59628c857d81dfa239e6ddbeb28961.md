# 00.4 Requirements - Use Cases - User Flows Traceability Matrix

**Project:** KHOJ BHET  

**Document:** Requirements ↔ Use Cases ↔ User Flows Traceability Matrix  

**Document ID:** KB-DOC-004  

**Status:** Active  

**Version:** 1.2  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-28  

**Parent:** 00. DOCUMENTATION FOUNDATION  

**Related:** 03. Requirements Specification, 05. User Stories & Use Cases, 06. User Flows, 07. UX/UI Specification, 08. Product & Business Rules, 00.1 Documentation & SDLC Framework  

**Purpose:** Formalize and maintain bidirectional traceability between requirements, use cases, and user flows.

---

# 1. Purpose

This document establishes the formal traceability model for the product-definition layer of KHOJ BHET.

The authoritative relationship is:

**Requirement → User Story → Use Case → User Flow → UX/UI → Business Rule → Technical Specification → Implementation → Test**

This document specifically formalizes the **REQ ↔ UC ↔ UF** portion of that chain.

The matrix is a governance artifact. It does not replace the detailed content of the Requirements, User Stories & Use Cases, or User Flows documents.

# 2. Traceability Principles

1. Every mature use case should trace to one or more requirements.
2. Every mature user flow should trace to one or more use cases.
3. A requirement may map to multiple use cases.
4. A use case may map to multiple user flows.
5. A user flow may support multiple use cases when the same process is reused.
6. A requirement may be system-oriented and therefore may not require a human-facing user flow.
7. Missing traceability is a documentation gap, not permission to invent a relationship.
8. Stable IDs must be used rather than titles alone.
9. Traceability must be bidirectional: starting from a requirement, the related UC/UF should be discoverable; starting from a UF, its originating UC/REQ should also be discoverable.
10. When a required stable ID does not yet exist, the matrix records the gap explicitly as **See 03.1 Requirements Register** rather than silently creating an identifier.

# 3. Artifact Definitions

| Artifact | ID Pattern | Purpose |
| --- | --- | --- |
| Requirement | KB-FR-xxx / KB-NFR-xxx / KB-BR-xxx / KB-DR-xxx / KB-CR-xxx | Defines what the product must provide or satisfy |
| User Story | KB-US-xxx | Expresses a user goal and expected benefit |
| Use Case | UC-xxx | Defines an actor/system interaction and outcome |
| User Flow | UF-xxx | Defines the navigable/process/state flow implementing a use case |
| UX/UI | UX-xxx | Defines interface behavior and presentation |

# 4. Relationship Rules

### 4.1 Requirement → Use Case

A requirement should map directly to the use case(s) that operationalize the requirement.

Example:

**KB-FR-001 User Registration → UC-001 Register Account**

### 4.2 Use Case → User Flow

A use case should map to the user flow that describes how the interaction progresses.

Example:

**UC-004 Create Listing → UF-004 Create Listing**

### 4.3 One-to-Many Relationships

Traceability is not required to be one-to-one.

Examples:

**UC-004 Create Listing → UF-004 Create Listing + UF-006 Submit Listing**

**UC-021 Manage Subscription → UF-021 Manage Subscription**

**UC-022 Enforce Entitlement → UF-022 Enforce Entitlement**

### 4.4 Shared Flows

A supporting process/state model may be referenced by multiple primary User Flows. A primary User Flow does not serve multiple Use Cases in the baseline catalogue.

For example, the listing lifecycle flow can support publication, pause/resume, expiration, archive, and related state transitions.

Where a shared flow is used, the matrix should list all relevant relationships rather than duplicating the flow definition.

# 5. Current Formal Traceability Matrix

The following matrix is based on the current requirement IDs in **03.1 Requirements Register** and the approved/baselined IDs and names in **05 and 06**.

| Requirement | Use Case | User Flow | Relationship Status | Notes |
| --- | --- | --- | --- | --- |
| KB-FR-001 | UC-001 Register Account | UF-001 Register Account | Confirmed | Explicit requirement ID currently defined |
| KB-FR-002–005 | UC-002 Sign In | UF-002 Sign In | Confirmed | Stable requirement IDs KB-FR-002 through KB-FR-005 are defined in 03.1; this row groups those IDs under UC-002. |
| KB-FR-006–010 | UC-003 Manage Profile | UF-003 Manage Profile | Confirmed | Profile capability exists in 03 |
| KB-FR-011–012, KB-FR-021–023, KB-FR-026–031 | UC-004 Create Listing | UF-004 Create Listing | Confirmed | Listing creation requirement domain exists |
| KB-FR-013, KB-FR-053–056 | UC-005 Edit Listing | UF-005 Edit Listing | Confirmed | Listing editing requirement domain exists |
| KB-FR-014–015 | UC-006 Submit Listing | UF-006 Submit Listing | Confirmed | Submission/validation requirement domain exists |
| KB-FR-016, KB-FR-057 | UC-007 Publish Listing | UF-007 Publish Listing | Confirmed | Publication/lifecycle requirement domain exists |
| KB-FR-017–018 | UC-008 Pause Listing | UF-008 Pause Listing | Confirmed | Shared flow also covers Resume |
| KB-FR-019–020 | UC-009 Archive Listing | UF-009 Archive Listing | Confirmed | Dedicated archive flow added; Listing Lifecycle remains the broader state-transition reference |
| KB-FR-032–033, KB-FR-036–037 | UC-010 Search Listings | UF-010 Search Listings | Confirmed | Search requirement domain exists |
| KB-FR-034–036 | UC-011 Filter Listings | UF-011 Filter Listings | Confirmed | Filter and sorting are combined in UF-011 |
| KB-FR-029, KB-FR-037–038 | UC-012 View Listing | UF-012 View Listing | Confirmed | Listing detail/view requirement domain exists |
| KB-FR-039–040 | UC-013 Save Listing | UF-013 Save Listing | Confirmed | Favorites/saved-listing requirement domain exists |
| KB-FR-041–043 | UC-014 Contact Poster | UF-014 Contact Poster | Confirmed | Contact/communication requirement domain exists |
| KB-FR-044, KB-FR-046–047 | UC-015 Report Listing | UF-015 Report Listing | Confirmed | Reporting/safety requirement domain exists |
| KB-FR-045–047 | UC-016 Report User | UF-016 Report User | Confirmed | Reporting/safety requirement domain exists |
| KB-FR-048–052 | UC-017 Moderate Listing | UF-017 Moderate Listing | Shared | UF-017 is the dedicated primary flow for listing moderation |
| KB-FR-048–050, KB-FR-058 | UC-018 Moderate User | UF-018 Moderate User + S-05 Account Restriction Process where required | Shared | UF-018 is the dedicated primary user-moderation flow; S-05 is the supporting restriction process |
| KB-FR-024–025 | UC-019 Manage Category | UF-019 Manage Category | Confirmed | Dedicated administrator flow added |
| KB-FR-026–031 | UC-020 Manage Location Data | UF-020 Manage Location Data | Confirmed | Dedicated administrator flow added for Nepal location hierarchy and supporting data |
| KB-FR-060–061 | UC-021 Manage Subscription | UF-021 Manage Subscription | Confirmed | Subscription capability exists; exact commercial rules remain open |
| KB-FR-029, KB-FR-042–043, KB-FR-059–061 | UC-022 Enforce Entitlement | UF-022 Enforce Entitlement | Confirmed | System/permission flow; does not require a conventional human journey |
| KB-FR-008–010, KB-FR-062 | UC-023 Manage Business | UF-023 Manage Business | Confirmed | Dedicated business-management flow added; UF-024 remains specifically for member management |
| KB-FR-010, KB-FR-062 | UC-024 Manage Business Members | UF-024 Manage Business Members | Confirmed | Flow directly represents member management |

# 6. Traceability Gap Resolution

The four previously identified flow-level gaps have now been resolved.

### 6.1 Archive Listing

**UC-009 Archive Listing → UF-009 Archive Listing**.

The dedicated flow covers the user-facing archive action, while the broader Listing Lifecycle Flow remains the authoritative state-transition context.

### 6.2 Manage Category

**UC-019 Manage Category → UF-019 Manage Categories**.

The new flow covers authorized administrator maintenance of the category hierarchy and category configuration.

### 6.3 Manage Location Data

**UC-020 Manage Location Data → UF-020 Manage Location Data**.

The new flow covers authorized administration of the Nepal location hierarchy and supporting locality/chowk/postal-code data.

### 6.4 Manage Business

**UC-023 Manage Business → UF-023 Manage Business**.

The new flow separates business representation management from **UF-024 Business Member Management**, which remains focused on member administration.

### 6.5 Shared Moderation Flow

**UF-017 Moderate Listing** is intentionally reusable across moderation targets.

It can support:

- UC-017 Moderate Listing
- UC-018 Moderate User

**UF-018 Account Restriction** provides the state/permission path when moderation results in an account restriction.

# 7. Coverage Status Model

Each matrix relationship should use one of these statuses:

| Status | Meaning |
| --- | --- |
| Confirmed | Explicit relationship exists in the source documents |
| Shared | Artifact intentionally supports multiple related artifacts |
| Partial | Relationship exists but additional dedicated detail may be required |
| Gap | Expected relationship is currently missing |
| See 03.1 Requirements Register | Capability exists, but a stable requirement ID has not yet been formalized |
| Not Applicable | No relationship is expected, such as certain system-only requirements |

A row may have more than one condition, for example:

**Confirmed UC↔UF / See 03.1 Requirements Register**

# 8. Bidirectional Traceability

The project should support both directions.

### Forward Traceability

**REQ → UC → UF**

Question answered:

> If this requirement changes, which use cases and flows may be affected?
> 

### Reverse Traceability

**UF → UC → REQ**

Question answered:

> If this flow changes, which use cases and requirements may be affected?
> 

### Impact Traceability

**REQ → UC → UF → UX → BR → Technical → Test**

Question answered:

> What downstream artifacts must be reviewed when a requirement changes?
> 

# 9. Change-Control Rule

When any of the following changes:

- requirement meaning;
- requirement priority;
- use-case goal;
- actor;
- use-case success/alternate/exception behavior;
- flow entry point;
- flow decision;
- flow state transition;
- permission-sensitive step;

the affected traceability relationships must be reviewed.

A change should not silently leave an orphaned requirement, use case, or flow.

# 10. Orphan Detection

The traceability review should identify:

### Orphan Requirement

A requirement with no linked user story/use case where a user-facing interaction is expected.

### Orphan Use Case

A use case with no originating requirement.

### Orphan User Flow

A flow with no originating use case or documented system/process reason.

### Broken Downstream Link

A UC/UF relationship exists, but the corresponding UX/UI or business-rule reference is missing where required.

# 11. Relationship to Existing Documents

| Document | Traceability Responsibility |
| --- | --- |
| 03. Requirements Specification | Defines authoritative requirement IDs and requirement meaning |
| 05. User Stories & Use Cases | Links user stories/use cases to requirements |
| 06. User Flows | Links flows to use cases and documents process behavior |
| 07. UX/UI Specification | Links screens and interface behavior to flows |
| 08. Product & Business Rules | Links rules to requirements, flows, and business behavior |
| 00.4 Requirements ↔ Use Cases ↔ User Flows Traceability Matrix | Provides the cross-document traceability view |

# 12. Working Rule for Future Documentation

For every new mature capability:

1. Create or identify the requirement ID.
2. Create the user story where a user goal exists.
3. Create the use case.
4. Create the user flow.
5. Add the relationship to this matrix.
6. Link UX/UI artifacts.
7. Link applicable business rules.
8. Continue the trace to API, database, implementation, and tests.
9. Review reverse traceability before approving significant changes.

# 13. Current Traceability Baseline

At this stage:

- **24 use cases** are catalogued in 05.
- **24 use cases** remain catalogued in 05.
- **24 primary User Flow identifiers** are catalogued in 06, one for each Use Case. The catalogue also contains **5 supporting S-XX models**, for **29 flow artifacts** total.
- **UC ↔ UF mapping is now substantially complete for the currently catalogued use cases;** the four previously identified flow gaps have been resolved.
- The remaining traceability work is downstream validation of UX/UI, business-rule, technical, and test relationships rather than creation of these four missing flow artifacts.

# 14. Governance

This matrix is the cross-document index; it does not replace the source artifacts.

The source of truth remains:

- Requirement definition → **03. Requirements Specification**
- Actor/use-case definition → **05. User Stories & Use Cases**
- Flow definition → **06. User Flows**
- UX behavior → **07. UX/UI Specification**
- Product/business rules → **08. Product & Business Rules**

When a conflict exists, the detailed source artifact must be reviewed and the matrix corrected rather than treating the matrix as an independent product decision.

# 15. Document Status

**Status:** Active  

**Version:** 1.1  

**Document ID:** KB-DOC-004

This document formalizes the current REQ ↔ UC ↔ UF traceability baseline. Version 1.1 resolves the Archive Listing, Manage Category, Manage Location Data, and Manage Business flow gaps.

# 16. Phase 2 — Flow Definition Reconciliation

**Review Date:** 2026-09-25  

**Scope:** Detailed formal flow definitions added to 06. User Flows, reconciled against this matrix, 05. User Stories & Use Cases, and 08. Product & Business Rules.

## 16.1 Result

The new detailed flow definitions are consistent with the existing **REQ ↔ UC ↔ UF** baseline at the relationship level.

### Confirmed mappings

- UC-001 → UF-001
- UC-002 → UF-002
- UC-003 → UF-003
- UC-004 → UF-004
- UC-005 → UF-005
- UC-006 → UF-006
- UC-007 → UF-007
- UC-008 → UF-008
- UC-009 → UF-009
- UC-010 → UF-010
- UC-011 → UF-011
- UC-012 → UF-012
- UC-013 → UF-013
- UC-014 → UF-014
- UC-015 → UF-015
- UC-016 → UF-016
- UC-017 → UF-017
- UC-018 → UF-017 + UF-018
- UC-019 → UF-019
- UC-020 → UF-020
- UC-021 → UF-021
- UC-022 → UF-022
- UC-023 → UF-023
- UC-024 → UF-024

This reconciliation establishes a clean primary relationship: 24 Use Cases → 24 primary User Flows. Supporting models are referenced separately and do not create additional primary UF mappings.

## 16.2 Shared-flow observations

### UF-008 — Pause/Resume Listing

The formal flow covers both Pause and Resume, while the current use-case catalogue contains UC-008 Pause Listing. This is acceptable under the existing shared-flow rule, but the future use-case catalogue may need an explicit Resume use case if Resume becomes independently governed, permission-sensitive, or otherwise materially distinct.

**Current status:** No new use case created.

### UF-017 — Moderate Listing

UF-017 is the dedicated primary flow for:

- UC-017 Moderate Listing
- UC-018 Moderate User

The current Whimsical implementation is listing-centric. The formal Notion flow definition should therefore remain the written source of truth until the Whimsical diagram is refined to make its supported scope explicit.

### UF-018 — Moderate User

UF-018 is the dedicated primary flow for UC-018 Moderate User and references S-05 when moderation results in an account restriction. It should not be treated as a new independent use case unless the product later establishes a separate actor goal and lifecycle for account-restriction management.

## 16.3 Business-rule reconciliation

The flow definitions correctly defer detailed product behavior to **08. Product & Business Rules** rather than embedding new commercial or policy decisions.

The following areas require particular attention during downstream validation:

1. **Listing publication/moderation:** the policy is now resolved: **every listing requires Review/moderation before publication**. The authoritative lifecycle is Draft → Review → Published. Any edit to a published listing returns it to Review before republication. Whimsical lifecycle diagrams must be kept aligned with this decision.
2. **Subscription/commercial behavior:** UF-021 describes the interaction sequence without inventing plan prices, billing periods, payment providers, renewal terms, or other commercial values.
3. **Entitlement:** UF-022 applies authentication, authorization, ownership/scope and subscription/entitlement checks without changing the existing visibility model.
4. **Location:** UF-020 manages location data; the flow does not redefine the Nepal location hierarchy already established elsewhere.
5. **Business membership:** UF-024 separates business-member administration from UF-023 business representation management.

## 16.4 Traceability quality findings

| Finding | Severity | Action |
| --- | --- | --- |
| UC ↔ UF mappings for the newly detailed flows are present | Green | No corrective action |
| Shared UF-008 covers Resume although only UC-008 is catalogued | Low | Monitor; do not create a new UC without a product reason |
| UF-017 is broader conceptually than its current listing-centric Whimsical diagram | Medium | Refine Whimsical before Traceability Verified |
| Listing publication requires Review/moderation | Resolved | Align lifecycle documentation and Whimsical with Draft → Review → Published |
| UF-021 commercial details are intentionally deferred | Medium | Define commercial rules before implementation |
| UF-022 is a system flow rather than a conventional user journey | Green | Keep as formal system flow |
| UF-024 and UF-023 remain correctly separated | Green | No corrective action |
| Requirement IDs are already represented in the matrix; no new IDs were invented | Green | No corrective action |

## 16.5 Phase 2 conclusion

**REQ ↔ UC ↔ UF relationship status: Substantially Reconciled**

No new requirement, use-case, or user-flow identifiers should be created as part of this reconciliation.

The remaining work before Whimsical generation is primarily:

1. verify that the resolved listing publication/moderation rule is reflected in every lifecycle diagram (Draft → Review → Published);
2. refine the existing Whimsical diagrams whose scope differs from the formal flow definitions;
3. create dedicated Whimsical diagrams for the currently missing formal flows;
4. perform final Notion → Whimsical traceability verification.

**Important:** A flow is not considered **Traceability Verified** merely because its UC mapping exists. The flow's business-rule references, unresolved decisions, and Whimsical representation must also be verified.

# 17. Technical & ADR Traceability Baseline

**Review Date:** 2026-09-28

The product traceability baseline now extends into the current technical-definition layer. The authoritative chain is:

**Requirement → User Story → Use Case → User Flow → UX/UI → Business Rule → Technical Document → ADR where applicable → Implementation → Test**

### 17.1 Current Technical Dependencies

| Technical Area | Authoritative Document | ADR Relationship |
| --- | --- | --- |
| Application architecture | 09. Software Architecture | ADR-001 — Accepted |
| Technology choices | 10. Technology Stack | Individual ADRs where architectural significance requires them |
| Development process | 11. Development Methodology | Cross-cutting ADR governance |
| Engineering conventions | 12. Engineering Standards | Cross-cutting ADR governance |
| Database/data model | 13. Database Architecture & Data Model | ADR-001, ADR-008 |
| API contracts | 14. API Specification | ADR-001, ADR-002 and relevant future decisions |
| Frontend architecture | 15. Frontend Architecture | ADR-001 and relevant technology decisions |
| Backend architecture | 16. Backend Architecture | ADR-001 |
| Mobile architecture | 17. Mobile Application Architecture | ADR-003 — Accepted |
| Authentication/authorization | 18. Authentication & Authorization | ADR-002 — Accepted |
| Security | 19. Security Architecture | ADR-002 and future security ADRs where required |
| Media/file storage | 20. Media & File Storage | ADR-005 — Accepted |
| Search | 21. Search Architecture | ADR-004 — Accepted; ADR-008 — Accepted |
| Notifications | 22. Notification System | ADR-007 — Accepted |
| SEO | 23. SEO Architecture | Related to public discovery requirements and search architecture |

### 17.2 Current ADR Coverage

All currently identified architectural decision topics have a dedicated ADR:

- ADR-001 — Application Architecture — **Accepted**
- ADR-002 — Authentication Architecture — **Accepted**
- ADR-003 — Mobile Application Framework — **Accepted**
- ADR-004 — Search Engine Strategy — **Accepted**
- ADR-005 — File Storage Strategy — **Accepted**
- ADR-006 — Payment Architecture — **Accepted**
- ADR-007 — Notification Architecture — **Accepted**
- ADR-008 — Database Search Strategy — **Accepted**

No additional ADR is required merely because a technical document exists. A new ADR is required only when a new architecturally significant decision is introduced.

### 17.3 Product Flow Coverage

The current baseline contains **24 primary Use Cases → 24 primary User Flows**, plus **5 supporting S-XX process/state models**, for **29 flow artifacts** total. The REQ ↔ UC ↔ UF relationships are maintained in this matrix and must remain synchronized with 05. User Stories & Use Cases and 06. User Flows.

### 17.4 Current Traceability State

- REQ ↔ UC ↔ UF: **Substantially Reconciled**
- UC ↔ UF primary coverage: **24/24** current use cases mapped
- Supporting flow models: **5** documented
- ADR coverage: **8/8** identified architectural topics have dedicated ADRs
- Technical-document linkage: **Established at architecture/domain level**
- UX/UI and business-rule downstream verification: **ongoing as implementation artifacts evolve**
- Whimsical diagram verification: **must continue against the Notion flow definitions**

This matrix remains the cross-document index. It must not invent missing relationships; source documents remain authoritative for the detailed definitions.

# 18. Document Status

**Status:** Active  

**Version:** 1.2  

**Last Reviewed:** 2026-09-28  

Version 1.2 extends the existing REQ ↔ UC ↔ UF baseline with current technical-document and ADR traceability and reconciles the project decision state as of 2026-09-28.

## V1 Scope Decision — 2026-10-18

UC-014 / UF-014 is in MVP scope for authenticated in-app conversations and the visitor sign-in prompt. UC-021 Manage Subscription and UC-022 Enforce Entitlement remain future-phase trace links and are not MVP acceptance criteria while Document 02 defers monetization to Stage 4. V1 does not disclose direct contact details or exact residential location to non-owners. Each V1 requirement must map to an approved use case, flow, API contract and test; a traceability link alone does not approve implementation scope.