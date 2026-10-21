# 01. Product Vision & Mission

**Project:** KHOJ BHET  

**Document:** Product Vision & Mission  

**Document ID:** KB-PROD-001  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-21  

**Parent:** 01. PRODUCT DEFINITION  

**Related:** 00.1 Documentation & SDLC Framework, 00.2 Terminology & Glossary, 00.3 Decision / ADR Register  

**Next:** 02. Product Scope & Roadmap

---

## Document Purpose

This document defines the long-term product direction of **KHOJ BHET**. It establishes the product's purpose, vision, mission, positioning, target users, core value proposition, guiding principles, and strategic boundaries.

It is the primary product-level reference for subsequent documents in the **01. PRODUCT DEFINITION** section.

<aside>
🎯

**Core idea:** KHOJ BHET is a Nepal-focused platform for discovering and connecting people with things, places, opportunities, and services they need — starting with a trusted, searchable marketplace.

</aside>

## 1. Product Identity

**Product:** KHOJ BHET

**Meaning:** *Khoj* = search / discover. *Bhet* = find / meet.

**Positioning:** A Nepal-focused discovery and marketplace platform where people can **find, buy, sell, rent, offer, request, and connect**.

**Core positioning statement:**

> **KHOJ BHET — Find • Buy • Sell • Rent • Connect**
> 

The platform is intended to evolve beyond a conventional classifieds website. The long-term product should provide a common discovery and transaction-oriented foundation that can support multiple categories and services without creating a separate platform for every use case.

## 2. Vision

### Vision Statement

> **To become a trusted digital marketplace and discovery platform for Nepal, making it simple for people to find what they need and for individuals and businesses to reach the people who need what they offer.**
> 

The vision is broader than listing advertisements. KHOJ BHET should progressively become a useful digital layer connecting:

- People ↔ People
- Buyers ↔ Sellers
- Tenants ↔ Owners
- Employers ↔ Workers
- Customers ↔ Service Providers
- Businesses ↔ Customers
- People ↔ Local opportunities

The product should make discovery **local, searchable, understandable, and accessible** across Nepal.

## 3. Mission

### Mission Statement

> **To build a simple, trustworthy, location-aware platform that helps people across Nepal discover relevant listings and opportunities while giving individuals and businesses practical tools to present, manage, and grow what they offer.**
> 

The mission is expressed through five commitments:

1. **Make discovery easier** — provide strong search, categories, filters, and location-based discovery.
2. **Make marketplaces more useful** — support buying, selling, renting, offering, and requesting through a common listing model.
3. **Improve local discoverability** — represent Nepal's administrative areas and locally recognized places accurately.
4. **Build trust into the platform** — provide verification, reporting, moderation, listing status, and clear information.
5. **Grow from a practical core** — launch a focused marketplace first and expand only when real user needs justify additional capabilities.

## 4. The Problem KHOJ BHET Solves

People searching for property, vehicles, used goods, rooms, jobs, workers, or services often face fragmented information.

Common problems include:

- Listings spread across many websites, social platforms, groups, and informal networks.
- Difficulty finding information for a specific local area.
- Inconsistent listing formats and incomplete information.
- Poor search and filtering.
- Unclear seller or poster identity.
- Old, duplicated, unavailable, or misleading listings.
- Difficulty comparing relevant listings.
- Lack of structured location information.
- Limited tools for ordinary individuals to publish and manage listings.
- Separation between different marketplace categories that could otherwise share the same discovery infrastructure.

KHOJ BHET addresses these problems through a **unified listing and discovery platform**.

## 5. Core Value Proposition

### For people looking for something

KHOJ BHET should help users:

- Search one place instead of checking many sources.
- Filter results according to their actual requirements.
- Search by meaningful Nepal locations.
- Compare relevant listings.
- Understand the basic information before contacting a poster.
- Save useful listings and searches.
- Contact the appropriate person or business.
- Report problematic listings.

### For people offering something

KHOJ BHET should help users:

- Publish listings without unnecessary complexity.
- Add photos, descriptions, price, location, facilities, and category-specific information.
- Manage multiple listings from one account.
- Reach users searching in relevant locations.
- Build a trustworthy profile over time.
- Upgrade capabilities when additional visibility or business functionality becomes useful.

### For businesses

The long-term product should provide businesses with:

- Business profiles.
- Multiple listings.
- Verification.
- Better visibility.
- Customer discovery.
- Analytics and management tools.
- Category-specific business capabilities.

## 6. Product Scope at the Vision Level

KHOJ BHET is designed as a **general discovery and marketplace platform**, not as a single-category website.

Potential product domains include:

- Property
- Vehicles
- Electronics
- Home & Furniture
- Fashion
- Jobs & Work
- Services
- Tickets
- Other local goods and opportunities

These are product modules rather than independent applications.

The platform should maintain a common foundation for:

- Users
- Profiles
- Listings
- Categories
- Locations
- Media
- Attributes
- Search
- Favorites
- Messaging/contact
- Reports
- Verification
- Moderation
- Notifications
- Business profiles

Category-specific requirements should extend this common foundation rather than create completely separate product systems.

## 7. Target Users

KHOJ BHET is intended to serve multiple participant types through one identity system.

### Individuals

- Buyers
- Sellers
- Owners
- Tenants
- Landlords
- Renters
- Vehicle owners
- Used-goods sellers
- Job seekers
- Employers
- Workers
- Service providers

### Professional users

- Dealers
- Agents
- Brokers
- Property managers
- Freelancers
- Local professionals

### Businesses

- Shops
- Agencies
- Dealers
- Builders
- Service businesses
- Local enterprises

A single account may participate in multiple roles.

**Principle:** one identity, multiple capabilities.

## 8. Geographic Focus

KHOJ BHET is initially focused on **Nepal**.

The product should treat location as a core part of the marketplace rather than merely an optional address field.

The location model should support, where applicable:

**Country → Province → District → Municipality → Ward → Locality/Tole → Chowk/Landmark → GPS**

The product should recognize that people frequently search using locally familiar names such as:

- Chowk
- Tole
- Bazaar
- Market
- Landmark
- Nearby institutions or public places

Official administrative data and locally recognized place names should therefore be handled as related but distinct concepts.

## 9. Trust as a Product Principle

Marketplace usefulness depends on trust.

KHOJ BHET should progressively support:

- Phone/email verification
- User verification
- Business verification
- Listing verification
- Clear listing status
- Reporting
- Moderation
- Fraud/scam reporting
- Duplicate detection
- Expiration of stale listings
- Seller/poster type
- Transparent verification meanings

A verification badge must describe **what was verified**. Verification of a user should not automatically mean that every listing posted by that user is legitimate.

## 10. Privacy and Information Access

KHOJ BHET should not assume that all listing information must be publicly exposed.

Depending on the listing and the poster's permissions, the platform may distinguish between:

**Public/basic information**

- Category
- Photos
- General location
- Basic price information
- General description
- Selected facilities

**Restricted information**

- Direct contact information
- Exact address
- Exact map location
- Additional seller information

Access to restricted information may later be governed by seller permission, user authorization, subscription entitlements, verification, or other explicit product rules.

For residential property especially, privacy and safety must take precedence over indiscriminate disclosure.

## 11. Marketplace Model

The core marketplace model is two-sided:

**People offering something ↔ People looking for something**

The platform should support both sides.

### Supply

- Sale
- Rent
- Lease
- Service
- Job
- Free
- Exchange

### Demand

- Wanted listings
- Requests
- Search-driven discovery

The **Wanted** concept is strategically important for the long-term platform because it allows demand to be represented explicitly rather than requiring users to wait for a matching seller listing.

## 12. Universal Listing Principle

The product should be built around a **universal listing model**.

Conceptually:

User → Listing → Category → Category-specific attributes

The same user should be able to create:

- A room-for-rent listing.
- A vehicle-for-sale listing.
- A mobile-for-sale listing.
- A furniture listing.

The platform should not require a separate account or completely separate marketplace architecture for each category.

**Core principle:**

> **One user → many listings → one universal listing engine → category-specific attributes.**
> 

This principle is central to the product's scalability.

## 13. Search and Discovery as Core Capabilities

Search is not a secondary feature of KHOJ BHET. It is one of the product's primary capabilities.

Users should be able to discover listings using combinations of:

- Keyword
- Category
- Listing type
- Price
- Location
- Category-specific attributes
- Facilities
- Condition
- Availability
- Seller/poster type

The search experience should progressively become more relevant through structured data, location intelligence, quality signals, and user behavior.

## 14. Product Principles

### 14.1 Local-first

The product should reflect how people in Nepal actually search, describe, and identify places and goods.

### 14.2 Simple by default

Creating and finding a listing should not require unnecessary complexity.

### 14.3 Structured information

Important information should be stored in structured form so it can be searched, filtered, compared, and reused.

### 14.4 One platform, many categories

Categories should share common infrastructure whenever the underlying behavior is the same.

### 14.5 Trust before monetization

The platform should establish useful marketplace activity and trust before aggressively restricting essential information behind paid features.

### 14.6 Privacy by design

Sensitive information, particularly exact residential location and direct contact details, should not be exposed without an appropriate access model.

### 14.7 SEO and discoverability

Important public marketplace content should be indexable and discoverable through search engines where appropriate.

### 14.8 Mobile accessibility

The product should work well on mobile devices because mobile access is central to the intended user base.

### 14.9 Incremental expansion

The product should begin with a focused set of high-value categories and expand based on actual usage and validated needs.

### 14.10 Modular internal design

The platform should be capable of adding new product modules without redesigning its fundamental identity, listing, location, media, search, and user systems.

## 15. Initial Product Direction

The first release should **not** attempt to implement the entire long-term vision.

The initial marketplace should concentrate on a practical core such as:

- Room / Flat / House
- Land
- Bike / Car
- Mobile / Electronics
- Furniture

The initial product should establish the fundamental loop:

**Register → Create listing → Discover → Search/filter → View listing → Contact → Report/manage**

Additional capabilities can be introduced after the core marketplace demonstrates real usage.

## 16. Long-Term Direction

KHOJ BHET may eventually expand from a marketplace into a broader local discovery platform supporting:

- Property discovery
- Goods marketplace
- Vehicle marketplace
- Jobs and workers
- Local services
- Wanted requests
- Business discovery
- Ticket discovery
- More advanced communication
- Payments and transaction workflows
- Business tools
- Recommendations and personalization

These capabilities are part of the **long-term product direction**, not automatic V1 requirements.

## 17. What KHOJ BHET Is Not

KHOJ BHET should not initially become:

- A collection of unrelated applications.
- A marketplace where every category has an independent user system.
- A platform that exposes every seller's private information by default.
- A platform that attempts to launch every planned category simultaneously.
- A payment-heavy transaction platform before basic marketplace liquidity exists.
- A system where every piece of data is forced into an unstructured dynamic attribute model.

The product should first become useful at its core.

## 18. Success Definition

At the product-vision level, success means that users can reliably complete the core discovery loop:

**Need → Search → Relevant results → Understand → Connect → Outcome**

For sellers and providers:

**Offer → Publish → Discoverability → Contact → Outcome**

Longer-term success should be measured through actual marketplace activity and quality indicators such as:

- Active listings
- Active users
- Search activity
- Listing views
- Contact interactions
- Successful connections
- Listing freshness
- Report rates
- Verification adoption
- Repeat usage
- Business participation

Specific measurable targets belong in the product roadmap and requirements documents rather than this vision document.

## 19. Strategic Guardrails

Future product decisions should be checked against these questions:

1. Does this make discovery easier?
2. Does it improve the usefulness of the marketplace?
3. Does it improve trust or reduce avoidable risk?
4. Does it respect user privacy?
5. Does it work for Nepal's local context?
6. Does it reuse the common platform foundation where appropriate?
7. Does it create unnecessary complexity for V1?
8. Is there evidence that users need it now?
9. Can the capability scale to additional categories later?
10. Does it support the long-term KHOJ BHET vision?

If a proposed feature conflicts with the core product principles, the conflict should be explicitly documented and decided rather than silently introduced.

## 20. Relationship to Other Product Documents

This document defines **why KHOJ BHET exists and where it is going**.

The next product documents should define:

- **02. Product Scope & Roadmap** — what is included, excluded, and when.
- **03. Requirements Specification** — what the product must do.
- **04. Users, Roles & Permissions** — who can do what.
- **05. User Stories & Use Cases** — how users interact with the product.
- **06. User Flows** — how key journeys work.
- **07. UX/UI Specification** — how those journeys are presented.
- **08. Product & Business Rules** — detailed behavioral and commercial rules.

Technical architecture should remain downstream of these product decisions.

## 21. Document Status

**Status:** Active / Foundational  

**Authority:** Product-level direction  

**Primary use:** Reference for product scope, requirements, design, architecture, and future decisions  

**Review trigger:** Major change to the product's purpose, target market, core marketplace model, geographic strategy, or fundamental value proposition

---

## Document Control

**Document ID:** KB-PROD-001  

**Document:** Product Vision & Mission  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-21  

**Parent:** 01. PRODUCT DEFINITION  

**Related:** 00.1 Documentation & SDLC Framework, 00.2 Terminology & Glossary, 00.3 Decision / ADR Register  

**Next:** 02. Product Scope & Roadmap