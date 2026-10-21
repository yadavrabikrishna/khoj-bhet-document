# 08. Product & Business Rules

**Project:** KHOJ BHET  

**Document:** Product & Business Rules  

**Document ID:** KB-PROD-008  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Product  

**Last Reviewed:** 2026-09-23  

**Parent:** 01. PRODUCT DEFINITION  

**Previous:** 07. UX/UI Specification  

**Next:** 09. Software Architecture  

**Related:** 03. Requirements Specification, 04. Users, Roles & Permissions, 05. User Stories & Use Cases, 06. User Flows, 07. UX/UI Specification, 00.2 Terminology & Glossary, 00.3 Decision / ADR Register

---

# 1. Document Purpose

This document defines the product-level rules that govern how KHOJ BHET behaves.

Requirements define **what the product must provide**. User stories/use cases define **what users need to accomplish**. User flows define **how those goals progress**. UX/UI defines **how the behavior is presented**.

This document defines the **rules, constraints, conditions, state transitions, visibility rules, and commercial/product policies** that govern those behaviors.

> **Core idea:** A business rule is authoritative product logic. It should not exist only inside a UI screen, API implementation, database constraint, or developer assumption.
> 

# 2. Rule Principles

Business rules should be:

1. **Explicit** — important behavior must be written down.
2. **Testable** — rules must produce observable outcomes.
3. **Traceable** — rules should map to requirements, flows, implementation, and tests.
4. **Technology-neutral** — product rules should not unnecessarily prescribe implementation.
5. **Consistent** — the same rule should produce the same outcome across clients.
6. **Privacy-aware** — sensitive information must have explicit visibility rules.
7. **State-aware** — actions must respect the current lifecycle state.
8. **Permission-aware** — ownership, role, authorization, and entitlement must be considered.
9. **Recoverable** — ordinary failures should not create ambiguous product states.
10. **Change-controlled** — significant rule changes should be documented.

# 3. Rule Identification

Recommended stable identifiers:

- **KB-BR-LIST-XXX** — Listing rules
- **KB-BR-USER-XXX** — User/account rules
- **KB-BR-LOC-XXX** — Location rules
- **KB-BR-SEARCH-XXX** — Search/discovery rules
- **KB-BR-MEDIA-XXX** — Media rules
- **KB-BR-CONTACT-XXX** — Contact/communication rules
- **KB-BR-MOD-XXX** — Moderation/safety rules
- **KB-BR-SUB-XXX** — Subscription/entitlement rules
- **KB-BR-PAY-XXX** — Payment rules
- **KB-BR-BIZ-XXX** — Business/representation rules
- **KB-BR-PRIV-XXX** — Privacy/visibility rules
- **KB-BR-ADMIN-XXX** — Administrative rules

Identifiers should remain stable when wording changes.

# 4. Rule Status

| Status | Meaning |
| --- | --- |
| Proposed | Candidate rule not yet approved |
| Approved | Accepted product rule |
| Active | Currently enforced rule |
| Deprecated | No longer recommended |
| Superseded | Replaced by another rule |
| Deferred | Intentionally postponed |

A proposed rule must not silently be treated as an approved product requirement.

# 5. Core Rule Model

A product action should conceptually pass through:

**Actor → Authentication → Authorization → Ownership/Scope → Entitlement → Validation → Business Rules → State Transition → Result → Audit**

Not every action requires every step, but sensitive actions should explicitly define the applicable checks.

# 6. User and Account Rules

### KB-BR-USER-001 — Account Identity

A marketplace account represents a unique platform identity.

One identity may participate in multiple marketplace capabilities without requiring separate accounts for each capability.

### KB-BR-USER-002 — Authentication

Authentication is required only where the requested action requires an authenticated identity.

Public browsing should remain available where the approved requirements permit it.

### KB-BR-USER-003 — Account Status

An account may have an operational status such as:

- Active
- Restricted
- Suspended
- Disabled
- Deleted/deactivated

The exact status model should be finalized before implementation.

### KB-BR-USER-004 — Restricted Account

A restricted account must not be able to perform actions that its restriction explicitly prevents.

Restriction scope should be explicit rather than assuming that every restriction blocks every feature.

### KB-BR-USER-005 — Account Ownership

Actions affecting private account resources require appropriate ownership or authorization.

### KB-BR-USER-006 — Verification

A verification label must represent only the specific information or identity that has actually been verified.

Phone verification must not be represented as identity verification unless identity verification has separately occurred.

# 7. Listing Ownership and Representation

### KB-BR-LIST-001 — Listing Owner

Every listing must have an identifiable responsible account or authorized representation context.

### KB-BR-LIST-002 — Poster Does Not Necessarily Equal Asset Owner

The account creating a listing is not automatically assumed to own the underlying asset.

The product must support representation relationships such as:

- Owner
- Seller
- Agent
- Broker
- Dealer
- Property Manager
- Authorized Representative

### KB-BR-LIST-003 — Management Authority

Only an authorized owner, poster, representative, moderator, or administrator may perform management actions on a listing.

The exact permission matrix is governed by **04. Users, Roles & Permissions**.

# 8. Listing Creation Rules

### KB-BR-LIST-010 — Category Required

A listing must belong to an enabled category before publication.

### KB-BR-LIST-011 — Required Common Fields

A listing must satisfy the required common-field rules applicable to its category and listing type before publication.

### KB-BR-LIST-012 — Category Attributes

A listing must satisfy required category-specific attributes before publication.

### KB-BR-LIST-013 — Listing Type

The selected listing type must be enabled for the selected category.

Examples include Sale, Rent, Lease, Free, Exchange, Offer, Wanted/Request, Service, or Job where enabled.

### KB-BR-LIST-014 — Price

Price requirements depend on listing type and category.

A free listing must not require a normal monetary price when the product rule defines it as free.

### KB-BR-LIST-015 — Draft Creation

An incomplete listing may be saved as a draft where draft creation is available.

A draft does not become publicly discoverable merely because it exists.

# 9. Listing Validation Rules

Before publication or another state transition that requires valid listing data:

1. Required fields must be present.
2. Values must satisfy applicable validation rules.
3. Category-specific requirements must be satisfied.
4. Media requirements must be satisfied where applicable.
5. Location requirements must be satisfied where applicable.
6. Contact/visibility configuration must satisfy applicable rules.
7. The account must be authorized to perform the transition.
8. Applicable moderation/business rules must be evaluated.

A failed validation must not produce a successful published state.

# 10. Listing Lifecycle Rules

Baseline lifecycle:

**Draft → Review → Published ↔ Paused → Expired → Archived**

Additional administrative outcomes may include Removed, Rejected, Restricted, and Deleted.

### KB-BR-LIST-020 — Draft

Draft listings are not publicly discoverable.

### KB-BR-LIST-021 — Submit

A poster may submit a draft only when the applicable submission requirements are satisfied.

### KB-BR-LIST-022 — Review/Validation

**Every listing requires review/moderation before publication.** A listing must pass the applicable review/validation process before entering Published state.

### KB-BR-LIST-023 — Published

A published listing is eligible for approved public discovery surfaces, subject to visibility and moderation rules.

### KB-BR-LIST-024 — Pause

An eligible published listing may be paused by the **owner, an authorized business member, or an Admin**.

A paused listing should not appear in normal active-listing discovery unless a specific product rule permits it.

### KB-BR-LIST-025 — Resume

An authorized actor may resume a paused listing only if the listing still satisfies the applicable requirements and the actor has permission to manage the listing.

### KB-BR-LIST-026 — Expiration

A listing may become expired according to an approved expiration rule.

Expiration must be deterministic and should not silently leave the listing appearing as active.

### KB-BR-LIST-027 — Archive

Archived listings are no longer active marketplace listings.

Whether archived listings remain viewable to their owner or publicly depends on access rules.

### KB-BR-LIST-028 — Delete

Both the **owner and Admin** may initiate listing deletion/removal, subject to authorization and retention rules.

Deletion must respect the product's retention, audit, moderation, and legal requirements.

A user-facing delete action does not necessarily mean immediate physical removal from every internal system.

### KB-BR-LIST-029 — Invalid Transition

An action that is not permitted from the current listing state must be rejected.

The UI should not offer invalid actions, but server-side validation remains authoritative.

# 11. Listing Editing Rules

### KB-BR-LIST-040 — Authorized Editing

Only an authorized actor may edit a listing.

### KB-BR-LIST-041 — Category Change

Changing category may invalidate category-specific attributes.

The product must either:

- preserve compatible attributes;
- request correction; or
- remove attributes that are no longer valid with appropriate user notification.

### KB-BR-LIST-042 — Significant Changes

Changes that materially affect trust, safety, search eligibility, price, location, or sensitive information may require re-validation or moderation.

The exact change catalogue should be finalized before implementation.

### KB-BR-LIST-043 — Published Edit

**Any edit to a Published listing returns the listing to Review.** The edited listing must pass review before it can become Published again. This rule applies to all published edits; there is no minor-edit bypass in the initial product baseline.

# 12. Listing Visibility Rules

Listing information should be classified conceptually as:

1. **Public**
2. **Restricted**
3. **Private/Internal**

### KB-BR-PRIV-001 — Public Information

Public listing information may be displayed to eligible public viewers and may be indexed when the listing is eligible for search discovery.

### KB-BR-PRIV-002 — Restricted Information

Restricted information may only be returned to a viewer who satisfies the applicable authorization, entitlement, consent, and safety conditions.

### KB-BR-PRIV-003 — Private/Internal Information

Private/internal information must not be exposed through normal public listing responses.

### KB-BR-PRIV-004 — UI Is Not Security

Hiding a field in the interface is not sufficient protection.

The server must enforce information-access rules.

### KB-BR-PRIV-005 — Seller Consent

Paid access or user entitlement must not automatically override a seller's explicit privacy restriction where seller consent is required.

# 13. Nepal Location Rules

KHOJ BHET should represent location using both administrative structure and meaningful local geography.

### KB-BR-LOC-001 — Administrative Hierarchy

The baseline administrative hierarchy is:

**Country → Province → District → Municipality → Ward**

### KB-BR-LOC-002 — Local Geography

The product should additionally support:

**Locality / Tole → Chowk / Landmark / Bazaar / Market**

### KB-BR-LOC-003 — Postal Code

Postal code is a distinct location attribute and must not be treated as a replacement for locality, tole, chowk, or other local naming.

### KB-BR-LOC-004 — Coordinates

Latitude/longitude may supplement structured location information but must not be the only representation of a user-friendly Nepal address.

### KB-BR-LOC-005 — Named Places

A named chowk, tole, bazaar, market, or landmark should be represented as a geographical place rather than incorrectly treating it as an administrative unit.

### KB-BR-LOC-006 — Example

A listing in Janakpur may reference a chowk such as Ramanand Chowk, Ram Janki Chowk, Pidari Chowk, Bhanu Chowk, or Kadam Chowk while separately storing its municipality, ward, and postal information.

These examples illustrate the model; they do not define a complete place catalogue.

# 14. Location Privacy Rules

### KB-BR-LOC-010 — Approximate Location

A public listing may expose an approximate location when permitted.

### KB-BR-LOC-011 — Exact Location

Exact residential or sensitive location must be protected according to explicit visibility rules.

### KB-BR-LOC-012 — Location Entitlement

Subscription entitlement alone must not be assumed to grant access to exact location.

Applicable seller consent, safety, privacy, and authorization conditions must also be satisfied.

### KB-BR-LOC-013 — Location Representation

Public location may be represented using an appropriate combination of:

- Municipality
- Ward
- Locality/Tole
- Chowk
- Landmark
- Approximate map area

The product should avoid unnecessarily precise exposure.

# 15. Search and Discovery Rules

### KB-BR-SEARCH-001 — Eligible Listings

Normal public search should return only listings eligible for public discovery.

Draft, deleted, restricted, or otherwise ineligible listings must not appear in normal public search unless an explicit rule permits them.

### KB-BR-SEARCH-002 — Category Filters

Filters must correspond to attributes applicable to the selected category.

### KB-BR-SEARCH-003 — Search Visibility

Restricted information must not become searchable or indexable merely because it exists in the underlying listing record.

### KB-BR-SEARCH-004 — Expired Listings

Expired listings should be removed from active discovery unless an approved historical/discovery rule permits otherwise.

### KB-BR-SEARCH-005 — Result Consistency

Search results and listing detail must apply consistent visibility and eligibility rules.

# 16. Favorites / Saved Listings Rules

### KB-BR-SEARCH-010 — Save

A registered user may save an eligible listing.

### KB-BR-SEARCH-011 — Duplicate Save

Saving an already-saved listing should be idempotent.

### KB-BR-SEARCH-012 — Unavailable Saved Listing

If a saved listing becomes unavailable, the saved record may remain while clearly reflecting its unavailable state, subject to retention rules.

# 17. Media Rules

### KB-BR-MEDIA-001 — Supported Media

Only approved media types and sizes may be uploaded.

### KB-BR-MEDIA-002 — Validation

Media must pass applicable type, size, safety, and processing validation before becoming available for public display.

### KB-BR-MEDIA-003 — Primary Media

A listing may have one designated primary image where the product requires one.

### KB-BR-MEDIA-004 — Ordering

Listing media order must be deterministic.

### KB-BR-MEDIA-005 — Failed Upload

A failed upload must not be treated as a successfully attached listing asset.

### KB-BR-MEDIA-006 — Replacement

Replacing media must not unintentionally remove unrelated valid media.

# 18. Contact and Communication Rules

### KB-BR-CONTACT-001 — Eligible Contact

A user may contact a poster only when the listing, user, account, and communication method are eligible.

### KB-BR-CONTACT-002 — Contact Visibility

Direct contact information must follow explicit visibility rules.

### KB-BR-CONTACT-003 — Restricted Contact

A contact button must not reveal restricted contact information until all applicable access conditions are satisfied.

### KB-BR-CONTACT-004 — Safety

Reporting/blocking/safety mechanisms should remain available where the communication model supports them.

### KB-BR-CONTACT-005 — Communication Audit

Important communication events may require audit records according to security, abuse-prevention, and compliance requirements.

### V1 Contact/Location Decision Summary — 2026-10-04

- Exact location entitlement code: `listing.exact_location`.
- Direct contact entitlement code: `listing.direct_contact`.
- Seller consent defaults: **false** for exact location and direct contact.
- In-app messaging consent defaults: **true** through `allow_in_app_contact`, subject to safety/blocking rules.
- Paid entitlement never overrides seller consent or higher-priority privacy/safety rules.
- Owner/business scope may access its own protected listing information without purchasing an entitlement.
- Public and ordinary registered-user listing responses expose only approximate/administrative location and never direct contact details.
- The API must return an access descriptor when protected fields are withheld, without exposing the protected value.

### KB-BR-LOC-014 — Exact Location Access

Exact location is a protected paid capability. A caller receives exact coordinates and address_line only when all of the following are true: the caller is authenticated; the listing is Published; the caller has an active `listing.exact_location` entitlement; the listing owner has explicitly enabled `exact_location_consent`; the caller is not blocked/restricted from the listing; and no moderation, privacy, safety, or account rule prohibits disclosure. The owner/business scope may view its own exact location without the paid entitlement.

### KB-BR-PRIV-006 — Listing-Level Consent Storage

Seller consent for protected listing disclosure is stored as authoritative listing state. V1 uses explicit opt-in fields on `listings`: `exact_location_consent` and `direct_contact_consent`. Both default to **false**. Consent may be revoked at any time and revocation takes effect immediately for future API responses; previously disclosed information cannot be technically recalled from a viewer.

### KB-BR-CONTACT-006 — Direct Contact Access

Direct seller contact details (for example verified phone/email) are a protected paid capability. A caller receives them only when authenticated, the listing is Published, the caller has an active `listing.direct_contact` entitlement, `direct_contact_consent=true`, and no authorization, privacy, safety, moderation, account, or block rule prohibits disclosure. The listing owner/business scope may view its own configured contact details without the paid entitlement.

### KB-BR-CONTACT-007 — In-App Conversation

In-app messaging is distinct from direct contact-detail disclosure. An authenticated user may start a conversation when the listing is Published, `allow_in_app_contact=true`, the caller is not blocked/restricted, and the communication policy permits contact. V1 does **not** require the paid direct-contact entitlement merely to start an in-app conversation. Direct phone/email disclosure remains entitlement- and consent-gated.

# 19. Reporting and Safety Rules

### KB-BR-MOD-001 — Report Eligibility

A user may submit a report only when the target and reporting action are eligible.

### KB-BR-MOD-002 — Report Reasons

Reports must use approved reason categories.

### KB-BR-MOD-003 — Report Creation

A valid report creates a moderation record.

### KB-BR-MOD-004 — Duplicate Reports

The system should define how repeated reports for the same target/reason are handled to avoid unnecessary duplicate cases while preserving useful evidence.

### KB-BR-MOD-005 — No Automatic Punishment

Submitting a report does not by itself establish that the target violated a rule.

Subsequent action follows the moderation process.

# 20. Moderation Rules

### KB-BR-MOD-010 — Authorization

Only authorized moderators/administrators may perform moderation actions.

### KB-BR-MOD-011 — Evidence

Moderation decisions should retain sufficient evidence/context for operational review where appropriate.

### KB-BR-MOD-012 — Auditing

Material moderation actions must be auditable.

### KB-BR-MOD-013 — State Change

Moderation actions may change listing/account state only when the actor has authority and the selected action is valid.

### KB-BR-MOD-014 — User Notification

Users should be notified of moderation outcomes when required by the applicable product policy.

# 21. Verification Rules

### KB-BR-USER-010 — Verification Scope

Verification is always tied to a defined subject and verification method.

### KB-BR-USER-011 — Verification Expiry

Where a verification method has an expiration or revocation condition, the product must not continue presenting it as current after that condition.

### KB-BR-USER-012 — Verification Display

The UI must not imply stronger verification than the underlying verification record supports.

# 22. Subscription and Entitlement Rules

### KB-BR-SUB-001 — Entitlement Source

Feature access must be determined from the user's current entitlement state, not merely from a UI selection.

### KB-BR-SUB-002 — Active Entitlement

An entitlement is active only when its applicable activation and validity conditions are satisfied.

### KB-BR-SUB-003 — Expired Entitlement

An expired entitlement must not continue granting protected functionality unless an explicit grace rule exists.

### KB-BR-SUB-004 — Feature Entitlement

Each paid/restricted feature should have an explicit entitlement definition.

Examples may include:

- Additional listing capability
- Contact access
- Enhanced seller features
- Exact location access where separately permitted
- Business features

These are examples, not approved commercial commitments.

### KB-BR-SUB-005 — Entitlement Does Not Override Safety

An entitlement cannot override higher-priority privacy, safety, moderation, authorization, or seller-consent rules.

# 23. Payment Rules

Payment rules should remain provider-neutral at the product level.

### KB-BR-PAY-001 — Payment Intent

A payment attempt should represent an intentional attempt to purchase an approved product/plan/feature.

### KB-BR-PAY-002 — Payment Status

Payment state must distinguish at least the conceptual outcomes:

- Pending
- Successful
- Failed
- Cancelled
- Expired
- Refunded where supported

### KB-BR-PAY-003 — Provider Reference

Provider transaction/reference identifiers should be retained where necessary for reconciliation.

### KB-BR-PAY-004 — Access After Payment

A successful payment must result in entitlement activation only after the product's payment-confirmation conditions are satisfied.

The UI must not grant protected access solely because a client reports success.

# 24. Business / Representation Rules

### KB-BR-BIZ-001 — Representation Context

A business or representative may act on behalf of another person/entity only within its authorized scope.

### KB-BR-BIZ-002 — Member Roles

Business membership may distinguish roles such as:

- Owner
- Administrator
- Manager
- Agent
- Staff

Exact permissions belong in **04. Users, Roles & Permissions**.

### KB-BR-BIZ-003 — Listing Attribution

Listings created through a business/representation context should preserve appropriate attribution to the responsible poster and representation context.

# 25. Notification Rules

### KB-BR-USER-020 — Relevant Events

Notifications should be generated only for approved product events.

Potential events include:

- Listing publication
- Listing status changes
- Contact requests
- Messages
- Moderation actions
- Saved-search matches
- Security/account events

### KB-BR-USER-021 — Preferences

Where notification preferences exist, delivery should respect the user's applicable preferences except where a security/mandatory notification is required.

### KB-BR-USER-022 — Delivery Failure

A failed delivery should not incorrectly be represented as successful delivery.

# 26. SEO and Public Visibility Rules

### KB-BR-SEARCH-020 — Public Eligibility

Only content explicitly eligible for public discovery may be exposed to search engines.

### KB-BR-SEARCH-021 — Restricted Data

Restricted/private information must not be exposed through:

- HTML source
- metadata
- structured data
- URLs
- API responses intended for public clients
- search indexes

when the viewer is not authorized.

### KB-BR-SEARCH-022 — Listing URL

Each publicly eligible listing should have a stable canonical public URL.

### KB-BR-SEARCH-023 — Unavailable Listing

The product should define how deleted, expired, and removed listing URLs behave for users and search engines.

Exact technical implementation belongs in SEO/architecture documentation.

# 27. Data Integrity Rules

### KB-BR-DATA-001 — Unique Identity

Primary business entities must have stable identifiers.

### KB-BR-DATA-002 — Referential Integrity

Relationships between users, listings, categories, locations, media, reports, and entitlements must remain consistent.

### KB-BR-DATA-003 — State Consistency

A record must not simultaneously represent incompatible lifecycle states.

### KB-BR-DATA-004 — Historical Trace

Important state changes should preserve sufficient history where required for moderation, auditing, troubleshooting, or business operations.

# 28. Abuse Prevention Rules

The product should define controls for:

- Excessive listing creation
- Spam
- Automated abuse
- Repeated reports
- Contact abuse
- Malicious media
- Fraud indicators
- Account creation abuse
- Rate-limited actions

Exact thresholds should be measurable and documented when finalized.

# 29. Rule Precedence

When rules conflict, the product should apply the following conceptual precedence:

1. Safety / legal / mandatory compliance constraints
2. Security and authorization
3. Explicit privacy restrictions
4. Approved product/business rules
5. User entitlements
6. UX convenience

A subscription entitlement or UI configuration must not override a higher-priority security, privacy, safety, or authorization rule.

# 30. Business Rule and UX Relationship

UX/UI should communicate business rules but must not become the enforcement layer.

Example:

**Rule:** Exact location is restricted.

**UX:** Show approximate location and an appropriate restricted-access explanation.

**Server:** Do not return the exact location to an unauthorized client.

**Test:** Verify unauthorized clients cannot obtain the protected value.

# 31. Business Rule and Technical Architecture Relationship

Business rules define product behavior.

Technical architecture defines how the system implements that behavior.

For example:

**Business Rule:** A published listing must satisfy required validation.

Possible later technical implementation:

**API → Validation Service → Domain Rule → Database Transaction → Listing State**

The technical design should preserve the rule without redefining it.

# 32. Traceability

Recommended chain:

**Requirement → User Story → Use Case → User Flow → UX/UI → Business Rule → API → Database → Test**

Example:

**Create Listing**

→ Requirement  

→ UC-004 Create Listing  

→ UF-004  

→ UX-006 through UX-010  

→ KB-BR-LIST-010 through KB-BR-LIST-015  

→ API specification  

→ Database model  

→ Acceptance tests

**Exact Location**

→ Location requirement  

→ View Listing / Contact use case  

→ UF-011 / UF-013  

→ UX-005 / UX-014  

→ KB-BR-LOC-010 through KB-BR-LOC-013  

→ Authorization/API rules  

→ Location data model  

→ Security/privacy tests

# 33. Rule Review Checklist

Before a business rule is approved:

- Rule has a stable ID.
- Purpose is clear.
- Scope is clear.
- Actor/subject is clear.
- Preconditions are defined.
- Trigger/action is defined.
- Result is defined.
- Exceptions are considered.
- Permission implications are considered.
- Privacy implications are considered.
- Related requirements are identified.
- Related user flows are identified.
- UX impact is identified.
- Technical implications are identified.
- Testability is established.
- Status is explicitly recorded.

# 34. Open Product Decisions

The following remain intentionally open and should not be treated as approved rules until separately decided:

- Exact listing expiration duration
- Exact paid listing limits
- Subscription pricing
- Subscription duration
- ~~Exact contact-information entitlement~~ — **RESOLVED 2026-10-04** by KB-BR-CONTACT-006/007 and the API contract in Document 14.
- ~~Exact-location entitlement~~ — **RESOLVED 2026-10-04** by KB-BR-LOC-014 and the API contract in Document 14.
- ~~Seller consent model for restricted information~~ — **RESOLVED 2026-10-04** by KB-BR-PRIV-006 and the listing-level consent fields in Document 13.
- Exact moderation thresholds
- Report escalation rules
- Exact verification levels
- Payment providers
- Refund policy
- Grace periods
- Category-specific required fields
- Exact media limits
- Exact abuse/rate-limit thresholds
- Final business-member permission matrix
- Final communication model
- Final account-deletion/retention policy

Where a decision materially affects architecture, record it in the ADR register.

# 35. Relationship to Other Documents

| Document | Relationship |
| --- | --- |
| 03. Requirements Specification | Defines required capabilities and constraints |
| 04. Users, Roles & Permissions | Defines actors and permission boundaries |
| 05. User Stories & Use Cases | Defines user goals and scenarios |
| 06. User Flows | Defines process/state/permission flows |
| 07. UX/UI Specification | Defines how rules are represented in the interface |
| 08. Product & Business Rules | Defines governing product behavior |
| 09. Software Architecture | Defines technical implementation structure |
| 13. Database Architecture | Defines persistent data representation |
| 14. API Specification | Defines system interfaces enforcing rules |
| 19. Security Architecture | Defines security controls supporting rules |

# 36. Document Status

**Status:** Active  

**Version:** 1.0  

**Document ID:** KB-PROD-008

This document establishes the baseline product/business-rule framework. Specific commercial thresholds and unresolved policy decisions remain open until explicitly approved.

# 37. Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-PROD-008 |
| Document | 08. Product & Business Rules |
| Status | Active |
| Version | 1.0 |
| Owner | KHOJ BHET Product |
| Last Reviewed | 2026-09-23 |
| Parent | 01. PRODUCT DEFINITION |
| Previous | 07. UX/UI Specification |
| Next | 09. Software Architecture |
| Related | 03. Requirements Specification, 04. Users, Roles & Permissions, 05. User Stories & Use Cases, 06. User Flows, 07. UX/UI Specification, 00.2 Terminology & Glossary, 00.3 Decision / ADR Register |

## 38. Decision Resolution Log — 2026-10-04

### Business-member permission matrix — RESOLVED

The previously open **final business-member permission matrix** in section 34 is now resolved for V1 by the approved matrix in **04. Users, Roles & Permissions, section 24**. Document 14 section 7.2 adopts the same matrix as the API authorization baseline.

**V1 roles:** `owner`, `admin`, `manager`, `member`.

**Approved capability boundary:**

- Owner/Admin: business profile and member administration; full business-listing lifecycle operations within scope.
- Manager: create/edit/submit/pause/resume business listings; no member administration or archive/delete authority.
- Member: create/edit business listings and represent the business; no submit/pause/resume/archive/delete or member administration authority.
- No business role grants platform-wide admin or moderation authority.

The old section-34 bullet remains historical text; this resolution is authoritative for V1 and supersedes that open status.

## 39. V1 Listing Expiration & Renewal Decision — 2026-10-04

**Decision status: APPROVED / ACTIVE**

This section resolves the previously open **exact listing expiration duration and renewal limits**. It is authoritative for product behavior; Document 14 defines the API contract and Document 13 provides the persistence model.

### 39.1 V1 Validity Duration

- Every listing that reaches **Published** receives a **30-calendar-day validity period**.
- The authoritative expiration timestamp is expires_at on the listing.
- The 30-day period begins from the timestamp at which the listing enters Published state.
- Draft and Review listings do not consume published validity time.
- All V1 listing types use the same 30-day default. Category-specific or listing-type-specific durations are deferred and must not be inferred by clients.

### 39.2 Expiration Behavior

- When expires_at is reached, the listing becomes **Expired** deterministically.
- An Expired listing is not eligible for normal public search, recommendations, feeds, or SEO discovery.
- Expiration must be recorded in listing_lifecycle_events.
- Expiration does not delete the listing or its media/history.
- There is **no V1 grace period** after expiration.
- A scheduled/background lifecycle process is responsible for enforcing expiration; API reads must also treat an overdue Published/Paused listing as no longer active even if asynchronous processing has not yet run.

### 39.3 Pause and Expiration

- Pausing a Published listing does **not** stop or reset its validity clock.
- expires_at remains unchanged while Paused.
- If the expiration time is reached while Paused, the listing becomes Expired and cannot be resumed directly.

### 39.4 Renewal

- Renewal is an explicit owner/authorized-business action through POST /listings/{id}/renew.
- Renewal is allowed only for an eligible **Expired** listing and an authorized owner or business representative.
- V1 renewal duration is **30 calendar days**.
- There is **no hard lifetime/consecutive-renewal count limit in V1**. Abuse, moderation, account restrictions, and subscription/listing-limit rules may still prevent renewal.
- Renewal is **not automatic** and does not occur merely because the listing previously had an active subscription or entitlement.
- A renewal request does **not** immediately return the listing to Published. It transitions the listing to **Review** because publication always requires moderation/review.
- The new 30-day validity period starts only when the renewal is approved and the listing re-enters Published state.
- If renewal review is rejected, the listing remains non-public and the rejection is recorded through the normal moderation/lifecycle records.

### 39.5 Renewal Validation

A renewal must re-check, at minimum:

1. listing ownership/authorized business representation;
2. account status and applicable restrictions;
3. category and listing-type eligibility;
4. required listing data and category attributes;
5. media and location requirements;
6. current privacy/contact consent configuration;
7. moderation/safety eligibility; and
8. applicable subscription/entitlement/listing-limit rules.

Renewal must not bypass the normal publication review requirement.

### 39.6 Renewal Idempotency and Concurrency

- POST /listings/{id}/renew is an authenticated state-changing operation and supports the durable API idempotency mechanism defined in Document 13 and Document 14.
- Repeating the same idempotency key with the same request payload returns the original result.
- A concurrent renewal request must not create multiple renewal transitions or duplicate lifecycle events.

### 39.7 Expiration Notifications

The notification module should issue owner-facing reminders before expiration at approximately **7 days** and **1 day** before the current expires_at.

Reminder delivery is best-effort and must not alter the authoritative expiration timestamp or lifecycle state.

### 39.8 Public/API Consequences

- Public listing responses must expose expiration metadata only where the API contract permits it; protected/internal lifecycle data must not be leaked.
- Expired listings may remain visible to their owner/authorized business scope for management and renewal.
- Public clients must not treat an expired listing as active merely because its record still exists.

### 39.9 Traceability

- Product authority: this section in **08. Product & Business Rules**.
- API authority: **14. API Specification**, Gate API-GATE-03.
- Persistence: Document 13 listings.expires_at and listing_lifecycle_events.
- Search rule: KB-BR-SEARCH-004 — Expired listings are excluded from active discovery.
- Lifecycle rules: KB-BR-LIST-026 and related lifecycle rules.

## 40. V1 Subscription Pricing, Grace Period & Listing Limits Decision — 2026-10-04

**Decision status: APPROVED V1 / ACTIVE**

This section resolves API-GATE-04. Subscription commercial values are configuration data, not API constants; the V1 plan catalogue, limits, billing periods, grace policy, and entitlement semantics are fixed for the initial implementation baseline.

### 40.1 V1 Plan Catalogue

| Plan | Monthly Price | Active Listing Limit | Primary Purpose |
| --- | --- | --- | --- |
| Free | NPR 0 | 3 | Ordinary marketplace participation |
| Plus | NPR 199 | 10 | Higher-volume individual users and protected buyer capabilities |
| Business | NPR 999 | 50 | Businesses/agencies/dealers with higher listing capacity |
- Prices are denominated in **NPR**.
- V1 billing period is **monthly** for paid plans.
- Paid plans are optional; Free remains a valid marketplace plan.
- Plan prices are stored in authoritative plan records and must not be hard-coded into clients.
- An already-active paid subscription retains its agreed commercial terms for its current billing period when future plan pricing changes.

### 40.2 Listing Limit Semantics

- The listing limit means the maximum number of **active managed listings** attributable to the subscription owner/account at one time.
- Draft listings do not consume the active quota until they enter Published.
- Published and Paused listings count toward the limit.
- Expired and Archived listings do not count toward the active limit.
- A user/business may not create or renew into a state that would exceed the applicable limit.
- Renewal is checked against the current applicable limit at approval.
- Business member roles do not independently multiply the business listing limit; the Business account/subscription is the quota owner.

### 40.3 Entitlement Semantics

- Subscription status is an **entitlement source**, not a replacement for authorization.
- A plan may grant feature entitlements, including protected capabilities such as listing.exact_location and [listing.direct](http://listing.direct)_contact, but seller consent, privacy, safety, authentication, listing state, and authorization remain mandatory.
- Plan entitlement changes are evaluated server-side.
- Expired, cancelled, suspended, or otherwise inactive subscriptions do not continue granting protected paid entitlements after their effective end.

### 40.4 Subscription Duration and Renewal

- Paid subscriptions use a one-month billing period.
- Subscription renewal is explicit through the payment/subscription flow; V1 does not assume automatic card/wallet charging.
- V1 initially uses manual/admin-approved payment, so a paid subscription becomes active only after payment acceptance and activation rules are satisfied.
- Renewal before expiry extends the subscription from the current end without overlapping entitlement periods.
- A new subscription after expiry starts from the approved activation time.

### 40.5 Grace Period Policy

- **V1 subscription grace period: 3 calendar days.**
- Grace begins immediately after a paid subscription reaches its scheduled ends_at when the account has an unresolved renewal/payment state.
- During grace, existing paid entitlements remain temporarily available for completing renewal, subject to the subscription state rules.
- Grace does **not** increase the listing quota and does **not** bypass seller consent, privacy, safety, moderation, or authorization.
- New paid-only access must not be treated as permanently active solely because grace exists.
- Successful renewal during grace restores active subscription status according to the renewal rules.
- If grace ends without successful renewal, paid entitlements terminate and Free-plan capabilities/limits apply.
- Grace is not a listing-expiration grace period; listing expiration remains governed by API-GATE-03 and has no grace period.

### 40.6 Cancellation / Downgrade

- Cancellation stops future renewal but does not retroactively invalidate the already-paid subscription period.
- At paid-subscription end, the account is evaluated against Free-plan limits.
- Existing listings above the Free quota are **not silently deleted**. They remain retained, but new listings and renewals that would exceed the active limit are blocked.
- The product may require the owner to select which listings remain active when quota reduction is required; server-side quota enforcement remains authoritative.

### 40.7 Commercial and API Safety

- Plan price, currency, duration, limits, and feature entitlements are server-controlled.
- Clients must not calculate authorization from displayed price or plan labels.
- Payment success alone does not grant an entitlement until the authoritative payment/subscription state is activated.
- Refunds, reversals, administrative suspension, and fraud controls may revoke or adjust entitlement according to authoritative payment/subscription state.
- Historical payment and subscription records remain auditable.

### 40.8 V1 Boundary

Explicitly deferred from V1: annual plans; promotional coupons/discount engines; family/team pooled subscriptions; automatic recurring wallet/card charging; prorated upgrades/downgrades; usage-based billing; category-specific listing quotas; unlimited plans.

### 40.9 Traceability

- Product authority: **08. Product & Business Rules**, this section.
- API authority: **14. API Specification**, API-GATE-04.
- Persistence authority: **13. Database Architecture & Data Model**, plans/subscriptions/entitlements/payment_intents.
- Payment architecture: provider-neutral manual/admin-approved V1 payment path.

## 41. V1 Moderation Thresholds & Escalation Decision — 2026-10-04

**Status: APPROVED / CLOSED**

V1 moderation is risk-based, server-authoritative, and auditable.

### Moderation outcomes

- **ALLOW:** no blocking rule or unresolved review condition; publication may proceed after all other gates pass.
- **REVIEW:** medium-risk content or configured escalation trigger; listing remains non-public pending human review.
- **BLOCK:** confirmed prohibited content or severe fraud/safety/legal violation; publication is prevented until the blocking condition is resolved and a new review is completed.

### Risk thresholds

- **50–79:** mandatory human Review.
- **80–100 + hard-policy signal:** Block.
- A score alone without a hard-policy signal does not permanently Block; it routes to Review.

### Report thresholds

- **1 report:** record only; no automatic unpublish solely from one unverified report.
- **3 reports on one listing within 24 hours:** suspend public visibility and escalate to High.
- **5 reports within 24 hours:** escalate to Urgent and keep visibility suspended pending review.
- Confirmed severe safety/fraud/legal reports may immediately suspend visibility regardless of count.
- Counts are deduplicated per reporter/listing/reason/window.

### Review targets

- Urgent: 4 hours.
- High: 24 hours.
- Normal: 72 hours.

These are operational targets, not end-user guarantees.

### V1 moderation actions

`warn`, `request_changes`, `suspend_listing`, `reject_listing`, `restore_listing`, `restrict_account`, `escalate`, `close_case`.

Every admin action records actor, reason, target, timestamp, and relevant metadata. Re-review/appeal is supported; restored listings must pass the normal publication gate again. Moderation history remains auditable.

### Enforcement constraints

Moderation and listing lifecycle are separate authorities. Clients cannot bypass moderation through status fields. Thresholds live in server configuration/registry. Safety-critical hard rules fail closed; unavailable required moderation dependencies route content to Review rather than Publish.

**Decision:** Gate #5 is CLOSED. Document 14 API-GATE-05 is the API contract for these rules; Document 13 provides moderation persistence; implementation must not introduce conflicting thresholds.

## 42. V1 Media Limits & Upload Policy Decision — 2026-10-04

**Status: APPROVED / CLOSED**

V1 listing media limits are defined centrally and enforced server-side. Limits apply across web and mobile clients and are configuration values, not client-side constants.

### Listing media limits

- **Images:** maximum **20 images per listing**.
- **Video:** maximum **1 video per listing**.
- **Total media:** maximum **21 media objects per listing** (20 images + 1 video).
- One image may be designated as the primary/cover media.
- Video is optional; listings do not require video.
- Media ordering is explicit and persisted through the listing-media relationship.

### File limits

- **Image maximum:** **10 MB per original upload**.
- **Video maximum:** **50 MB per upload**.
- **Video duration:** maximum **60 seconds**.
- Accepted image formats: JPEG, PNG, WebP.
- Accepted video format: MP4 (H.264/AAC baseline for V1).
- SVG, executable formats, archives, documents, and arbitrary MIME types are not accepted as listing media.
- The server validates the actual file signature/content type; client-supplied MIME type is never trusted by itself.

### Processing

- Uploaded media is treated as untrusted input.
- Images are normalized/processed asynchronously where appropriate and may generate thumbnails/variants.
- Video processing is asynchronous; publication must not expose an unprocessed or failed media object as a public asset.
- Failed processing marks the media unavailable and must not bypass publication/moderation requirements.
- Original and derived media metadata remain associated with the authoritative media record.
- Storage remains behind the V1 storage abstraction and uses local application/server storage.

### Replacement/deletion

- Authorized listing editors may remove or reorder media while the listing is editable.
- Editing a Published listing, including a material media change, returns the listing to Review according to the approved lifecycle policy.
- Deleted/replaced media is not exposed through public listing responses after authorization/visibility checks.
- Media referenced by audit/history must remain traceable according to the retention policy.

### Abuse and quota interaction

- Per-file limits and per-listing limits are separate from API rate limits.
- Upload attempts that exceed limits are rejected before storage is finalized.
- Repeated failed/abusive uploads remain subject to the separate rate-limit and abuse-control policy.
- Subscription plans do **not** increase media limits in V1; Free, Plus, and Business use the same per-listing media limits.

### Decision

These limits are the V1 product baseline. Future category-specific media limits, higher video limits, additional video formats, and larger object-storage uploads require an explicit product/architecture decision.

**Decision:** Gate #6 is CLOSED.

## 43. V1 Rate-Limit & Abuse-Control Decision — 2026-10-04

**Status: APPROVED for V1.** This decision closes Gate #7 and replaces the earlier Proposed defaults wording for rate-limit thresholds.

### 43.1 Principles

- Rate limiting protects availability, fairness, authentication, messaging, media, reporting, and paid-capability endpoints from overload and abuse.
- Limits are enforced server-side. Client-side throttling is UX only.
- Redis may be used for counters and distributed atomic limiting. MySQL remains the transactional source of truth.
- Limits are independent from business listing quotas, subscription limits, moderation thresholds, and media-per-listing limits.
- A legitimate request that exceeds a technical rate limit receives HTTP 429; a business-policy violation uses authorization/business-rule errors.
- Anonymous abuse controls may combine IP, network reputation, and short-lived device/browser signals. Authenticated controls may combine user, IP, and device signals.
- No single identifier is trusted as the only abuse signal.

### 43.2 Approved V1 Thresholds

| Scope | Applies to | Key | Limit |
| --- | --- | --- | --- |
| Public read | Browse, public listing detail, public reference/search reads | IP | 120/minute |
| Authenticated read | Authenticated GET endpoints | User | 240/minute |
| Standard write | Create/edit/favorite/ordinary commands | User | 60/minute |
| Auth bootstrap | POST /auth/session | User + IP | 5/minute |
| Contact reveal | POST /listings/{id}/contact-reveals | User + IP | 10/minute |
| Conversation creation | POST /listings/{id}/conversations | User + IP | 10/minute |
| Message send | Message creation | User + conversation | 30/minute and 300/hour |
| Report submit | Report creation | User + IP | 5/hour |
| Media upload | Listing media upload | User | 20/hour |
| Listing publish/submit | Submit/re-submit commands | User | 10/hour |
| Listing renew | Renewal command | User | 10/hour |
| Payment initiation | Payment intent creation/retry | User | 10/hour |
| Search | Search/filter requests | IP or authenticated user | Covered by public/authenticated read limit |
| Webhooks | Provider callbacks | Provider signature/source | Provider-specific |

These are enforcement defaults for V1. They may be tightened operationally during an incident without changing the product contract, but a material permanent change requires a new decision.

### 43.3 Window and Burst Behaviour

- Limits use a sliding-window or equivalent token-bucket implementation with atomic distributed enforcement.
- Short bursts are permitted within the stated limit; sustained traffic is bounded by the same rate.
- Separate endpoint limits do not create an unlimited aggregate allowance. Global user/IP abuse controls may apply in addition to endpoint limits.
- The media limit is a rolling 60-minute limit, not merely a per-request burst allowance.
- A successful retry protected by an idempotency key must not create a second business operation, although the HTTP request may still consume rate-limit budget.

### 43.4 Abuse Escalation

1. First threshold breach: return 429 with Retry-After.
2. Repeated breaches from the same user/IP/device within 15 minutes: temporary endpoint throttle.
3. Continued coordinated abuse: temporary account or network restriction using account_restrictions where an authenticated account is implicated.
4. Severe automated abuse, credential attacks, spam, malicious payloads, or deliberate evasion may trigger immediate security controls and administrative review.

Security controls must avoid permanently blocking users solely from one transient 429 event.

### 43.5 Special Rules

- OTP/password delivery is handled by Firebase Authentication/provider controls and is not reimplemented as a marketplace API quota.
- Listing active-count limits remain the subscription/business rule; exceeding them is not a 429.
- Media-per-listing limits remain the media policy; exceeding 20 images, 1 video, or the per-file size/duration limit is a validation/business-rule failure, not a rate-limit event.
- Report thresholds for moderation escalation remain separate from report submission rate limits.
- Paid plans do not receive higher API rate limits in V1.
- Admin/Filament traffic uses separate operational controls and is not constrained by the public client quotas above.

### 43.6 429 Contract

When a technical rate limit is exceeded:

- HTTP status: 429 Too Many Requests
- Problem Details code: rate_limited
- Retry-After: integer seconds until the relevant limit can be retried
- Response includes RateLimit-Limit, RateLimit-Remaining, and RateLimit-Reset
- X-Request-Id is always present
- Error details never disclose internal counters, detection rules, reputation scores, or other security-sensitive signals.

### 43.7 Acceptance

**Gate #7 — Rate-limit and abuse thresholds: CLOSED — 2026-10-04.**

## 44. V1 Communication, Read-State & User-Safety Decision — 2026-10-04

**Decision status: APPROVED / ACTIVE for V1.**

### Communication

- V1 in-app communication is listing-originated and authenticated.
- Conversations are two-party threads between the initiating user and listing-side recipient.
- Conversation creation requires a Published listing, allow_in_app_contact=true, authentication, and successful account, moderation, privacy, safety, and communication checks.
- Business-owned listings route new conversations to the active primary business representative; historical participants remain unchanged.
- Duplicate creation for the same listing and same two users returns the existing active conversation.
- In-app messaging is distinct from direct phone/email disclosure.

### Read state

- Each conversation participant has a last_read_message_id cursor and server-maintained last_read_at timestamp.
- The read cursor advances only forward.
- unread_count is derived from messages after the participant cursor and is not an independent authoritative counter.
- [notifications.read](http://notifications.read)_at remains independent from conversation read state.

### User safety relationship

- V1 supports a directional user-to-user safety relationship that prevents unwanted communication.
- A user cannot create the relationship with themselves or duplicate an existing relationship.
- While active, the affected user cannot start a new conversation, send new messages, or receive new messages through the relationship.
- Existing conversations and messages are retained; the safety relationship is not deletion.
- Removing the relationship restores communication eligibility only after all normal listing, account, consent, safety, moderation, and communication checks pass.
- Reporting remains available while communication is unavailable.

### V1 boundaries

- No group conversations, message editing, forwarding, reactions, disappearing messages, or per-message read receipts.
- Typing/presence may be ephemeral realtime UX and is not authoritative persisted state.
- Listing expiration does not delete existing conversations.
- Protected seller contact details must not be exposed through historical message or conversation responses.

### Traceability

- Persistence authority: Document 13 section 55.
- API authority: Document 14 API-GATE-08.
- Existing contact consent: KB-BR-CONTACT-007 and the 2026-10-04 contact/location decision.
- Rate controls: API-GATE-07.
- Account retention remains governed by Gate #9.

**Gate #8 — Communication, Read-State & User-Safety Model: CLOSED — 2026-10-04.**

## Gate #9 — Account Deletion & Retention Policy — 2026-10-04

**Status: CLOSED / Approved V1**

### KB-BR-USER-010 — Deactivation Is Reversible

Deactivation is a reversible account state, not personal-data deletion. A deactivated account loses normal interactive marketplace access; its existing marketplace records are retained according to the applicable retention rules. `POST /me/deactivation` and `POST /me/reactivation` are idempotent state operations.

### KB-BR-USER-011 — Deletion Request and Cooling-Off Period

An eligible authenticated user may request account deletion through `POST /me/deletion-requests`. The request creates a durable deletion request and moves the account into `deletion_pending`. V1 uses a **30-calendar-day cooling-off period**.

During the cooling-off period:

- normal marketplace access is disabled;
- active listings are removed from public discovery and cannot be newly published;
- existing conversations remain retained but cannot receive new messages from the pending account;
- subscriptions/entitlements do not extend because of the deletion request;
- the user may cancel the request through `POST /me/deletion-requests/cancel` and return to Active if no blocking administrative/legal condition exists.

Repeated deletion requests while one is pending are idempotent and return the existing pending request.

### KB-BR-USER-012 — Final Account Deletion

When the 30-day cooling-off period expires, the platform executes deletion as an asynchronous server-side workflow. The account becomes `deleted`/anonymized only after the authoritative transaction is committed.

The workflow must:

1. disable marketplace authentication and interactive access;
2. revoke active sessions/tokens and application access;
3. remove the account from normal public/profile discovery;
4. anonymize or detach personal profile/contact fields that are not required for retention;
5. archive/remove the user's active marketplace listings from discovery;
6. remove non-essential user-owned preferences and saved data;
7. remove Firebase Authentication identity after the Laravel/MySQL deletion workflow reaches its safe terminal stage;
8. preserve only records required for legal, financial, security, fraud, moderation, dispute, or audit purposes.

Deletion must be retry-safe and must not produce a partially deleted public account.

### KB-BR-USER-013 — Retained Records

The following V1 retention policy applies:

- **Financial/payment/tax/accounting records:** retain for **7 years** or the longer period required by applicable law.
- **Security, fraud, moderation, report, and audit evidence:** retain for **7 years** or the longer period required by applicable law or an active dispute/investigation.
- **Conversation/message history:** retain for **24 months after account deletion**, unless required longer for safety, fraud, dispute, or legal purposes.
- **Operational deletion-request records:** retain for **7 years** as audit evidence.
- **Backups containing deleted personal data:** expire through the normal backup lifecycle and must not be restored as a way to re-create a deleted account; target maximum backup retention is **35 days**.
- **Non-essential profile/contact data:** delete or irreversibly anonymize as part of final deletion.
- **Derived search/cache/projection data:** remove or rebuild so the deleted account and its listings are no longer discoverable.

Retention does not authorize continued public display. Retained records are access-controlled and excluded from normal marketplace APIs.

### KB-BR-USER-014 — Listings Owned by a Deleted Account

A deleted user's listings are not transferred to another user automatically. Published/paused/draft listings become unavailable and are removed from normal discovery. Historical listing records may remain internally where required for moderation, disputes, payment, audit, or legal retention.

### KB-BR-USER-015 — Conversations and Safety Records

Account deletion does not erase evidence required for safety, abuse prevention, moderation, disputes, or legal compliance. Retained messages must not expose the deleted user's former private contact information through normal APIs. Where identity is no longer required, the deleted participant is represented using an anonymized/deleted-user reference.

### KB-BR-USER-016 — Firebase Authentication Coordination

Firebase Authentication is an identity provider, not the authoritative marketplace deletion store. Laravel/MySQL remains authoritative for marketplace account state and deletion workflow. Firebase UID linkage must not be used to recreate a deleted marketplace account automatically. Final Firebase identity deletion occurs only after the marketplace deletion workflow reaches its safe terminal stage.

### KB-BR-USER-017 — Administrative/Safety Holds

A deletion request cannot bypass an active legal hold, payment dispute, fraud investigation, moderation case, or administrator-imposed safety restriction. The platform may defer final personal-data deletion only for the minimum period necessary to satisfy the applicable hold/retention requirement, with the reason recorded in the deletion-request audit trail.

### V1 Account Deletion State Model

**Active → Deactivated → Active**  

**Active → Deletion Pending → Active** (cancellation during 30-day cooling-off)  

**Active/Deactivated → Deletion Pending → Deleted/Anonymized**

`Deleted` is terminal for the marketplace identity. Re-registration creates a new marketplace identity; Firebase UID reuse must not automatically restore the old account.

### Gate #9 Acceptance Criteria

- Deactivation and deletion are separate operations.
- 30-day deletion cooling-off period is explicit and cancelable.
- Deletion requests are durable and idempotent.
- Final deletion is asynchronous and retry-safe.
- Listings, conversations, reports, moderation, payments, audit, media, and Firebase identity have explicit treatment.
- Retained records are never public by default.
- Legal/safety holds can defer deletion only as necessary and must be auditable.
- `POST /me/reactivation` cannot resurrect a terminally deleted account.

## Gate #10 — Verification Levels beyond Phone/Email — 2026-10-04

**Status: CLOSED / Approved V1**

### KB-BR-USER-020 — Verification Is Subject-Specific

Verification is not a single global trust score. Every verification record identifies the subject, verification type, method, state, timestamps, and reviewer/process where applicable. A badge or API field must describe exactly what was verified.

Phone and email verification remain contact/authentication verification. They do not establish legal identity, business ownership, professional qualification, or listing legitimacy.

### KB-BR-USER-021 — V1 Verification Levels

V1 supports the following verification types:

| Verification type | Subject | V1 status | Purpose |
| --- | --- | --- | --- |
| `phone` | User | Active | Confirm control of the phone number |
| `email` | User | Active | Confirm control of the email address |
| `identity` | User | Active, optional | Verify a person's identity using approved identity evidence and review |
| `business` | Business | Active, optional | Verify a business/organization using approved registration/business evidence and review |
| `professional` | User | Deferred | No V1 professional-license/qualification verification workflow |
| `address` | User | Deferred | No standalone residential-address verification badge in V1 |
| `listing` | Listing | Existing moderation/verification process | Listing eligibility is not equivalent to identity verification |

Verification types are independent. `identity_verified` does not imply `business_verified`, `professional_verified`, `address_verified`, or `listing_verified`.

### KB-BR-USER-022 — Identity Verification

Identity verification is optional in V1 and is performed through an approved administrative review workflow. The platform may accept government-issued identity evidence approved for the product, such as Nepal citizenship documentation, National ID, passport, or driving licence, subject to the final verification procedure and applicable legal requirements.

The system must verify that the evidence is sufficient for the declared verification purpose. A successful identity verification establishes that the reviewed identity evidence matched the account subject to the extent defined by the verification procedure; it does not prove ownership of every listing or transaction.

Rejected, expired, withdrawn, or invalid evidence must not produce an active identity-verification state.

### KB-BR-USER-023 — Business Verification

Business verification is optional in V1 and applies to a specific Business entity, not automatically to every member of that Business.

V1 business review may use approved business-registration and tax/registration evidence appropriate to the organization's type. The platform must record what was verified without exposing internal evidence or sensitive document contents through public APIs.

A verified business does not automatically mean that every business member, listing, product, property, vehicle, service, or claim is independently verified.

### KB-BR-USER-024 — Verification States

Supported verification lifecycle states are:

- `pending` — submitted and awaiting review;
- `approved` — verification requirement satisfied;
- `rejected` — evidence/process did not satisfy the requirement;
- `expired` — previously approved verification is no longer valid;
- `revoked` — previously approved verification was withdrawn;
- `canceled` — verification attempt was canceled before completion.

Only `approved` is an active positive verification state. Expired/revoked/rejected/canceled records must not display an active verification badge.

### KB-BR-USER-025 — Verification Review and Reverification

Identity and business verification are reviewable, auditable processes. Administrators/authorized verification operators may approve, reject, request correction/re-submission, expire, or revoke a verification according to policy.

V1 does not automatically impose a universal periodic reverification interval. A verification may instead require re-review when evidence expires, material identity/business information changes, fraud/safety concerns arise, or an administrator requires it.

### KB-BR-USER-026 — Verification and Permissions

Verification is an input to eligibility, not a replacement for authorization. A verified user may still be restricted, suspended, blocked, or moderated.

Any feature that requires verification must name the exact required type and state. Examples:

- identity verification may be required for a future high-trust transaction or sensitive marketplace capability;
- business verification may be required for selected Business capabilities;
- phone verification may be required for communication or account-recovery operations.

Paid subscription/entitlement does not create or imply verification.

### KB-BR-USER-027 — Privacy and Evidence

Verification evidence is private/internal. Public APIs expose only the minimum verification label/state needed by the product.

Public responses must never expose identity-document numbers, document images, tax identifiers, internal review notes, reviewer identity, or verification evidence merely because a verification exists.

Verification evidence must follow the project's deletion/retention policy and applicable legal requirements.

### Gate #10 Acceptance Criteria

- V1 identity and business verification are explicitly supported and optional.
- Phone/email remain separate from identity verification.
- Verification is subject-specific and not a global trust score.
- Verification states and transitions are defined.
- Identity and business evidence are reviewed rather than blindly accepted.
- Verification does not automatically grant authorization.
- Public APIs expose only appropriate verification labels/states.
- Professional and standalone address verification are deferred.
- Listing verification/moderation remains distinct from user identity verification.

## Gate #11 — Push-device Token Persistence — 2026-10-04

**Status: CLOSED / Approved V1**

### Product and business rules

1. Push-device registration is a per-user, per-app-installation resource. One user may have multiple active devices.
2. V1 push provider is **Firebase Cloud Messaging (FCM)**, consistent with ADR-007. Provider-specific delivery is an implementation detail behind the notification module.
3. A push token is a delivery credential, **not** an authentication credential, identity proof, verification signal, or authorization grant.
4. Each app installation has a stable client-generated installation_id. The server may maintain one current active FCM token for each (user, installation_id, provider) tuple. Token rotation updates the existing registration rather than creating uncontrolled duplicates.
5. The same FCM token must not remain active on multiple authoritative device rows. Token identity is protected by a server-side hash/lookup key; the raw token is private and never returned by ordinary APIs.
6. Multiple devices may receive the same eligible notification. Notification preferences and notification eligibility remain separate from device-token persistence.
7. Device registration requires an authenticated marketplace user. Registration does not itself grant notification permission; the client OS permission state is recorded separately when supplied.
8. Logout/revocation removes that authenticated installation's active push registration. Other devices remain registered unless separately revoked.
9. Token refresh/rotation is idempotent. Invalid/unregistered provider feedback marks the registration invalid or revoked and it must no longer be selected for delivery.
10. Deactivated, deletion-pending, suspended, or otherwise communication-prohibited accounts must not receive normal push delivery. Account deletion removes active push registrations as part of the deletion workflow.
11. Notification delivery must tolerate stale devices. Provider failures for invalid/unregistered tokens trigger revocation/invalidation and do not repeatedly retry permanently invalid tokens.
12. Notification preferences do not delete a device token. They control whether an eligible notification may be delivered through that channel/category.
13. Push tokens, installation identifiers, provider responses, and device metadata are private operational data. They must not appear in public listing/profile resources, search results, analytics exposed to users, or ordinary public APIs.
14. V1 does not treat device fingerprinting, rooted-device state, advertising IDs, or hardware identifiers as authoritative identity/security controls.

### Approved V1 device states

- active — eligible for push delivery when notification/account rules allow it.
- revoked — explicitly disabled by user/server/logout/security action.
- invalid — provider indicates the token is no longer deliverable.

OS notification permission is a separate value: granted, denied, or unknown, and is not equivalent to token state.

### Persistence

Authoritative persistence is defined in Document 13 as user_push_devices. The table stores the encrypted token, a server-side token hash, installation identity, platform/provider, state, permission state, and operational timestamps. The raw FCM token is never exposed through ordinary API responses.

### Rate-limit/security alignment

Device registration/update operations are authenticated write operations and are subject to the standard authenticated write rate-limit policy. Token values are treated as sensitive credentials: TLS in transit, encrypted storage where retained, access restricted to notification infrastructure, and no token logging.

### Deferred

- APNs-direct provider records
- Expo-specific push tokens as a separate V1 provider
- Device trust scoring
- Device fingerprinting as identity/security authority
- Per-device notification-category overrides beyond the existing preference model

## Gate #13 — Final Report Reason/Target Code Registry — 2026-10-04

**Status: CLOSED / Approved V1**

### Registry authority

Document 08 defines the product meaning of report codes. Document 14 exposes the API enum contract. Document 13 persists the selected target/reason codes. The same stable codes must be used across UI, API, moderation, analytics, audit, and tests.

### V1 report target types

| Code | Target | V1 |
| --- | --- | --- |
| listing | Marketplace listing | Active |
| user | Marketplace user/profile | Active |
| message | In-app message | Active |

No business entity, conversation, media object, or arbitrary URL is a standalone V1 report target. A problematic business-owned listing is reported as the listing; a business-related user issue is reported against the user. A communication/content issue is reported against the specific message where a message target is available.

### V1 report reason registry

| Code | Meaning | Applicable target(s) |
| --- | --- | --- |
| spam | Repetitive, unwanted, bulk, or promotional abuse | listing, user, message |
| fraud_scam | Fraud, scam, deceptive transaction, or attempted financial abuse | listing, user, message |
| impersonation | Pretending to be another person, business, or organization | user, listing, message |
| misleading_information | Materially false, deceptive, or misleading listing/profile information | listing, user |
| prohibited_item_service | Prohibited or restricted item/service offered through the marketplace | listing, message |
| counterfeit | Suspected counterfeit, replica, or unauthorized imitation goods | listing, message |
| stolen_property | Suspected stolen goods/property | listing, message |
| illegal_activity | Suspected illegal activity or transaction | listing, user, message |
| unsafe_hazardous | Material safety, dangerous-goods, or hazardous-content concern | listing, message |
| harassment_abuse | Harassment, bullying, abusive conduct, or targeted abuse | user, message, listing |
| threats_violence | Threats of violence, credible intimidation, or violent solicitation | user, message, listing |
| hateful_content | Serious hateful or protected-group abuse | user, message, listing |
| sexual_content | Prohibited sexual content or sexual solicitation | user, message, listing |
| privacy_violation | Unauthorized disclosure, solicitation, or misuse of private/personal information | user, message, listing |
| malicious_link | Malicious, phishing, malware, or deceptive external link | listing, message |
| duplicate_listing | Duplicate or substantially repeated marketplace listing | listing |
| wrong_category | Listing is materially placed in the wrong category | listing |
| price_manipulation | Artificial, deceptive, or materially misleading price presentation | listing |
| intellectual_property | Suspected copyright, trademark, or other intellectual-property infringement | listing, message |
| other | Valid report that does not fit another approved category | listing, user, message |

### Applicability is server-authoritative

The API must reject a reason/target combination that is not in the registry. Clients must not determine applicability independently.

### Reporting behavior

- A report records an allegation; it does not establish that the target violated policy.
- One submitted report creates one authoritative report record.
- Duplicate/repeated reports are handled by existing deduplication and moderation-threshold rules.
- Severe safety/fraud/legal allegations may enter expedited moderation according to Gate #5, but the reason code itself does not automatically punish the target.
- other requires a human-readable explanation.
- Reason codes are stable identifiers; display labels and localized descriptions may change without changing the code.
- Deprecated codes remain recognizable for historical records but are not selectable for new reports.
- New V1 codes require controlled product/API change and Gate #14 enum reconciliation.

### Gate #13 acceptance

- [x]  Target types finalized.
- [x]  Reason codes finalized.
- [x]  Target/reason applicability finalized.
- [x]  Invalid combinations explicitly rejected.
- [x]  other behavior defined.
- [x]  Historical/deprecated-code behavior defined.
- [x]  Reporting does not equal confirmed violation.
- [x]  Existing moderation thresholds remain authoritative.

**Gate #13: CLOSED.**

## Gate #14 — Final Public API Enum Registry — Product/Business Alignment — 2026-10-04

**Status: CLOSED / APPROVED V1**

Document 14 is the authoritative public API enum registry. Document 08 adopts the registry for product-facing values; it does not create a second enum source.

### V1 public API enum rules

- Enum values are lowercase `snake_case` strings.
- Clients must send only registered values.
- Unknown values are rejected; they are never silently mapped to `other`, a default, or a legacy value.
- Deprecated values remain readable where historical compatibility requires them, but are not selectable for new writes.
- Adding, removing, renaming, or changing the meaning of a public enum is an API contract change and requires Document 14 review plus OpenAPI/contract-test updates.
- Internal moderation, audit, storage, provider, and infrastructure states are not exposed merely because the database stores them.

### Authoritative V1 registries

**Listing type**

- `sale`
- `rent`
- `lease`
- `free`
- `exchange`
- `offer`
- `wanted`
- `service`
- `job`

**Listing lifecycle status**

- `draft`
- `review`
- `published`
- `paused`
- `expired`
- `archived`
- `rejected`

**Visibility**

- `public`
- `restricted`
- `private`

**Pricing mode**

- `fixed`
- `negotiable`
- `range`
- `free`
- `contact_only`
- `upon_request`

**Price period**

- `once`
- `hourly`
- `daily`
- `weekly`
- `monthly`
- `yearly`
- `per_item`

**Verification type**

- `phone`
- `email`
- `identity`
- `business`

**Verification state**

- `pending`
- `approved`
- `rejected`
- `expired`
- `revoked`
- `canceled`

**Report target**

- `listing`
- `user`
- `message`

**Report reason**

- `spam`
- `fraud_scam`
- `impersonation`
- `misleading_information`
- `prohibited_item_service`
- `counterfeit`
- `stolen_property`
- `illegal_activity`
- `unsafe_hazardous`
- `harassment_abuse`
- `threats_violence`
- `hateful_content`
- `sexual_content`
- `privacy_violation`
- `malicious_link`
- `duplicate_listing`
- `wrong_category`
- `price_manipulation`
- `intellectual_property`
- `other`

### Product/API separation

The following remain product/domain rules rather than a second public enum registry: category-specific listing-type applicability, attribute option registries, moderation thresholds, subscription commercial rules, rate-limit thresholds, entitlement eligibility, seller consent, and safety restrictions.

**Database impact:** none. Gate #14 changes the API contract registry only; no new table or foreign key is required.

## Approved V1 Decision — Monetization Deferred; Contact and Location Policy (2026-10-18)

**Status: APPROVED V1 BASELINE.** This section supersedes earlier wording that implies a paid entitlement is required to launch, purchase, or unlock contact or exact-location information in the Marketplace MVP. Paid subscription and entitlement enforcement are deferred to Stage 4 under Document 02. No MVP purchase, payment-submission, recurring-billing, or gateway-checkout flow is required.

### KB-BR-CONTACT-006 — Visitor Must Authenticate to Initiate Contact

A visitor may browse and search publicly eligible listings and see a generic contact action. Initiating an in-app conversation requires authentication. After authentication, the backend must re-evaluate the listing state, account status, seller's `allow_in_app_contact` setting, blocks, safety restrictions and all authorization rules. A sign-in prompt must not disclose protected contact data.

### KB-BR-CONTACT-007 — V1 In-App Contact Only

V1 platform-mediated contact is in-app conversation only. Direct phone/email values are not disclosed by the public listing API, authenticated non-owner listing detail, SEO metadata, JSON-LD, XML sitemap, `llms.txt`, client cache, notification/push payload, or public media. A seller voluntarily typing contact details into a conversation is user-generated message content and remains subject to safety and moderation controls; it is not an API contact-reveal entitlement.

### KB-BR-LOC-013 — Exact Location Is Private in V1

Public and authenticated non-owner responses expose only the approved approximate/administrative location representation. Exact residential coordinates/address are available only to the listing owner or an explicitly authorized operational role for a legitimate purpose. Seller consent to in-app messaging does not authorize exact-location disclosure. No paid exact-location entitlement is active in V1.

### KB-BR-SUB-006 — Monetization Is Deferred

Subscription plans, subscription purchase, paid entitlements, entitlement activation/expiry for paid features, and payment-to-entitlement automation are outside MVP scope. Documents 05's subscription use cases remain future-phase traceability only. Do not implement subscription or payment endpoints as active V1 functionality unless a later product decision reopens this scope.

### Enforcement and acceptance

The API must enforce these rules server-side on every request; client hiding is not security. Tests must cover Visitor, authenticated non-owner, listing owner, authorized admin/moderator, blocked user, unpublished/expired listing, and seller-disabled in-app contact. Verify protected fields are absent from responses, page source, metadata, structured data, sitemaps, `llms.txt`, caches, logs and push notifications. This decision does not authorize a new database field or change the existing physical schema without the normal schema gate.