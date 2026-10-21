# 21. Search Architecture

> **Implementation status clarification — 2026-10-15:** “Active” means this is the current authoritative design baseline, not that implementation is release-ready. Implementation sign-off remains gated by the final OpenAPI 3.1 contract, successful clean-MySQL migration/runtime validation, and the relevant component tests. Component-specific schema or provider gates documented below remain independently binding.
> 

## Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-TECH-021 |
| Status | Active — Search Architecture Baseline |
| Version | 1.0 |
| Owner | KHOJ BHET Engineering |
| Last Reviewed | 2026-10-08 |
| Parent | 02. TECHNICAL DEFINITION |
| Previous | 20. Media & File Storage |
| Next | 22. Notification System |

## 1. Purpose

This document defines the authoritative search architecture for KHOJ BHET, including keyword search, category-aware filtering, structured attributes, location search, ranking, sorting, pagination, autocomplete, search indexing, privacy, SEO boundaries, and future migration to a dedicated search engine.

The V1 architecture is **MySQL-first**. Search indexes and projections are derived data and never become the source of truth.

## 2. V1 API Boundary and Deferred Search Features

Document 14 is authoritative for the V1 public search API. This architecture may describe future search capabilities, but the V1 client must not expose a feature as operational unless its request parameters, validation, response fields, authorization rules, and errors exist in Document 14.

For V1, use only the documented structured location filters (province, district, municipality, and any other explicitly registered API fields); do not use an undocumented `location=` parameter. Radius search, distance sorting, autocomplete, featured ordering, and saved searches remain deferred until Document 14 defines the contract and the relevant gate is closed. In particular, saved searches are not considered approved merely because this architecture has a section describing them.

All public search reads must enforce listing visibility and `expires_at > UTC_NOW()` at query time. Scheduler-driven status updates and cached search results are not substitutes for this predicate. Search/cache invalidation must prevent expired or restricted listings from continuing to appear.

**Early search validation gate:** Document 14 permits two-character search queries, while MySQL full-text tokenization defaults may exclude short tokens and Nepali/Devanagari tokenization can behave differently from Latin text. Before locking the V1 query implementation, run representative Nepali and English search tests—including two-character terms, common short Nepali words, mixed scripts, and zero-result behavior—against the pinned MySQL 9.7.x baseline. If native FULLTEXT fails the approved cases, evaluate an ngram parser or a different indexed-query strategy through a documented decision; do not silently raise the minimum query length or add a dedicated search engine.

## 2. Core Architecture

The search flow is:

**Client → Laravel Search API → Search Service → MySQL**

Future architecture may become:

**Client → Laravel Search API → Search Service → Search Adapter → Dedicated Search Engine**

The public API and business rules must remain stable when the underlying search technology changes.

Search never becomes authoritative for ownership, authorization, moderation, subscriptions, privacy, or listing lifecycle.

## 3. Search Principles

1. Search results contain only discoverable resources.
2. Authorization and privacy are enforced before ranking.
3. MySQL remains authoritative.
4. Search indexes are rebuildable derived data.
5. Category and attribute definitions come from the authoritative catalogue.
6. Structured data is searched as typed data, not arbitrary text.
7. Web and mobile use the same search semantics.
8. Search failure must never fail open.
9. Pagination must be deterministic.
10. Search performance must never justify exposing protected data.

## 4. Search Scope

V1 marketplace search covers:

- categories and subcategories;
- listing titles;
- approved searchable descriptions;
- listing types;
- structured category attributes;
- price;
- municipality;
- postal code;
- locality/chowk;
- approximate geographic position;
- facilities/features;
- condition and other approved attributes;
- approved seller/business context;
- freshness and ranking signals.

Private user records, verification records, payment records, and internal administrative records are not general marketplace search targets.

## 5. Search Eligibility

A listing enters ordinary search only when its lifecycle and moderation state permit discovery.

Typical requirements:

- listing exists;
- listing is published/active;
- listing is not deleted;
- listing is not suspended;
- required moderation rules have passed;
- category is valid;
- searchable data is valid;
- visibility rules permit discovery.

Draft, rejected, archived, deleted, suspended, or otherwise non-discoverable listings must not appear in public search.

## 6. Search Visibility vs Detail Visibility

Search visibility and detail visibility are separate.

A listing may expose title, price, gallery, approximate location, and selected facilities in search while keeping exact location, direct contact, or premium information protected.

Search therefore returns a **search-result projection**, not the complete listing record.

## 7. Search Result Projection

The public projection may contain:

- listing ID;
- title;
- category/subcategory;
- listing type;
- permitted location summary;
- price;
- permitted attributes;
- authorized media preview references;
- permitted seller/business summary;
- freshness/relevance information where appropriate.

It must never contain:

- exact protected location;
- private contact data;
- verification documents;
- internal moderation notes;
- payment information;
- storage credentials;
- hidden administrative fields.

## 8. Query Types

The Search Service supports:

1. Keyword search.
2. Category/subcategory search.
3. Structured filter search.
4. Location search.
5. Combined search.
6. Browse/sort search.
7. Autocomplete/suggestion search.

## 9. Keyword Search

Searchable text may include:

- title;
- approved description fields;
- category/subcategory names;
- approved searchable attribute labels and values;
- locality/chowk names.

Search text is normalized consistently at indexing and query time.

## 10. Nepali and Multilingual Search

KHOJ BHET must support Nepali and English marketplace searches.

The architecture must account for:

- Devanagari;
- Latin-script English;
- mixed Nepali-English queries;
- Unicode normalization;
- common spelling variation;
- locality names with multiple representations.

Controlled transliteration and synonym handling may be introduced without changing authoritative source values.

## 11. Text Normalization

Search normalization may include:

- Unicode normalization;
- case folding;
- whitespace normalization;
- punctuation normalization;
- controlled tokenization;
- approved synonym mapping;
- controlled transliteration.

Original database values remain authoritative. Normalized search values are derived data.

## 12. Category-Aware Search

The authoritative CAT-001–CAT-025 catalogue controls search categories and applicable attributes.

Search must not maintain an independent catalogue that can drift.

Different categories may expose different filters. For example:

- property: bedrooms, bathrooms, furnishing, area, facilities;
- vehicles: make, model, year, fuel type;
- mobiles: brand, storage, RAM, condition.

## 13. Dynamic Attribute Search

For each searchable attribute, the system must know:

- attribute identity;
- data type;
- predefined options where applicable;
- unit;
- multi-value behavior;
- category applicability;
- whether searchable;
- whether filterable;
- whether sortable.

Unsupported client-defined filter fields must be rejected.

## 14. Structured Filtering

Structured filters should use typed data.

Examples:

- category/subcategory;
- listing type;
- minimum/maximum price;
- bedrooms;
- area;
- year;
- brand/model;
- condition;
- furnishing;
- facilities;
- municipality;
- locality.

Numeric values must not be searched as formatted strings when typed data exists.

## 15. Multi-Value Attributes

Multi-value filters must have explicit semantics such as:

- match any selected value;
- match all selected values.

The API contract must define the behavior and web/mobile clients must use identical semantics.

## 16. Price Search

Price filtering and sorting use authoritative numeric price data.

Requirements:

- explicit currency;
- minimum and maximum validation;
- no negative values;
- invalid ranges rejected;
- formatted display strings never used for filtering.

Negotiable/offered-price semantics remain separate from numeric comparison.

## 17. Location Search

Location is a first-class search dimension.

Supported concepts include:

- province/district where available;
- municipality;
- postal code;
- locality/chowk;
- neighborhood/area;
- approximate coordinates.

The system must not require latitude/longitude alone.

## 18. Geographic Search and Privacy

For V1, location search uses only the structured geographic filters defined in Document 14 (province, district, municipality, and any other explicitly registered fields). Coordinates must remain separate from public exact coordinates, and exact location remains protected according to the authorization/privacy architecture.

Radius search, nearest-results queries, and distance sorting are future capabilities only; do not expose them in V1 clients until their API parameters, privacy behavior, limits, and response semantics are approved in Document 14.

## 19. Facilities and Feature Search

Facilities use canonical catalogue/attribute definitions.

Examples include parking, water supply, electricity, furnishing, internet, balcony, lift, and security.

Predefined facilities should be searched by canonical identifiers rather than inconsistent free text.

## 20. Sorting

Public sort modes must be explicit.

Potential modes include:

- relevance;
- newest;
- price low to high;
- price high to low.

Distance sorting and featured ordering are deferred until Document 14 defines and approves the corresponding V1 API contract.

Clients cannot submit arbitrary SQL expressions, fields, or sort clauses.

## 21. Ranking

Ranking is applied only after eligibility filtering.

Possible ranking signals:

1. Exact title/category match.
2. Token relevance.
3. Attribute match.
4. Location relevance.
5. Freshness.
6. Listing completeness/quality.
7. Approved featured weighting.
8. Future approved engagement signals.

Ranking must never override authorization, moderation, privacy, suspension, or deletion.

## 22. Featured Listings

Paid or subscription-based promotion may influence ordering only through explicit business rules.

A featured listing must still be eligible, moderated, visible, and safe.

Entitlement controls the feature; it does not override security or moderation.

## 23. Pagination

Cursor-based pagination is preferred for large public result sets.

Cursors must be opaque and contain enough state to preserve the requested sort context.

Every result set requires deterministic tie-breaking, such as:

**primary sort → secondary ranking key → stable listing identifier**

This prevents duplicate or missing records between pages.

## 24. Search Consistency

Search is derived from authoritative data.

V1 should target near-real-time visibility.

Critical listing visibility transitions must not rely on an uncontrolled stale search index.

The operational target for indexing delay must be measurable and tested.

## 25. MySQL Indexing

MySQL indexes must be designed around real query patterns.

Likely indexed dimensions include:

- publication/lifecycle state;
- moderation eligibility;
- category/subcategory;
- listing type;
- price;
- municipality;
- postal code;
- locality;
- searchable timestamps;
- commonly combined structured filters.

Query plans must be measured using realistic data volumes.

## 26. Search Projection

A search projection may contain:

- listing ID;
- category/subcategory;
- normalized title;
- approved searchable text;
- normalized price;
- location search fields;
- filterable attribute values;
- media preview reference;
- timestamps;
- ranking signals;
- eligibility flags.

The projection is rebuildable and never authoritative.

## 27. Dynamic Attribute Search Storage

The authoritative attribute model remains relational.

Search-specific denormalization is permitted when it:

- is derived;
- can be rebuilt;
- cannot change business truth;
- has deterministic synchronization.

## 28. Search Synchronization

Authoritative changes should trigger search projection updates.

Relevant changes include:

- listing creation/update;
- publication;
- pause/resume;
- archive/delete;
- moderation approval/rejection;
- searchable attribute changes;
- location changes;
- representative media changes;
- approved featured-entitlement changes.

Jobs must revalidate sensitive state before consequential visibility changes.

## 29. Reindexing

The system must support:

- full rebuild;
- listing-scoped rebuild;
- category-scoped rebuild;
- failed-item retry;
- consistency verification.

A corrupted projection must be recoverable from authoritative MySQL data.

## 30. Search Failure

If optional search infrastructure fails:

- authoritative listing operations continue where possible;
- safe MySQL fallback may be used;
- degraded relevance is preferable to unsafe visibility;
- API errors follow Document 14;
- infrastructure details are not exposed.

Search failure must never cause fail-open visibility.

## 31. Autocomplete

Autocomplete is a separate low-latency path.

It may suggest:

- categories;
- subcategories;
- municipalities;
- localities/chowks;
- approved marketplace terms;
- approved listing titles where permitted.

It must not expose unpublished content, private user data, or internal records.

## 32. Search Suggestions and Synonyms

Suggestion sources should be controlled:

- approved catalogue terms;
- approved location registry;
- reviewed synonym dictionaries;
- privacy-safe aggregated search terms;
- approved popular queries.

Raw arbitrary user queries must not automatically become globally visible suggestions.

Synonym dictionaries must be versioned and reviewed.

## 33. Typo Tolerance

Typo tolerance may be introduced for keyword queries.

It must remain bounded to prevent irrelevant matches, excessive database work, and ambiguous category mapping.

Structured identifiers and filters should not be fuzzily interpreted.

## 34. Query Complexity Protection

Search requests must have bounded complexity.

Controls include:

- maximum query length;
- maximum number of filters;
- maximum attribute filters;
- maximum radius;
- maximum result size;
- restricted expensive operations;
- query timeouts;
- rate limits.

Clients cannot submit SQL, arbitrary expressions, index hints, or provider-specific query DSL.

## 35. Search API Security

Search endpoints enforce:

- endpoint-specific authentication;
- authorization-aware result filtering;
- safe parameter parsing;
- parameterized database queries;
- rate limiting;
- query complexity limits;
- maximum page size;
- abuse monitoring.

Search input is untrusted input.

## 36. Search Privacy

Search must not reveal:

- exact protected location;
- private contact data;
- verification documents;
- internal moderation state;
- hidden seller information;
- unpublished/deleted/suspended listings;
- internal ranking/debug data.

## 37. Search Caching

Safe search responses may be cached.

Cache keys must include every input that changes result or authorization semantics.

User-specific or protected search results must not enter shared caches unless the cache is explicitly authorization-safe.

Visibility changes must invalidate or bypass stale cached results as required.

## 38. Search Analytics

Search analytics may measure:

- query volume;
- zero-result queries;
- filter usage;
- category usage;
- click-through;
- conversion;
- latency;
- failures.

Retention and access follow the project's privacy/data-lifecycle rules.

## 39. Subscription Entitlements

Subscriptions may affect:

- featured placement;
- promoted ranking;
- business tools;
- listing limits;
- analytics.

They cannot bypass authorization, moderation, suspension, privacy, or deletion.

## 40. Business Listings

Business membership controls management capabilities, not automatic public search visibility.

A member's ability to edit a listing does not itself change discoverability.

Private business resources are not public marketplace search results unless explicitly designed as such.

## 41. Search and Media

Search may return authorized media preview references.

Media delivery remains governed by Document 20.

Search must never expose storage credentials, private object keys, or unrestricted signed URLs.

## 42. SEO and Web Crawlers

Public search pages may be indexed only according to Document 15's web SEO policy.

That policy controls:

- indexability;
- canonical URLs;
- robots directives;
- sitemap inclusion;
- faceted-navigation indexing;
- crawl-budget behavior.

Private, duplicate, low-value, and unauthorized search states must not become indexable merely because the API can generate them.

## 43. LLM/AI Crawlers

Public search content intended for AI/LLM discovery follows the public frontend and robots policy.

Search APIs are not unrestricted public datasets.

AI/LLM crawler access must follow the project's explicit public-web policy.

## 44. Mobile Search

React Native/Expo clients use the same search API and business semantics as web.

Mobile may provide recent searches and local filter presets. Saved searches and server-backed location convenience features are deferred until their API contracts are defined and the relevant decision gate is closed.

These client features never alter server-side authorization.

## 45. Saved Searches — Deferred

Saved searches are not a V1 implementation commitment while the API/database gate remains open. If approved in a later gate, they must belong to the authenticated user, remain private, execute under current search rules, handle obsolete filters safely, and respect current listing visibility. Do not expose save/list/update/delete saved-search operations until Document 14 defines them.

- do not grant access to listings.

## 46. Background Jobs

Background jobs may handle:

- projection updates;
- reindexing;
- synonym updates;
- cleanup;
- analytics aggregation.

Jobs must be idempotent and must revalidate sensitive visibility state when required.

## 47. Observability

Monitor:

- search latency;
- query volume;
- zero-result rate;
- error rate;
- slow queries;
- indexing lag;
- failed indexing jobs;
- stale projection count;
- cache hit ratio;
- rate-limit events;
- ranking anomalies.

Sensitive result payloads must not be unnecessarily logged.

## 48. Performance Targets

Implementation must define measurable targets for:

- common search latency;
- complex filtered-search latency;
- autocomplete latency;
- indexing delay;
- reindex throughput;
- error rate.

Targets must be validated using realistic catalogue volume and query distributions.

## 49. Dedicated Search Engine Migration

A dedicated engine may be introduced when MySQL no longer satisfies scale or relevance requirements.

Potential drivers include:

- catalogue scale;
- query volume;
- advanced relevance;
- multilingual analysis;
- typo tolerance;
- geographic search;
- faceting;
- autocomplete scale;
- complex ranking.

Future architecture:

**Authoritative MySQL → Search Indexer → Search Engine → Search Adapter → Laravel Search Service**

Public API semantics should remain unchanged.

## 50. Search Adapter Boundary

A future search adapter should expose operations conceptually equivalent to:

- search;
- suggest;
- index;
- update;
- delete;
- bulk index;
- reindex;
- health check.

Provider-specific query syntax remains behind the adapter.

## 51. Search Index Security

A dedicated search index is derived infrastructure.

It must use:

- least-privilege access;
- encryption/access controls where supported;
- private network access where appropriate;
- separate credentials;
- no direct client access;
- controlled backups;
- rebuild capability;
- auditability.

The index must not become a shadow database containing unnecessary private data.

## 52. Testing

### Functional

- keyword matching;
- category filters;
- structured attributes;
- price;
- location;
- sorting;
- pagination;
- autocomplete;
- zero-result behavior.

### Security

- unauthorized listings never appear;
- exact location never leaks;
- private media is not exposed;
- unpublished/deleted/suspended listings are excluded;
- search identifiers cannot bypass authorization;
- subscription rules cannot bypass security.

### Consistency

- publish makes a listing searchable;
- pause removes it according to policy;
- delete removes it;
- attribute changes update filters;
- location changes update search;
- moderation changes update eligibility.

### Performance

- common queries meet target;
- expensive filters are bounded;
- pagination remains stable;
- indexing lag remains within target.

## 53. Security Invariants

1. Search never grants authorization.
2. Search results are always eligibility-filtered.
3. MySQL remains authoritative.
4. Search indexes are rebuildable derived data.
5. Exact protected location cannot be exposed through search.
6. Private contact data cannot be exposed through search.
7. Unpublished, deleted, or suspended resources cannot appear.
8. Client filters cannot become SQL.
9. Client sort parameters cannot become arbitrary SQL.
10. Subscription entitlement cannot bypass security or moderation.
11. Ranking cannot override eligibility.
12. Search failure never fails open.
13. Search indexes contain only necessary data.
14. Public search does not imply unrestricted detail access.
15. Web and LLM crawler access follows the public frontend/robots policy.

## 54. Cross-Document Contracts

| Document | Search Contract |
| --- | --- |
| 08 Product & Business Rules | Discoverability, lifecycle, ranking/business rules |
| 09 Software Architecture | Service boundaries and derived-data principles |
| 10 Technology Stack | MySQL/search technology decisions |
| 12 Engineering Standards | Implementation and testing standards |
| 13 Database Architecture & Data Model | Authoritative listing, catalogue, attribute, and location structures |
| 14 API Specification | Public search API, pagination, errors, enums |
| 15 Frontend Architecture | Web search UX, SEO, robots, canonical URLs, crawl policy |
| 16 Backend Architecture | Laravel Search Service/query implementation |
| 17 Mobile Application Architecture | Mobile search UX and API usage |
| 18 Authentication & Authorization | Actor/resource authorization |
| 19 Security Architecture | Trust boundaries and security controls |
| 20 Media & File Storage | Media references and delivery |
| 21 Search Architecture | End-to-end marketplace search |

## 55. Implementation Rules

1. Implement V1 search on MySQL.
2. Keep search behind a Search Service abstraction.
3. Treat projections as derived data.
4. Build category filters from the authoritative catalogue.
5. Use typed structured attributes.
6. Keep exact location separate from approximate searchable location.
7. Filter eligibility before ranking.
8. Use deterministic ordering.
9. Prefer stable cursor pagination for large public result sets.
10. Bound query complexity.
11. Enforce server-side rate limits.
12. Keep public result projections minimal.
13. Never expose private storage credentials or object keys.
14. Rebuild projections from authoritative MySQL.
15. Make indexing jobs idempotent.
16. Revalidate sensitive visibility transitions.
17. Keep web and mobile semantics identical.
18. Keep SEO/crawler policy separate from API authorization.
19. Add negative-path security tests.
20. Record material search architecture changes through an ADR.

## 56. Acceptance Checklist

- [ ]  MySQL is authoritative for V1 search.
- [ ]  Search Service abstraction exists.
- [ ]  Search eligibility rules are defined.
- [ ]  Search result projection is defined.
- [ ]  Category-aware filtering is implemented.
- [ ]  Dynamic attributes use the authoritative catalogue.
- [ ]  Numeric filters use typed values.
- [ ]  Enumerated filters use canonical values.
- [ ]  Multi-value semantics are explicit.
- [ ]  Price filtering and sorting are numeric.
- [ ]  Municipality/postal/locality search is supported.
- [ ]  Geographic search does not expose protected coordinates.
- [ ]  Nepali/English normalization is defined.
- [ ]  Sorting modes are explicit.
- [ ]  Ranking cannot override eligibility.
- [ ]  Featured ranking follows entitlement/business rules.
- [ ]  Stable pagination is implemented.
- [ ]  Projection synchronization exists.
- [ ]  Full and scoped reindexing are supported.
- [ ]  Search failure cannot fail open.
- [ ]  Autocomplete is bounded and privacy-safe.
- [ ]  Query complexity limits exist.
- [ ]  Search rate limits exist.
- [ ]  Search caching is authorization-safe.
- [ ]  SEO/crawler behavior follows frontend policy.
- [ ]  Mobile uses the same search contract.
- [ ]  Search observability exists.
- [ ]  Security and consistency tests exist.
- [ ]  Dedicated search-engine migration remains possible.

## 57. Status

**Active — Search Architecture Baseline**

This document is the authoritative architectural baseline for KHOJ BHET marketplace search. Implementation details may evolve, but MySQL authority, Search Service abstraction, eligibility-before-ranking, privacy boundaries, category-driven filtering, stable pagination, rebuildability, and security invariants must remain intact unless changed through the appropriate architecture or ADR process.

## V1 Search Contract Decision — 2026-10-18

Normalize Unicode to NFC, trim and collapse whitespace, compare Latin text case-insensitively, preserve Devanagari, and do not automatically transliterate Romanized Nepali in V1. Empty queries must return a validation error; zero matches return an empty result. Use the approved MySQL-first approach, but test the supported MySQL version, collation, FULLTEXT token rules, short queries, Devanagari and mixed-script queries before implementation. Search results must apply the same publication, moderation, visibility and privacy rules as listing discovery. DOC-09 remains open until these behaviors are tested and the actual results are recorded.

## Search Validation Matrix — Required Runtime Evidence (2026-10-18)

**Status: Contract specified; validation not run / evidence pending.** Execute against the pinned supported MySQL 9.7.x build and record expected result, actual result, query plan and pass/fail for each test.

| Case | Example / condition | Required assertion |
| --- | --- | --- |
| Latin case normalization | `Mobile`, `mobile`, `MOBILE` | Contractually equivalent matching behavior |
| Whitespace normalization | leading/trailing and repeated spaces | Trim/collapse before matching |
| Unicode normalization | equivalent NFC/NFD input | Normalize to NFC before comparison |
| Devanagari | representative Nepali query and listing text | Correct documented matches; no loss/corruption of script |
| Mixed script | Nepali + English brand/model | Expected combined matching behavior |
| Two-character term | common 2-character Nepali/Latin terms | Measured behavior recorded; no assumption that FULLTEXT finds it |
| Romanized Nepali | Latin transliteration of Nepali phrase | No automatic transliteration in V1; behavior explicitly tested/documented |
| Empty query | empty or whitespace-only string | Validation error, not unbounded browse/search |
| No matches | valid query with no eligible listing | Empty result with normal response schema |
| Visibility and moderation | draft, review, rejected, paused, expired or restricted listing | Excluded from public results as required by authoritative eligibility rules |
| Privacy | protected contact fields and exact residential location | Never leaked through search result payloads |
| Pagination/stability | multiple pages, repeated request | Contract-compliant cursor behavior without exposing cursors as crawlable page numbers |

If MySQL FULLTEXT or collation behavior fails the agreed test cases, measure alternatives and propose a documented schema/query strategy change. Do not silently introduce an external search engine or Romanized transliteration into V1.