# 02. Product Scope & Roadmap

**Project:** KHOJ BHET  

**Document:** Product Scope & Roadmap  

**Document ID:** KB-PROD-002  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-21  

**Parent:** 01. PRODUCT DEFINITION  

**Related:** 01. Product Vision & Mission, 00.1 Documentation & SDLC Framework, 00.3 Decision / ADR Register  

**Next:** 03. Requirements Specification

---

## Document Purpose

This document defines the product scope of KHOJ BHET and establishes a roadmap framework for deciding what should be built, what should not be built yet, and how the product should expand over time.

It translates the product direction defined in **01. Product Vision & Mission** into a controlled progression from the initial marketplace foundation toward the broader KHOJ BHET platform.

<aside>
🗺️

**Core idea:** Build one common marketplace foundation with the approved 25-category catalogue available from day one, while expanding specialized capabilities and future categories only when justified.

</aside>

## 1. Scope Management Principles

KHOJ BHET scope should be managed according to these principles:

1. **Vision before features** — features must support the product vision.
2. **Core before expansion** — establish the common marketplace foundation before adding many categories.
3. **Foundation before specialization** — shared capabilities should be designed before category-specific complexity.
4. **Small releases** — deliver usable increments rather than attempting the entire long-term platform at once.
5. **Evidence-driven expansion** — major additions should be supported by user needs, operational evidence, or clearly documented strategic requirements.
6. **Avoid premature complexity** — capabilities that are not required for the current product stage should remain outside the active scope.
7. **Reusable architecture** — new categories should reuse common platform capabilities wherever practical.
8. **Explicit decisions** — significant scope changes should be documented through requirements, roadmap updates, or ADRs as appropriate.

## 2. Product Scope Model

KHOJ BHET scope is divided into four levels:

### Level 1 — Platform Foundation

Shared capabilities required across multiple marketplace categories.

Examples:

- User accounts
- Authentication
- Profiles
- Listing engine
- Categories
- Location system
- Media management
- Search
- Filters
- Favorites
- Contact mechanisms
- Reports
- Moderation
- Notifications
- Administrative tools

### Level 2 — Initial Marketplace Catalogue

The approved marketplace catalogue is available from day one at the category-data level. The catalogue baseline is **25 top-level categories with 372 documented subcategories**, each governed by the authoritative **13.1 Category & Attribute Catalogue**.

The full category baseline is listed in Section 3.3.

### Level 3 — Future Expansion

New categories or specialized marketplace domains that are not part of the current 25-category baseline may be introduced after the foundation demonstrates sufficient stability and usage.

Potential future additions:

- Tickets / Events marketplace workflows
- Wanted / Request listings
- Additional specialized commercial categories
- Additional verticals justified by user demand

### Level 4 — Advanced Platform Capabilities

Longer-term capabilities that may require additional product, technical, operational, or commercial maturity.

Potential capabilities:

- Advanced messaging
- Payments
- Transaction workflows
- Business subscriptions
- Advanced verification
- Recommendations
- Personalization
- Analytics
- Business management tools
- Location intelligence
- Matching systems

These levels describe scope progression, not fixed release dates.

## 3. In Scope for the Initial Product

The initial product should establish the complete basic marketplace loop.

### 3.1 Identity and Accounts

- User registration
- Login and logout
- Basic account management
- User profile
- Contact verification where required

### 3.2 Universal Listing Engine

- Create listing
- Edit listing
- Save draft
- Publish listing
- Pause/unpublish listing
- Expire listing
- Delete/archive listing
- Listing status
- Multiple listings per user
- Category-specific attributes

### 3.3 Day-One Category Catalogue

The initial product should establish the complete basic marketplace loop across the approved category catalogue. The authoritative category and attribute definitions are maintained in **13.1 Category & Attribute Catalogue**.

**Catalogue baseline:** 25 top-level categories and 372 documented subcategories are approved for the day-one marketplace data model. Category-specific attributes are represented through the generic category-attribute model rather than separate physical listing tables.

The 25 approved top-level categories are:

- Property
- Mobile & Electronics
- Furniture & Home
- Vehicles
- Fashion & Clothing
- Home Appliances & Kitchen
- Sports, Fitness & Outdoor
- Jobs & Employment
- Services
- Business, Office & Commercial Equipment
- Baby, Kids & Toys
- Books, Media & Collectibles
- Food, Agriculture Products & Livestock
- Health, Beauty & Personal Care Products
- Home & Garden
- Pet Supplies & Animals
- Travel, Luggage & Accessories
- Construction, Tools & Building Materials
- Industrial, Machinery & Heavy Equipment
- Weddings, Events & Party Supplies
- Office, School & Stationery Supplies
- Religious, Spiritual & Cultural Items
- Health, Medical & Wellness Equipment
- Security, Safety & Emergency Products
- Baby, Maternity & Parenting Products

**Scope decision:** The 25-category catalogue is a day-one product baseline. This does not require every category to receive a separate application module; the universal listing, category, attribute, location, search, media, moderation, and authorization foundations are shared.

### 3.4 Location

The initial location model should support Nepal-focused structured location data:

**Country → Province → District → Municipality → Ward → Locality/Tole → Chowk/Landmark → GPS**

The system should distinguish:

- Official administrative divisions
- Locality / Tole
- Chowk / Landmark
- Approximate public location
- Exact restricted location

### 3.5 Search and Discovery

- Keyword search
- Category filtering
- Listing-type filtering
- Location filtering
- Price filtering where applicable
- Category-specific filters
- Listing detail pages
- Basic sorting
- Relevant listing discovery

### 3.6 Contact and Safety

- Contact seller/poster through approved mechanisms
- Report listing
- Block or restrict where required
- Listing status visibility
- Basic moderation workflow
- Basic anti-spam controls

### 3.7 Media

- Listing photo upload
- Multiple photos
- Primary/featured photo
- Media ordering
- Basic media validation

### 3.8 Administration

- User management
- Listing management
- Category management
- Location management
- Reports
- Moderation actions
- Basic platform configuration

## 4. Initial Product Loop

The first product should support this end-to-end flow:

**Register → Create Listing → Publish → Discover → Search / Filter → View Listing → Contact → Report / Manage**

For a person looking for something:

**Need → Search → Relevant Results → Understand → Contact → Outcome**

For a person offering something:

**Offer → Publish → Discoverability → Contact → Outcome**

A release should be considered incomplete if the core loop cannot be completed reliably.

## 5. Explicitly Out of Scope for Initial Release

The following should not be treated as required V1 scope unless a documented decision changes the roadmap:

- Full online payment processing
- Escrow
- Complex transaction settlement
- Delivery/logistics management
- Full e-commerce checkout
- Advanced recommendation engines
- AI-driven personalization
- Complex auction systems
- Multi-country marketplace support
- Large-scale business ERP functionality
- Fully automated verification of every listing
- Complex loyalty/rewards systems
- Unnecessary category-specific applications
- Features whose primary purpose is monetization without clear marketplace value

Being out of scope does not mean these capabilities can never be built. It means they are not required for the initial product baseline.

## 6. Roadmap Stages

### Stage 0 — Product and Architecture Foundation

**Objective:** Establish the decisions and shared foundation required to build the marketplace safely.

Focus:

- Product documentation
- Requirements definition
- User and permission model
- Core data model
- Location model
- Listing model
- Category model
- Technical architecture
- Security baseline
- Development workflow
- Deployment foundation

**Exit condition:** Core product and technical foundations are sufficiently defined to begin controlled implementation.

### Stage 1 — Marketplace MVP

**Objective:** Launch the first usable marketplace.

Focus:

- Accounts
- Profiles
- Universal listing engine
- Approved 25-category catalogue and Nepal location hierarchy
- Listing media
- Search
- Filters
- Listing detail pages
- Contact
- Favorites
- Reporting
- Basic moderation
- Administration

**Exit condition:** Users can publish, discover, evaluate, contact, and manage listings through the complete core loop.

### Stage 2 — Marketplace Stabilization

**Objective:** Improve reliability, quality, trust, and usability after the MVP is operational.

Focus:

- Listing quality improvements
- Better search relevance
- Listing freshness
- Duplicate detection
- Improved moderation
- Verification improvements
- Better reporting
- Performance optimization
- Analytics
- Operational monitoring
- UX improvements based on actual usage

**Exit condition:** The marketplace has stable core operations and measurable usage patterns that can guide expansion.

### Stage 3 — Category & Capability Expansion

**Objective:** Expand the marketplace beyond the approved day-one catalogue without fragmenting the platform.

Potential additions:

- Tickets / Events marketplace workflows
- Wanted / Request listings
- Additional specialized commercial categories
- Additional verticals justified by user demand

Expansion should reuse the universal listing, identity, location, media, search, and moderation foundations.

**Exit condition:** New categories operate effectively without requiring separate core platform systems.

### Stage 4 — Business and Monetization

**Objective:** Introduce sustainable commercial capabilities while protecting core marketplace usefulness.

Potential capabilities:

- Seller/business subscriptions
- Featured listings
- Additional visibility
- Business profiles
- Verification packages
- Restricted information access
- Analytics
- Business management tools

Monetization should not unnecessarily hide essential marketplace information or undermine user trust.

**Exit condition:** Commercial capabilities provide measurable value to users and the platform without degrading the core discovery experience.

### Stage 5 — Advanced Marketplace

**Objective:** Add advanced interaction and transaction capabilities when sufficient product maturity exists.

Potential capabilities:

- Advanced messaging
- Payments
- Transaction workflows
- Booking
- Matching
- Recommendations
- Personalization
- Advanced location intelligence
- Business APIs
- Advanced analytics

These capabilities require separate requirements, security, legal, operational, and technical decisions before implementation.

## 7. Category Expansion Strategy

New categories should be evaluated using a common framework.

Before adding a category, assess:

1. User demand
2. Supply availability
3. Search behavior
4. Required attributes
5. Location requirements
6. Trust and verification requirements
7. Moderation complexity
8. Privacy implications
9. Operational cost
10. Revenue potential
11. Reuse of existing platform capabilities
12. Technical complexity
13. Data quality requirements
14. Whether the category creates a meaningful new user need

A category should not be added merely because it is technically possible.

## 8. Scope Prioritization Framework

| Dimension | Question |
| --- | --- |
| User value | Does this solve an important user problem? |
| Marketplace value | Does this improve discovery, supply, demand, or connection? |
| Trust | Does this improve safety or information quality? |
| Reach | Does this materially increase useful discoverability? |
| Reuse | Can the capability serve multiple categories? |
| Complexity | How much product and technical complexity does it introduce? |
| Risk | What privacy, security, fraud, or operational risks exist? |
| Evidence | What evidence supports building it now? |
| Dependency | What foundational capability must exist first? |
| Reversibility | Can the decision be changed later without major cost? |

This framework supports prioritization without turning the roadmap into a fixed promise of dates.

## 9. Roadmap Governance

The roadmap is a living product-management document.

Changes should be made when:

- Product strategy changes.
- User evidence changes.
- Major technical constraints are discovered.
- Regulatory or operational requirements change.
- A dependency changes.
- A major product decision is approved.
- A planned capability is no longer justified.

Major architectural consequences should also be recorded in the **ADR Register**.

Requirements should remain the detailed authority for what a specific capability must do.

## 10. Release Planning Rules

Each release should define:

- Release objective
- Scope
- Explicit exclusions
- Dependencies
- Acceptance criteria
- Risks
- Required documentation
- Required testing
- Operational readiness
- Rollback considerations

A release should not be defined only as a list of features.

### Release boundaries

A capability should be delayed when:

- A required dependency is incomplete.
- Security or privacy requirements are unresolved.
- The user value is unclear.
- Operational support is not ready.
- The capability creates disproportionate complexity for the current stage.

## 11. Scope Boundaries

### Product boundary

KHOJ BHET is responsible for the marketplace and discovery experience, not every external service required by users.

### Data boundary

The platform should store information necessary to operate its product while avoiding unnecessary collection of sensitive data.

### Privacy boundary

Exact residential locations and sensitive contact information should have explicit access rules.

### Technical boundary

Technology choices should serve documented product and technical requirements rather than define the product scope themselves.

### Commercial boundary

Monetization should support the marketplace rather than become the primary definition of the product.

## 12. Roadmap Dependencies

The following dependency direction should generally be respected:

**Vision → Scope → Requirements → Roles & Permissions → User Stories / Use Cases → User Flows → UX/UI → Architecture → Implementation → Testing → Release → Operations**

Shared platform foundations should normally precede category-specific implementations.

For example:

**Identity + Listing + Category + Location + Media + Search**

should exist conceptually before implementing many independent category systems.

## 13. Success Measures by Roadmap Stage

### Foundation

- Required product decisions documented
- Core models defined
- Architecture documented
- Major risks identified

### MVP

- Users can complete the core marketplace loop
- Listings can be created and discovered
- Search and filters work
- Contact mechanisms work
- Reports and moderation work

### Stabilization

- Listing quality improves
- Search relevance improves
- Duplicate/stale listings are controlled
- Operational reliability improves
- User feedback can be measured

### Expansion

- New categories can reuse the common platform
- Category-specific requirements remain manageable
- Search and discovery remain coherent

### Monetization

- Paid capabilities provide clear additional value
- Core marketplace usefulness remains intact
- Commercial operations are measurable

### Advanced Marketplace

- Complex interactions operate safely
- Transaction-related capabilities have appropriate controls
- Platform scalability supports additional use cases

Specific numerical targets should be maintained in product metrics, analytics, or release planning documents rather than permanently embedding them here.

## 14. Roadmap Anti-Patterns

KHOJ BHET should avoid:

- Building fully specialized workflows for every category simultaneously.
- Creating separate user systems per category.
- Adding features solely because competitors have them.
- Treating every user request as an immediate roadmap commitment.
- Designing monetization before understanding marketplace behavior.
- Exposing sensitive information for convenience.
- Introducing complex AI or recommendation systems before sufficient structured data exists.
- Making fixed long-term delivery promises without validated dependencies.
- Allowing technical implementation details to silently redefine product scope.

## 15. Relationship to Other Product Documents

This document defines **what is in scope, what is out of scope, and how the product should progress**.

Related documents:

- **01. Product Vision & Mission** — why KHOJ BHET exists and where it is going.
- **03. Requirements Specification** — detailed product requirements.
- **04. Users, Roles & Permissions** — access and capability model.
- **05. User Stories & Use Cases** — user goals and system interactions.
- **06. User Flows** — detailed journeys.
- **07. UX/UI Specification** — interface behavior and presentation.
- **08. Product & Business Rules** — detailed operational and commercial rules.
- **00.3 Decision / ADR Register** — significant architectural and technical decisions.

This roadmap does not replace requirements or implementation planning.

## 16. Document Status

**Status:** Active / Product Planning  

**Authority:** Product scope and roadmap direction  

**Primary use:** Control product boundaries, sequencing, release planning, and expansion decisions  

**Review trigger:** Major scope change, new product direction, major release decision, significant user evidence, or architectural constraint

---

## Document Control

**Document ID:** KB-PROD-002  

**Document:** Product Scope & Roadmap  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-21  

**Parent:** 01. PRODUCT DEFINITION  

**Related:** 01. Product Vision & Mission, 00.1 Documentation & SDLC Framework, 00.3 Decision / ADR Register  

**Next:** 03. Requirements Specification

## Approved V1 Scope Decision — Monetization Deferred (2026-10-18)

**Decision status: APPROVED BASELINE — supersedes any earlier implication that paid subscriptions or paid entitlements are required to launch the Marketplace MVP.**

The Marketplace MVP does not include paid subscription purchase, paid entitlement enforcement, recurring billing, payment-gateway checkout, or monetization-dependent access controls. Business subscriptions and monetization remain Stage 4 capabilities and require a separate approved scope/ADR before implementation. Existing subscription use cases may remain in the long-term product model but are not MVP acceptance criteria.

V1 must remain useful to non-paying users. The backend must not return protected phone/email or exact-location data simply because monetization is deferred. Use the free-V1 contact and location rules in Document 08. Manual payment submission and admin review are not part of MVP unless separately approved; gateway redirects, callbacks and webhooks are not V1 behavior.

**Required dependent-document treatment:** Documents 05, 07, 08, 13, 14, 17 and 22 must treat subscription/payment/entitlement flows as deferred UI/API capabilities except for authorization interfaces that are needed for future compatibility. Do not create a paid checkout or subscription purchase flow in the MVP. Reopen this decision only through the product change-control process.