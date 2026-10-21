# 11. Development Methodology

**Document ID:** KB-TECH-011  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Engineering  

**Last Reviewed:** 2026-09-24  

**Parent:** 02. TECHNICAL DEFINITION  

**Previous:** 10. Technology Stack  

**Next:** 12. Engineering Standards

---

# 1. Purpose

This document defines how Khoj Bhet will be planned, designed, developed, tested, reviewed, released, and maintained.

It establishes the engineering workflow that connects product requirements to production software.

This document defines **how the team works**. It does not replace product requirements, business rules, architecture, technology stack, API specification, database architecture, UX/UI specification, or engineering standards.

# 2. Methodology Summary

Khoj Bhet will use an **iterative, incremental, Agile-oriented SDLC** with short development cycles and continuous validation.

The project will not attempt to build the entire marketplace at once. Development will proceed through:

**Requirement → Specification → Design → Technical Design → Implementation → Testing → Review → Release → Monitoring → Feedback → Iteration**

The methodology supports the current modular-monolith architecture while keeping API contracts and domain boundaries suitable for future evolution, including a possible Node.js + Express.js backend and/or MongoDB if future requirements justify such a change.

# 3. Core Development Principles

1. **Specification before implementation** — important behavior should be documented before coding.
2. **Small increments** — implement bounded features rather than large uncontrolled batches.
3. **Domain-first design** — business rules remain independent from UI frameworks and infrastructure.
4. **API-first integration** — web and mobile clients consume stable API contracts.
5. **Server-side authority** — security, ownership, entitlement, validation, and business rules are enforced by the backend.
6. **Testable behavior** — important business behavior must have automated tests.
7. **Review before merge** — production-bound code requires review.
8. **Migration-friendly design** — avoid unnecessary coupling to Laravel, MySQL, or any single infrastructure provider.
9. **Observable production systems** — failures and important business events must be diagnosable.
10. **Document important decisions** — architectural decisions belong in the ADR system.
11. **Security by default** — authentication, authorization, privacy, validation, and audit requirements are considered during design.
12. **Reversible decisions where practical** — prefer decisions that can be changed without major rework when requirements are uncertain.

# 4. Development Lifecycle

**Idea → Requirement → User Story → Acceptance Criteria → Use Case → User Flow → UX/UI → Business Rules → Architecture/API/Data Design → Implementation → Automated Tests → Code Review → QA → Release → Monitoring → Feedback**

A feature should not move directly from an idea to production code without passing through the appropriate specification and validation stages.

# 5. Work Breakdown Hierarchy

| Level | Purpose |
| --- | --- |
| Product Goal | Defines the business/product outcome |
| Epic | Groups a major product capability |
| Feature | Defines a meaningful user-facing capability |
| User Story | Defines a user need |
| Acceptance Criteria | Defines conditions for completion |
| Use Case | Defines actor/system interaction |
| User Flow | Defines the interaction sequence |
| UX/UI Specification | Defines interface behavior and presentation |
| Business Rule | Defines domain constraints |
| Technical Specification | Defines implementation behavior |
| Task | Defines an executable engineering unit |
| Test Case | Verifies expected behavior |
| Release | Delivers completed functionality |

# 6. Requirement Definition

Every significant feature should identify:

- Problem being solved
- Target actor/user
- Business objective
- Functional requirements
- Non-functional requirements
- Business rules
- Dependencies
- Security/privacy implications
- Data requirements
- API requirements
- UX/UI requirements
- Acceptance criteria
- Open questions
- Related ADRs

Requirements should be sufficiently clear that another developer can understand the intended behavior without relying only on conversation history.

# 7. User Story Standard

User stories should normally follow:

**As a [user/actor], I want [capability], so that [outcome].**

Each story should have Story ID, Title, Actor, Description, Preconditions, Main scenario, Alternative scenarios, Error scenarios, Acceptance criteria, Related use cases, Related user flows, and Dependencies.

# 8. Acceptance Criteria

Acceptance criteria define observable completion conditions.

Preferred format:

**Given [context]**  

**When [action]**  

**Then [expected result]**

Acceptance criteria should cover normal behavior, validation failures, authorization failures, ownership restrictions, entitlement restrictions, empty states, duplicate submissions, external-service failures where relevant, boundary conditions, and privacy/visibility rules.

A feature is not considered complete merely because its primary screen works.

# 9. Use Case and User Flow Process

Use cases describe system behavior from an actor perspective. User flows describe the sequence of interaction.

Recommended order:

**Requirement → User Story → Use Case → User Flow → UX/UI**

Whimsical is used for visual flows and process diagrams. Notion remains the authoritative written specification.

# 10. UX/UI Development Process

UX/UI work should begin after user behavior and business rules are sufficiently understood.

1. Identify user goal.
2. Define states and scenarios.
3. Define user flow.
4. Create low-fidelity structure.
5. Define information hierarchy.
6. Create high-fidelity UI.
7. Define responsive behavior.
8. Define interaction states.
9. Define validation, loading, empty, and error states.
10. Review against requirements.
11. Hand off implementation specifications.

Figma is the primary design workspace for UI specifications and reusable components.

# 11. Technical Design Before Coding

Before implementing a significant feature, identify backend module/domain, API operations, request/response contracts, authorization, entitlement, database changes, transactions, background jobs, events, notifications, media handling, search indexing, caching, logging/auditing, external integrations, and failure/retry behavior.

Small changes may use lightweight technical design. High-risk or cross-domain changes require explicit technical design and, where appropriate, an ADR.

# 12. API-First Development

Web and mobile applications should depend on documented API contracts rather than directly depending on backend implementation details.

**Current:** Next.js / React + React Native / Expo → Axios → REST API → Laravel → MySQL

**Future option:** Next.js / React + React Native / Expo → Axios → REST API → Node.js + Express.js → database layer

The API contract should remain as independent as practical from the backend framework. This allows future backend evolution without requiring complete client rewrites.

# 13. Implementation Workflow

1. Read the linked specification.
2. Confirm acceptance criteria.
3. Identify affected modules.
4. Confirm API/data implications.
5. Implement the smallest complete change.
6. Add or update automated tests.
7. Run formatting/static analysis.
8. Run relevant test suites.
9. Review security implications.
10. Review performance implications.
11. Update documentation when behavior changes.
12. Submit for code review.

# 14. Branching Strategy

Recommended branches:

- **main** — production-ready code
- **develop** — integration branch if needed during early development
- **feature/*** — feature work
- **fix/*** — bug fixes
- **hotfix/*** — urgent production fixes
- **chore/*** — maintenance/tooling work

Branch names should remain short and descriptive.

# 15. Commit Standards

Commits should be small, focused, atomic where practical, descriptive, and buildable/testable where practical.

Recommended format: **type(scope): description**

Examples: **feat(listings): add listing creation endpoint**, **fix(auth): reject expired verification token**, **test(listings): add ownership validation tests**.

Avoid vague commits such as changes, update, fix stuff, final, or new code.

# 16. Pull Request / Code Review Process

A pull request should include what changed, why it changed, related requirement/story, technical approach, database changes, API changes, security considerations, test coverage, deployment considerations, screenshots for UI changes where useful, and known limitations.

Reviewers should check correctness, architecture/module boundaries, security, data integrity, API consistency, testing, observability, and operational impact.

# 17. Definition of Ready

A feature/task is **Ready for Development** when the requirement is understood, acceptance criteria are defined, relevant use case/user flow is available, UX/UI requirements are sufficiently defined, business rules are identified, dependencies are known, technical approach is understood, required ADRs are identified, and API/data impact is understood sufficiently to begin implementation.

Not every small task requires every artifact, but omissions should be intentional.

# 18. Definition of Done

A feature is **Done** when applicable requirements have been satisfied and:

- Code is implemented.
- Automated tests are added/updated.
- Relevant tests pass.
- Validation and authorization are implemented.
- API documentation is updated.
- Database migrations are reviewed.
- UX/UI behavior matches specification.
- Error/loading/empty states are handled.
- Security implications are addressed.
- Code review is complete.
- Documentation is updated.
- Deployment requirements are known.
- Production monitoring/logging is adequate.
- No known blocking defect remains.

# 19. Testing Strategy

| Test Level | Purpose |
| --- | --- |
| Unit | Verify isolated business logic |
| Integration | Verify module/service/database interactions |
| API | Verify HTTP contracts and authorization |
| Component | Verify UI component behavior |
| End-to-End | Verify critical user journeys |
| Security | Verify access/privacy/security controls |
| Performance | Verify important performance characteristics |
| Regression | Ensure existing functionality remains stable |

Testing effort should be proportional to risk. Authentication, authorization, listing ownership, payments, entitlements, moderation, and sensitive contact/location visibility require stronger coverage.

# 20. Test-Driven and Test-After Development

Khoj Bhet does not require every feature to use strict Test-Driven Development.

Use TDD where it provides clear value, especially for complex domain rules, financial calculations, authorization policies, visibility/entitlement logic, search/filter logic, data transformations, and state transitions.

For other work, tests may be written immediately after implementation provided the acceptance criteria remain the source of expected behavior.

# 21. Database Change Process

**Requirement → Data model change → Migration → Constraints/indexes → Application change → Tests → Migration verification → Deployment**

Schema changes must be version-controlled. Production schema changes should be reversible where practical. Destructive changes require additional review. Large data migrations should be separated from normal schema migrations when appropriate.

MySQL remains the primary source of truth in the current architecture.

# 22. API Change Process

API changes should consider compatibility before implementation.

For breaking changes: identify affected clients, define a migration path, decide whether versioning is required, update documentation, update web/mobile clients, test compatibility, deploy in a controlled sequence, and retire the old contract only after migration.

Avoid breaking API contracts merely to simplify an internal implementation.

# 23. Background Jobs and Asynchronous Work

Long-running or non-critical synchronous operations should be considered for background processing.

Examples include image processing, search indexing, notifications, email/SMS dispatch, geocoding, analytics/event processing, expiration processing, cleanup, import/export, and media transcoding.

Current intended mechanism: **Laravel Queue + Redis**.

Jobs should be designed with idempotency, retry policy, failure handling, logging, appropriate timeout, backoff, and duplicate-execution safety.

# 24. External Service Integration

External services should be isolated behind adapters/providers where practical.

Examples include Firebase Auth, Firestore, payment gateways, maps, geocoding, notification providers, search providers, and cloud storage.

The application domain should not contain widespread provider-specific logic. This supports future replacement without rewriting the entire application.

# 25. Environment Management

Separate environments should be maintained as the project grows:

- Local development
- Testing/CI
- Staging
- Production

Environment-specific values must not be hard-coded. Secrets must not be committed to source control.

# 26. Continuous Integration

CI should automatically perform appropriate checks for every merge/pull request.

Minimum intended checks:

1. Dependency installation
2. Formatting/linting
3. Static analysis where configured
4. Unit tests
5. Integration/API tests
6. Build verification
7. Migration/schema checks where applicable

Later stages may add security scanning, dependency vulnerability scanning, end-to-end tests, performance checks, and container image scanning.

# 27. Continuous Delivery and Deployment

Preferred flow:

**Merge → CI → Build → Deploy to Staging → Smoke Test → Production Approval → Production Deploy → Health Check → Monitor**

For early development, deployment may be simpler. The process should become more automated as production risk increases.

Hostinger is the initial hosting environment, but deployment design should avoid unnecessary provider lock-in.

# 28. Release Strategy

Releases should be incremental.

Release types include feature releases, bug-fix releases, security releases, infrastructure releases, database releases, and emergency hotfixes.

Each release should identify version/release identifier, included changes, database changes, configuration changes, migration requirements, known issues, and rollback considerations.

# 29. Rollback and Recovery

Every production deployment should consider application rollback, database rollback limitations, configuration rollback, queue/job effects, cache invalidation, and external-service side effects.

Database rollback is not always safely reversible. For destructive data changes, backup and recovery strategy must be considered before deployment.

# 30. Bug Management

Suggested severity levels:

- **Critical** — security, data loss, severe outage, or core service unavailable
- **High** — major feature unusable or significant user impact
- **Medium** — important defect with workaround
- **Low** — minor defect or cosmetic issue

Bug reports should contain summary, environment, reproduction steps, expected behavior, actual behavior, evidence/logs, severity, affected feature, regression information, and proposed fix if known.

# 31. Security Development Lifecycle

Security is part of normal development rather than a final-stage activity.

For each significant feature consider authentication, authorization, ownership, entitlement, input validation, output filtering, rate limiting, abuse prevention, privacy, sensitive data handling, audit logging, file upload security, external-service security, and secret management.

Security-sensitive changes require explicit review.

# 32. Privacy-by-Design

Khoj Bhet has potentially sensitive listing information such as exact address, contact information, precise location, seller information, payment information, and uploaded identity/payment evidence where applicable.

A client should receive only the fields permitted by **User role + ownership + entitlement + listing visibility + business rules**.

Never rely on frontend hiding alone.

# 33. Performance Development Process

Performance should be measured rather than assumed.

Important areas include Next.js SSR/ISR response performance, API latency, database query performance, search latency, image delivery, mobile network usage, cache effectiveness, background job throughput, Core Web Vitals, and large listing/gallery responses.

Optimization should be driven by measured bottlenecks.

# 34. Documentation Synchronization

When implementation changes documented behavior, update the relevant specification.

Potentially affected documents include product requirements, user stories, use cases, user flows, UX/UI specification, business rules, ADRs, software architecture, technology stack, database architecture, API specification, security architecture, SEO architecture, and related technical documents.

Documentation should not intentionally drift from production behavior.

# 35. ADR Process

Architectural decisions should use the ADR system.

Create an ADR when a decision affects architecture, has meaningful long-term consequences, changes technology selection, changes data ownership, changes security architecture, changes API strategy, changes deployment architecture, introduces a significant external dependency, or requires choosing between materially different approaches.

Examples relevant to Khoj Bhet include Laravel modular monolith, MySQL as source of truth, Firebase Auth, Firestore secondary usage, REST API, future Node.js/Express.js migration, possible future MongoDB adoption, search provider selection, and payment gateway architecture.

The ADR Register remains an index; detailed decisions should live in separate ADR pages.

# 36. Whimsical / Figma / Notion Responsibilities

| Tool | Primary Responsibility |
| --- | --- |
| Notion | Written requirements, specifications, decisions, technical documentation |
| Whimsical | Processes, user flows, architecture diagrams, conceptual/system diagrams |
| Figma | UX/UI, interaction design, components, design system, visual specifications |
| Git repository | Source code, tests, migrations, configuration, implementation |
| CI/CD system | Automated verification and deployment workflow |

The same artifact should not have conflicting authoritative versions.

# 37. Development Cadence

### Planning

Define the next small set of implementation-ready features.

### Development

Implement features in short increments.

### Review

Perform code review and automated validation continuously.

### QA

Validate acceptance criteria and critical user journeys.

### Release

Deploy completed increments.

### Review

Capture defects, feedback, performance observations, and architectural lessons.

### Documentation

Update specifications and ADRs where decisions changed.

# 38. MVP Development Strategy

The first production version should prioritize a coherent end-to-end marketplace rather than maximum feature count.

A typical vertical slice should be capable of progressing through:

**User Authentication → Browse/Search → View Listing → Create Listing → Manage Listing → Contact/Interaction → Moderation → Notification**

Once the foundational flow is stable, additional capabilities can be added incrementally.

# 39. Future Backend Migration Strategy

The current backend is **Laravel + Filament + MySQL**.

Future technology candidates include **Node.js + Express.js** and potentially **MongoDB**.

These are **future architectural options, not current implementation requirements**.

To preserve migration capability:

- Maintain stable REST API contracts.
- Keep business rules separated from framework-specific controllers.
- Use domain/application service boundaries.
- Isolate persistence behind appropriate interfaces where justified.
- Isolate external providers through adapters.
- Avoid leaking Laravel-specific concepts into client contracts.
- Avoid designing the current database schema solely around a hypothetical MongoDB migration.
- Evaluate future migration using measured requirements.

A future migration should be justified by concrete requirements such as scale, team capability, operational constraints, ecosystem requirements, or domain-specific data characteristics.

# 40. Technology Migration Gate

Before replacing a major technology, evaluate:

1. Problem being solved
2. Current system limitations
3. Measured evidence
4. Migration cost
5. Operational cost
6. Developer capability
7. Security implications
8. Data migration complexity
9. API compatibility
10. Rollback strategy
11. Long-term maintenance
12. Opportunity cost

A technology migration requires an ADR before execution.

# 41. Quality Gates

**Gate 1 — Requirement:** Requirement understood; acceptance criteria defined.

**Gate 2 — Design:** Flow and UX/UI defined; business rules identified.

**Gate 3 — Technical:** API/data/security implications understood.

**Gate 4 — Implementation:** Code complete; tests complete.

**Gate 5 — Review:** Code review passed; documentation updated.

**Gate 6 — QA:** Acceptance criteria verified; critical regressions checked.

**Gate 7 — Release:** Deployment plan ready; monitoring and rollback considered.

# 42. Engineering Metrics

Useful metrics may include deployment frequency, lead time for changes, change failure rate, mean time to recovery, automated test reliability, API error rate, production incident count, defect escape rate, background job failure rate, search latency, database query latency, and Core Web Vitals.

Metrics should be interpreted together with product impact and system context.

# 43. Documentation Traceability

Every major feature should be traceable through:

**Requirement → User Story → Use Case → User Flow → UX/UI → Business Rule → Architecture → API → Database → Implementation → Test → Release**

This traceability is a core SDLC control for Khoj Bhet.

# 44. Development Checklist

### Before implementation

- [ ]  Requirement understood
- [ ]  Acceptance criteria defined
- [ ]  Related use case identified
- [ ]  User flow identified
- [ ]  UX/UI requirements identified
- [ ]  Business rules identified
- [ ]  API impact identified
- [ ]  Database impact identified
- [ ]  Security impact identified
- [ ]  ADR requirement checked

### During implementation

- [ ]  Small focused change
- [ ]  Server-side rules enforced
- [ ]  Tests added
- [ ]  Error handling implemented
- [ ]  Logging added where needed
- [ ]  Documentation updated where behavior changes

### Before release

- [ ]  CI passes
- [ ]  Code review complete
- [ ]  Acceptance criteria verified
- [ ]  Database migration reviewed
- [ ]  Security checks completed
- [ ]  Deployment plan reviewed
- [ ]  Rollback/recovery considered
- [ ]  Monitoring available

# 45. Relationship to Technical Documents

| Document | Responsibility |
| --- | --- |
| 09. Software Architecture | Defines system structure and boundaries |
| 10. Technology Stack | Defines selected and candidate technologies |
| 11. Development Methodology | Defines how software is developed and delivered |
| 12. Engineering Standards | Defines coding, naming, testing, security, Git, API, and implementation standards |
| 13. Database Architecture | Defines data architecture and persistence rules |
| 14. API Specification | Defines API contracts |
| 15. Frontend Architecture | Defines web frontend architecture |
| 16. Backend Architecture | Defines backend implementation architecture |
| 17. Mobile Application Architecture | Defines React Native + Expo architecture |
| 18. Authentication & Authorization | Defines identity and access control |
| 19. Security Architecture | Defines security controls and boundaries |
| 20. Media & File Storage | Defines media lifecycle and storage |
| 21. Search Architecture | Defines search indexing and retrieval |
| 22. Notification System | Defines notification architecture |
| 23. SEO Architecture | Defines search-engine and discoverability architecture |

# 46. Document Status

**Status:** Proposed

This methodology should be refined as the project moves from documentation into active development.

Changes to the development process that materially affect engineering governance should be documented and reviewed rather than silently changing the methodology.