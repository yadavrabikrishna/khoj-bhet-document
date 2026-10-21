# 05. User Stories & Use Cases

# Document Metadata

| Field | Value |
| --- | --- |
| Project | KHOJ BHET |
| Document | 05. User Stories & Use Cases |
| Document ID | KB-PROD-005 |
| Status | Active |
| Version | 1.0 |
| Owner | KHOJ BHET Product |
| Last Reviewed | 2026-09-21 |
| Parent | 01. PRODUCT DEFINITION |
| Related | 01. Product Vision & Mission, 02. Product Scope & Roadmap, 03. Requirements Specification, 04. Users, Roles & Permissions, 00.2 Terminology & Glossary, 00.3 Decision / ADR Register |
| Next | 06. User Flows |

# 1. Document Purpose

This document defines how KHOJ BHET expresses user needs and system interactions through user stories and use cases.

It translates product requirements into understandable, testable descriptions of what users need to accomplish and how the platform should respond.

This document is the bridge between:

**Product Vision → Requirements → User Stories / Use Cases → User Flows → UX/UI → Technical Design → Implementation**

# 2. Objectives

User stories and use cases shall:

- represent real user goals rather than implementation details;
- cover the major actors and capabilities of KHOJ BHET;
- provide traceability to requirements;
- identify alternate and exceptional scenarios;
- support UX, API, database, development and testing activities;
- remain understandable to product, design and engineering participants;
- avoid prematurely locking implementation choices.

# 3. User Story Model

A user story describes a user goal from the user's perspective.

Standard format:

> **As a [user/actor], I want to [goal], so that [benefit/outcome].**
> 

Each story should have:

- Story ID
- Actor
- Goal
- Benefit
- Related requirement(s)
- Priority
- Acceptance criteria
- Dependencies
- Status
- Related use case(s), where applicable

# 4. User Story Quality Rules

A good user story should be:

- **Independent** where practical
- **Valuable** to a defined actor
- **Negotiable** before implementation
- **Specific enough** to understand
- **Testable**
- **Traceable**
- **Free of unnecessary implementation detail**

Stories should describe outcomes, not technical tasks.

Example:

> As a registered user, I want to create a listing so that other people can discover what I am offering.
> 

Avoid:

> As a user, I want the backend to insert a listing record into the listings table.
> 

The latter is an implementation task, not a user story.

# 5. Acceptance Criteria

Acceptance criteria define the conditions under which a story is considered complete.

Preferred form:

**Given** [initial condition]  

**When** [user/system action]  

**Then** [expected result]

Acceptance criteria should cover:

- normal success;
- required validation;
- permission restrictions;
- important alternate paths;
- relevant failure conditions;
- privacy/security expectations where applicable.

Acceptance criteria should be observable and testable.

# 6. Use Case Model

A use case describes an interaction between an actor and KHOJ BHET to achieve a defined outcome.

Each use case should contain:

1. Use Case ID
2. Name
3. Goal
4. Primary Actor
5. Supporting Actors / Systems
6. Preconditions
7. Trigger
8. Main Success Scenario
9. Alternate Flows
10. Exception Flows
11. Postconditions
12. Business Rules
13. Related Requirements
14. Related User Stories
15. Priority
16. Status

# 7. User Story vs Use Case

| Aspect | User Story | Use Case |
| --- | --- | --- |
| Primary purpose | Express user need | Describe interaction |
| Perspective | User-centric | Actor + system |
| Detail | Concise | Detailed |
| Main question | What does the user need and why? | How does the interaction occur? |
| Acceptance | Acceptance criteria | Main, alternate and exception flows |
| Typical use | Product backlog | Analysis, UX, architecture and testing |

They are complementary, not competing artifacts.

# 8. Actor Model

User stories and use cases should use the actor model defined in **04. Users, Roles & Permissions**.

Primary actors may include:

- Visitor
- Registered User
- Poster
- Buyer / Seeker
- Owner
- Professional User
- Business User
- Moderator
- Administrator

Supporting actors may include:

- Authentication service
- Notification service
- Media service
- Search service
- Location service
- Payment/subscription service
- External identity providers
- Messaging/communication services

The actor model may expand as the product evolves.

# 9. Initial User Story Domains

The initial story backlog should be organized by capability domain.

## 9.1 Account and Identity

Examples:

- Register an account
- Sign in
- Sign out
- Recover account access
- Manage account information
- Manage verification status
- Deactivate account
- Request account deletion

## 9.2 Profile

Examples:

- Create a profile
- Edit profile information
- Control public profile information
- Manage business identity
- Represent a business or organization

## 9.3 Listing Management

Examples:

- Create a listing
- Save a listing as draft
- Edit a listing
- Preview a listing
- Publish a listing
- Pause a listing
- Resume a listing
- Mark a listing as sold/rented/closed where applicable
- Archive a listing
- Delete a listing

## 9.4 Listing Information

Examples:

- Select a category
- Select a listing type
- Enter title
- Enter description
- Add price information
- Add category-specific attributes
- Add facilities/features
- Add location
- Add contact preferences
- Add media

## 9.5 Discovery

Examples:

- Browse categories
- Search listings
- Filter listings
- Sort listings
- View listing details
- View approximate location
- View available facilities
- Save a listing
- Share a listing

## 9.6 Location

Examples:

- Select province
- Select district
- Select municipality
- Select ward
- Enter locality/tole
- Select or enter chowk/landmark
- Set map location
- Control location precision shown publicly

Nepal's location model should support the product's planned hierarchy without assuming that every locality or address has the same level of formal administrative status.

## 9.7 Contact and Communication

Examples:

- Contact a poster
- Choose an available contact method
- Start a conversation
- Receive a response
- Control contact visibility
- Block/report unwanted communication

## 9.8 Safety and Reporting

Examples:

- Report a listing
- Report a user
- Report inappropriate communication
- Block a user
- Submit evidence
- Track report status where exposed to the reporter

## 9.9 Moderation

Examples:

- Review reported content
- Review listing status
- Take moderation action
- Request changes
- Restrict content
- Suspend a user where authorized
- Record moderation action

## 9.10 Subscription and Entitlements

Examples:

- View available plans
- Subscribe to a plan
- View current entitlement
- Access restricted listing information when entitled
- Manage subscription status
- Handle entitlement expiration

Implementation of paid plans remains subject to the scope and monetization decisions defined elsewhere.

# 10. Initial Use Case Catalogue

The following catalogue establishes the initial analysis baseline.

| ID | Use Case | Primary Actor | Domain |
| --- | --- | --- | --- |
| UC-001 | Register Account | Visitor | Identity |
| UC-002 | Sign In | Registered User | Identity |
| UC-003 | Manage Profile | Registered User | Profile |
| UC-004 | Create Listing | Poster | Listing |
| UC-005 | Edit Listing | Poster | Listing |
| UC-006 | Submit Listing | Poster | Listing |
| UC-007 | Publish Listing | Authorized Poster / System | Listing |
| UC-008 | Pause Listing | Poster | Listing |
| UC-009 | Archive Listing | Poster | Listing |
| UC-010 | Search Listings | Visitor / Registered User | Discovery |
| UC-011 | Filter Listings | Visitor / Registered User | Discovery |
| UC-012 | View Listing | Visitor / Registered User | Discovery |
| UC-013 | Save Listing | Registered User | Discovery |
| UC-014 | Contact Poster | Registered User | Communication |
| UC-015 | Report Listing | Visitor / Registered User | Safety |
| UC-016 | Report User | Registered User | Safety |
| UC-017 | Moderate Listing | Moderator | Moderation |
| UC-018 | Moderate User | Moderator / Administrator | Moderation |
| UC-019 | Manage Category | Administrator | Administration |
| UC-020 | Manage Location Data | Administrator | Administration |
| UC-021 | Manage Subscription | Registered User / Business User | Subscription |
| UC-022 | Enforce Entitlement | System | Subscription |
| UC-023 | Manage Business | Business User | Business |
| UC-024 | Manage Business Members | Business Owner / Business Admin | Business |

This catalogue is a baseline. Detailed use cases should be expanded only when the corresponding feature is sufficiently defined.

# 11. Example User Story

**Story ID:** KB-US-001

**Story:**

> As a registered user, I want to create a listing so that people can discover what I am offering.
> 

**Acceptance Criteria:**

1. Given an authenticated user, when the user starts creating a listing, then the system provides the required listing fields.
2. Given a selected category, when category-specific information is required, then the relevant fields are displayed.
3. Given required information is missing, when the user attempts to submit the listing, then the system identifies the missing information.
4. Given valid required information, when the user saves the listing, then the listing is stored under the user's ownership/authorization scope.
5. A saved draft must not be publicly discoverable until it reaches an appropriate publication state.

# 12. Example Use Case

**Use Case ID:** UC-004  

**Name:** Create Listing  

**Primary Actor:** Poster

### Goal

Create a structured listing that can later be published and discovered by other users.

### Preconditions

- The actor has an account.
- The actor is authorized to create listings.
- Required account restrictions do not prevent listing creation.

### Trigger

The actor selects the option to create a new listing.

### Main Success Scenario

1. System opens the listing creation flow.
2. Actor selects the category.
3. System loads applicable listing fields.
4. Actor enters title and description.
5. Actor provides price/listing-type information where applicable.
6. Actor provides category-specific attributes.
7. Actor provides location information.
8. Actor uploads permitted media.
9. Actor configures available contact information.
10. Actor saves the listing.
11. System validates the submitted data.
12. System creates the listing in the appropriate lifecycle state.
13. System confirms the result to the actor.

### Alternate Flows

- Actor saves incomplete information as a draft.
- Actor changes category before submission.
- Actor removes or replaces media.
- Actor changes location information.
- Actor chooses a different contact method.
- Actor pauses the process and returns later.

### Exception Flows

- Authentication expires.
- Required data is invalid.
- Media upload fails.
- Location data cannot be resolved.
- Account permission is insufficient.
- Platform validation fails.

### Postconditions

- A listing record exists under the appropriate ownership/authorization scope.
- The listing has a defined lifecycle state.
- The listing is not publicly discoverable unless its state and visibility rules permit publication.

# 13. Listing Lifecycle Use Cases

Listing-related stories and use cases should reflect the lifecycle defined by the permission model:

**Draft → Review/Validation → Published → Paused → Expired/Archived**

Not every category or listing will necessarily use every state.

Lifecycle transitions must be controlled by authorization, business rules and platform policy.

# 14. Ownership and Representation

User stories must distinguish between the person interacting with the platform and the person or organization represented by a listing.

A Poster may be:

- the Owner;
- Seller;
- Agent;
- Broker;
- Dealer;
- Property Manager;
- Authorized Representative;
- Business member.

Therefore stories should not assume:

> Poster = Owner
> 

unless a specific business rule establishes that relationship.

# 15. Visibility and Access

User stories and use cases must account for information access levels.

Potential information classes include:

- Public
- Restricted
- Private
- Subscription/entitlement controlled

Examples:

- approximate location may be publicly visible;
- exact address may be restricted;
- contact details may be restricted;
- private account information must not be exposed through ordinary listing discovery.

The exact entitlement rules are defined in product/business rules and subscription specifications.

# 16. Traceability

Every mature user story should be traceable to one or more requirements.

The formal cross-document REQ ↔ UC ↔ UF index is maintained in [00.4 Requirements ↔ Use Cases ↔ User Flows Traceability Matrix](../00%20DOCUMENTATION%20FOUNDATION/00%204%20Requirements%20-%20Use%20Cases%20-%20User%20Flows%20Traceab%203e59628c857d81dfa239e6ddbeb28961.md).

Recommended relationship:

**Requirement → User Story → Use Case → User Flow → UX/UI → Implementation → Test**

The matrix must support both forward and reverse traceability:

- Requirement → Use Case → User Flow
- User Flow → Use Case → Requirement

The matrix must record gaps explicitly rather than inventing missing identifiers or relationships.

Example:

| Artifact | Example |
| --- | --- |
| Requirement | KB-FR-001 |
| User Story | KB-US-001 |
| Use Case | UC-004 |
| User Flow | UF-004 |
| UI | Figma screen/component |
| Implementation | GitHub issue/PR |
| Test | Test case |

# 17. Prioritization

User stories should use the requirement priority model:

- **P0 Critical**
- **P1 High**
- **P2 Medium**
- **P3 Low**

Priority should reflect product necessity and release scope rather than implementation convenience.

A story may also have a lifecycle status such as:

- Proposed
- Approved
- In Progress
- Implemented
- Verified
- Deferred
- Rejected
- Superseded

# 18. Story Splitting Rules

Large stories should be split when they contain multiple independent outcomes.

Possible splitting dimensions:

- user capability;
- workflow stage;
- category;
- permission level;
- platform surface;
- happy path vs exceptional behavior;
- public vs restricted information;
- MVP vs later capability.

Avoid splitting a story merely into technical layers such as:

- frontend story;
- backend story;
- database story;

unless separate tracking is genuinely useful for implementation.

# 19. Use Case Detail Rules

A detailed use case should be created when:

- multiple actors interact;
- the workflow has important alternate paths;
- permissions are significant;
- business rules affect the interaction;
- failure handling matters;
- the workflow affects several system components;
- the behavior needs to support UX or technical design.

Simple capabilities may remain represented primarily as user stories and acceptance criteria.

# 20. Non-Functional and System Stories

Not every requirement has a human user story.

Technical and system requirements may instead be represented as:

- system use cases;
- operational scenarios;
- technical requirements;
- acceptance criteria;
- architecture decisions;
- automated test cases.

Examples include:

- system validates authorization server-side;
- system records audit events;
- system prevents unauthorized access to restricted listing information;
- system processes media safely;
- system maintains required performance characteristics.

# 21. Definition of Ready

A user story is ready for implementation analysis when:

- actor is identified;
- user outcome is clear;
- scope is understandable;
- acceptance criteria are defined;
- relevant requirements are linked;
- dependencies are known or explicitly tracked;
- major permission considerations are understood;
- unresolved product decisions are identified.

# 22. Definition of Done

A user story is considered complete when:

- implementation satisfies acceptance criteria;
- relevant tests pass;
- required security/authorization behavior is verified;
- documentation is updated where necessary;
- related technical artifacts are linked;
- the story reaches the appropriate completed/verified state.

# 23. AI-Assisted Story and Use Case Generation

AI may assist with:

- generating candidate user stories from requirements;
- identifying missing actors;
- identifying alternate and exception flows;
- drafting acceptance criteria;
- detecting duplicate stories;
- linking stories to requirements;
- proposing story splits;
- maintaining traceability;
- generating diagrams from approved flows;
- identifying documentation inconsistencies.

AI-generated artifacts must remain subject to human review and product decisions.

AI should not silently change approved requirements, business rules or architectural decisions.

# 24. Relationship to Other Product Documents

| Document | Relationship |
| --- | --- |
| 01. Product Vision & Mission | Defines product purpose and direction |
| 02. Product Scope & Roadmap | Defines what is planned and when |
| 03. Requirements Specification | Provides requirement sources |
| 04. Users, Roles & Permissions | Defines actors and authorization concepts |
| 05. User Stories & Use Cases | Converts requirements into actor goals and interactions |
| 06. User Flows | Converts use cases into navigable/process flows |
| 07. UX/UI Specification | Defines interface behavior and presentation |
| 08. Product & Business Rules | Defines governing business behavior |

# 25. Document Status

**Status:** Active  

**Version:** 1.0

This document establishes the baseline model for KHOJ BHET user stories and use cases. Detailed stories and use cases should evolve as requirements, flows and business rules become more specific.

# 26. Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-PROD-005 |
| Document | 05. User Stories & Use Cases |
| Status | Active |
| Version | 1.0 |
| Owner | KHOJ BHET Product |
| Last Reviewed | 2026-09-21 |
| Parent | 01. PRODUCT DEFINITION |
| Related | 01. Product Vision & Mission, 02. Product Scope & Roadmap, 03. Requirements Specification, 04. Users, Roles & Permissions, 00.2 Terminology & Glossary, 00.3 Decision / ADR Register |
| Next | 06. User Flows |

## V1 Scope Clarification — Contact and Subscription Use Cases (2026-10-18)

**Approved baseline:** UC-014 / UF-014 may be implemented for authenticated in-app contact subject to Document 08 and Document 14. A visitor may view public listings but must sign in before starting a conversation. V1 does not disclose protected phone/email or exact location through the platform API.

UC-021 Manage Subscription and UC-022 Enforce Entitlement remain in the long-term model for traceability and future planning, but **paid subscription purchase, paid entitlement activation, and monetization-dependent contact/location disclosure are deferred beyond the Marketplace MVP** under Document 02. They are not V1 acceptance criteria. Do not implement payment/entitlement flows in MVP merely because a use case exists in this document. Keep privacy, authorization, seller consent and safety rules active regardless of monetization scope.