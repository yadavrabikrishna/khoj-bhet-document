# 12. Engineering Standards

**Document ID:** KB-TECH-012  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Engineering  

**Last Reviewed:** 2026-09-24  

**Parent:** 02. TECHNICAL DEFINITION  

**Previous:** 11. Development Methodology  

**Next:** 13. Database Architecture

---

## 1. Purpose

This document defines the engineering standards developers should follow when designing, implementing, reviewing, testing, and maintaining KHOJ BHET.

It defines **how engineering work should be implemented**. It does not replace the Software Architecture, Technology Stack, Database Architecture, API Specification, Security Architecture, SEO Architecture, or approved ADRs.

Where a specific technical document or approved ADR conflicts with a generic standard here, the specific approved decision takes precedence.

## 2. Engineering Principles

1. Correctness before convenience
2. Simple solutions before unnecessary complexity
3. Explicit boundaries between domains
4. Stable and documented API contracts
5. Security and privacy as implementation requirements
6. Validate input at system boundaries
7. Never trust client-side authorization or entitlement claims
8. Prefer readable code over clever code
9. Automate repetitive and error-prone work
10. Make important behavior testable
11. Avoid premature optimization
12. Document important decisions
13. Design for observability and recovery
14. Keep external providers replaceable
15. Preserve backward compatibility where practical

## 3. Naming Conventions

### 3.1 General

Names must be descriptive, consistent, unambiguous, searchable, and domain-oriented. Avoid unexplained abbreviations.

### 3.2 Database

Use snake_case, a consistent table naming convention, descriptive names, and explicit foreign-key names such as user_id, listing_id, and category_id.

Examples:

- users
- listings
- media
- outbox_events

These are illustrative entity names, not a substitute for the current Document 13 physical table registry. Do not introduce table names such as listing_images unless they exist in the authoritative schema.

Primary keys and foreign keys must follow a project-wide convention.

### 3.3 API

Use resource-oriented nouns and predictable HTTP semantics.

Examples:

- GET /api/v1/listings
- GET /api/v1/listings/{id}
- POST /api/v1/listings
- PATCH /api/v1/listings/{id}
- DELETE /api/v1/listings/{id}

The API Specification is authoritative for exact endpoint naming.

### 3.4 Frontend

Use PascalCase for React components, camelCase for variables/functions, and use hook names beginning with use.

Examples:

- ListingCard
- SearchFilters
- useListing
- useSearchResults

## 4. Code Organization

Organize code by responsibility and domain.

Recommended conceptual layers:

Domain → business concepts and rules

Application → use cases and orchestration

Contracts → DTOs, request/response contracts, interfaces

Infrastructure → external services and framework-specific integrations

Persistence → database access and repositories where appropriate

Presentation → HTTP controllers, API resources, frontend screens/components

Dependencies should point toward stable abstractions rather than forcing business logic to depend directly on infrastructure.

## 5. Laravel / PHP Standards

Laravel is the current backend framework.

Standards:

- Follow PSR-12-compatible PHP style.
- Use strict typing where practical.
- Keep controllers thin.
- Keep business rules out of controllers.
- Use Form Requests or equivalent validation mechanisms.
- Use Policies/Gates for authorization.
- Use API Resources or explicit transformers for response formatting.
- Use Services/Actions for substantial application operations.
- Avoid uncontrolled N+1 queries.
- Use database transactions for operations requiring atomicity.
- Use queues for work that does not need to block HTTP requests.
- Keep configuration in configuration/environment mechanisms.
- Never place secrets in source code.

Laravel-specific implementation details must not leak into API contracts.

## 6. Future Node.js / Express.js Compatibility

Node.js + Express.js is a future candidate documented in **10. Technology Stack**. Current implementation remains Laravel.

Avoid unnecessary coupling between REST contracts, business rules, persistence implementation, and framework-specific controller behavior.

The objective is a clean migration boundary, not premature implementation of Node.js conventions.

A future Node.js implementation must satisfy approved API contracts and business requirements unless an ADR explicitly changes them.

## 7. React / Next.js Standards

Next.js + React is the current web frontend.

Standards:

- Prefer TypeScript.
- Use reusable components for repeated behavior.
- Keep components focused on one clear responsibility.
- Separate presentation from data-fetching/business orchestration where practical.
- Use server rendering where it provides SEO or performance value.
- Use client components only when browser interactivity requires them.
- Avoid unnecessary client-side JavaScript.
- Keep public listing pages indexable.
- Use semantic HTML.
- Provide accessible labels, focus states, and keyboard interaction.
- Never expose private listing information in public HTML or client bundles.

### Rendering

Use SSR where request-time data is required, ISR where cached/generated content can safely be reused, and static generation where appropriate.

Rendering strategy must be selected per page/use case.

## 8. React Native / Expo Standards

React Native + Expo is the planned mobile application stack.

- Reuse domain/API contracts with web where practical.
- Do not duplicate backend business rules inside mobile clients.
- Treat the API as the source of business truth.
- Handle offline/network failure explicitly.
- Protect locally stored sensitive information.
- Use platform-appropriate permissions.
- Keep navigation and screen responsibilities clear.
- Avoid unnecessary native dependencies.
- Test on representative Android and iOS environments before release.

## 9. TypeScript Standards

Where TypeScript is used:

- Prefer explicit domain types.
- Avoid any unless there is a documented reason.
- Model nullable/optional values explicitly.
- Validate external data at runtime where type safety alone is insufficient.
- Do not treat TypeScript types as a substitute for backend validation.
- Keep API response types aligned with the API Specification.
- Prefer discriminated unions for well-defined state variants where appropriate.

## 10. API / REST Standards

The REST API is the principal integration contract between clients and backend services.

Requirements:

- Version public APIs where compatibility requires it.
- Use appropriate HTTP methods and status codes.
- Validate incoming data.
- Authorize every protected operation.
- Return predictable response structures.
- Return machine-readable error information.
- Never expose internal stack traces or secrets.
- Use pagination for potentially large collections.
- Define filtering, sorting, and search parameters explicitly.
- Document authentication requirements.
- Document entitlement/privacy behavior for protected listing fields.

### Backward Compatibility

Breaking API changes require impact analysis, a migration/deprecation plan, documentation updates, tests, and an ADR when architecturally significant.

## 11. Axios Client Standards

Axios is the selected HTTP client.

Use a centralized API client layer for:

- base URL configuration
- authentication headers
- request/response handling
- timeout configuration
- error normalization
- retry behavior where appropriate

Do not scatter raw Axios configuration throughout components.

Do not automatically retry unsafe operations such as payments or listing creation without an explicit idempotency strategy.

## 12. MySQL Standards

MySQL is the system of record.

- Use migrations for schema changes.
- Use foreign keys where appropriate.
- Define indexes based on actual query patterns.
- Avoid unnecessary duplicated derived data.
- Use transactions for atomic business operations.
- Avoid unbounded queries.
- Use pagination for large datasets.
- Review query plans for performance-critical queries.
- Avoid N+1 access patterns.
- Use appropriate data types and constraints.
- Preserve important audit information.

MongoDB is a future candidate, not a current database requirement. Current MySQL design must be based on actual KHOJ BHET requirements rather than a hypothetical MongoDB migration.

## 13. Firebase / Firestore Standards

Firebase/Firestore is a secondary capability.

Use it only for approved use cases such as realtime capabilities and Firebase Authentication integration.

Rules:

- Do not create conflicting sources of truth without explicit design.
- Define ownership for synchronized data.
- Handle delayed or failed synchronization.
- Do not assume Firestore writes are automatically reflected in MySQL.
- Review Firestore security rules independently from backend authorization.

## 14. Redis, Cache and Queue Standards

Redis is disposable infrastructure.

### Cache

- Cache only data that can safely be reconstructed.
- Define TTLs intentionally.
- Invalidate or refresh cache when required by consistency.
- Never rely on cache as authoritative business data.

### Queue

Use queues for media processing, notifications, search indexing, non-critical integrations, and other long-running work.

Jobs must be retry-safe, observable, appropriately time-limited, and idempotent where practical.

Failed jobs must not silently disappear.

## 15. Search Standards — MySQL-first V1

MySQL is the V1 search engine and authoritative data source, consistent with Documents 10, 13, 14, 21 and ADR-004/ADR-008. Do not add Meilisearch or another dedicated search service as a V1 dependency.

- Search behavior and query parameters must match Document 14 and Document 21.
- Search results must apply listing lifecycle, expiry-at-read-time, visibility, and entitlement rules.
- Private fields must never enter publicly searchable documents or projections.
- Query plans, indexes, full-text behavior (including Nepali/Devanagari queries), and latency must be tested against the pinned MySQL version.
- Any future dedicated search engine is a derived, rebuildable projection and requires a measured need, approved ADR, privacy/visibility parity tests, and a documented full-rebuild process.

## 16. Validation and Error Handling

### Validation

Validate request payloads, query parameters, uploaded files, identifiers, ownership/resource access, payment callbacks, and external provider responses.

Server-side validation is mandatory even when the frontend performs the same checks.

### Errors

Errors should be predictable, actionable, safe, and logged at the appropriate level.

Never expose passwords, tokens, payment secrets, private contact information, or internal stack traces.

## 17. Authentication, Authorization and Entitlement

These are separate concerns.

- **Authentication:** determines who the user is.
- **Authorization:** determines what the user is allowed to do.
- **Ownership / Resource Scope:** determines whether the user may operate on a specific resource.
- **Entitlement:** determines whether the user has access to a capability.
- **Visibility / Privacy:** determines what information may be shown to a particular viewer.

Client-side checks are for user experience only. Backend enforcement is authoritative.

## 18. Security Standards

Minimum standards:

- HTTPS for production traffic.
- Secure authentication flows.
- Strong session/token handling.
- Server-side authorization.
- Input validation.
- Output encoding where required.
- CSRF protection where applicable.
- Rate limiting for abuse-sensitive endpoints.
- Secure file-upload validation.
- Secret management through environment/secret mechanisms.
- Dependency updates and vulnerability review.
- Audit logging for security-sensitive administrative actions.

Detailed security requirements belong to **19. Security Architecture**.

## 19. Media and File Standards

Uploaded media is untrusted input.

- Validate file type using content as well as extension where practical.
- Enforce size limits.
- Generate safe filenames.
- Never trust user-provided paths.
- Handle metadata according to privacy requirements.
- Process images/videos asynchronously where appropriate.
- Store only approved formats.
- Generate required variants/thumbnails through controlled processing.
- Prevent executable content from being uploaded as media.
- Apply authorization checks before private media access.

## 20. Logging and Observability

Production telemetry must be sufficient to diagnose failures without exposing sensitive information.

Log important events such as authentication failures, authorization failures, critical application errors, payment events, moderation actions, background-job failures, external-provider failures, and significant state transitions.

Use correlation identifiers where available.

Never log passwords, authentication secrets, private payment credentials, or unnecessary personal data.

## 21. Testing Standards

Testing should exist at multiple levels:

### Unit Tests

For isolated business logic and important rules.

### Feature / Integration Tests

For API behavior, persistence interactions, authorization, and integration boundaries.

### End-to-End Tests

For critical user journeys.

### Contract Tests

For important API contracts and external integrations where justified.

Critical behavior should cover authentication, authorization, listing lifecycle, ownership, visibility/privacy, search, favorites, contact access, reports/moderation, subscriptions/entitlements, payments, and important administrative actions.

Coverage percentage alone is not a quality metric; critical-path behavior matters more than an arbitrary target.

## 22. Git Standards

Use version control for all application and infrastructure code.

### Branches

Use clear names such as:

- feature/...
- fix/...
- refactor/...
- docs/...
- chore/...

### Commits

Commits should describe one logical change where practical, use clear action-oriented messages, avoid unrelated changes, and never contain secrets.

### Pull Requests

PRs should describe purpose, implementation summary, affected areas, tests performed, database/API changes, migration/deployment requirements, and screenshots for relevant UI changes.

## 23. Code Review Standards

Reviewers should check:

**Correctness:** requirements and edge cases.

**Architecture:** module/layer boundaries and responsibility placement.

**Security:** server-side authorization and sensitive-data exposure.

**Data:** transactions, constraints, indexes, and migrations.

**API:** predictable and backward-compatible contracts.

**Performance:** N+1 queries, unnecessary network calls, excessive client-side work.

**Maintainability:** readability and testability.

**Testing:** coverage of critical behavior.

## 24. Environment and Configuration Standards

Maintain separate environments for local development, testing/staging, and production.

Rules:

- Never commit production secrets.
- Keep environment-specific configuration outside source code.
- Use consistent environment-variable naming.
- Document required variables.
- Fail safely when required configuration is missing.
- Never reuse production credentials in development.

## 25. Performance Standards

Performance must be measured rather than assumed.

Consider:

- database query efficiency
- API response time
- caching
- background processing
- image optimization
- JavaScript bundle size
- rendering strategy
- mobile network conditions
- search latency

Web performance must include Core Web Vitals and real-user behavior where measurable.

Optimize measured bottlenecks rather than hypothetical ones.

## 26. Accessibility Standards

Web and mobile interfaces should:

- use semantic controls
- support keyboard navigation where applicable
- provide accessible names/labels
- maintain usable focus behavior
- provide sufficient contrast
- support screen readers where applicable
- avoid communicating important information by color alone
- provide meaningful error messages

Accessibility should be considered during UX/UI design, not only final testing.

## 27. SEO Engineering Standards

Public marketplace content must be implemented with search-engine accessibility in mind.

Requirements:

- server-rendered/indexable public listing content where appropriate
- canonical URLs
- correct metadata
- structured data where applicable
- clean URL structure
- appropriate robots directives
- sitemap integration
- controlled pagination/indexation
- internal linking
- fast page delivery
- no accidental indexing of private/user-only content

Detailed requirements belong to **23. SEO Architecture**.

## 28. Documentation Standards

Technical changes must keep documentation synchronized.

Update documentation when a change affects architecture, technology choice, API contracts, database structure, security model, search behavior, media processing, authentication, or business-critical engineering rules.

Use ADRs for significant architectural decisions.

Documentation hierarchy:

- **Notion:** authoritative written documentation
- **Whimsical:** system/process diagrams
- **Figma:** UX/UI and visual design
- **Code:** executable implementation

These artifacts must not contradict one another.

## 29. ADR Standards

An ADR is required when a decision:

- changes architecture
- introduces/removes significant technology
- changes major integration strategy
- creates an important data ownership boundary
- introduces a significant security/privacy approach
- changes major API compatibility strategy
- creates a difficult-to-reverse technical commitment

The ADR register is the index. Individual ADRs remain separate documents.

## 30. Deprecation and Compatibility

Before removing or changing an established interface:

1. Identify consumers.
2. Document the change.
3. Provide migration guidance where needed.
4. Introduce a deprecation period when practical.
5. Monitor usage.
6. Remove old behavior only after the migration condition is satisfied.

This applies to APIs, database fields, events, search indexes, frontend interfaces, and integrations.

## 31. Quality Gates

A change should not be considered complete until applicable gates pass:

- requirements satisfied
- acceptance criteria satisfied
- code standards satisfied
- security reviewed
- tests pass
- database migrations verified
- API contract verified
- UI reviewed where applicable
- performance considered
- documentation updated
- deployment/rollback considerations addressed

Critical production changes require stronger verification than low-risk documentation changes.

## 32. Engineering Checklist

Before merging:

- [ ]  Requirement understood
- [ ]  Correct module/layer selected
- [ ]  Naming follows standards
- [ ]  Input validated
- [ ]  Authorization enforced
- [ ]  Sensitive data protected
- [ ]  Database access reviewed
- [ ]  API contract reviewed
- [ ]  Error handling implemented
- [ ]  Tests added/updated
- [ ]  Performance impact considered
- [ ]  Logs/observability considered
- [ ]  Documentation updated
- [ ]  ADR created if required
- [ ]  No secrets committed

Before production:

- [ ]  Tests pass
- [ ]  Migration reviewed
- [ ]  Configuration verified
- [ ]  Monitoring/logging verified
- [ ]  Rollback plan understood
- [ ]  Critical user flows verified

## 33. Relationship to Other Technical Documents

| Document | Responsibility |
| --- | --- |
| 09. Software Architecture | Architectural structure and boundaries |
| 10. Technology Stack | Current technologies and future migration strategy |
| 11. Development Methodology | Development process and lifecycle |
| **12. Engineering Standards** | **Implementation and engineering conventions** |
| 13. Database Architecture | Data model and database architecture |
| 14. API Specification | API contracts |
| 15. Frontend Architecture | Web frontend structure |
| 16. Backend Architecture | Backend implementation architecture |
| 17. Mobile Application Architecture | Mobile application structure |
| 18. Authentication & Authorization | Identity/access architecture |
| 19. Security Architecture | Security controls and threat considerations |
| 20. Media & File Storage | Media/file architecture |
| 21. Search Architecture | Search/index architecture |
| 22. Notification System | Notification architecture |
| 23. SEO Architecture | Search-engine optimization architecture |

## 34. Document Status

**Status:** Active

This document is the baseline engineering standard for KHOJ BHET. Specific accepted ADRs and the current approved API/database contracts take precedence over generic examples in this document.

Standards may evolve as the project gains implementation experience. Significant changes should be reviewed and recorded through the appropriate documentation and ADR process.