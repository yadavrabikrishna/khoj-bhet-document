# 07. UX/UI Specification

**Project:** KHOJ BHET  

**Document:** UX/UI Specification  

**Document ID:** KB-PROD-007  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Product  

**Last Reviewed:** 2026-09-23  

**Parent:** 01. PRODUCT DEFINITION  

**Related:** 03. Requirements Specification, 04. Users, Roles & Permissions, 05. User Stories & Use Cases, 06. User Flows, 08. Product & Business Rules  

**Previous:** 06. User Flows  

**Next:** 08. Product & Business Rules

---

# 1. Document Purpose

This document defines the user experience and interface behavior required to turn the approved product requirements, user stories/use cases, and user flows into a consistent marketplace experience.

It defines **how users interact with KHOJ BHET** at the product-behavior level. It does not define visual branding, final colors, typography, pixel-level layouts, or implementation-specific component code. Those decisions belong in later design-system and implementation work.

The written UX/UI specification is the product source of truth for interface behavior.

> **Core idea:** A screen should exist because it supports a defined user goal, requirement, use case, flow, permission, or business rule.
> 

# 2. UX/UI Principles

KHOJ BHET should follow these principles:

1. **Goal-oriented** — interfaces should support a clear user goal.
2. **Simple by default** — show necessary information without unnecessary complexity.
3. **Progressive disclosure** — reveal advanced fields and restricted information only when relevant.
4. **Consistent** — common actions and states should behave consistently across categories.
5. **Trust-aware** — clearly communicate verification, listing state, seller identity, and restrictions.
6. **Privacy-aware** — do not expose exact location or private contact information without authorization.
7. **Mobile-first behavior** — core marketplace tasks must remain usable on small screens.
8. **Responsive** — layouts should adapt to supported device sizes.
9. **Accessible** — controls, labels, errors, contrast, keyboard behavior, and touch targets should support applicable accessibility requirements.
10. **Recoverable** — users should not lose meaningful work because of ordinary interruption or recoverable failure.
11. **Localized for Nepal** — location, currency, language, and terminology should support Nepal-specific usage.
12. **Traceable** — major UI behavior should map to requirements, stories/use cases, and user flows.

# 3. UX/UI Scope

The initial UX/UI specification covers:

- Public discovery
- Search and filtering
- Listing results
- Listing detail
- Listing creation
- Drafts and listing management
- Listing editing
- Listing lifecycle actions
- Authentication-related screens
- User profile
- Favorites/saved listings
- Contact poster
- Reporting
- Permission and entitlement states
- Location selection
- Subscription/entitlement presentation
- Moderation interfaces at a conceptual level
- Loading, empty, validation, error, unavailable, and restricted states
- Responsive and accessibility behavior
- Navigation and information hierarchy

Visual identity and final design tokens are intentionally outside this document.

# 4. Information Architecture

The initial product information architecture should be organized around the following areas:

| Area | Primary Purpose |
| --- | --- |
| Home / Discovery | Discover marketplace content |
| Search | Find listings using queries |
| Categories | Browse by marketplace category |
| Search Results | Review matching listings |
| Listing Detail | Inspect one listing |
| Create Listing | Create a new listing |
| My Listings | Manage owned/managed listings |
| Saved Listings | Access favorites |
| Messages / Contact | Manage permitted communication |
| Profile | Manage user-facing account information |
| Notifications | Review relevant events |
| Subscription | View plans/entitlements where enabled |
| Reports / Safety | Report problematic content |
| Administration | Authorized operational management |

The exact navigation structure may vary by client, but core concepts should remain consistent.

# 5. Navigation Model

## 5.1 Primary Navigation

The primary navigation should provide access to the highest-frequency marketplace functions.

Core concepts:

- Home / Discover
- Search
- Categories
- Create Listing
- Saved
- My Listings
- Profile

Not every item must appear as a permanent navigation item on every device.

## 5.2 Contextual Navigation

Contextual actions should appear close to the object they affect.

Examples:

- Edit on the owner's listing
- Save on a listing
- Contact on a listing detail
- Report on a listing or profile
- Pause/Resume in listing management
- Delete/Archive in management actions

## 5.3 Back Navigation

Back navigation should preserve user context where practical.

Examples:

- Returning from listing detail should preserve search results and filters.
- Returning from a category selector should preserve previously entered listing information.
- Returning from an interrupted listing-creation step should preserve the draft when safe.

# 6. Core Screen Catalogue

The initial screen catalogue should include:

| ID | Screen / View | Primary Actor | Related Flow |
| --- | --- | --- | --- |
| UX-001 | Home / Discovery | Visitor / User | UF-009 |
| UX-002 | Search | Visitor / User | UF-009 |
| UX-003 | Search Results | Visitor / User | UF-009 / UF-010 |
| UX-004 | Filter & Sort | Visitor / User | UF-010 |
| UX-005 | Listing Detail | Visitor / User | UF-011 |
| UX-006 | Create Listing — Category | Poster | UF-004 |
| UX-007 | Create Listing — Details | Poster | UF-004 |
| UX-008 | Create Listing — Location | Poster | UF-004 |
| UX-009 | Create Listing — Media | Poster | UF-004 |
| UX-010 | Create Listing — Preview | Poster | UF-004 / UF-006 |
| UX-011 | My Listings | Poster | UF-005 / UF-008 |
| UX-012 | Edit Listing | Poster | UF-005 |
| UX-013 | Saved Listings | Registered User | UF-012 |
| UX-014 | Contact Poster | Registered User | UF-013 |
| UX-015 | Report Listing | Visitor / User | UF-014 |
| UX-016 | Report User | Registered User | UF-015 |
| UX-017 | Profile | Registered User | UF-003 |
| UX-018 | Notifications | Registered User | Notification flows |
| UX-019 | Subscription / Entitlements | Registered User | UF-018 / UF-019 |
| UX-020 | Moderation Queue | Moderator | UF-016 |
| UX-021 | Moderation Review | Moderator | UF-016 |
| UX-022 | Account / Access Restriction | User / Moderator | UF-017 |

This catalogue is a baseline and may expand as approved requirements become more specific.

# 7. Home and Discovery UX

The discovery experience should allow a user to understand what KHOJ BHET offers and begin finding relevant listings quickly.

Core elements may include:

- Search entry
- Category navigation
- Relevant location context
- Recent or relevant listings
- Popular categories where supported
- Saved/recent discovery where appropriate
- Clear entry to create a listing

The interface should avoid requiring authentication merely to browse public listings unless a specific feature requires it.

# 8. Search and Discovery UX

**Related flows:** UF-009 Search Listings, UF-010 Filter and Sort Listings.

## 8.1 Search Entry

The search interface should support:

- Free-text query
- Category selection
- Location selection
- Search suggestions where implemented
- Clear/reset behavior
- Submission through an explicit action or supported immediate search behavior

## 8.2 Search Results

Each result should provide enough information for a user to assess relevance without opening every listing.

Typical result information:

- Primary image
- Title
- Price representation where applicable
- Category/listing type
- Public location
- Relevant category attributes
- Listing state where relevant
- Poster/verification indicators where applicable
- Saved state

## 8.3 Filters

Filters should be category-aware.

Common filters may include:

- Category
- Location
- Price range
- Listing type
- Condition
- Availability
- Facilities
- Category-specific attributes

The UI should not expose filters that have no meaningful relationship to the selected category.

## 8.4 Sorting

Possible sorting options:

- Relevance
- Newest
- Price
- Distance where supported

Only meaningful options should be displayed.

## 8.5 Result State

The search interface should define:

- Results available
- No results
- Invalid/insufficient query
- Loading
- Search failure
- Expired/unavailable result
- Restricted result information

Search context should be preserved when navigating into a listing and returning.

# 9. Listing Detail UX

**Related flow:** UF-011 View Listing.

The listing detail view is the primary information surface for a marketplace listing.

It should organize information into clear sections such as:

1. Media
2. Title and primary summary
3. Price
4. Location
5. Description
6. Category-specific attributes
7. Facilities/features
8. Availability/condition
9. Poster/seller information
10. Verification indicators
11. Contact actions
12. Save/share actions
13. Report action
14. Listing metadata where useful

## 9.1 Media

Media behavior should support:

- Primary image
- Multiple images
- Ordered gallery
- Full-screen or expanded viewing where supported
- Loading state
- Failed media state
- Appropriate alternative text/accessibility behavior

## 9.2 Location

The interface should distinguish:

- Public approximate location
- Structured administrative location
- Locality/Tole
- Chowk/Landmark
- Exact/restricted location

Exact location must not be displayed merely because a listing is publicly discoverable.

## 9.3 Restricted Information

When information is restricted, the UI should clearly communicate:

- What information is restricted
- Why access is restricted at a product level
- What action may provide access, if an approved entitlement exists

The interface must not reveal the protected value in hidden HTML, accessible labels, previews, metadata, or other client-visible mechanisms when the viewer is not authorized.

# 10. Create Listing UX

**Related flow:** UF-004 Create Listing.

Create Listing should be a structured multi-step experience rather than an uncontrolled single long form.

Recommended conceptual sequence:

**Category → Basic Details → Category Attributes → Location → Media → Contact/Visibility → Preview → Submit**

## 10.1 Category Selection

The user selects the category before category-specific fields are presented.

The interface should:

- Show category hierarchy
- Explain the selected category
- Load relevant fields
- Allow correction before submission
- Warn when changing category may remove or invalidate category-specific data

## 10.2 Basic Details

Common fields include:

- Title
- Description
- Listing type
- Price where applicable
- Availability where applicable

Required fields must be clearly identified.

## 10.3 Category Attributes

Only relevant attributes should be presented.

Examples:

**Property**

- Property type
- Bedrooms
- Bathrooms
- Floor
- Furnishing
- Area
- Facilities

**Vehicle**

- Brand
- Model
- Year
- Mileage
- Fuel type
- Transmission
- Condition

**Mobile / Electronics**

- Brand
- Model
- Storage
- Condition
- Warranty
- Accessories

The category model should remain extensible without redesigning the common listing flow.

## 10.4 Location Entry

The listing form should support:

**Country → Province → District → Municipality → Ward → Locality/Tole → Chowk/Landmark → GPS**

Postal code should be represented separately from locality/tole/chowk.

The UI should allow the poster to provide only the location detail appropriate for public display and the approved privacy model.

## 10.5 Media Upload

The media step should support:

- Multiple images
- Primary image selection
- Ordering
- Replacement
- Removal
- Upload progress
- Validation feedback
- Retry after failure

Future video/document support should be added only when approved.

## 10.6 Contact and Visibility

The poster should understand what contact information and location information will be visible to different viewers.

The UI should distinguish:

- Public information
- Restricted information
- Private/internal information

Visibility controls must correspond to actual server-side authorization rules.

## 10.7 Draft and Recovery

Users should be able to save an incomplete listing as a draft where supported.

The interface should communicate:

- Draft saved
- Unsaved changes
- Save failure
- Resume later
- Cancellation consequences

# 11. Listing Preview and Submission

Before submission, the user should be able to review the listing as a viewer would see it.

Preview should expose:

- Title
- Description
- Price
- Media
- Location representation
- Attributes
- Facilities
- Contact presentation
- Visibility/restriction indicators

The submit action should clearly distinguish:

- Save Draft
- Submit / Publish
- Cancel

Validation errors should be associated with the relevant field or section.

# 12. My Listings

The My Listings area should allow a poster to manage listings under their permitted scope.

Each listing should expose relevant:

- Status
- Title
- Primary image
- Price
- Last updated time
- Key location
- Management actions

Actions may include:

- View
- Edit
- Pause
- Resume
- Submit
- Archive
- Delete
- Duplicate where later approved

Actions should depend on listing state and user permission.

# 13. Listing Lifecycle UX

The baseline lifecycle from the user-flow specification is:

**Draft → Review/Validation → Published → Paused → Expired/Archived**

The UI should make the current state visible and avoid offering actions that are invalid for that state.

Examples:

| State | Typical Available Actions |
| --- | --- |
| Draft | Edit, Submit, Delete |
| Review/Validation | View status, Edit/Return where allowed |
| Published | View, Edit, Pause, Contact/Share |
| Paused | View, Edit, Resume, Archive |
| Expired | View, Renew/Resume where approved, Archive |
| Archived | View, Restore/Renew where approved |
| Deleted | No normal user management action |

Exact transitions are governed by **08. Product & Business Rules**.

# 14. Edit Listing UX

Edit behavior should reuse the create-listing structure where practical.

The user should be able to:

- Edit common fields
- Edit category-specific fields
- Replace/remove media
- Update location
- Update contact/visibility settings where permitted
- Review changes
- Save changes

The interface should communicate whether an edit:

- takes effect immediately;
- requires re-validation;
- requires moderation;
- changes the listing state.

# 15. Favorites / Saved Listings

Registered users should be able to:

- Save a listing
- Remove a saved listing
- View saved listings
- Open the original listing
- Handle listings that are unavailable, expired, or deleted

The saved state should be visually clear and accessible.

# 16. Contact Poster UX

**Related flow:** UF-013 Contact Poster.

Contact actions should be presented only when the user and listing are eligible.

The interface should:

1. Explain the available contact method.
2. Check applicable permissions/entitlements.
3. Present the permitted action.
4. Confirm or open the communication context.
5. Preserve relevant listing context.

If direct contact information is restricted, the interface should not reveal it simply because a contact button exists.

Safety mechanisms such as report/block should remain available where applicable.

# 17. Reporting UX

**Related flows:** UF-014 Report Listing, UF-015 Report User.

The report interface should be concise and structured.

It should include:

- Report target
- Reason category
- Optional supporting information/evidence
- Submit action
- Cancellation
- Confirmation

Possible reasons include:

- Spam
- Fraud/scam
- Incorrect information
- Duplicate listing
- Prohibited content
- Inappropriate content
- Safety concern
- Other approved category

After submission, the user should receive a clear confirmation without exposing internal moderation information.

# 18. Profile UX

The profile area should expose only information intended for the user or public profile.

Possible areas:

- Display name
- Profile photo
- Contact verification state
- User type
- Business information where applicable
- Verification state
- Active listings
- Account status
- Account settings

Private account/security information should remain separated from public profile information.

# 19. Authentication and Access UX

Authentication-related interfaces should support the approved authentication architecture without coupling the product UX to a particular provider.

Core states include:

- Registration
- Sign in
- Verification
- Recovery
- Session expiration
- Unauthorized access
- Restricted action
- Account disabled/restricted

When authentication is required during a flow, the system should preserve safe user context and return the user to the intended action after successful authentication where practical.

# 20. Permission and Entitlement UX

The conceptual sequence is:

**Authentication → Authorization → Resource Scope → Action Permission → Information Visibility**

The UI should distinguish:

- Not signed in
- Signed in but not authorized
- Authorized
- Entitled
- Not entitled
- Resource unavailable
- Resource restricted

The UI is not the security boundary. Server-side authorization remains authoritative.

For paid/restricted features, the UI should explain the access requirement without implying that payment automatically grants access to information that remains restricted by seller consent, privacy rules, safety policy, or other business rules.

# 21. Subscription and Entitlement UX

Where subscription functionality is enabled, the interface may include:

- Available plans
- Plan comparison
- Current plan
- Entitlements
- Activation state
- Expiration/renewal information
- Restricted-feature explanation
- Upgrade/access path

The UI should describe entitlements in user-understandable terms.

The exact commercial rules belong in **08. Product & Business Rules** and later payment documentation.

# 22. Nepal Location UX

Location is a major part of the KHOJ BHET experience.

The interface should support:

**Administrative location**

- Province
- District
- Municipality
- Ward
- Postal code

**Local/geographical naming**

- Locality
- Tole
- Chowk
- Bazaar/Market
- Landmark/POI

**Coordinates**

- Latitude
- Longitude

Users should be able to search and select meaningful local names rather than relying exclusively on coordinates.

Examples of local naming patterns include chowks within a municipality/ward such as Ramanand Chowk, Ram Janki Chowk, Pidari Chowk, Bhanu Chowk, and Kadam Chowk.

The UI should distinguish a named place from an administrative unit.

# 23. Privacy and Location Visibility UX

The product should support at least these conceptual visibility levels:

| Information | Public | Restricted | Private/Internal |
| --- | --- | --- | --- |
| Province/District | Yes where appropriate | — | — |
| Municipality/Ward | Yes where appropriate | Possible | — |
| Locality/Tole | Yes where appropriate | Possible | Possible |
| Chowk/Landmark | Yes where appropriate | Possible | Possible |
| Exact GPS | Only if explicitly permitted | Possible | Possible |
| Seller phone/contact | Only if approved | Possible | Possible |

These are UX visibility concepts, not final authorization rules. The exact rules must be defined in the business-rule document.

# 24. Loading, Empty, Error and Unavailable States

Every important screen should define at least:

- Initial loading
- Refresh/loading
- Empty state
- Validation error
- Network/service error
- Permission restriction
- Authentication requirement
- Unavailable/expired resource
- Successful completion

## 24.1 Loading

Loading indicators should communicate that work is in progress without blocking unrelated navigation unnecessarily.

## 24.2 Empty

Empty states should explain why there is no content and provide a useful next action where possible.

Examples:

- No search results → modify search/filter
- No saved listings → browse listings
- No own listings → create listing
- No notifications → continue using the marketplace

## 24.3 Error

Errors should:

- explain the problem;
- avoid exposing internal system details;
- preserve user input when safe;
- provide recovery or retry where possible.

# 25. Forms and Validation

Forms should use consistent behavior for:

- Labels
- Required fields
- Help text
- Validation
- Error messages
- Input formatting
- Character limits
- Upload validation
- Unsaved changes

Validation should occur at appropriate points rather than waiting until the final submission for every error.

Errors should be actionable and associated with the affected field.

# 26. Accessibility

Core journeys should support applicable accessibility requirements.

Minimum UX considerations include:

- Keyboard accessibility where applicable
- Logical focus order
- Visible focus state
- Accessible labels
- Semantic controls
- Text alternatives for meaningful images
- Sufficient contrast
- Error identification
- Non-color-only status communication
- Adequate touch targets
- Screen-reader-compatible interaction
- Responsive text/layout behavior

Accessibility should be validated during implementation and testing rather than assumed from visual design alone.

# 27. Responsive Behavior

The product should support appropriate behavior across:

- Mobile phones
- Tablets
- Desktop browsers

Responsive design should prioritize:

- Search
- Listing browsing
- Listing detail
- Listing creation
- Media upload
- Forms
- Contact/report actions

The same product rules should apply across devices even when layout and navigation differ.

# 28. Design System Boundary

This document defines behavior and information hierarchy.

A later design-system specification should define:

- Color tokens
- Typography
- Spacing
- Icons
- Buttons
- Inputs
- Cards
- Navigation components
- Modals/dialogs
- Toasts/alerts
- Status indicators
- Responsive breakpoints
- Component variants

The design system should implement the UX behavior defined here rather than independently redefining product rules.

# 29. CRUD Representation

The core listing CRUD model is:

**User → Create Listing → Listing**  

**User → Read Listing → Listing**  

**User → Update Listing → Listing**  

**User → Delete/Remove Listing → Listing**

CRUD should not be treated as the complete product flow.

For KHOJ BHET, listing management also includes:

- Draft
- Preview
- Submit
- Validate
- Publish
- Pause
- Resume
- Expire
- Archive
- Report
- Moderate

The connected Figma/FigJam CRUD overview provides a visual reference for the basic CRUD relationship. Detailed lifecycle and permission behavior remain defined by the product documents.

# 30. Traceability

UX/UI elements should maintain traceability through the product lifecycle.

Recommended chain:

**Requirement → User Story → Use Case → User Flow → UX/UI → Business Rule → Technical Specification → Implementation → Test**

Examples:

**KB-FR-xxx → UC-004 Create Listing → UF-004 → UX-006/007/008/009/010 → BR-LIST-xxx → API/DB → TEST**

**KB-FR-xxx → Search → UF-009/010 → UX-002/003/004 → Search Rules → API/Search Layer → TEST**

**KB-FR-xxx → View Listing → UF-011 → UX-005 → Visibility Rules → API/Authorization → TEST**

Exact requirement IDs and business-rule IDs should be inserted as those documents are finalized.

# 31. UX Review Checklist

A screen or flow should not be considered ready until:

- User goal is clear.
- Primary actor is known.
- Related flow is identified.
- Entry point is defined.
- Primary action is clear.
- Required information is identified.
- Permissions are considered.
- Sensitive information visibility is defined.
- Validation behavior is defined.
- Loading state is defined.
- Empty state is defined.
- Error state is defined.
- Cancellation/recovery behavior is defined.
- Success state is defined.
- Mobile behavior is defined.
- Accessibility considerations are addressed.
- Related business rules are identified.
- Traceability is established.

# 32. Relationship to Other Documents

| Document | Relationship |
| --- | --- |
| 03. Requirements Specification | Defines what the product must provide |
| 04. Users, Roles & Permissions | Defines actors and authorization concepts |
| 05. User Stories & Use Cases | Defines user goals and scenarios |
| 06. User Flows | Defines interaction/process paths |
| 07. UX/UI Specification | Defines interface behavior and information presentation |
| 08. Product & Business Rules | Defines governing product rules |
| 09. Software Architecture | Defines system-level technical structure |
| 13. Database Architecture | Defines persistent data structure |
| 14. API Specification | Defines system interfaces |
| Figma | Defines detailed visual design and components |
| Whimsical | Provides visual representations of flows and system concepts |

# 33. Whimsical / Figma Relationship

The authoritative written definitions remain in Notion.

**Whimsical** should be used for:

- User-flow diagrams
- Lifecycle diagrams
- Permission/visibility flows
- Location flows
- System/process diagrams

**Figma** should be used for:

- Screen designs
- Interaction prototypes
- Component designs
- Responsive layouts
- Visual design system
- Design-to-code reference

Neither visual tool should silently change an approved requirement or business rule.

# 34. Open Decisions

The following remain intentionally open until the relevant product/technical decisions are approved:

- Final mobile application framework and implementation-specific UX constraints, if not already fixed by the accepted technical baseline
- Final storage strategy and any remaining user-visible upload/storage behavior
- Final payment providers
- Final subscription/entitlement commercial rules, including whether paid entitlements belong in the Marketplace MVP or a later monetization stage
- Final category-specific field catalogue and any unresolved attribute UX
- Final visual design system

The authentication provider is governed by the accepted Firebase marketplace-authentication decision; the V1 search strategy is MySQL-first; and contact-information/exact-location visibility is defined in 08. Product & Business Rules. These are not open UX decisions unless a formal change is proposed. Remaining open decisions should be recorded in the appropriate ADR or product/business-rule document rather than being prematurely fixed in UX/UI.

# 35. Document Status

**Status:** Active  

**Version:** 1.0  

**Purpose:** Baseline UX/UI behavior specification for KHOJ BHET.

This document should evolve when approved requirements, user flows, business rules, or major UX decisions change.

# 36. Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-PROD-007 |
| Document | 07. UX/UI Specification |
| Status | Active |
| Version | 1.0 |
| Owner | KHOJ BHET Product |
| Last Reviewed | 2026-09-23 |
| Parent | 01. PRODUCT DEFINITION |
| Previous | 06. User Flows |
| Next | 08. Product & Business Rules |
| Related | 03. Requirements Specification, 04. Users, Roles & Permissions, 05. User Stories & Use Cases, 06. User Flows, 08. Product & Business Rules |

## Approved V1 UX Decision — Free Contact and Protected Information (2026-10-18)

Paid plans, subscription purchase, and paid entitlement states are not part of the Marketplace MVP. Do not show paywalls, purchase/renewal prompts, payment submission screens, or paid-plan CTAs as live V1 functionality. Subscription screens may exist only as explicitly marked future-phase designs and must not appear in the MVP navigation or acceptance scope.

Visitors may browse public listings. When a visitor selects an in-app contact action, show a sign-in/register prompt and preserve the intended listing context after successful authentication. Authenticated users may start an in-app conversation only when the API says contact is allowed. V1 screens must not reveal protected phone/email or exact residential location. Explain unavailable contact actions without exposing the protected value or leaking whether a hidden value exists. The seller's in-app-contact setting and safety/blocking restrictions remain effective.

These rules supersede any screen inventory or entitlement-state example that implies paid contact/location access is an active V1 feature.