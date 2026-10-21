# 03.1 Requirements Register

**Project:** KHOJ BHET  

**Document:** Requirements Register  

**Document ID:** KB-PROD-003.1  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-24  

**Parent:** 03. Requirements Specification  

**Related:** 05. User Stories & Use Cases, 06. User Flows, 07. UX/UI Specification, 08. Product & Business Rules, 00.4 Requirements ↔ Use Cases ↔ User Flows Traceability Matrix

# 1. Purpose

This page is the **detailed requirement register** for KHOJ BHET.

It converts the requirement domains defined in **03. Requirements Specification** into stable, individually traceable requirement records.

The register is the authoritative source for requirement IDs. The parent document remains the requirements framework and governance document.

# 2. Requirement Record Model

Each requirement has:

- Stable ID
- Requirement statement
- Priority
- Status
- Related Use Case(s)
- Related User Flow(s), where applicable
- Notes/dependencies

**Status:** Approved means the requirement is part of the current baseline. Proposed means it requires product approval before becoming baseline.

# 3. Functional Requirements

## 3.1 Account and Identity

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-001 | The system shall allow a visitor to create an account using an approved registration method. | P0 | Approved | UC-001 |
| KB-FR-002 | The system shall authenticate registered users through an approved authentication method. | P0 | Approved | UC-002 |
| KB-FR-003 | The system shall allow an authenticated user to sign out by clearing the client-side Firebase authentication state. The marketplace API remains stateless and does not create a Laravel application session; server-side token-revocation behavior follows the approved Firebase configuration. | P0 | Approved | UC-002 |
| KB-FR-004 | The system shall provide an approved account-recovery mechanism for eligible users. | P1 | Approved | UC-002 |
| KB-FR-005 | The system shall maintain an account status that controls whether the account may perform restricted actions. | P0 | Approved | UC-002, UC-018 |
| KB-FR-006 | The system shall allow an eligible user to deactivate or request deletion of the account according to applicable retention and policy rules. | P1 | Approved | UC-003 |

## 3.2 User Profiles and Representation

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-007 | The system shall allow an authenticated user to create and manage an appropriate marketplace profile. | P1 | Approved | UC-003 |
| KB-FR-008 | The system shall support profile information for individual users and, where approved, business users. | P1 | Approved | UC-003, UC-023 |
| KB-FR-009 | The system shall distinguish the account acting as Poster from the person or organization represented by a listing. | P0 | Approved | UC-004, UC-023 |
| KB-FR-010 | The system shall support authorized business-member relationships where a business listing is managed by multiple permitted users. | P2 | Approved | UC-023, UC-024 |

## 3.3 Listing Creation and Management

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-011 | The system shall allow an authorized Poster to create a listing. | P0 | Approved | UC-004 |
| KB-FR-012 | The system shall allow an authorized Poster to save an incomplete listing as a draft. | P0 | Approved | UC-004 |
| KB-FR-013 | The system shall allow an authorized Poster to edit a listing within the permissions and lifecycle rules applicable to that listing. | P0 | Approved | UC-005 |
| KB-FR-014 | The system shall allow an authorized Poster to submit a listing for validation or review. | P0 | Approved | UC-006 |
| KB-FR-015 | The system shall validate required listing information before a listing enters a state that requires valid publishable information. | P0 | Approved | UC-006, UC-007 |
| KB-FR-016 | The system shall allow an authorized listing to be published when publication conditions are satisfied. | P0 | Approved | UC-007 |
| KB-FR-017 | The system shall allow an authorized Poster to pause an eligible published listing. | P1 | Approved | UC-008 |
| KB-FR-018 | The system shall allow an authorized Poster to resume an eligible paused listing. | P1 | Approved | UC-008 |
| KB-FR-019 | The system shall support listing expiration and archival according to applicable lifecycle rules. | P1 | Approved | UC-009 |
| KB-FR-020 | The system shall allow an authorized Poster to delete or remove an eligible listing according to lifecycle and retention rules. | P1 | Approved | UC-009 |

## 3.4 Listing Structure and Categories

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-021 | The system shall maintain a universal listing structure containing common listing information shared across supported categories. | P0 | Approved | UC-004, UC-012 |
| KB-FR-022 | The system shall support category-specific listing attributes without requiring duplication of the common listing structure. | P0 | Approved | UC-004, UC-019 |
| KB-FR-023 | The system shall support configured listing types including Sale, Rent, Lease, Free, Exchange, Offer, Wanted/Request, Service and Job where enabled. | P1 | Approved | UC-004 |
| KB-FR-024 | The system shall support hierarchical categories. | P0 | Approved | UC-019 |
| KB-FR-025 | The system shall support category activation/deactivation and category-specific validation and filtering configuration. | P1 | Approved | UC-019 |

## 3.5 Location

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-026 | The system shall support Nepal-focused administrative location hierarchy: Country → Province → District → Municipality → Ward. | P0 | Approved | UC-004, UC-010, UC-020 |
| KB-FR-027 | The system shall support local geographic names such as Locality/Tole and Chowk/Landmark separately from formal administrative units. | P0 | Approved | UC-004, UC-010, UC-020 |
| KB-FR-028 | The system shall support coordinates where available without making coordinates a replacement for human-readable location. | P1 | Approved | UC-004, UC-020 |
| KB-FR-029 | The system shall support approximate and exact location representations with different visibility controls. | P0 | Approved | UC-004, UC-012, UC-022 |
| KB-FR-030 | The system shall support location-based discovery using applicable administrative and local geographic levels. | P1 | Approved | UC-010, UC-011 |
| KB-FR-031 | The system shall treat postal code as a location attribute distinct from locality, Tole, Chowk or Landmark. | P1 | Approved | UC-004, UC-020 |

## 3.6 Search, Filtering and Discovery

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-032 | The system shall provide search across listings eligible for the requesting viewer. | P0 | Approved | UC-010 |
| KB-FR-033 | The system shall support keyword, category, listing-type and location search criteria where applicable. | P0 | Approved | UC-010 |
| KB-FR-034 | The system shall provide category-aware filters for supported listing attributes. | P0 | Approved | UC-011 |
| KB-FR-035 | The system shall provide meaningful sorting options appropriate to the selected discovery context. | P1 | Approved | UC-011 |
| KB-FR-036 | The system shall exclude listings from active discovery when their lifecycle or visibility state makes them ineligible. | P0 | Approved | UC-010, UC-011 |
| KB-FR-037 | The system shall provide sufficient structured listing information in search results for a viewer to assess relevance without exposing restricted information. | P0 | Approved | UC-010, UC-012 |

## 3.7 Listing Detail and Saved Discovery

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-038 | The system shall provide a listing detail view containing information permitted for the requesting viewer. | P0 | Approved | UC-012 |
| KB-FR-039 | The system shall allow an authenticated user to save an eligible listing. | P1 | Approved | UC-013 |
| KB-FR-040 | The system shall allow an authenticated user to remove a saved listing and view saved listings. | P1 | Approved | UC-013 |

## 3.8 Contact and Communication

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-041 | The system shall provide an approved mechanism for an eligible user to contact a listing Poster. | P1 | Approved | UC-014 |
| KB-FR-042 | The system shall determine available contact methods according to listing, Poster, viewer, privacy and entitlement rules. | P0 | Approved | UC-014, UC-022 |
| KB-FR-043 | The system shall prevent unauthorized direct exposure of restricted personal contact information. | P0 | Approved | UC-014, UC-022 |

## 3.9 Reporting and Safety

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-044 | The system shall allow an eligible user to report a problematic listing using approved report categories. | P0 | Approved | UC-015 |
| KB-FR-045 | The system shall allow an eligible user to report a problematic user using approved report categories. | P0 | Approved | UC-016 |
| KB-FR-046 | The system shall record submitted reports with their target, reason, reporter, timestamp and applicable evidence. | P0 | Approved | UC-015, UC-016 |
| KB-FR-047 | The system shall route submitted reports into the applicable moderation workflow. | P0 | Approved | UC-015, UC-016, UC-017, UC-018 |

## 3.10 Moderation and Verification

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-048 | The system shall allow authorized moderators to review reported listings and users. | P0 | Approved | UC-017, UC-018 |
| KB-FR-049 | The system shall allow authorized moderators to apply permitted moderation actions to listings or accounts. | P0 | Approved | UC-017, UC-018 |
| KB-FR-050 | The system shall record material moderation actions and outcomes for audit purposes. | P0 | Approved | UC-017, UC-018 |
| KB-FR-051 | The system shall support defined verification states for supported verification types. | P1 | Approved | UC-003, UC-017, UC-018 |
| KB-FR-052 | The system shall display verification information only to the extent supported by the actual verification state. | P0 | Approved | UC-012, UC-017 |

## 3.11 Media and Notifications

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-053 | The system shall allow eligible listings to contain multiple validated media items. | P0 | Approved | UC-004, UC-005 |
| KB-FR-054 | The system shall support a primary listing image and deterministic media ordering. | P1 | Approved | UC-004, UC-005 |
| KB-FR-055 | The system shall validate media type and configured size limits before accepting media for a listing. | P0 | Approved | UC-004, UC-005 |
| KB-FR-056 | The system shall allow authorized users to remove or replace listing media. | P1 | Approved | UC-005 |
| KB-FR-057 | The system should generate notifications for approved listing, account, contact, moderation and security events. | P1 | Approved | UC-003, UC-007, UC-014, UC-017, UC-018 |

## 3.12 Administration and Entitlements

| ID | Requirement | Priority | Status | UC |
| --- | --- | --- | --- | --- |
| KB-FR-058 | The system shall provide authorized administrators with management capabilities for users, listings, categories, locations, reports, moderation and configuration as approved. | P0 | Approved | UC-018, UC-019, UC-020 |
| KB-FR-059 | The system shall evaluate applicable entitlement state before exposing entitlement-controlled functionality or information. | P0 | Approved | UC-022 |
| KB-FR-060 | The system shall maintain entitlement state separately from the underlying listing or user resource. | P0 | Approved | UC-021, UC-022 |
| KB-FR-061 | The system shall support subscription/entitlement activation and expiration according to approved product rules. | P1 | Approved | UC-021 |
| KB-FR-062 | The system shall support authorized business owners/admins in managing permitted business members. | P2 | Approved | UC-023, UC-024 |

# 4. Data Requirements

| ID | Requirement | Priority | Status | Related UC |
| --- | --- | --- | --- | --- |
| KB-DR-001 | The system shall maintain a stable unique identifier for each user account. | P0 | Approved | UC-001, UC-002 |
| KB-DR-002 | The system shall maintain a stable unique identifier for each listing. | P0 | Approved | UC-004, UC-012 |
| KB-DR-003 | Listing records shall retain category, listing type, title, description, price representation, status, ownership/representation and relevant dates. | P0 | Approved | UC-004, UC-005, UC-012 |
| KB-DR-004 | Listing attributes shall support common fields and category-specific attributes without requiring category-specific duplication of the core listing entity. | P0 | Approved | UC-004, UC-019 |
| KB-DR-005 | Location data shall preserve administrative hierarchy and local geographic information as distinct concepts. | P0 | Approved | UC-004, UC-020 |
| KB-DR-006 | Location records shall support public/restricted location state and approximate/exact representations where applicable. | P0 | Approved | UC-012, UC-022 |
| KB-DR-007 | Media metadata shall retain file reference, media type, ordering, primary status and processing state. | P1 | Approved | UC-004, UC-005 |
| KB-DR-008 | Moderation data shall retain reporter, target, reason, evidence reference where applicable, action, actor, timestamp and outcome. | P0 | Approved | UC-015, UC-016, UC-017, UC-018 |
| KB-DR-009 | Verification data shall identify verification type, state and relevant verification lifecycle information. | P1 | Approved | UC-003, UC-017 |
| KB-DR-010 | Entitlement data shall identify the subject, entitlement type, lifecycle state and applicable validity period. | P1 | Approved | UC-021, UC-022 |

# 5. Business Requirements

| ID | Requirement | Priority | Status | Related UC |
| --- | --- | --- | --- | --- |
| KB-BR-001 | KHOJ BHET shall support a universal marketplace listing model capable of serving multiple product categories. | P0 | Approved | UC-004, UC-019 |
| KB-BR-002 | The product shall preserve essential marketplace usefulness for non-paying users while allowing approved subscription-controlled capabilities. | P1 | Approved | UC-021, UC-022 |
| KB-BR-003 | Paid entitlement shall not override authorization, privacy, safety, seller consent or other higher-precedence restrictions. | P0 | Approved | UC-014, UC-022 |
| KB-BR-004 | Listing representation shall distinguish Poster from Owner, Seller, Agent, Broker, Dealer, Property Manager and Authorized Representative where applicable. | P0 | Approved | UC-004, UC-023 |
| KB-BR-005 | Nepal-specific location terminology and address conventions shall be supported without treating Chowk, Tole or Landmark as administrative units. | P0 | Approved | UC-004, UC-010, UC-020 |
| KB-BR-006 | Product rules shall remain category-aware while reusing common listing behavior wherever possible. | P1 | Approved | UC-004, UC-019 |

# 6. Non-Functional Requirements

The following requirements establish the initial quality baseline. Exact numeric budgets that require technical benchmarking remain to be defined in technical specifications.

| ID | Requirement | Priority | Status |
| --- | --- | --- | --- |
| KB-NFR-001 | Core public discovery and listing interactions shall provide a responsive user experience appropriate to the target release. | P1 | Approved |
| KB-NFR-002 | Search, listing browsing and listing detail performance shall be measured using defined technical performance budgets before production release. | P1 | Approved |
| KB-NFR-003 | The platform shall enforce authorization server-side for protected actions and information. | P0 | Approved |
| KB-NFR-004 | The platform shall validate and safely process user-provided input and uploaded media. | P0 | Approved |
| KB-NFR-005 | The platform shall apply rate limiting and abuse-prevention controls to security-sensitive and abuse-prone operations. | P0 | Approved |
| KB-NFR-006 | Sensitive information shall be protected against unauthorized disclosure through application interfaces, public pages and search/discovery surfaces. | P0 | Approved |
| KB-NFR-007 | Important account, listing, moderation, verification and sensitive-access events shall be auditable where required. | P0 | Approved |
| KB-NFR-008 | The system shall provide operational logging, metrics, error visibility and health monitoring appropriate to the release stage. | P1 | Approved |
| KB-NFR-009 | Core modules shall have documented boundaries and interfaces to support maintainability and controlled change. | P1 | Approved |
| KB-NFR-010 | The architecture shall support growth in users, listings, media, search volume and geographic coverage without requiring unnecessary redesign of common product concepts. | P1 | Approved |
| KB-NFR-011 | Core user journeys shall meet accessibility standards adopted by the project. | P1 | Approved |
| KB-NFR-012 | Public eligible listing content shall use stable, meaningful URLs and appropriate structured metadata for discoverability. | P1 | Approved |
| KB-NFR-013 | Restricted or private information shall not become publicly indexable through SEO metadata, structured data, URLs or public APIs. | P0 | Approved |
| KB-NFR-014 | The product shall support the approved Nepal localization requirements for language, currency, date/time and location representation. | P1 | Approved |
| KB-NFR-015 | Supported browser, operating-system and device classes shall be explicitly defined for each release. | P1 | Approved |

# 7. Compliance / Policy Requirements

| ID | Requirement | Priority | Status |
| --- | --- | --- | --- |
| KB-CR-001 | The product shall apply applicable privacy and data-protection requirements to collection, storage, access, disclosure and retention of personal information. | P0 | Approved |
| KB-CR-002 | Administrative and moderation capabilities shall be restricted to authorized actors. | P0 | Approved |
| KB-CR-003 | Important moderation and administrative actions shall retain sufficient audit information for accountability. | P0 | Approved |
| KB-CR-004 | The product shall maintain controls for prohibited, fraudulent, unsafe or policy-violating marketplace content. | P0 | Approved |
| KB-CR-005 | Payment-related capabilities, when introduced, shall comply with applicable provider, platform and legal requirements. | P0 | Approved |
| KB-CR-006 | New high-risk product capabilities shall undergo appropriate privacy, security, safety and policy review before release. | P0 | Approved |

# 8. Requirement-to-Flow Baseline

The detailed REQ → UC → UF relationship is maintained in **00.4 Requirements ↔ Use Cases ↔ User Flows Traceability Matrix**.

Primary current mappings include:

| Requirement Group | Main UC | Main UF |
| --- | --- | --- |
| KB-FR-001–006 | UC-001–003 | UF-001–003 |
| KB-FR-011–020 | UC-004–009 | UF-004–008 + Listing Lifecycle |
| KB-FR-026–031 | UC-004, UC-010, UC-011, UC-012, UC-020 | UF-004, UF-009, UF-010, UF-011 |
| KB-FR-032–040 | UC-010–013 | UF-009–012 |
| KB-FR-041–043 | UC-014, UC-022 | UF-013, UF-019 |
| KB-FR-044–047 | UC-015, UC-016, UC-017, UC-018 | UF-014–016 |
| KB-FR-048–052 | UC-017, UC-018 | UF-016, UF-017 |
| KB-FR-053–057 | UC-004, UC-005, UC-007, UC-014 | UF-004, UF-005, UF-007, UF-013 |
| KB-FR-058–062 | UC-018–024 | UF-016–020 |
| KB-DR-* | Multiple | Depends on consuming capability |
| KB-NFR-* | System-wide | Usually system/technical scenarios rather than user flows |
| KB-BR-* | Multiple | Depends on affected business behavior |
| KB-CR-* | Multiple | Usually cross-cutting |

# 9. Traceability Rules

1. A stable requirement ID must not be silently reused for another requirement.
2. Requirement wording may evolve while the ID remains stable unless the requirement's identity fundamentally changes.
3. A materially different requirement should receive a new ID.
4. A superseded requirement retains its historical ID.
5. Every mature functional requirement should map to one or more use cases or explicitly be classified as system/cross-cutting.
6. A requirement that has no human-facing flow must not be forced into an artificial UF relationship.
7. The matrix in **00.4** is the cross-document relationship index.
8. This register is the authority for the requirement IDs and requirement statements.
9. Changes to approved requirements require impact review across user stories, use cases, flows, UX/UI, business rules, architecture and tests.

# 10. Status and Baseline

The requirements in this register are marked **Approved** because they formalize the capability domains already established in the existing 03 Requirements Specification.

This does **not** finalize:

- subscription pricing;
- exact entitlement limits;
- exact listing expiration durations;
- payment provider;
- exact contact exposure policy;
- exact-location commercial entitlement;
- moderation thresholds;
- exact media limits;
- rate-limit numeric thresholds;
- category-specific field catalogs;
- final technology choices.

Those remain subject to the open decisions and later specifications already defined elsewhere.

# 11. Document Control

**Document ID:** KB-PROD-003.1  

**Document:** Requirements Register  

**Status:** Active  

**Version:** 1.0  

**Authority:** Detailed requirement IDs and baseline statements  

**Parent:** 03. Requirements Specification  

**Cross-document traceability:** 00.4 Requirements ↔ Use Cases ↔ User Flows Traceability Matrix

## Approved V1 Requirement Scope Addendum — 2026-10-18

Subscription/entitlement requirements in this register are conditional/future-phase requirements unless they express general authorization or privacy enforcement. The Marketplace MVP does not require paid subscription purchase, paid entitlement activation, payment submission for paid plans, gateway checkout, recurring billing, or paid contact/location unlocks. Preserve the baseline requirements that unauthorized disclosure is prevented and essential marketplace usefulness is available to non-paying users. Before MVP acceptance, trace each requirement to an approved V1 use case and API route; mark deferred commercial requirements as deferred rather than treating them as failed or implementing them by assumption.

V1 contact acceptance: visitors can browse eligible public listings but must authenticate to initiate in-app conversations; authenticated conversation creation is gated by listing/account eligibility, seller in-app-contact setting, blocking, moderation and safety. Protected phone/email and exact residential location are not exposed to non-owners through platform API or public web/SEO surfaces.