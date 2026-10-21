# ADR-008 — Database Search Strategy

# ADR Metadata

- **ADR ID:** ADR-008
- **Status:** Accepted
- **Date:** 2026-09-20
- **Decision Owner:** KHOJ BHET Project Team
- **Area:** Data / Search
- **Related ADRs:** ADR-004
- **Implementation Status:** Not started

# 1. Context

KHOJ BHET will use a relational database for authoritative marketplace data.

A separate architectural question is which searchable information should remain queried directly from the relational database and when a dedicated search index becomes necessary.

# 2. Decision Drivers

- Data consistency
- Search performance
- Query complexity
- Filtering
- Faceting
- Location search
- Attribute search
- Index maintenance
- Operational cost
- Reindexing
- Data synchronization
- Failure recovery

# 3. Alternatives

## Database-First Search

Search directly against MySQL using appropriate indexes and query strategies.

## Database Full-Text Search

Use MySQL full-text capabilities for suitable text fields.

## Dedicated Search Index

Replicate searchable listing data into a dedicated search engine.

## Hybrid

Use MySQL as the authoritative source while maintaining a derived search index for search workloads.

# 4. Decision

**Accepted decision:** MySQL is the authoritative system of record for core marketplace data and the V1 search implementation. Search infrastructure beyond MySQL, if introduced later, is a derived/read-optimized representation and must be rebuildable from MySQL. A dedicated search index must not become the authoritative source for core transactional records.

# 5. Data Ownership Principle

The relational database remains the system of record for users, listings, categories, attributes, locations, subscriptions, moderation records, and other transactional entities.

A search index, if introduced, is a derived representation.

# 6. Synchronization

A future index architecture may follow:

Database Change → Indexing Event/Job → Search Index

The design should handle create, update, publish, pause, sold/rented state changes, delete, category/attribute changes, location changes, and reindexing.

# 7. Consequences

Database-first search reduces infrastructure and synchronization complexity.

A dedicated index can improve search performance and capabilities but creates an additional data pipeline and consistency model.

Treating the search index as derived reduces the risk of making search infrastructure a second system of record.

# 8. Acceptance Criteria

Define V1 search patterns, required filters, expected data volume, performance targets, search consistency requirements, indexing frequency, migration triggers, and reindex strategy.

# 9. Relationship to ADR-004

ADR-004 addresses the broader search engine strategy. ADR-008 specifically defines the boundary between authoritative database data and search-optimized data. They are related but should remain separate unless the project later determines one ADR fully covers both.

# 10. Related Documentation

- 
    1. Requirements Specification
- 
    1. Database Architecture
- 
    1. Search Architecture
- ADR-004 — Search Engine Strategy

# 11. Status History

- 2026-09-20 — Created as Decision Pending.
- 2026-09-28 — Accepted; MySQL remains authoritative and search indexes remain derived/rebuildable.