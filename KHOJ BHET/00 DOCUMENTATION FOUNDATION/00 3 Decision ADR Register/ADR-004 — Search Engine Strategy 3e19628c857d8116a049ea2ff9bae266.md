# ADR-004 — Search Engine Strategy

# ADR Metadata

- **ADR ID:** ADR-004
- **Status:** Accepted
- **Date:** 2026-09-20
- **Decision Owner:** KHOJ BHET Project Team
- **Area:** Search
- **Related ADRs:** ADR-008
- **Implementation Status:** Not started

# 1. Context

Search is a core marketplace capability. Users need keyword search, category, location, price, condition, listing type, facilities, and category-specific attributes.

The platform should use an inexpensive initial architecture while retaining a migration path as listing volume, search complexity, and traffic increase.

# 2. Decision Drivers

- Search relevance
- Nepali and English text
- Filtering and faceting
- Location search
- Attribute filtering
- Query performance
- Operational complexity
- Cost
- Indexing complexity
- Scalability
- Migration effort

# 3. Alternatives

## MySQL Search

Relational database queries and indexes.

## MySQL Full-Text Search

Database full-text capabilities for suitable text fields.

## Typesense

Dedicated search infrastructure focused on fast search and filtering.

## Elasticsearch / OpenSearch

More feature-rich dedicated search infrastructure with greater operational complexity.

# 4. Decision

**Accepted decision:** KHOJ BHET will use **MySQL-based search initially for V1**, including indexed relational queries and MySQL full-text search where appropriate. The application must keep search access behind a search abstraction so a dedicated search engine can be introduced later without changing marketplace domain ownership.

A dedicated search engine is not part of the initial implementation. Introduction requires measurable evidence such as sustained search-latency problems, database resource pressure, advanced faceting/relevance requirements, typo tolerance, or other documented V1/V2 requirements.

# 5. Migration Triggers

Potential triggers include excessive search latency, database CPU caused by search, large listing volume, advanced faceting requirements, typo tolerance, sophisticated relevance, or advanced geospatial search.

Exact thresholds should be defined from real measurements.

# 6. Consequences

Starting with MySQL reduces infrastructure and operational complexity. A later dedicated engine requires an indexing pipeline, synchronization, reindexing, failure recovery, monitoring, and additional infrastructure.

The domain model should not become coupled to one search vendor.

# 7. Acceptance Criteria

Define V1 search requirements, expected listing/query volume, relevance requirements, Nepali-language requirements, location requirements, performance targets, and migration triggers.

# 8. Related Documentation

- 
    1. Requirements Specification
- 
    1. Database Architecture
- 
    1. Search Architecture
- ADR-008 — Database Search Strategy

# 9. Status History

- 2026-09-20 — Created as Decision Pending.
- 2026-09-28 — Accepted: MySQL-based search is the initial V1 search strategy; dedicated search remains a future migration option based on measurable requirements.