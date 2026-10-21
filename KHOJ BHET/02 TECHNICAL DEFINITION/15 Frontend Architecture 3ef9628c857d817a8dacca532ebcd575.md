# 15. Frontend Architecture

> **Implementation status clarification — 2026-10-09:** “Active” means this is the current architecture design baseline, not that implementation is release-ready. Implementation remains gated by Document 14's regenerated OpenAPI 3.1 contract and successful clean-MySQL runtime validation.
> 

Document ID: KB-TECH-015

Status: Active — Frontend Architecture Baseline

Version: 1.0

Owner: KHOJ BHET Engineering

Last Reviewed: 2026-10-04

Parent: 02. TECHNICAL DEFINITION

Previous: 14. API Specification

Next: 16. Backend Architecture

Related: 07. UX/UI Specification, 08. Product & Business Rules, 09. Software Architecture, 10. Technology Stack, 12. Engineering Standards, 13. Database Architecture & Data Model, 14. API Specification, 17. Mobile Application Architecture, 18. Authentication & Authorization, 19. Security Architecture, 20. Media & File Storage, 21. Search Architecture, 22. Notification System, 23. SEO Architecture

# 1. Document Purpose

This document defines the web frontend architecture of KHOJ BHET. It translates the approved UX/UI, software architecture, technology stack, business rules, database model, and API contract into a production-oriented frontend structure for the public marketplace web application.

The frontend is responsible for routing, rendering, interaction, API consumption, forms, UI state, server-state handling, accessibility, responsive behavior, SEO presentation, loading/error/empty states, media presentation, and approved analytics/observability hooks.

The frontend is NOT authoritative for authorization, listing ownership, lifecycle, entitlement, privacy, exact-location access, contact access, moderation, payment validity, category eligibility, attribute validation, or report permissions.

Core rule: client-side checks improve UX only. The Laravel API remains authoritative for every business decision.

# 2. Architectural Authority

The frontend follows this chain:

Product Requirements → User Stories / Use Cases → User Flows → UX/UI Specification → Business Rules → Software Architecture → Technology Stack → API Specification → Frontend Architecture → Implementation → Tests

Primary authorities:

1. 
    1. UX/UI Specification — interface and interaction behavior.
2. 
    1. Product & Business Rules — business behavior.
3. 
    1. Software Architecture — system boundaries.
4. 
    1. Technology Stack — concrete technologies.
5. 
    1. Engineering Standards — implementation conventions.
6. 
    1. API Specification — API contract.
7. 
    1. Frontend Architecture — web implementation architecture.

# 3. Technology Baseline

| Area | Baseline |
| --- | --- |
| Framework | Next.js 16.2.x |
| UI | React 19.2.x |
| Language | TypeScript |
| Rendering | Server Components by default; Client Components where interaction requires them |
| Public rendering | SSR / static generation / ISR where appropriate |
| HTTP client | Axios 1.20.x |
| API | Laravel REST API /api/v1 |
| Authentication | Firebase Authentication |
| Primary data source | Laravel API backed by MySQL |
| Search | Laravel API → MySQL search for V1 |
| Maps | MapLibre-compatible implementation |
| Mobile | Separate React Native + Expo application |
| Node | 24.x LTS |

Exact versions are pinned in the project lockfile. Major-version changes require deliberate review and, where materially architectural, an ADR.

# 4. Architectural Goals

The frontend optimizes for:

- SEO-first marketplace discovery.
- Fast initial rendering.
- Accessibility.
- Predictable API integration.
- Minimal duplicated business logic.
- Clear server/client boundaries.
- Responsive mobile-first UI.
- Safe restricted-information handling.
- Dynamic category-driven listing forms.
- Maintainability and testability.
- Provider independence.
- Low initial infrastructure complexity.

# 5. High-Level Architecture

Browser

→ Next.js Web Application

→ Server Components / Client Components

→ Feature Modules

→ Typed API Client

→ Laravel REST API /api/v1

→ Authorization / Business Rules / MySQL / Redis / Queues / External Adapters

The browser must never connect directly to MySQL, Redis, internal storage, payment gateways, or administrative services.

Normal path:

UI → Feature → API client → Laravel API → authoritative domain/data layer.

# 6. Server and Client Components

Server Components are the default.

Use Server Components for:

- public listing pages;
- category pages;
- location pages;
- public search initialization;
- SEO metadata;
- public data fetching;
- stable public configuration.

Use Client Components only for:

- interactive forms;
- dialogs;
- image selection/preview;
- map interaction;
- client-side filters;
- browser storage;
- Firebase client authentication;
- real-time UI;
- drag-and-drop;
- browser-only APIs.

Do not make an entire route a Client Component merely because one child needs interactivity. Prefer server page plus small Client Components.

# 7. Route Architecture

Conceptual route tree:

/

├── search

├── category/[...categoryPath]

├── location/[locationSlug]

├── listing/[slugAndPublicId]

├── business/[businessSlug]

├── create-listing

├── my-listings/[id]

├── favorites

├── messages

├── notifications

├── account

│   ├── profile

│   ├── security

│   ├── subscriptions

│   └── settings

├── reports

└── auth

├── sign-in

└── callback

Routes represent user-facing resources and journeys, not database tables.

Public listing URLs use the canonical listing slug. Internal database IDs are not exposed unnecessarily. Filament admin routes remain outside the marketplace frontend.

# 8. Canonical Listing Route

Canonical public routes follow Document 23:

- Listing: `/listing/{slug}-{public-id}` (Next.js route segment: `[slugAndPublicId]`; parse the final public-ID suffix without treating the slug as identity).
- Category: `/category/{category-slug}`.
- Approved locality landing page: `/location/{location-slug}`.
- Eligible public business page: `/business/{business-slug}`.

The Laravel API remains authoritative for resource identity, visibility, and canonical slug history. Document 14's slug resolver must accept enough information to resolve the public-ID suffix and detect stale slug history; the API/web contract must be reconciled before implementation. The web/SEO layer emits HTTP 301 only when the current canonical resource is still eligible for public access.

# 9. Feature-Oriented Structure

Recommended conceptual structure:

src/

├── app/

├── features/

│   ├── auth/

│   ├── listings/

│   ├── categories/

│   ├── search/

│   ├── locations/

│   ├── businesses/

│   ├── business-members/

│   ├── verification/

│   ├── favorites/

│   ├── conversations/

│   ├── contact-reveal/

│   ├── user-safety/ (blocking/reporting)

│   ├── notifications/

│   ├── notification-preferences/

│   ├── reports/

│   ├── subscriptions/

│   ├── payments/

│   └── account/ (deactivate/reactivate/delete/cancel deletion)

├── components/

│   ├── ui/

│   ├── layout/

│   ├── feedback/

│   └── media/

├── lib/

│   ├── api/

│   ├── auth/

│   ├── config/

│   ├── formatting/

│   ├── validation/

│   ├── seo/

│   └── telemetry/

├── hooks/

├── types/

└── styles/

This is an architectural baseline; exact physical placement may evolve without changing the boundaries.

# 10. Frontend Layers

Layer 1 — App/Routing: routes, layouts, loading/error boundaries, metadata.

Layer 2 — Feature Modules: listings, search, businesses/members, verification, favorites, conversations/read cursor, contact reveal, user safety/blocking, notifications/preferences, account lifecycle, reports, subscriptions, and payments.

Layer 3 — Presentation: design-system primitives and reusable visual components.

Layer 4 — API Client: transport, auth headers, request IDs, idempotency, ETag/If-Match, API errors.

Layer 5 — Shared Utilities: formatting, configuration, telemetry, SEO helpers, non-authoritative validation.

# 11. API Client Architecture

Do not scatter raw Axios calls throughout components.

Preferred:

Feature → Typed API function → Shared Axios client → /api/v1

The shared client must implement Document 14 conventions:

- Authorization: Bearer Firebase ID token.
- Idempotency-Key.
- If-Match.
- X-Request-Id.
- ETag.
- Rate-limit headers.
- Retry-After.
- Deprecation and Sunset.

# 12. OpenAPI and Type Safety

Authority chain:

Document 14 → OpenAPI 3.1 → generated TypeScript types → implementation → contract tests.

Generated API types should be used for Listing, Category, Category Attribute, Location, User, Favorite, Conversation, Message, Notification, Subscription, Payment, Report, and other contract resources.

Do not independently redefine API models when an official generated type exists.

View models may be introduced when the UI requires a deliberate transformation.

# 13. Authentication

Marketplace users authenticate with Firebase Authentication.

Frontend:

1. Start Firebase sign-in/sign-up flow.
2. Maintain Firebase client auth state.
3. Obtain/refresh Firebase ID token.
4. Attach token to protected API requests.
5. Handle expiry and sign-out.

Backend:

1. Verify token.
2. Map identity to users.
3. Check account state and restrictions.
4. Authorize operation.
5. Enforce business rules.

The frontend must never send passwords or OTP codes to the marketplace business API and must never trust a client-supplied user ID.

# 14. Server State and UI State

Server state:

- listings;
- categories;
- locations;
- favorites;
- notifications;
- conversations;
- messages;
- subscriptions;
- account profile;
- entitlements.

UI state:

- modal state;
- selected tab;
- form step;
- gallery index;
- temporary input;
- drawer visibility;
- map viewport.

Do not copy entire API resources into global state without a demonstrated need.

# 15. Data Fetching

Public SEO-critical data should normally be server-fetched.

Authenticated interactive data may use client fetching.

Highly interactive temporary data should remain local to the component/feature.

Avoid aggressive global polling. Refresh only where user value justifies it.

# 16. Caching

Caching is an optimization, never the source of truth.

Suitable candidates:

- category metadata;
- category attribute definitions;
- Nepal reference locations;
- public listing representations;
- stable configuration.

Never share authorization-sensitive cached responses between users.

# 17. Dynamic Category and Attribute Forms

This is a critical architecture requirement.

The marketplace uses the approved category catalogue, category-specific attribute applicability, controlled options, free-text/numeric rules, multi-value attributes, and listing-type eligibility.

Preferred flow:

Select Category

→ Select Subcategory

→ Fetch Applicable Attributes

→ Resolve Controlled Options

→ Build Form Schema

→ Render Controls

→ Submit API Payload

→ Server Validation

GET /api/v1/categories/{slug}/attributes is authoritative for applicable attributes.

The frontend must not hard-code a separate full form implementation for every category.

# 18. Attribute Rendering

Map authoritative API definitions to reusable controls.

Examples:

- text → text input;
- long_text → textarea;
- integer/decimal → numeric input;
- boolean → checkbox/switch;
- date → date picker;
- enum → select/radio;
- multi-value enum → multi-select/checkbox group;
- location → location selector;
- media → media picker.

The form engine must honor required, filterable, searchable, multi-value, options, units, and category-specific nullable overrides.

# 19. Controlled Options

Controlled catalogue options are authoritative.

The client must never invent enum values.

Controlled flow:

API registry → frontend rendering → API submission.

Free-text values are allowed only where the catalogue/API defines the field as free text.

# 20. Listing Creation

The UI may use multiple steps, but the API contract requires category and listing type in the initial creation request. The frontend must not imply that an empty draft can be created before those required fields are known.

Select Category + Listing Type

→ `POST /listings` with required category and listing type

→ Receive created listing representation

→ `GET /listings/{id}/readiness`

→ Complete basic information, category attributes, price, location, and media

→ Refresh representation/readiness

→ Preview

→ Submit

→ Server validation / review

The readiness endpoint and server response are authoritative; the client must display missing requirements returned by the API.

# 21. Listing Lifecycle

The frontend presents lifecycle states returned by the API, such as:

- draft;
- review;
- published;
- paused;
- expired;
- archived;
- rejected.

The final API lifecycle enum is `draft`, `review`, `published`, `paused`, `expired`, `archived`, and `rejected`. `removed` is not a client-assignable lifecycle state; deletion/removal is a separately authorized operation. Do not allow arbitrary status assignment. Domain actions follow Document 14: submit, pause, resume, archive, restore, renew, and DELETE where authorized.

# 22. Optimistic Concurrency

Where the API supplies ETag:

1. retain the current ETag;
2. send If-Match on supported edits;
3. handle a supplied stale ETag with the documented 412 response;
4. inform the user that the resource changed and offer refresh/reconciliation.

Document 14 makes If-Match optional in V1. If omitted, the documented last-write-wins behavior applies; do not imply the API guarantees conflict detection for a request that omits the precondition. Prefer sending ETags wherever supported.

# 23. Idempotent Mutations

Retry-sensitive operations must follow Document 14 idempotency rules.

Examples:

- listing submission;
- payment initiation;
- renewal;
- account deletion request;
- other documented unsafe writes.

Reuse the same idempotency key for retries of the same logical operation. Generate a new key only for a new logical operation.

# 24. Price Presentation

The API uses decimal strings plus currency code.

The frontend must:

- preserve decimal precision;
- avoid binary floating-point business calculations;
- format NPR consistently;
- distinguish fixed, range, periodic, free, contact-only, and other approved pricing modes;
- never invent pricing states.

# 25. Nepal Location Architecture

The UI must support:

Country → Province → District → Municipality → Ward → Locality/Tole → Chowk/Landmark

Optional data:

- postal code;
- latitude/longitude;
- approximate location;
- exact location;
- landmark.

The UI must respect entitlement/privacy rules. Coordinates alone are not the canonical human-readable location.

# 26. Map Integration

Use a MapLibre-compatible abstraction.

Prefer:

Location Feature → Map Adapter / Location UI → MapLibre-compatible implementation

Do not spread provider-specific map calls throughout feature modules.

Geocoding remains behind the Location Service/provider abstraction.

# 27. Media Architecture

Media UI supports images and the single approved V1 listing video. It supports file selection/capture, preview, image ordering/primary image, validation, upload progress, retry, removal, and server processing state. V1 limits are governed by Document 20: up to 20 images (JPEG/PNG/WebP, 10 MB each) and at most one MP4 H.264/AAC video (50 MB, 60 seconds). Video processing is asynchronous; show pending/failed/ready states and the generated poster/playback representation returned by the API. Typical state: selected → validating → uploading (direct multipart) → processing → ready. A local file is not permanently stored until the server confirms persistence.

# 28. Search Frontend

V1 path:

Browser → Laravel API → MySQL search.

Search is a query capability, not a direct database query.

Search state may be URL-backed, for example:

/search?q=...&category=...&province=...&district=...&municipality=...&price_min=...&price_max=...

SEO behavior for query parameters follows 23. SEO Architecture.

# 29. Pagination

Use the authoritative API pagination model.

Choose pagination, load-more, or infinite scrolling according to UX and SEO requirements.

For SEO-critical public pages, crawlable pagination is preferred where appropriate. Infinite scrolling must not be the only way to discover more results.

# 30. Favorites

Favorites are authenticated server state.

The UI may optimistically update the control but must reconcile with the API response.

A visual button change is not proof of successful persistence.

# 31. Conversations and Messaging

MySQL is authoritative for conversations, participants, and messages.

Firestore may be used only as a secondary realtime projection/transport where implemented.

The web frontend consumes the authoritative API.

Messaging UI should represent sending, sent, failed, retry, unread/read, restricted, and unavailable states where exposed by the contract.

Business-owned listing conversations route to the active primary business representative under the current V1 rule.

# 32. Notifications

The frontend consumes notification records from the backend.

Support:

- list;
- unread state;
- read action;
- deep links;
- listing context where present;
- empty/error states.

Push delivery failure must not corrupt notification persistence.

# 33. Subscription and Entitlement UI

The frontend may show or hide UX based on entitlement state, but the API remains authoritative.

Examples:

- exact location;
- contact information;
- premium facilities;
- subscription state.

Never use a local premium flag as a security boundary.

# 34. Protected Data Rendering

Represent restricted information explicitly:

- visible;
- restricted;
- not_available;
- not_applicable;
- loading;
- error.

Never reconstruct restricted data from HTML, images, cache, URL parameters, browser storage, or other listings.

# 35. Error Handling

Classify errors:

- validation → field/form errors;
- authentication → sign-in/reauthentication;
- authorization → access explanation;
- not found → not-found state;
- conflict → refresh/reconcile;
- rate limited → retry guidance;
- network → retry;
- server → safe generic error + request ID;
- payment → payment-specific state;
- media → item-level retry.

Never expose raw stack traces or internal exception messages.

# 36. Loading and Empty States

Every major data surface defines:

1. loading;
2. loaded;
3. empty;
4. partial/secondary loading;
5. error;
6. retry.

Examples include search, favorites, notifications, messages, category attributes, and location data.

# 37. Accessibility

Accessibility is a first-class requirement.

Use:

- semantic HTML;
- keyboard navigation;
- visible focus;
- accessible names;
- correct labels;
- field/error association;
- contrast;
- screen-reader support;
- reduced-motion behavior;
- accessible dialogs/menus;
- logical heading hierarchy.

Accessibility testing belongs in the frontend test strategy.

# 38. Responsive Design

Support mobile browsers, tablets, laptops, and large desktops.

Use mobile-first responsive design.

Do not duplicate business logic for desktop and mobile web. Use one feature implementation with responsive presentation.

React Native + Expo remains a separate client architecture under Document 17.

# 39. SEO Boundary

The frontend is responsible for SEO presentation:

- canonical URLs;
- title/description;
- structured data where approved;
- crawlable public content;
- indexability;
- Open Graph metadata;
- sitemap integration;
- correct unavailable/removed listing behavior.

SEO logic must not become domain logic.

# 40. Performance

Priorities:

1. minimize client JavaScript;
2. use Server Components by default;
3. lazy-load heavy interactive components;
4. optimize images;
5. avoid unnecessary dependencies;
6. prevent duplicate API requests;
7. cache stable public data;
8. measure Core Web Vitals.

Performance optimization must never weaken privacy or authorization.

# 41. Image Strategy

Use responsive image delivery.

The frontend should:

- request appropriate dimensions;
- lazy-load below-the-fold images;
- prioritize primary images;
- preserve aspect ratio;
- use placeholders;
- handle broken images;
- avoid unnecessary full-resolution loads.

Media transformation/storage rules belong to Document 20.

# 42. Forms

Forms use reusable accessible primitives with:

- typed values;
- field validation;
- server-error mapping;
- loading state;
- duplicate-submit prevention;
- unsaved-change handling where appropriate.

Client validation improves UX; server validation remains authoritative.

# 43. Dynamic Form State

A conceptual listing payload is:

category_id

subcategory_id

listing_type

attributes[]

Actual field names and shapes must follow Document 14.

When category changes, incompatible attribute values must be cleared or deliberately reconciled.

# 44. Security Boundary

Never expose:

- API secrets;
- private keys;
- database credentials;
- payment secrets;
- Firebase Admin credentials;
- private storage credentials.

Only approved public configuration may enter browser code.

Treat browser state as user-controlled.

# 45. Firebase Boundary

Only Firebase client authentication capabilities required by the marketplace run in the browser.

Firebase Admin credentials remain server-side.

The browser must not use Firebase/Firestore to bypass the Laravel marketplace API.

Intended path:

Firebase Authentication → Firebase ID Token → Laravel API.

# 46. Environment Configuration

Public browser configuration may include:

- public API URL;
- Firebase public configuration;
- public map configuration;
- approved analytics identifiers.

Server-only configuration includes:

- provider secrets;
- signing secrets;
- private storage credentials;
- internal service credentials.

Environment separation must prevent server-only secrets entering client bundles.

# 47. Persistent Client State

Keep persistent browser state minimal.

Possible candidates:

- UI preferences;
- non-sensitive draft helpers where approved;
- display settings;
- temporary onboarding state.

Do not persist authoritative subscription, permission, payment, moderation, or restriction state as the source of truth.

# 48. Localization and Display

Use a centralized localization mechanism.

Requirements:

- UI strings are translatable;
- dates/numbers/currency are locale-aware;
- API enum values are not used directly as display labels;
- localized labels do not change API values.

Display language is presentation; API enum values remain stable.

# 49. Enum Registry

Public API enum values must be mapped through a centralized display registry.

Example:

published → localized label

paused → localized label

expired → localized label

Do not duplicate enum-to-label mappings throughout components.

The final public enum registry from the API contract is authoritative.

# 50. Date, Time, Money and Units

API timestamps are UTC ISO 8601 values.

The frontend parses UTC and displays according to approved locale/time-zone rules.

Money remains decimal-safe.

Units must be displayed through reusable unit-aware formatters. Stored/API values remain authoritative.

# 51. Component Architecture

Three levels:

1. Primitive UI — Button, Input, Select, Dialog, Tabs, Badge, Skeleton.
2. Domain-neutral composites — SearchBar, PriceRange, ImageGallery, LocationPicker, EmptyState.
3. Feature components — ListingCard, ListingAttributeForm, ListingStatusActions, FavoriteButton, ConversationComposer, SubscriptionGate.

Feature-specific components stay close to their feature.

# 52. Design System

The code design system derives from 07. UX/UI Specification and approved Figma representations.

It should define:

- typography;
- spacing;
- color tokens;
- borders/radii;
- responsive breakpoints;
- component states;
- accessibility behavior.

Repeated patterns should not receive arbitrary one-off styling without reason.

# 53. Error Boundaries

Route segments should provide appropriate loading, error, and not-found boundaries.

A failure in a secondary feature should not unnecessarily destroy the whole page.

Examples:

- map failure should not prevent listing details;
- recommendations failure should not prevent search results;
- notification failure should not prevent account access.

# 54. Network Resilience

The web application is not an offline authoritative datastore.

For temporary network failure:

- show retry;
- preserve unsent form data where appropriate;
- prevent duplicate submissions;
- reuse idempotency keys for retries.

Never show an unsafe mutation as successful until the server confirms it.

# 55. Analytics

Analytics is not business truth.

Allowed events may include:

- page view;
- search interaction;
- listing view;
- favorite interaction;
- listing creation funnel;
- performance;
- safe error events.

Never send passwords, OTPs, payment credentials, private messages, moderation notes, exact private addresses, or unnecessary personal data.

# 56. Observability

Frontend observability covers:

- JavaScript errors;
- failed API requests;
- route failures;
- performance metrics;
- asset failures;
- listing funnel failures;
- media upload failures;
- payment initiation failures.

Where useful, preserve X-Request-Id for support.

# 57. Testing Architecture

Unit tests:

- formatters;
- pure functions;
- enum mappings;
- validation helpers;
- attribute mapping.

Component tests:

- forms;
- accessibility;
- loading/error/empty states;
- listing cards;
- search controls;
- protected-data presentation.

Integration tests:

- API client;
- authentication;
- feature workflows;
- server/client boundaries.

E2E tests:

- browse;
- search;
- sign in;
- create listing;
- submit;
- edit;
- lifecycle actions;
- favorites;
- contact/message;
- entitlement;
- report;
- subscription/payment;
- account reactivation/deletion flows.

Contract tests:

- generated types and API assumptions remain aligned with OpenAPI 3.1.

# 58. Critical E2E Priorities

P0:

- public browse;
- search;
- listing detail;
- authentication;
- create listing;
- edit listing;
- submit listing;
- lifecycle actions;
- protected information entitlement.

P1:

- favorites;
- contact/message;
- reports;
- subscription/payment;
- reactivation;
- deletion request.

# 59. Dependency Management

Rules:

1. Prefer native Next.js/React capabilities where sufficient.
2. Avoid multiple libraries for the same concern.
3. Keep dependencies within the approved version line.
4. Review security advisories.
5. Commit lockfile changes.
6. Remove unused dependencies.
7. Do not add global state infrastructure without demonstrated need.

# 60. Performance Budget

Establish measurable budgets for:

- JavaScript bundle size;
- route-level client JavaScript;
- image payload;
- initial API request count;
- server render latency;
- Core Web Vitals.

Budgets should be monitored in CI or performance tooling where practical.

# 61. Deployment

Initial topology:

Internet

→ Reverse Proxy / TLS

→ Next.js Web Runtime

→ Laravel API

→ MySQL / Redis / other infrastructure

The frontend must not depend on development-only proxies or local filesystem behavior.

Environment configuration is injected during deployment.

# 62. CI/CD Gate

Frontend pull requests should pass, as applicable:

1. dependency installation;
2. type checking;
3. linting;
4. unit tests;
5. component tests;
6. build;
7. API contract validation;
8. accessibility checks;
9. E2E smoke tests;
10. dependency/security scan.

A successful Next.js build alone is not release readiness.

# 63. API Drift Prevention

The frontend must not silently adapt to undocumented backend behavior.

Preferred workflow:

API Contract Change

→ OpenAPI Update

→ Generated Types

→ Frontend Implementation

→ Backend Implementation

→ Contract Tests

Undocumented API behavior is treated as drift and must be resolved explicitly.

# 64. Feature Development Workflow

Requirement

→ Use Case

→ User Flow

→ UX/UI

→ Business Rules

→ API Contract

→ Frontend Feature Design

→ Components

→ Implementation

→ Tests

→ Accessibility / SEO / Performance Review

→ Release

Complex UI work should not begin before the relevant API contract and business behavior are sufficiently defined.

# 65. Responsibility Matrix

| Concern | Frontend | Backend |
| --- | --- | --- |
| Form UX | Presentation authority | Validation authority |
| Authentication UI | Yes | Token verification |
| Authorization | UX hints | Authoritative |
| Listing lifecycle | Render/actions | Authoritative |
| Category fields | Render from API | Applicability authority |
| Enum labels | Presentation | Contract |
| Entitlements | Present state | Authoritative |
| Exact location | Display if permitted | Permission authority |
| Price formatting | Yes | Value/currency truth |
| Search UI | Yes | Search semantics |
| Moderation | Display state | Authority |
| Payment status | Display | Authority |
| Messaging state | Display | Authority |
| SEO | Presentation | Canonical/resource authority |
| Database | Never direct | Authority |
| Redis | Never direct | Infrastructure |
| Firestore | No business authority | Optional secondary/realtime |

# 66. What Frontend Must Never Do

The web frontend must never:

- connect directly to MySQL;
- implement authoritative permissions;
- send Firebase credentials as business authorization;
- expose admin REST surfaces;
- decide payment success;
- manufacture API enum values;
- invent category attributes or controlled options;
- expose restricted location/contact data;
- bypass lifecycle commands;
- treat cached data as authoritative;
- trust browser storage for entitlement;
- silently overwrite concurrency conflicts;
- retry unsafe operations with new idempotency keys;
- expose secrets;
- leak private data to analytics.

# 67. Frontend Architecture Principles

FE-PR-001 — Server-first rendering: Server Components and server rendering by default.

FE-PR-002 — API authority: marketplace business data comes through the API boundary.

FE-PR-003 — Feature ownership: feature modules own feature-specific presentation and interaction.

FE-PR-004 — Generated contract types: API types derive from OpenAPI.

FE-PR-005 — Minimal global state: global state requires demonstrated need.

FE-PR-006 — Dynamic catalogue: listing forms derive from authoritative category/attribute definitions.

FE-PR-007 — Secure presentation: UI is never the privacy or authorization boundary.

FE-PR-008 — SEO-first public pages: public marketplace pages remain crawlable and performant.

FE-PR-009 — Responsive by default: one web application adapts across screen sizes.

FE-PR-010 — Measured optimization: complexity and performance decisions are evidence-driven.

# 68. Relationship to Mobile Architecture

Web and mobile are separate presentation applications.

Shared:

- API contract;
- domain vocabulary;
- public identifiers;
- business rules;
- authentication model;
- entitlement semantics;
- listing lifecycle;
- catalogue;
- public enums.

Not shared directly:

- Next.js rendering;
- React Native UI;
- browser APIs;
- web routing;
- mobile navigation;
- platform-specific UI.

Detailed mobile architecture belongs in Document 17.

# 69. Relationship to Backend Architecture

Document 15 defines how the web client consumes the backend.

Document 16 defines Laravel implementation concerns including:

- domain modules;
- application services;
- controllers;
- request validation;
- API resources;
- policies;
- persistence;
- queues;
- events;
- provider adapters.

Frontend code must not depend on Laravel implementation details that are absent from Document 14.

# 70. Relationship to UX/UI

1. UX/UI Specification remains authoritative for interface behavior.

Document 15 answers how the web application technically implements that approved experience.

UX/UI = what the user should experience.

Frontend Architecture = how the web application implements it.

Technical constraints must not silently alter approved product behavior.

# 71. Traceability

Example: Public Listing

Requirement → Listing Use Case → Listing Flow → Listing UX → Business Rules → API → Next.js route → E2E test.

Example: Create Listing

Requirement → UC-004 → Creation Flow → Dynamic Attribute UI → Listing API → MySQL-backed backend → E2E.

Example: Search

Requirement → Search Use Case → Search UX → Search API → Next.js Search → API test → E2E.

Example: Protected Contact

Requirement → Contact Use Case → Contact UX → Entitlement Rule → API Authorization → Protected UI → E2E.

# 72. Review Checklist

Architecture:

- Server/client boundaries explicit.
- Feature boundaries clear.
- API access centralized.
- Generated API types used.
- Global state justified.
- Dynamic catalogue implemented.

Security:

- No secrets in browser.
- Authorization server-side.
- Restricted data protected.
- Firebase Admin credentials server-side.
- Browser storage is not authoritative.

API:

- /api/v1 contract followed.
- Auth headers correct.
- Idempotency correct.
- ETag/If-Match implemented where required.
- Request IDs preserved.
- Enums match final registry.

UX:

- Loading states.
- Empty states.
- Error states.
- Retry behavior.
- Accessibility.
- Responsive behavior.

SEO:

- Public pages crawlable.
- Canonical URLs correct.
- Metadata correct.
- Restricted information excluded.
- Listing lifecycle handled.

Performance:

- Client JavaScript minimized.
- Images optimized.
- Heavy components lazy-loaded.
- Duplicate API requests controlled.
- Core Web Vitals measured.

Testing:

- Type check.
- Unit/component tests.
- Contract tests.
- Accessibility tests.
- Critical E2E tests.

# 73. Deferred Frontend Decisions

These remain implementation choices unless later elevated by an ADR:

- exact UI component library;
- exact form library;
- exact server-state library;
- analytics provider;
- error-monitoring provider;
- web push implementation;
- map tile provider;
- media CDN;
- dedicated search engine;
- final deployment topology.

The choices must remain compatible with this architecture and Document 14.

# 74. Recommended Implementation Order

1. Project/bootstrap.
2. TypeScript, lint, test infrastructure.
3. Design tokens and UI primitives.
4. Shared layout/navigation.
5. API client and generated types.
6. Firebase authentication.
7. Public category/location/listing pages.
8. Search and filtering.
9. Listing detail.
10. Dynamic listing creation forms.
11. Listing management/lifecycle.
12. Favorites.
13. Protected contact/location.
14. Conversations.
15. Notifications.
16. Account settings.
17. Subscription/entitlement.
18. Payment UI.
19. Reporting.
20. SEO hardening.
21. Accessibility hardening.
22. Performance optimization.
23. E2E and production readiness.

# 75. Definition of Done

A frontend feature is complete only when:

- requirement/use case identified;
- UX/UI behavior implemented;
- API contract aligned;
- TypeScript types correct;
- authorization assumptions server-backed;
- loading/empty/error states implemented;
- accessibility met;
- responsive behavior tested;
- SEO handled where applicable;
- performance acceptable;
- useful unit/component tests present;
- critical E2E coverage present;
- no restricted data or secrets exposed;
- architecture documentation updated when boundaries changed.

# 76. Final Architectural Baseline

Next.js 16.2.x

- 

React 19.2.x

- 

TypeScript

- 

Server Components / SSR / ISR

- 

Client Components where required

- 

Feature Modules

- 

Shared UI / Design System

- 

Typed Axios API Client

- 

Firebase Authentication

↓

Laravel REST API /api/v1

↓

Authorization + Business Rules + MySQL + Redis/Queues + Provider Adapters

Final rule: the KHOJ BHET web frontend is a presentation and interaction layer over the authoritative API. It should be server-rendered where beneficial, client-interactive where necessary, feature-oriented, type-safe, accessible, SEO-capable, responsive, and deliberately thin in business authority.

# 77. Document Control

Document: 15. Frontend Architecture

Document ID: KB-TECH-015

Status: Active — Frontend Architecture Baseline

Version: 1.0

Owner: KHOJ BHET Engineering

Last Reviewed: 2026-10-04

Previous: 14. API Specification

Next: 16. Backend Architecture

Architecture conclusion: The web frontend architecture is sufficiently defined to begin implementation after the current runtime/database validation and API contract gates are satisfied. Implementation must use Document 14 as the API contract and must not introduce client-side business authority that belongs to the backend.