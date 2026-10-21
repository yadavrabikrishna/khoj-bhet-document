# 04. Users, Roles & Permissions

**Project:** KHOJ BHET  

**Document:** Users, Roles & Permissions  

**Document ID:** KB-PROD-004  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-21  

**Parent:** 01. PRODUCT DEFINITION  

**Related:** 01. Product Vision & Mission, 02. Product Scope & Roadmap, 03. Requirements Specification, 00.2 Terminology & Glossary  

**Next:** 05. User Stories & Use Cases

---

## Document Purpose

This document defines the user model, roles, permissions, access boundaries, and authorization principles for KHOJ BHET.

It establishes how one identity can participate in different marketplace activities while ensuring that capabilities are controlled according to role, ownership, verification state, listing state, and other applicable access rules.

<aside>
👥

**Core idea:** One identity can have multiple marketplace capabilities, while permissions determine what that identity is allowed to see, create, modify, publish, manage, or administer.

</aside>

## 1. User Model

KHOJ BHET should use a **single identity model** rather than creating separate accounts for buyers, sellers, landlords, tenants, businesses, or other marketplace participants.

Conceptually:

**User Account → Profile → Capabilities / Roles → Listings / Activities**

A single user may simultaneously:

- Search for a room.
- Sell a mobile.
- Rent out a property.
- Offer a service.
- Post a wanted request.
- Operate a business profile.

The account should not need to change identity when the user's marketplace activity changes.

## 2. User Types

User type describes the broad nature of the account or participant.

### 2.1 Visitor

A visitor is an unauthenticated person accessing publicly available platform content.

Typical capabilities:

- Browse public pages
- Search eligible public listings
- View eligible listing details
- View public profiles
- Register or log in

Restrictions:

- Cannot perform authenticated account actions.
- Cannot access restricted information without authorization.
- Cannot create or manage listings.

### 2.2 Registered User

A registered user has an authenticated KHOJ BHET account.

Typical capabilities:

- Manage own profile
- Create listings where permitted
- Manage own listings
- Save listings
- Search and filter
- Contact listing posters through approved mechanisms
- Report listings
- Manage account settings

### 2.3 Seller / Poster

A seller/poster is a registered user who publishes an offer, sale, rental, service, job, or other listing.

The term **poster** should be used when the person's relationship to the underlying item or service is not necessarily ownership.

A seller/poster may:

- Create listings
- Edit own drafts
- Publish eligible listings
- Manage active listings
- Respond to inquiries
- Pause or archive own listings
- View permitted listing activity

### 2.4 Buyer / Seeker

A buyer/seeker is a user looking for a product, property, service, job, opportunity, or other listing.

A buyer/seeker may:

- Search
- Filter
- Save listings
- Contact posters
- Submit inquiries
- Report problematic listings
- Create wanted/request listings where enabled

### 2.5 Owner

An owner is a person who legally or otherwise legitimately owns the item/property being represented.

**Owner** and **seller/poster** are not interchangeable.

A listing may be posted by:

- The owner
- An authorized agent
- A broker
- A dealer
- A property manager
- Another authorized representative

Where relevant, the platform may capture the relationship between poster and underlying owner.

### 2.6 Professional User

Professional users may include:

- Agents
- Brokers
- Dealers
- Freelancers
- Property managers
- Local professionals

Professional status should not automatically grant administrative privileges.

### 2.7 Business User

A business user represents a commercial organization or professional operation.

Capabilities may include:

- Business profile
- Multiple listings
- Business verification
- Business contact information
- Business analytics
- Team capabilities in future releases

Business functionality should be enabled through explicit product rules.

### 2.8 Moderator

A moderator is an authorized operational user responsible for reviewing reports and enforcing marketplace policies.

Moderator permissions should be limited to the operational responsibilities assigned to the role.

### 2.9 Administrator

An administrator is an authorized platform-management user with elevated privileges.

Administrative capabilities should be granted according to least-privilege principles.

## 3. Role Model

User type and role should be treated as separate concepts.

**User type** describes what the participant is.

**Role** describes what the participant is allowed to do.

For example:

A registered user may have the practical capabilities of:

- Buyer
- Seller
- Property owner
- Service provider

without requiring separate accounts.

Administrative roles should remain separate from ordinary marketplace capabilities.

## 4. Core Roles

The initial role model should include:

| Role | Primary Purpose |
| --- | --- |
| Visitor | Public discovery |
| User | Authenticated marketplace participation |
| Poster | Listing publication and management |
| Moderator | Marketplace safety and moderation |
| Administrator | Platform administration |

Additional specialized roles can be introduced when justified.

## 5. Capability Model

Capabilities should be granted according to explicit authorization rules.

Core capability groups:

### Account

- Register
- Authenticate
- Manage own account
- Deactivate account
- Request account recovery

### Profile

- View public profile
- Edit own profile
- Manage business profile where enabled

### Listing

- Create listing
- Edit own listing
- Submit for publication
- Publish
- Pause
- Resume
- Archive
- Delete
- View listing status
- Manage listing media

### Discovery

- Search
- Filter
- Sort
- Save listing
- Save search where enabled

### Communication

- Contact poster
- Respond to inquiry
- Manage own conversations where messaging is enabled

### Safety

- Report listing
- Report user
- Block/restrict where enabled

### Moderation

- Review reports
- Review flagged listings
- Apply moderation action
- Record moderation outcome

### Administration

- Manage users
- Manage listings
- Manage categories
- Manage locations
- Manage reports
- Manage verification
- Manage configuration
- Review audit information

## 6. Permission Principles

KHOJ BHET authorization should follow these principles:

### 6.1 Least Privilege

Users should receive only the permissions necessary for their current role or task.

### 6.2 Default Deny

A capability should not be accessible merely because the underlying endpoint or interface exists.

### 6.3 Ownership

Users should normally be able to modify or manage only resources they own or are explicitly authorized to manage.

### 6.4 Explicit Elevation

Administrative and moderation capabilities must require explicit authorization.

### 6.5 Separation of Duties

Where appropriate, sensitive actions should not be controlled by one unrestricted role.

### 6.6 Server-Side Enforcement

Permissions must be enforced by the backend or authoritative service, not only by hiding UI elements.

### 6.7 Auditability

Important privileged actions should be attributable to the authorized actor.

## 7. Resource Ownership

KHOJ BHET should distinguish between:

**User-owned resources**

- Profile
- Listings
- Saved listings
- Saved searches
- User preferences

**Platform-owned resources**

- Categories
- Administrative location data
- System configuration
- Moderation policies
- Platform settings

**Shared or controlled resources**

- Reports
- Verification records
- Business profiles
- Conversations
- Moderation evidence

Access to shared resources must be explicitly defined.

## 8. Listing Ownership and Representation

A listing should identify the account responsible for publishing it.

Where relevant, the platform may additionally represent:

- Owner
- Seller
- Agent
- Broker
- Dealer
- Property manager
- Authorized representative

The platform should not assume:

**Poster = Owner**

unless that relationship has been explicitly established.

A representative should only manage a listing on behalf of another person or business when appropriate authorization exists.

## 9. Listing Permission Lifecycle

Listing permissions should depend on listing state.

Example lifecycle:

**Draft → Review/Validation → Published → Paused → Expired/Archived**

Typical rules:

| Action | Draft | Published | Paused | Archived |
| --- | --- | --- | --- | --- |
| Owner edit | Yes | Yes | Yes | Controlled |
| Publish | Yes | — | Yes | No |
| Pause | No | Yes | — | No |
| Resume | No | No | Yes | Controlled |
| Delete | Yes | Controlled | Yes | Controlled |
| Public view | No | Yes | No | No |

Exact lifecycle rules belong in the product/business rules and listing requirements.

## 10. Public, Restricted, and Private Access

Information should be classified according to visibility.

### Public

Potential examples:

- Listing title
- Public photos
- General category
- Approximate location
- Public price information
- General description
- Selected public facilities

### Restricted

Potential examples:

- Exact location
- Direct contact information
- Additional seller information
- Private listing attributes

Access may depend on:

- Authentication
- Listing settings
- Subscription entitlement
- Verification
- Explicit permission
- Product policy

### Private / Internal

Examples:

- Password-related data
- Internal moderation evidence
- Administrative notes
- Security information
- Internal audit information
- Private user data not intended for marketplace display

Internal information must not be exposed through public APIs or normal marketplace interfaces.

## 11. Business and Team Access

Future business functionality may allow multiple people to operate under one business.

Potential model:

**Business → Members → Roles → Business Resources**

Possible business roles:

- Business Owner
- Business Admin
- Manager
- Listing Manager
- Staff

Business team permissions should be scoped to the business rather than automatically granting platform-wide administrative privileges.

## 12. Verification and Permissions

Verification should not automatically grant unrestricted permissions.

Examples:

**Phone verified**

→ may satisfy a contact-verification requirement.

**Business verified**

→ may enable a business verification indicator.

**Identity verified**

→ may satisfy specific identity requirements.

Verification should be treated as a state or attribute that can affect eligibility where explicitly defined.

A verification badge must not imply that every action or listing of the account has been independently verified.

## 13. Subscription and Entitlement Model

If KHOJ BHET introduces paid plans, subscription status should be treated as an **entitlement**, not as a replacement for authorization.

Conceptually:

**User / Business → Subscription → Entitlements → Allowed Features**

Examples of potential entitlements:

- Additional listing limits
- Featured placement
- Advanced analytics
- Business tools
- Restricted-information access where approved

A paid subscription must not bypass:

- Security controls
- Moderation actions
- Platform policy
- Legal restrictions
- Administrator-only permissions

## 14. Authentication vs Authorization

These concepts must remain distinct.

**Authentication:** Who is the user?

**Authorization:** What is the authenticated user allowed to do?

Successful authentication does not imply permission to perform every action.

## 15. Administrative Roles

Administrative roles should be separated according to responsibility where practical.

Potential roles:

### Platform Administrator

Broad platform configuration and management.

### Content Moderator

Listing, report, and content moderation.

### Support Operator

User-support operations with limited administrative access.

### Verification Operator

Review of verification-related information.

### Technical Operator

Infrastructure and operational responsibilities.

These roles should not automatically inherit all permissions from one another.

## 16. Permission Matrix Baseline

The following is a conceptual baseline:

| Capability | Visitor | User | Poster | Moderator | Administrator |
| --- | --- | --- | --- | --- | --- |
| Browse public listings | Yes | Yes | Yes | Yes | Yes |
| Search | Yes | Yes | Yes | Yes | Yes |
| Save listing | No | Yes | Yes | Yes | Yes |
| Create listing | No | Yes | Yes | Controlled | Yes |
| Manage own listing | No | Yes | Yes | Controlled | Yes |
| Contact poster | Controlled | Yes | Yes | Controlled | Yes |
| Report listing | Yes | Yes | Yes | Yes | Yes |
| Review reports | No | No | No | Yes | Yes |
| Moderate listing | No | No | No | Yes | Yes |
| Manage users | No | No | No | Limited | Yes |
| Manage categories | No | No | No | No/Limited | Yes |
| Manage locations | No | No | No | No/Limited | Yes |
| Manage system configuration | No | No | No | No | Yes |

**Controlled** means the exact permission depends on the relevant product rule and context.

## 17. Authorization Scope

Permissions should be evaluated at the appropriate scope.

Possible scopes:

### Platform

Applies across KHOJ BHET.

### Business

Applies only to a specific business.

### Listing

Applies only to a specific listing.

### Conversation

Applies only to a communication thread.

### Resource

Applies to a specific record or resource.

This allows future team and delegated-access capabilities without making every role globally privileged.

## 18. Account Status and Access

Account state may affect permissions.

Potential states:

- Active
- Pending verification
- Restricted
- Suspended
- Deactivated
- Deleted/anonymized

Examples:

- A suspended account may be prevented from creating or publishing listings.
- A deactivated account may lose normal interactive access.
- A pending account may have limited capabilities until required verification is completed.

Exact state-transition rules should be defined in product/business rules.

## 19. Permission Change and Governance

Changes to roles or permissions should identify:

- Role or capability affected
- Previous permission
- New permission
- Reason
- Impact
- Security implications
- Affected requirements
- Approval
- Effective version

Significant security or architectural changes should be evaluated for an ADR.

## 20. Security Requirements for Authorization

Authorization mechanisms should include:

- Server-side permission checks
- Resource ownership checks
- Role validation
- Session/token validation
- Protection against privilege escalation
- Protection against insecure direct object references
- Administrative access controls
- Audit logging for important privileged actions
- Revocation of access when account status changes
- Secure handling of service-to-service authorization

Permission checks should be centralized or consistently implemented to avoid contradictory authorization behavior.

## 21. Future Role Extensions

The model should be capable of supporting future participants such as:

- Landlord
- Tenant
- Property agent
- Vehicle dealer
- Employer
- Job seeker
- Worker
- Service provider
- Customer
- Business member
- Business manager
- Verified professional

These should generally be modeled as capabilities, profiles, relationships, or scoped roles rather than forcing every participant type into a separate account class.

## 22. Relationship to Other Product Documents

This document defines **who can perform actions and how access should be controlled**.

Related documents:

- **01. Product Vision & Mission** — product purpose and user model.
- **02. Product Scope & Roadmap** — capabilities introduced by release.
- **03. Requirements Specification** — functional and non-functional requirements.
- **05. User Stories & Use Cases** — user goals and interactions.
- **06. User Flows** — journeys that use these permissions.
- **07. UX/UI Specification** — how permissions are reflected in the interface.
- **08. Product & Business Rules** — detailed access and behavior rules.
- **00.2 Terminology & Glossary** — authoritative definitions.

Technical implementation of authentication and authorization belongs in technical architecture and security documentation.

## 23. Document Status

**Status:** Active / Access Control Baseline  

**Authority:** Product-level user, role, and permission model  

**Primary use:** Requirements, UX, authorization design, security, implementation, and testing  

**Review trigger:** New user type, new business capability, new subscription model, new sensitive data access, security change, or major product release

---

## Document Control

**Document ID:** KB-PROD-004  

**Document:** Users, Roles & Permissions  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-21  

**Parent:** 01. PRODUCT DEFINITION  

**Related:** 01. Product Vision & Mission, 02. Product Scope & Roadmap, 03. Requirements Specification, 00.2 Terminology & Glossary  

**Next:** 05. User Stories & Use Cases

## 24. Approved V1 Business Member Permission Matrix — 2026-10-04

**Status: Approved.** This section supersedes the earlier conceptual business-role baseline wherever it conflicts with this V1 matrix. The four V1 `business_members.role` values are `owner`, `admin`, `manager`, and `member`.

| Capability | Owner | Admin | Manager | Member |
| --- | --- | --- | --- | --- |
| View business resources within scope | Yes | Yes | Yes | Yes |
| Edit business profile | Yes | Yes | No | No |
| Invite members | Yes | Yes | No | No |
| Change member role/status | Yes | Yes, except owner | No | No |
| Remove members | Yes | Yes, except owner | No | No |
| Create business listings | Yes | Yes | Yes | Yes |
| Edit business listings | Yes | Yes | Yes | Yes |
| Submit business listings | Yes | Yes | Yes | No |
| Pause business listings | Yes | Yes | Yes | No |
| Resume business listings | Yes | Yes | Yes | No |
| Archive business listings | Yes | Yes | No | No |
| Delete business listings | Yes | Yes | No | No |
| Act as business representative on authorized listings | Yes | Yes | Yes | Yes |
| Platform administration/moderation | No | No | No | No |

**Rules:**

1. Membership must be active and scoped to the target business.
2. Business roles never grant platform-wide administrative or moderation authority.
3. Business Admin may manage ordinary members but cannot modify, remove, or demote the Business Owner.
4. Manager may operate listings through submit/pause/resume but cannot manage members or archive/delete listings.
5. Member may create/edit listings and represent the business, but cannot submit/pause/resume/archive/delete listings or manage members.
6. All listing operations remain subject to listing ownership/representation, lifecycle, moderation, privacy, consent, entitlement, account-status, and safety rules.
7. Any future ownership transfer or expanded delegation requires an explicit product/ADR decision; it is not implied by this matrix.

This matrix is the product-level authority consumed by Document 14 section 7.2 and the future implementation details in Document 18.

## Gate #10 — Verification Levels Alignment — 2026-10-04

**Status: Approved V1**

The conceptual permission model is now aligned with the approved verification registry.

V1 verification subjects/types:

- User: phone, email, identity
- Business: business
- Listing: listing eligibility/moderation remains separate

Verification does not automatically grant unrestricted permissions. A capability that depends on verification must explicitly identify the required verification type and approved state.

Professional and standalone address verification remain deferred for V1.

## Gate #11 — Push-device Token Persistence Alignment — 2026-10-04

**Status: Approved V1**

Push-device registration is a user-owned resource. A user may have multiple active devices, but may manage only their own registrations. Registering a push device does not grant a role, verification level, subscription entitlement, or administrative capability.

V1 capabilities:

- User may register/update their own push device after authentication.
- User may list their own registered devices using safe metadata.
- User may revoke their own push device registration.
- Platform notification infrastructure may invalidate a device token based on provider feedback.
- Administrative/operational access to raw push tokens is restricted to the notification infrastructure and authorized operational controls; raw tokens are not ordinary user/admin marketplace data.

Account deactivation/deletion, suspension, communication restrictions, and security controls take precedence over device registration. Push delivery is therefore an entitlement/notification-channel operation, not an authorization mechanism.

## Approved V1 Contact and Visitor Permission Decision — 2026-10-18

**Decision status: APPROVED BASELINE — supersedes any ambiguous Visitor → Contact poster permission that could be interpreted as permitting a visitor to initiate contact.**

- **Visitor:** may browse and search eligible public listings and see the available contact-action labels, but must authenticate before initiating an in-app conversation. Visitors cannot retrieve protected phone numbers, email addresses or exact residential coordinates through API, web HTML, metadata, structured data, sitemap, `llms.txt`, cache or media responses.
- **Authenticated non-owner:** may initiate in-app contact only when the account, listing, seller's in-app-contact setting, block/safety rules and moderation/lifecycle checks permit it. V1 does not expose direct phone/email or exact location through a paid entitlement, because paid entitlements are deferred.
- **Listing owner/authorized business representative:** may manage their own contact settings and view the information they supplied, subject to account and resource authorization.
- **Seller consent:** `allow_in_app_contact` controls in-app contact. Consent to in-app contact does not imply consent to disclose phone/email or exact location.
- **Admin/moderator:** access is limited to an explicitly authorized operational purpose and audited where applicable; privileged access does not make protected data public.

The permission matrix, use cases, flow diagrams, API access descriptors and tests must follow these rules. Publicly visible contact methods are not equivalent to public disclosure of the underlying protected contact value.