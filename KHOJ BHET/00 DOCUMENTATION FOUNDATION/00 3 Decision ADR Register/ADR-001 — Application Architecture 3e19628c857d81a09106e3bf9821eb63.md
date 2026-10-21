# ADR-001 — Application Architecture

# ADR Metadata

- **ADR ID:** ADR-001
- **Status:** Accepted
- **Date:** 2026-09-20
- **Decision Owner:** KHOJ BHET Project Team
- **Area:** Application Architecture
- **Related ADRs:** ADR-002, ADR-003, ADR-004, ADR-005
- **Implementation Status:** Not started

# 1. Context

KHOJ BHET is intended to become a long-term Nepal-focused marketplace supporting property, vehicles, electronics, furniture, jobs, services, tickets, and future transaction workflows.

The system needs clear domain boundaries, maintainable code, practical deployment, and a path to scale without unnecessary operational complexity at the beginning.

# 2. Decision Drivers

- Maintainability
- Development speed
- Clear module boundaries
- Operational simplicity
- Deployment simplicity
- Scalability
- Testability
- Security
- Team capability
- Future service extraction
- Cost control

# 3. Alternatives Considered

## Option A — Modular Monolith

One deployable backend application containing clearly separated business modules such as Identity, Listings, Categories, Locations, Media, Search, Favorites, Messaging, Notifications, Subscriptions, Payments, and Moderation.

## Option B — Traditional Monolith

One application with fewer explicit module boundaries. Simpler initially, but potentially harder to maintain as the marketplace grows.

## Option C — Microservices

Separate deployable services for major domains. Provides independent scaling and isolation but adds infrastructure, deployment, networking, monitoring, and data-consistency complexity.

# 4. Proposed Decision

**Accepted decision:** Use a modular monolith for the initial KHOJ BHET backend. The initial implementation should maintain explicit module boundaries so a high-load or independently evolving module can potentially be extracted later.

# 5. Rationale

A modular monolith provides strong internal architecture without requiring the operational overhead of multiple independently deployed services. It allows domain boundaries to be established early while keeping development, deployment, debugging, transactions, and infrastructure relatively simple.

# 6. Consequences

### Benefits

- Single deployment unit
- Lower operational complexity
- Easier local development and debugging
- Straightforward transactions
- Lower initial infrastructure cost
- Clear path toward modular growth

### Trade-offs

- Modules initially share the same runtime
- Some database coupling may remain
- Independent scaling is limited
- Strong discipline is required to prevent tight coupling

### Future Migration

If a module later requires independent scaling, deployment, security isolation, or ownership, it may be evaluated for extraction into a separate service. That change requires a new ADR.

# 7. Implementation Guidance

Detailed implementation belongs in Software Architecture, Backend Architecture, Database Architecture, and Engineering Standards.

The application should use explicit module boundaries, defined interfaces, controlled cross-module access, and automated tests around important boundaries.

# 8. Acceptance Criteria

Before acceptance, confirm module boundaries, deployment model, expected initial scale, team capability, operational requirements, and criteria for future service extraction.

# 9. Related Documentation

1. Requirements Specification
2. Software Architecture
3. Technology Stack
4. Database Architecture
5. Backend Architecture

# 10. Status History

- 2026-09-20 — Created as Proposed.
- 2026-09-28 — Accepted as the current application architecture baseline.