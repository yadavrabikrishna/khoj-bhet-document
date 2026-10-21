# Architecture Cross-Document Audit & Closure Register

> **Additional schema correction verified 2026-10-09:** Document 13 Gate #11 previously described user_push_devices.user_id as ULID even though [users.id](http://users.id) is BIGINT UNSIGNED. The Gate #11 FK type has been corrected to BIGINT UNSIGNED to match [users.id](http://users.id). The regenerated DBML, Laravel migration and validation SQL must carry this correction and verify the FK on clean MySQL.
> 

## Expanded Reconciliation — Claude Findings Reviewed 2026-10-09

This section supersedes the earlier short audit summary where it overlaps. Findings were checked against the connected Notion pages available at review time. “Resolved in documentation” does not mean implementation or runtime tests have passed.

### A. Confirmed decisions already aligned in current Notion text

| Finding | Current decision / status |
| --- | --- |
| Marketplace web session vs bearer API | Resolved in Document 18 and accepted ADR-002 addendum: Firebase ID-token Bearer auth; Laravel does not create marketplace web sessions, session cookies or CSRF requirements for this API flow. |
| Public route convention | Mostly resolved: Documents 15 and 23 use /listing/{slug}-{public-id}, /category/{slug}, /location/{slug}, /business/{slug}. Document 14 includes /listings/by-public-id/{public_id}. Location slug data/resolution remains a blocker. |
| Listing lifecycle and restore | Resolved in Documents 15 and 17: draft, review, published, paused, expired, archived, rejected. Removal is a separately authorized DELETE/moderation action, not a client-assignable lifecycle state. Actions include submit, pause, resume, archive, restore, renew and authorized DELETE. |
| Listing creation flow | Resolved in Documents 15 and 17: collect category and listing type first; POST /listings includes both in its body; use the returned representation and then GET /listings/{id}/readiness. |
| V1 push tokens | Resolved in Documents 10 and 17: provider is fcm; native FCM registration tokens only, not Expo push-service tokens. Android uses FCM; iOS must obtain the FCM token through Firebase Messaging. Real-device tests remain required. |
| V1 payments | Resolved in Documents 10, 16 and 17: manual submission with proof and admin review only. Gateway redirects, callbacks, webhooks and automated reconciliation are future-phase only. |
| Transactional outbox | Resolved in Documents 09 and 16: business mutation and outbox_events row commit in the same MySQL transaction; a relay publishes to workers. Dispatch-after-commit alone is insufficient. |
| Idempotency persistence | Resolved in Documents 14 and 16: MySQL api_idempotency_keys is authoritative; Redis may only accelerate locks/cache behavior. |
| Optimistic concurrency | V1 If-Match is optional. Stale supplied ETags are rejected; if the header is omitted, documented last-write-wins applies. Document 16 was clarified accordingly. |
| Stack versions | Documents 10 and 16 align on PHP 8.5.x and MySQL 9.7.x LTS-compatible baseline. Old PHP 8.4+/MySQL 8.x wording is not current. |
| Admin MFA | Documents 10, 18 and 19 require MFA for privileged administration. Actual enforcement and secure persistence remain implementation/schema gates. |
| Time zone | Document 22 sets APP_TIMEZONE=UTC and UTC persistence/comparison; Asia/Kathmandu is for local display, scheduling and calendar boundaries. |
| Search engine | Documents 10, 12 and 21 specify MySQL-first V1; no dedicated engine is a V1 dependency. Nepali/Devanagari and two-character queries still need early full-text testing. |
| Media limits | Document 20 specifies up to 20 images, 21 total media items including at most one video, 10 MB/image; JPEG, PNG and WebP inputs only. HEIC/HEIF is not accepted in V1. |
| Video | Decision exists: one MP4/H.264/AAC video per listing, max 50 MB/60 seconds, asynchronous processing, poster frame, playback derivative and HTTP byte-range support. ADR-005 says local storage abstraction; CDN is not required for V1. End-to-end tests remain open. |
| Expiry enforcement | Documents 21 and 23 require approved visibility plus expires_at > UTC_NOW() at read time for public reads, search, recommendations, SEO, sitemap, SSR and caches. Scheduler updates are not the visibility boundary. |
| Notification scope | Document 22 limits V1 to transactional/security/account notices, in-app read state, preferences and approved FCM push. Campaigns, quiet hours, browser push and WhatsApp are deferred. Do not assume bulk-read or unread-count endpoints unless Document 14 defines them. |
| Media upload | V1 is direct multipart through Laravel. Document 20 has been clarified to label upload-intent/complete as future-only. |
| Contact reveal | Document 14 was corrected: POST /listings/{id}/contact-reveals is canonical; GET /listings/{id}/contact is superseded and must not be implemented. |
| Navigation | Documents 19–23 point to the correct adjacent documents. |

### B. Open decisions or schema/API gates

| ID | Open issue | Required closure |
| --- | --- | --- |
| CR-01 | Location slug registry/resolver: route is planned but current location model uses integer IDs and has no canonical public slug source. | Decide stable unique slugs on the approved locality/municipality model or a dedicated registry. Update Documents 13, 14 and 23 together. Until then, location SEO pages are not implementation-ready. |
| CR-02 | Sitemap producer contract — CLOSED (2026-10-09). | Next.js generates V1 XML sitemaps from existing documented public API/reference responses; no dedicated sitemap-feed endpoint is added. Cursor pagination is internal only. Canonical eligibility, lifecycle/expiry filtering, freshness and invalidation are specified in Document 23. Location sitemap entries remain blocked by CR-01 until location slugs have an approved source/resolver. |
| CR-03 | Crawlable pagination — POLICY CLOSED; implementation tests remain. | Do not expose opaque cursors or assume `?page=N` works. Search/filter result variants remain non-indexable by default; only curated canonical category/location/listing routes may be indexed. Verify canonical tags, internal links and sitemap output against Document 23. |
| CR-04 | Two-character and Nepali/Devanagari full-text behavior. | Test representative Nepali, English, mixed-script and two-character queries against pinned MySQL 9.7. Approve ngram/parser changes only from measured results. |
| CR-05 | Notification bulk-read/unread-count APIs. | Use only endpoints specified in Document 14, or add each endpoint and response schema before clients implement it. |
| CR-06 | Notification locale/deduplication schema: no dedicated locale, classification, expiry or dedupe-key fields and no templates table are established. | Keep templates in versioned code/config for V1 and use durable outbox identity plus idempotent consumers only if duplicates are prevented. Choose a locale policy independent of an unrelated request's Accept-Language. Extend Document 13 first if durable per-notification fields are required. |
| CR-07 | Media metadata schema: not every generic classification/quarantine/checksum/detected-MIME/resource-target field described in Document 20 exists in Document 13. | Restrict V1 to supported schema or approve a Document 13 schema gate before implementing unsupported metadata. |
| CR-08 | Verification evidence/payment proof linkage: payment proof currently uses submitted_payment_proof_reference (VARCHAR), not a declared media FK. | Validate and authorize the referenced media public ID. Never store a filesystem path, storage key or signed URL. Add a schema FK only through an approved gate. |
| CR-09 | Business logo/cover persistence. | Confirm physical business schema; add approved media relationships or limit V1 to supported fields. Do not invent columns. |
| CR-10 | Admin MFA persistence: admins has no explicit MFA columns. | Select a Laravel/Filament-compatible mechanism and verify migrations, secret protection, recovery and challenge flows. Deny privileged access until MFA completes. |
| CR-11 | Public-read IP rate limits through Next.js SSR. | Configure trusted proxies; honor forwarded addresses only from trusted proxies; test user quotas through SSR. Service credentials must not bypass end-user quotas. |
| CR-12 | ULID public identifiers with Eloquent. Internal primary keys remain BIGINT and public_id is a separate unique CHAR(26). | Generate public_id without changing primary-key incrementing semantics. If using HasUlids, verify/customize unique-ID behavior to target public_id; route binding should use public_id. Add model tests. |
| CR-13 | Slug history. Listing public ID enables current-slug resolution without a dedicated listing history table for basic redirects. | Verify resolver returns current canonical slug and redirects only while resource is public. Category/business slug sources and location slugs need deterministic resolution. |
| CR-14 | Expiry/cache behavior. | Set bounded cache TTLs and invalidate on lifecycle/expiry changes; test expired, paused, archived, deleted and renewed listings across API, SSR, structured data and sitemap. |
| CR-15 | Video pipeline/schema/runtime. | Test signatures/MIME, limits, async state, poster/playback generation, cleanup, Range/206, Nginx/PHP limits, timeouts/temp storage and private-media isolation. |
| CR-16 | Firebase OTP abuse controls. | Verify App Check where supported, Nepal (+977) SMS restrictions where supported, anti-enumeration, spend monitoring and deployed Firebase settings. Laravel must not reimplement OTP verification. |
| CR-17 | OpenAPI authority/generation. | Document 16 now specifies contract-first OpenAPI 3.1. Generate and validate the final artifact only after schema artifacts and clean-MySQL validation pass. |
| CR-18 | Schema/artifact drift. | Static reconciliation PASS on 2026-10-09: the available Gate #14 DBML contains 55 tables / 89 declared references; the Laravel migration contains 55 table creations / 89 FK declarations; the validation SQL expects 55/89 and checks the current pricing/verification enums; the schema review reports static PASS. The migration and DBML both define `user_push_devices.user_id` as BIGINT UNSIGNED and link it to `users.id`. Remaining gate: run the migration and validation SQL on a clean supported MySQL instance, record tool/version/command/exit code and resolve any failure. Regenerate artifacts only if runtime testing or an approved schema change exposes drift. |
| CR-19 | Business-member/safety feature parity. | Trace businesses/members, verification, blocking, contact reveal, conversation read cursor and account lifecycle to use case, API, schema owner, permission policy and tests. Defer unsupported items explicitly. |
| CR-20 | Verification vocabulary — DECISION CLOSED; artifact/runtime verification remains under CR-18. | Current V1 verification state registry is `pending`, `approved`, `rejected`, `expired`, `revoked`, `canceled`; only `approved` is the positive active state. `verified` is superseded for this enum. Do not globally replace unrelated user phone/email verification claims that legitimately use `verified`. Regenerated artifacts must implement the current registry. |

### C. Housekeeping applied during this review

- Document 14: superseded contact GET wording; canonical POST contact-reveals.
- Document 16: clarified optional If-Match/last-write-wins and replaced RemoveListing wording with authorized deletion.
- Document 18: checklist now requires admin MFA enforcement and testing.
- Document 20: direct-multipart lifecycle and processing flow now supersede V1 upload-intent guidance.
- Document 09: explicitly points to MySQL-first search decisions.
- Accepted ADR-002 and ADR-005 addenda already settle bearer-only marketplace API authentication and V1 video/local-storage direction. Older proposal paragraphs below those addenda are historical context, not current decisions.

### D. Release status

**Architecture documentation: conditional pass after reconciliation. Implementation readiness: NOT YET.** Do not mark clean-MySQL runtime validation or OpenAPI generation as passed until the actual artifacts and execution evidence exist.

This register records the cross-document architecture audit for KHOJ BHET Documents 15–23 against Documents 04, 10, 13, 14 and the accepted architecture decisions ADR-002, ADR-005, ADR-007 and the MySQL-first search decision.

**Audit outcome: CONDITIONAL PASS — architecture direction is aligned; release/implementation gates remain open.** This is not a claim that the clean-MySQL runtime migration has passed or that the final OpenAPI 3.1 artifact has been generated.

## 1. Authoritative decisions confirmed

- Marketplace web: Next.js / React frontend; Laravel REST API is the business and authorization boundary.
- Mobile: separate React Native + Expo application consuming the same Laravel REST API. React Native version follows the pinned Expo SDK baseline; do not independently upgrade either.
- Marketplace identity: Firebase Authentication; Laravel verifies Firebase ID tokens and maps the identity to the MySQL user record.
- Administration: dedicated Laravel/Filament authentication and admin identity store; admin identities are not Firebase marketplace users.
- Data authority: MySQL is authoritative for transactional marketplace data, including conversations/messages, notification records and device-token persistence. Firestore, Redis, caches and search projections are secondary/derived only.
- Media: local application/server storage for V1 behind a provider-agnostic abstraction; MySQL stores metadata/references. Restricted verification/property documents must not become public through predictable paths or CDN rules.
- Search: MySQL-first for V1; any future search index is a rebuildable projection and must preserve visibility and entitlement checks.
- Notifications: central notification module; FCM is the V1 push provider. Device tokens are persisted in the approved `user_push_devices` table; Expo-specific token persistence is deferred. WhatsApp Business API is a later-phase capability.
- SEO: public indexability is policy-driven and tied to listing lifecycle/visibility. `robots.txt` is crawl policy, not access control. Canonical URLs, sitemap output, structured data, metadata and `llms.txt` must expose only approved public content.

## 2. Navigation audit

- 19 → 20: corrected to Media & File Storage.
- 20 → 21: corrected to Search Architecture.
- 21 → 22: corrected to Notification System.
- 22 → 23: corrected to SEO Architecture.
- 23 → 24: corrected to Testing & QA.
- Document 22's Previous field was also corrected from 23 to 21.

## 3. Findings and closure status

| ID | Finding | Status | Closure condition |
| --- | --- | --- | --- |
| ARCH-01 | Stale document sequence/navigation in Documents 19, 20 and 22 | Closed | Fetch verification confirms correct adjacent-document references. |
| ARCH-02 | Physical schema count drift: older Document 13 Version 1.4 text describes 52 tables, while later closed database gates establish a 55-table / 89-FK baseline | Closed for static artifact reconciliation; runtime remains blocked under ARCH-04 | Document 13's 2026-10-09 addendum reports the available DBML, Laravel migration, validation SQL and schema review statically reconciled at 55 tables / 89 FKs. Preserve old counts only when explicitly labelled historical/superseded; clean-MySQL execution remains a separate gate. |
| ARCH-03 | Document 14 contained older 52-table and pre-Gate-11 gap statements alongside newer gate-closure notes | Partial — current status/count snapshots corrected; legacy-section sweep remains open | Keep the current contract summary at 55 tables / 89 FKs and canonical `/me/push-devices` endpoints. Mark each remaining obsolete count/gap statement as historical/superseded without deleting useful audit history. |
| ARCH-04 | Clean-MySQL runtime validation remains unchecked in Document 14; Document 13 explicitly says the prior environment lacked a MySQL server/client | Blocked on runtime environment | Execute the regenerated migration and validation SQL against a clean supported MySQL instance; capture actual command output and results. Do not mark PASS without evidence. |
| ARCH-05 | Final OpenAPI 3.1 artifact has not been generated/audited after the final schema and enum gates | Blocked by ARCH-04 runtime validation | Generate only after schema artifacts are regenerated and runtime/contract prerequisites are met; validate endpoints, request/response schemas, enums, errors, auth, and device registration paths. |
| ARCH-06 | Device-token persistence must agree across Documents 13, 14, 17, 18, 19 and 22 | Decision aligned; generated artifacts pending | Use `user_push_devices`, user-scoped authorization, safe metadata-only responses, and FCM V1. Never return raw tokens in ordinary API responses. |
| ARCH-07 | Public listing exposure must agree across Documents 15, 16, 20, 21 and 23 | Policy aligned; implementation tests pending | Verify premium exact location/contact fields are absent from public API, HTML, metadata, JSON-LD, sitemap, `llms.txt`, caches and public media. |
| ARCH-08 | Expo SDK / React Native version baseline must remain synchronized with Document 10 | Documentation aligned; install/build verification pending | Pin versions and verify the selected Expo SDK compatibility matrix during implementation. |
| ARCH-09 | SEO crawl policy and security boundaries | Policy aligned; implementation tests pending | Test robots output, staging noindex, canonical redirects, sitemap lifecycle, `llms.txt`, structured data and protected-field exclusion. |

## 4. Current database baseline authority

The latest closed database decision gates in Document 13 establish **55 tables / 89 declared foreign-key relationships** after Gate #11 added `user_push_devices`. Later Gates #12–#14 do not add tables or foreign keys. The older 52-table / 80-FK or 49-table baselines are historical and must not be used to regenerate current artifacts.

The available static artifacts have been inspected and match the 55-table / 89-FK decision baseline. This is **not** proof that the migration runs successfully on clean MySQL; runtime validation remains an independent release gate.

## 5. Release gates — do not skip

1. Run the statically reconciled DBML/migration/validation SQL set against a clean MySQL database; record actual MySQL version, commands, exit codes, and table/FK counts.
2. Resolve every runtime failure, regenerate affected artifacts if required, and rerun from a clean database.
3. Generate and validate OpenAPI 3.1 against the runtime-validated schema and approved public API enum registry.
4. Run cross-client contract tests for Next.js and React Native/Expo; test auth, entitlement, listing lifecycle, media privacy, search visibility, notification tokens and SEO output.
5. Only then change the runtime/contract gate statuses to PASS and mark the architecture baseline implementation-ready.

## 6. Audit limitation

The available Library artifact set was inspected through its indexed file content; raw-byte materialization was unavailable in this session. Static counts, current enum markers, and the `user_push_devices.user_id` FK were checked from the available content. No clean MySQL server execution was performed in this review, so the runtime gate remains pending. The artifacts must be run, not merely inspected, before the database gate can pass.

## 7. Source documents

- [04. Users, Roles & Permissions](../01%20PRODUCT%20DEFINITION/04%20Users,%20Roles%20&%20Permissions%203e29628c857d815e86d2e929507c0913.md)
- [10. Technology Stack](10%20Technology%20Stack%203e59628c857d81cebba8d70b8817846d.md)
- [13. Database Architecture & Data Model](13%20Database%20Architecture%20&%20Data%20Model%203e99628c857d81e1ab70e3b26d66c38a.md)
- [14. API Specification](14%20API%20Specification%203ed9628c857d81a6b7e7ea0697cef4d1.md)
- [15. Frontend Architecture](15%20Frontend%20Architecture%203ef9628c857d817a8dacca532ebcd575.md)
- [16. Backend Architecture](16%20Backend%20Architecture%203ef9628c857d81ea99d2fd71307f1dd6.md)
- [17. Mobile Application Architecture](17%20Mobile%20Application%20Architecture%203f39628c857d81cf85dced2f9bbb9fca.md)
- [18. Authentication & Authorization](18%20Authentication%20&%20Authorization%203f39628c857d81d680bdc90722214ae8.md)
- [19. Security Architecture](19%20Security%20Architecture%203f39628c857d816f9d21d587cc54dc4f.md)
- [20. Media & File Storage](20%20Media%20&%20File%20Storage%203f39628c857d81ecb39ee99dc8d09625.md)
- [21. Search Architecture](21%20Search%20Architecture%203f39628c857d81ac909ad47b747dd736.md)
- [22. Notification System](22%20Notification%20System%203f39628c857d816bb696de959b5420ce.md)
- [23. SEO Architecture](23%20SEO%20Architecture%203f39628c857d8196b2b2f65736197186.md)

## 8. Expanded contract audit — findings from 2026-10-09 review

The following findings are reconciled against the connected Notion pages. Closed means text was changed and verified; Decision/implementation open means the point still requires a product/technical decision, schema work, or runtime tests.

| ID | Area | Required resolution | Status |
| --- | --- | --- | --- |
| X-01 | Web authentication | Doc 18 and the 2026-10-09 ADR-002 addendum specify Firebase Bearer ID tokens to Laravel and prohibit a Laravel marketplace session/cookie/CSRF flow for the bearer-token API. | Closed in docs — ADR-002 addendum confirms bearer-only marketplace API; implementation/configuration tests pending |
| X-02 | Public route convention | Doc 15 was changed to Doc 23's /listing/{slug}-{public-id}, /category/{slug}, /location/{slug}, /business/{slug} convention. Doc 14 resolves listings by stable public ID and returns the current canonical slug. Location slug source/resolution remains open; a dedicated listing slug-history table is not required for basic current-slug redirects. | Partial / open |
| X-03 | Lifecycle vocabulary | Docs 15 and 17 state the final API enum and distinguish removal/deletion from a client-assignable state. Doc 16 was updated to avoid treating removed as an enum. Audit remaining older lifecycle prose and schema enums. | Partial / open |
| X-04 | Listing creation | Doc 17 now requires category + listing type in POST /listings, then reads the created representation and GET /listings/{id}/readiness. | Closed in Doc 17; tests pending |
| X-05 | Push token provider | Docs 10 and 17 specify FCM native device tokens for V1; Expo Notifications may be a client library, not the accepted Expo push-token provider. iOS implementation must use a compatible Firebase Messaging/native token path or the API contract must be amended. | Decision stated; platform build verification open |
| X-06 | Payments | Docs 14, 16 and 17 consistently specify manual-submission + admin review only for V1. Gateway initiation, redirects, callbacks and webhooks are future-phase and must not ship as active V1 behavior. | Closed in documentation — Doc 16 and Doc 14 both specify manual submission/admin review for V1; gateway initiation/callbacks/webhooks are future-phase. Implementation and payment-state tests remain pending. |
| X-07 | Transactional outbox | Doc 16 and Doc 22 require an outbox_events row in the same transaction and an idempotent relay worker; dispatch-after-commit alone is insufficient. | Text updated; implementation/test open |
| X-08 | If-Match | Doc 16 follows Doc 14: optional in V1; supplied stale ETag returns 412; missing header follows documented last-write-wins. Mandatory 428 is not adopted. | Text updated; verify all clients |
| X-09 | Idempotency persistence | Doc 16 identifies MySQL api_idempotency_keys as authoritative; Redis is only a lock/cache accelerator. | Text updated; implementation/test open |
| X-10 | SSR and IP rate limits | Doc 14 addendum requires trusted-proxy configuration, no spoofed forwarded headers, and end-user quota testing through the proxy chain. | Contract note added; deployment test open |
| X-11 | Time zones | Doc 22 sets APP_TIMEZONE=UTC; Asia/Kathmandu is only for local display/scheduling/quiet-hour interpretation. | Text updated; configuration test open |
| X-12 | Admin MFA | Docs 10 and 18 say MFA is required for privileged admin access, matching Doc 19. Schema/Filament enforcement tests remain open. | Text updated; implementation/test open |
| X-13 | Video media | Doc 20 specifies one MP4 H.264/AAC video, max 50 MB/60 seconds, async processing, poster frame, range requests, and proxy/PHP limits. End-to-end transcoding and range delivery remain unverified. | Text updated; implementation/test open |
| X-14 | Upload model and limits | Doc 20 specifies direct multipart V1, JPEG/PNG/WebP, max 20 images, 21 total items including at most one video, 10 MB/image, and no plan-based media-limit uplift. Reconcile schema metadata and Doc 14 endpoint definitions. | Text updated; contract/schema verification open |
| X-15 | ULID storage paths | Backend doc states BIGINT internal PK + public_id ULID route key and warns not to assume HasUlids handles a separate column automatically. Public object keys/URLs must avoid sequential IDs. | Partial / implementation tests open |
| X-16 | Missing modules/use cases | Businesses/members, verification, user blocking, contact reveal, conversation read cursor, account deactivate/reactivate/delete-cancel, and notification preferences require a traceability matrix against Docs 05/08/14/13 and UI docs. | Open |
| X-17 | Search scope | Radius/distance, autocomplete, featured ordering, saved searches, and location= must not be promised unless present in the API contract. Use province/district/municipality/etc. parameters. Test Devanagari full-text tokenization and two-character queries early on MySQL 9.7; consider ngram only after measured failure and compatible-engine verification. | Open |
| X-18 | SEO feed/API | Next.js sitemap generation from existing documented public API/reference responses is now the V1 decision; opaque cursors remain internal and are not crawlable page numbers. See CR-02/CR-03 above. Location slug resolution remains open under CR-01. | Decision closed; implementation tests pending |
| X-19 | Expired/unavailable listing | Doc 23 requires expires_at > UTC_NOW() at public read/search/index/render time, a non-disclosing 404 for expired/unavailable public detail, authorized owner views, and cache TTL/invalidation that cannot outlive expiry. | Closed in documentation — Doc 23 expiry/404 behavior is specified; runtime and cache tests pending |
| X-20 | Notification endpoints/locales | Doc 22 must not promise mark-all-read, multi-read, unread-count endpoints unless Doc 14 defines them. Define V1 language fallback/template locale and defer campaigns, quiet hours, browser push, and WhatsApp if not explicitly approved. | Open |
| X-21 | OpenAPI generation strategy | Doc 16 BE-PR-003 and the 2026-10-09 addendum select contract-first OpenAPI 3.1 as the public contract, with Laravel request/response tests validating implementation. Generate the final artifact only after schema/runtime gates close. | Decision closed; artifact generation and validation pending |
| X-22 | Version pinning | Doc 16 updated from PHP 8.4+/MySQL 8.x to PHP 8.5.x and MySQL 9.7.x LTS-compatible baseline. Validate exact installable production versions before lockfiles/CI. | Text updated; environment validation open |
| X-23 | Upstream standards | Current fetches of Documents 10 and 12 already specify MySQL-first V1 and state that Meilisearch is not a V1 dependency. Treat any older audit note claiming otherwise as stale. Continue to ensure examples do not introduce non-authoritative physical table names. | Open |
| X-24 | Schema/media/notification/admin gaps | Review media, verification evidence, payment proof references, business logo/cover, notification dedupe/classification/expiry/locale/template fields, and admin MFA persistence against actual V1 needs. Add columns/tables only through explicit schema-gate review; otherwise trim docs to capabilities supported by current schema. | Open |
| X-25 | OTP abuse protection | Doc 18 now states Firebase owns OTP expiry/attempt/resend controls and recommends Firebase App Check and Nepal (+977) SMS restriction where supported. Verify actual Firebase project settings and test SMS-pumping defenses; Laravel must not implement a second OTP verifier. | Text updated; configuration/test open |
| X-26 | Notification V1 scope | Core V1 scope is transactional/security notifications, preferences, in-app state and approved FCM push. Campaigns, quiet hours, browser push and WhatsApp are post-V1 unless separately accepted. Doc 22 now states this boundary; endpoint/locale and schema compatibility findings remain tracked in X-20 and X-24. | Scope aligned in docs; endpoint/locale/schema gates remain open |
| X-27 | Contact reveal | Docs 08 and 14 both use POST /listings/{id}/contact-reveals as the canonical contact-disclosure command; no GET /listings/{id}/contact route remains in the current business-rule page or API inventory. Verify the generated OpenAPI contract before release. | Closed in current documentation; generated OpenAPI verification pending |
| X-28 | Slug history/location slugs | No verified slug-history table or location public-slug contract was established in the reviewed schema excerpts. Do not promise redirects until persistence/resolution is designed. | Open |
| X-29 | Active vs Draft status | Documents 15–23 are current architecture design baselines, not evidence of executable readiness. Their headers now clarify that Active means authoritative design rather than release readiness; final OpenAPI 3.1, clean-MySQL migration/runtime tests and component-specific gates remain required. | Closed in documentation; implementation gates remain open |

## 9. Edits applied in this audit pass

- Doc 18: bearer-only Firebase marketplace API flow; Firebase-owned OTP controls; mandatory admin MFA wording.
- Doc 10: required admin MFA; FCM native device token wording.
- Doc 15: canonical public route convention; final lifecycle enum; search query location parameters.
- Doc 16: PHP/MySQL baseline; transactional outbox; MySQL idempotency authority; optional If-Match; module-first architecture; explicit ULID route-key guidance; removed state no longer treated as a public enum.
- Doc 17: FCM native-token wording; listing creation/readiness flow; V1 manual payment only; final lifecycle enum.
- Doc 20: direct multipart upload; approved image formats/limits; one-video processing and delivery requirements; fixed media limits independent of subscription tier.
- Doc 22: UTC canonical timezone; mandatory transactional outbox wording.
- Doc 14: current database/API reconciliation addenda for 55 tables/89 FKs, push devices, contact reveal, public routes, upload model, subscription endpoint semantics, concurrency, SSR rate limits, SEO feed gap, outbox and idempotency.

These are documented edits, not runtime proof. Schema, OpenAPI, production configuration, media processing, and end-to-end checks remain open until evidence is captured.

## 10. Audit-register amendments — verified after row-level review

- **X-21 OpenAPI tooling:** The decision is already closed in Document 16 BE-PR-003: contract-first. Only generation, schema validation, and CI contract tests remain pending.
- **X-27 Contact reveal:** The current Document 14 endpoint inventory contains POST /listings/{id}/contact-reveals. A GET /listings/{id}/contact route was not found in the current endpoint table; the addendum records it as non-canonical. Check Document 08 and generated OpenAPI for any stale reference before release.
- **X-28 Slugs:** Listing canonical redirects are now specified through the stable public_id in /listing/{slug}-{public-id} and GET /listings/by-public-id/{public_id}; a separate listing slug-history table is not required for basic canonical redirects. Location landing pages still need a stable slug source/resolver because the current location schema uses integer IDs.
- **X-19 Expired listing behavior:** Document 23 now requires expiry checks at read time across public detail, search, recommendations, sitemap, structured data, SSR, and caches; V1 public expired/temporarily unavailable detail routes return a non-disclosing 404. 410 is reserved for irreversible permanent removal.
- **Document 12 status and search standards:** its header and final status now both say Active; the Meilisearch-specific V1 standard is replaced by MySQL-first V1 rules, and sample physical table examples were corrected.
- **Document 13 verification state:** the current schema text now uses pending, approved, rejected, expired, revoked, canceled, matching Document 14's final registry. Generated migrations/SQL still require regeneration and runtime validation.

## Documentation-Wide Audit Pass — 2026-10-15

**Scope:** Documentation foundation, canonical sequence, numbered Documents 01–28, supporting registers/catalogues, and ADR register consistency. This is a documentation review; it does not substitute for runtime, schema, OpenAPI, deployment, or production evidence.

### Corrections applied

- Updated **00. Project Documentation Guide** to align its hierarchy and next-step guidance with the current 00–32 sequence, define common document-status semantics, distinguish document status from decision and implementation status, and clarify that ADRs are indexed by 00.3 rather than being a separate Document 33.
- Updated **00.1 Documentation & SDLC Framework** to align its lifecycle terminology with the common status convention.
- Updated **Documentation Sequence** with the supporting-register/catalogue inventory. The planned-entry note for Documents 29–32 was subsequently corrected on 2026-10-18 after confirming that all four canonical pages exist.
- Updated **00.3 Decision / ADR Register** summaries for ADR-001 through ADR-008 so they describe accepted decisions instead of leaving the entries worded as unanswered questions.
- Standardized current status wording for Documents 14 and 26–28. “Active” denotes the authoritative current document baseline; it does not mean the implementation is complete.
- Added implementation-gate clarification to Documents 17–23 to keep architecture status distinct from release readiness.

### Open audit items

| ID | Finding | Required closure | Status |
| --- | --- | --- | --- |
| DOC-01 | **Resolved — canonical taxonomy confirmed 2026-10-16.** CAT-002 is “Mobile & Electronics”; Television remains subcategory CAT-002-05. The 25-category / 372-subcategory baseline and all assigned CAT IDs are preserved. | Keep the master catalogue and detailed page aligned with this decision. Continue CAT-002 attribute/option reconciliation separately; do not infer seed readiness from taxonomy approval. | Closed — taxonomy decision recorded; detail completeness remains open under DOC-07 |
| DOC-02 | **Document 14 is an active API design baseline, but the final generated OpenAPI 3.1 artifact and clean-MySQL migration/runtime validation remain gated.** | The available schema artifacts are statically reconciled at 55 tables / 89 FKs. Execute the migration and validation SQL on a clean supported MySQL instance, capture the actual output, then generate and audit the final OpenAPI 3.1 artifact against that validated schema before release-readiness sign-off. | Open — clean-MySQL runtime and final OpenAPI gate |
| DOC-03 | **Resolved 2026-10-18 — Documents 29–32 exist as canonical numbered pages.** The Documentation Sequence governance note was corrected to reflect their creation. Archived similarly named pages remain historical and must not be treated as current authority without review. | Keep the canonical sequence linked to the current numbered pages. During the remaining inventory pass, verify that each page has the expected content, metadata, cross-references, and no stale status claims; retain archived pages as history. | Closed — canonical pages exist and sequence note corrected; detailed page audit remains in scope |
| DOC-04 | **Archived legacy pages remain visible by title with an “ARCHIVED —” prefix.** They may contain useful history but can be mistaken for active authority if linked without context. | Preserve them as history; ensure canonical current documents are linked from the sequence and do not reactivate duplicate pages without an explicit decision. | Closed for baseline policy — keep monitoring for drift |
| DOC-05 | **Document metadata and presentation styles differ across older pages.** Several documents use a metadata table, while others use key-value headers; some have older review dates. | Apply the common required metadata fields during the detailed per-document review. Update Last Reviewed only when the document's substantive content has actually been reviewed; do not change review dates solely to make them look current. | Open — detailed normalization |

### Audit interpretation

- **Active document:** current authoritative baseline.
- **Accepted ADR:** approved architectural decision; implementation may still be Not Started, In Progress, Blocked, or Validated.
- **Implementation gate open:** a required artifact, schema, test, or operational proof is still missing.
- **Archived page:** historical reference; not the default source of current truth.

The project-wide audit is not closed until DOC-01 is resolved or explicitly accepted as-is, DOC-02 has the required evidence, the detailed metadata and cross-document checks are completed, and every remaining conflict is either corrected or recorded with a responsible owner and closure criterion.

## Follow-up Audit Pass — 2026-10-16

This follow-up records issues verified by reading the canonical catalogue index, CAT-001–CAT-005 detail pages, and the traceability matrix. On 2026-10-16 the project owner confirmed CAT-002 = Mobile & Electronics and Television = CAT-002-05; DOC-01 is closed with existing IDs preserved. This does not certify catalogue seed readiness or database/OpenAPI runtime gates.

### Corrections applied

- **CAT-003 detail page:** changed the section label from “Proposed Subcategories” to “Approved Subcategories” to match its approved status and the 13.1 catalogue baseline.
- **00.4 Traceability Matrix:** corrected the UC-002 row note. KB-FR-002 through KB-FR-005 already have stable IDs in 03.1; the matrix groups them under UC-002 rather than lacking IDs.
- **03.1 Requirements Register:** corrected KB-FR-003 to specify client-side Firebase sign-out and a stateless Laravel marketplace API, removing ambiguous wording that could imply an application session or immediate server-side token invalidation.
- **Schema/API gate tracking:** updated ARCH-02 to reflect the documented static reconciliation of the available 55-table / 89-FK artifacts; updated ARCH-03 to show the Document 14 historical-text sweep is only partial; clarified that final OpenAPI generation and runtime sign-off remain blocked by clean-MySQL validation.

### Newly verified findings

| ID | Finding | Required closure | Status |
| --- | --- | --- | --- |
| DOC-06 | DOC-01 resolution — 2026-10-16: the project owner confirmed option A. CAT-002 remains “Mobile & Electronics” and Television remains CAT-002-05. No category IDs or hierarchy are changed by this decision. | Preserve current CAT IDs. Continue the separate CAT-002 detailed-attribute/option reconciliation before generating final category seeds. | Closed — decision confirmed; DOC-07 remains open |
| DOC-07 | CAT-002 now enumerates all 96 master attribute identifiers (the 69 identifiers missing from the original detail tables have been added) and has been re-audited against Phase 3B §43–§44. The 2026-10-21 audit applied only unambiguous approved semantic fallbacks; the page still contains 48 required/filterable/searchable flag cells across 16 attributes, eight unresolved product-specific option sets, unresolved measurement-unit/range decisions, and pending applicability/ordering validation. | Obtain catalogue-owner decisions for the listed flags, options, and measurement rules; preserve CAT-002 = Mobile & Electronics and CAT-002-05 = Television; then validate attribute and listing-type applicability before seed generation. Do not infer missing metadata. | Partially reconciled — identifier coverage complete; attribute metadata decisions remain open; NOT seed-ready |
| DOC-08 | Document metadata and catalogue presentation are not yet normalized consistently. CAT-001 and CAT-002 now include the shared Project and Parent fields, but still lack a Last Reviewed field; other catalogue pages also differ in metadata and review-date conventions. | Normalize metadata only after each page receives substantive review. Do not advance Last Reviewed dates just to make pages appear current. Keep catalogue approval state separate from implementation/seed readiness. | Open — detailed review required |

### Scope and release-gate interpretation

- The approved catalogue index is not sufficient by itself to prove every child catalogue is complete or seed-ready.
- The CAT-001–CAT-005 pass found at least one explicit status-label mismatch (corrected above) and one incomplete detailed catalogue (CAT-002; still open).
- The full documentation audit remains open until the taxonomy decision, catalogue completeness, remaining metadata/cross-reference review, and required schema/OpenAPI/runtime evidence are closed or explicitly accepted with owners and exit criteria.

## Follow-up Audit Pass — 2026-10-18

### Corrections applied

- **Documentation Sequence:** corrected the governance note to state that Documents 29–32 exist as canonical numbered pages.
- **DOC-03:** closed the obsolete claim that Documents 29–32 were still planned. The canonical-page existence issue is closed; substantive page-by-page review and metadata checks remain in the overall audit scope.

### Newly verified findings

| ID | Finding | Required closure | Status |
| --- | --- | --- | --- |
| DOC-09 | **Nepali/English search normalization remains incompletely specified.** Document 21 requires Nepali and English search and describes controlled transliteration/synonym handling, but also retains an unchecked item stating that normalization is not yet defined. It separately flags MySQL FULLTEXT behavior for two-character queries and Devanagari tokenization as an early validation gate. | Define the V1 normalization and matching contract: Unicode normalization, Devanagari handling, Romanized Nepali/transliteration scope, synonym policy, token-length behavior, mixed-script queries, and expected zero-result behavior. Create representative acceptance tests and run them against the pinned MySQL 9.7.x configuration. If native FULLTEXT does not meet the cases, record an explicit implementation decision before changing query behavior. | Open — specification and runtime search validation required |

### Current audit boundary

This pass verifies specific statements in the connected Notion pages; it is not yet a complete line-by-line audit of all Documents 00–32. Keep schema/runtime, OpenAPI generation, location slug resolution, payment-proof integrity, catalogue completeness, and remaining metadata/cross-reference checks open until their own closure evidence is recorded.

## Product Definition Audit — 2026-10-18 (Documents 01–08)

**Scope reviewed:** Documents 01–08, Requirements Register 03.1, and Traceability Matrix 00.4. This is a targeted cross-document pass, not a complete line-by-line sign-off of every paragraph or visual diagram.

### Confirmed correction applied

- **Document 06 — User Flows:** UF-006, UF-007 and S-01 previously retained stale wording that treated moderation-before-publication as an open decision or allowed a branch to direct publication. Document 08 and the traceability matrix already establish that every listing must pass Review/moderation before publication, and that edits to a Published listing return it to Review. Document 06 was updated to reflect the approved mandatory-review rule and the Draft → Review → Published ↔ Paused → Expired → Archived baseline. This is a documentation correction; the linked Whimsical diagrams have not yet been independently checked or updated.

### Newly verified finding

| ID | Finding | Required closure | Status |
| --- | --- | --- | --- |
| DOC-10 | **Flow-definition drift — mandatory listing review.** Documents 08 and 00.4 establish mandatory Review/moderation before publication, but Document 06 previously marked this rule as an open decision in UF-006/UF-007 and its flow steps allowed direct publication when review was not required. The written Notion flow definitions are now corrected. | Review the linked Whimsical diagrams for UF-006, UF-007 and S-01 and update them to prohibit direct publication, show review outcomes (approve, reject, return for correction), and require a Published-listing edit to return to Review. Then verify UC ↔ UF ↔ business-rule consistency and record evidence. Do not treat Notion text correction as proof that diagrams or runtime behavior are aligned. | Partially closed — Notion flow text corrected; Whimsical and implementation verification remain open |

### Product Definition pass observations

- Documents 01–04 and 08 broadly align on the product direction, Nepal location concepts, one identity with multiple capabilities, server-enforced permissions, privacy/consent, and the distinction between product roles and verification states.
- Document 02 keeps full online payment processing out of the initial release; Document 08's subscription/payment rules are conditional and do not by themselves make full checkout a V1 requirement. Exact commercial terms remain open as documented.
- Document 03 uses broad capability language for communication and future expansion; the V1 contact behavior must continue to follow Document 08 and the API/security baselines rather than being interpreted as a promise of every future communication channel.
- Search normalization and Nepal-script behavior remain tracked under DOC-09. Location SEO slug resolution, payment-proof integrity, catalogue completeness, schema/runtime validation, and final OpenAPI generation remain separate open gates.
- Metadata/review-date normalization remains open under DOC-05. Last Reviewed dates must only be advanced after substantive review.

### Scope boundary

This pass does not certify all acceptance criteria, every use-case/flow mapping, UX completeness, Whimsical diagram correctness, database compatibility, or implementation readiness. Continue with a detailed cross-check of Documents 05–08 against the requirements register, traceability matrix, API, and architecture before closing the Product Definition phase.

### Additional Product Scope Finding — 2026-10-18

| ID | Finding | Required closure | Status |
| --- | --- | --- | --- |
| DOC-11 | **MVP-versus-monetization scope conflict: paid entitlements.** Document 02 places seller/business subscriptions, restricted-information access and related monetization in Stage 4, while Document 08 labels exact-location and direct-contact entitlements as protected paid capabilities in its V1 rules. Document 05 also includes subscription use cases but says implementation remains subject to roadmap scope. These statements do not establish unambiguously whether the Marketplace MVP must ship paid entitlement enforcement or whether the rules describe a future capability. | Make an explicit product-owner decision: (A) include a minimal paid-entitlement/payment flow in the MVP, or (B) defer paid entitlement enforcement to the monetization stage. If deferred, keep the privacy/consent restrictions active in V1 but specify a safe free-V1 contact/location behavior and remove any requirement that users purchase an entitlement before access unless another approved policy justifies it. If included, update Document 02 roadmap/scope and document payment verification, failure states, entitlement lifecycle, provider choice, UX and acceptance tests. Reconcile Documents 02, 05, 07, 08, 13, 14, 17 and 22 before implementation. | Open — product decision required; do not infer a monetization release commitment from the business rules alone |

### Additional correction applied

- **Document 07 — UX/UI Specification:** its open-decision list previously repeated authentication provider, search-engine strategy, and contact/exact-location visibility as unresolved even though these are governed by accepted authentication/search decisions and Document 08. The list was corrected to distinguish those established baselines from remaining UX/product decisions. Storage, mobile framework, commercial scope, category-field completeness and visual design remain subject to their authoritative decisions and review.

### DOC-12 — Visitor contact permission is underspecified

**Finding:** Document 04's permission matrix labels Visitor → Contact poster as “Controlled,” while Document 08 defines in-app conversation initiation for an authenticated user and direct contact-detail disclosure for an authenticated, entitled caller with seller consent. The intended visitor behavior is therefore not explicit in the role matrix.

**Required closure:** Align Document 04 and UX/API behavior: explicitly state whether visitors may only view a contact prompt, must sign in before starting in-app contact, and cannot access protected phone/email or exact location. Keep any allowed public contact channel separate from protected contact-detail disclosure and test each role/access state.

**Status:** Open — role matrix and UX/API acceptance criteria need explicit alignment.

</tr>

## Technical Definition Audit — 2026-10-18 (Documents 09–23, targeted pass)

**Scope reviewed:** Documents 09–23 and relevant ADRs, including the current Software Architecture, Technology Stack, Frontend/Backend/Mobile architectures, Security, Media, Search, SEO, Notification System, and ADR-002/ADR-005/ADR-006/ADR-007. This is a targeted cross-document pass, not a full line-by-line or runtime sign-off.

### DOC-13 — Authentication OTP ownership versus notification SMS wording

**Finding:** ADR-002 and Document 19 assign marketplace authentication OTP delivery/verification to Firebase Authentication and prohibit a second Laravel OTP verifier. ADR-007 and Document 22 previously used ambiguous wording (“SMS/OTP” and “separate SMS-provider path” for OTP/communications), which could be read as allowing the notification SMS adapter to send or verify sign-in/recovery OTPs.

**Correction applied:** Added explicit boundary clarifications to ADR-007 and Document 22 on 2026-10-18: Firebase Authentication exclusively owns marketplace sign-in/recovery OTP; separate notification SMS is for approved transactional/application messages and must not create a second authentication-verification path.

**Required closure:** Sweep older occurrences of “SMS/OTP” in ADR-007 and Document 22 and ensure each is either explicitly scoped to Firebase Authentication or rewritten as transactional SMS. Verify the final authentication and notification flows in API/security tests and provider configuration before release.

**Status:** Partially closed — clarifying addenda added; older wording sweep and implementation/configuration evidence remain open.

### Technical Definition pass observations

- Documents 09–23 consistently establish Firebase Bearer ID tokens for marketplace users, a separate Laravel/Filament admin identity boundary, MySQL as transactional source of truth, MySQL-first V1 search, local V1 media storage behind an abstraction, Redis-backed queues/cache/locks with a transactional outbox, manual payment submission/admin review, and FCM native device tokens for V1.
- Document 13 and Document 14 continue to mark the 55-table / 89-FK artifact set as statically reconciled, not runtime-validated. Clean-MySQL execution remains open; final OpenAPI 3.1 generation/contract testing remains gated on the schema/runtime gate.
- Location SEO slug source/resolution remains an explicit blocker: public `/location/{slug}` is planned, but the current physical location model does not establish the canonical slug source/resolver. Do not generate location SEO routes or sitemap entries from integer IDs.
- Payment proof remains a media public ID/reference stored in a VARCHAR, with Laravel ownership/type/exposure validation; database-level media referential integrity remains a schema decision. Do not store raw paths, storage keys, signed URLs, or binary proof in that field.
- Document 20 describes security/processing concepts (classification, checksum, detected MIME, generic target association, quarantine) that are not all represented by dedicated fields in Document 13. V1 must stay within current schema guarantees or pass an approved schema gate before relying on those guarantees.
- Search remains MySQL-first but must pass the documented representative Nepali/English, two-character, mixed-script and zero-result validation gate. DOC-09 remains open.
- Admin MFA is mandatory, but secure MFA enrollment/recovery persistence is not established by the current `admins` schema. Select a compatible implementation or approve schema changes, then verify enforcement and tests.
- The notification architecture says a locale policy must be selected and warns that notification locale/classification/expiry/dedupe columns and a templates table are not established in the current schema. Decide and document the V1 locale/fallback and idempotency guarantee; add schema only if required by that decision.

**Readiness conclusion:** This pass does not close technical implementation gates. Do not begin feature coding until product decisions DOC-11/DOC-12 are resolved or explicitly deferred, the schema and OpenAPI gates are completed, and the relevant component-specific acceptance tests are defined.

## Engineering & Operations Audit — 2026-10-18 (Documents 24–32, targeted pass)

**Scope reviewed:** Documents 24–32, including Testing & QA, DevOps & CI/CD, Infrastructure & Deployment, Monitoring/Logging/Backup, Git & GitHub Workflow, Developer Onboarding, Admin & Operations, Release Management, and Incident & Troubleshooting. This was a targeted cross-reference/readiness pass, not a complete procedural execution or line-by-line acceptance audit.

### DOC-14 — Release Management referenced incorrect architecture document numbers

**Finding:** Document 31's authority section previously identified Document 25 as Security Architecture, Document 26 as Database Architecture, and Document 27 as Deployment & Infrastructure. The canonical sequence actually assigns Document 19 to Security Architecture, Document 13 to Database Architecture & Data Model, and Document 26 to Infrastructure & Deployment. The wrong references could send implementers/release owners to unrelated documents.

**Correction applied and verified:** Document 31 §3 now references Document 19 for security, Document 13 for database authority, and Document 26 for deployment/infrastructure. Document 24 remains Testing & QA, and Document 28 remains Git & GitHub Workflow.

**Status:** Closed — corrected in Document 31 and verified by fetching the updated section.

### Engineering & Operations pass observations

- Documents 24–32 consistently distinguish a documented process baseline from proof that CI/CD, production monitoring, alerting, backups, recovery tooling, access controls, or deployment runbooks are actually configured. Do not treat a checklist as operational evidence.
- Documents 24, 25 and 31 correctly keep clean-MySQL validation and final OpenAPI 3.1 contract validation as gates rather than claiming completion.
- Documents 29–32 exist as canonical numbered pages and their authority/role boundaries generally point to the relevant operational guides. Named owners, repository settings, CI enforcement, escalation contacts, and provider-specific procedures still require verification against the real implementation/environment.
- Document 27's backup/restore standard correctly requires restore testing; a successful backup job alone is not proof of recoverability.

**Readiness conclusion:** Documentation is improving, but the complete 00–32 audit remains open. Before coding/release, finish the remaining cross-document review, resolve or explicitly defer DOC-11 (MVP versus later paid entitlements) and DOC-12 (visitor contact behavior), close DOC-09 search normalization, and complete the schema/runtime/OpenAPI gates with evidence.

# Final Documentation Audit & Implementation-Readiness Decision — 2026-10-18

## 1. Overall decision

**Documentation architecture: CONDITIONAL PASS. Implementation readiness: NOT READY.** The documentation is substantial and has a coherent baseline, but unresolved product decisions and evidence gates prevent a responsible start of feature implementation. This decision does not mean the whole documentation set has been exhaustively validated line by line, nor that any runtime or production control has passed.

## 2. Final gate register

| Gate | Current state | Required evidence/action | Owner |
| --- | --- | --- | --- |
| DOC-09 — Nepali/English search normalization | Contract defined; validation open | Document 21 now defines NFC/whitespace/Latin-case behavior, preserves Devanagari, defers automatic transliteration, and requires short-query and visibility tests. Run the tests on the supported MySQL version and record actual evidence before closing. | Backend + QA |
| DOC-11 — paid entitlements in MVP vs later monetization | Closed — deferred to Stage 4 | Documents 02, 04, 05, 07, 08, 14, 22 and the Requirements Register now define paid plans and paid entitlement enforcement as future-phase scope, not MVP acceptance. | Product owner |
| DOC-12 — visitor contact behavior | Closed — V1 policy approved | Visitors browse public listings but must authenticate before starting in-app conversations. V1 does not disclose protected direct contact details or exact residential location to non-owners. | Product + UX + Backend |
| DOC-13 — authentication OTP ownership | Partially closed | Clarifications added to ADR-007 and Document 22; sweep all remaining legacy “SMS/OTP” wording and verify Firebase provider configuration and tests. | Security + Backend |
| DOC-14 — Release Management cross-references | Closed | Corrected Document 31 authority references and verified the updated section. | Documentation owner |
| Location SEO slug source/resolver | Open | Approve unique, stable slug storage/generation, canonical resolution, rename behavior and API/schema implications across Documents 13, 14 and 23. No location SEO/sitemap entries before closure. | Product + Backend + SEO |
| Payment proof referential integrity | Open schema decision | Decide whether application-level media-public-ID validation is sufficient or a nullable media FK is required; never persist raw path, storage key, signed URL or binary proof in the reference field. | Backend + Data owner |
| Database runtime gate | Not run / no evidence recorded here | Run current migration and validation SQL on a clean supported MySQL instance; record exact MySQL version, command, exit code, and table/FK/enum checks. Static 55-table/89-FK reconciliation is not runtime validation. | Backend + QA |
| OpenAPI 3.1 gate | Pending database/runtime gate | Generate the canonical artifact from the approved API baseline after schema/runtime pass; validate syntax, routes, schemas, auth, error contracts and contract tests. Record artifact revision and results. | Backend + QA |
| Admin MFA | Design required; implementation unverified | Select a Laravel/Filament-compatible mechanism with secure secret storage, enrollment, challenge, recovery and deny-by-default enforcement; approve schema changes only if required. | Security + Backend |
| Media capability/schema alignment | Open implementation boundary | Keep V1 within fields actually represented by Document 13 or approve a schema gate for classification, detected MIME, checksum, quarantine and generic target association. | Backend + Security |
| Notification locale/idempotency | Open design/schema boundary | Decide V1 locale/fallback and delivery deduplication guarantees. Do not rely on locale, expiry, classification, template or dedupe columns absent from the approved physical schema. | Product + Backend |
| CAT-002 detailed catalogue | Approved taxonomy; not seed-ready | Complete the subcategory attribute review and required/optional/filterable/multi-value validation; run catalogue validation before generating seed data. CAT-002 remains Mobile & Electronics and Television remains CAT-002-05. | Product + Data owner |
| Whimsical flow diagrams | Not verified | Update/verify UF-006, UF-007 and S-01 to match mandatory review before publication and edit-to-Review behavior. Notion text correction alone does not close the diagram gate. | Product + UX |
| Operational readiness | Documentation baseline only | Verify repository protections, CI/CD, secrets, admin access, monitoring/alerts, backup jobs and a successful restore test against the actual environment. | Engineering + Operations |

## 3. Required product decisions before feature coding

1. **Paid entitlements:** recommended default is to defer paid entitlements and monetization enforcement from the Marketplace MVP if Document 02's Stage 4 roadmap is the intended commitment. If chosen, V1 still needs an explicit privacy-safe contact/location policy; do not silently expose protected information or imply that a future paid gate already exists. Product owner approval is required.
2. **Visitor contact:** recommended default is public listing discovery for visitors, but require authentication to initiate in-app conversations and deny protected phone/email and exact-location disclosure unless the approved policy, seller consent and entitlement checks authorize it. Product owner approval is required.
3. **Search:** approve a written, testable V1 behavior contract before selecting additional search infrastructure. Do not introduce a new search engine merely to bypass undefined acceptance criteria.

Decision status updated 2026-10-18: the product owner approved the recommended V1 scope baseline for this documentation workflow. DOC-11 is closed with paid monetization deferred to Stage 4; DOC-12 is closed with visitor sign-in required for in-app contact and protected contact/location data withheld from non-owners in V1. DOC-09 has a written contract but remains open pending MySQL test evidence.

## 4. Evidence and governance rules

- Preserve historical counts and old audit statements only when clearly marked historical/superseded; current static schema baseline is 55 tables / 89 declared FK relationships.
- Do not change “Last Reviewed” dates simply to make pages look current. Advance them only after a substantive review of the relevant page and any dependent artifacts.
- “Active” or “Approved” identifies a documentation baseline, not proof of code, provider configuration, deployment or runtime validation.
- Every closure must cite an observable artifact, test result, approved decision, or verified page correction. An appended intention or checklist checkbox is not evidence of execution.

## 5. Go/no-go rule

**No-go for full feature implementation until the team has a written, prioritized first-sprint scope and the applicable readiness gates are met.** DOC-11 and DOC-12 were resolved on 2026-10-18. The database/OpenAPI gates must be completed before API implementation is considered contract-ready. Component-specific gates (DOC-09 search validation, location slugs, payment-proof schema, admin MFA, media schema, notifications and category seed data) must be closed before implementing the affected capability. A narrow repository/bootstrap spike may be used to establish the toolchain and test harness, but it must not be represented as feature implementation or as proof that open gates passed.

## Decision Implementation Update — 2026-10-18

### DOC-11 — CLOSED: Monetization deferred from Marketplace MVP

**Approved outcome:** Paid subscriptions, paid entitlement enforcement, paid contact/location unlocks, payment submission for paid plans, recurring billing and gateway checkout are deferred to Stage 4. Documents 02, 04, 05, 07, 08, 14, 22 and the Requirements Register now carry superseding V1 scope clarifications. Long-term subscription use cases remain for future-phase traceability, not MVP acceptance. Reopen only through product change control.

### DOC-12 — CLOSED: Visitor contact and V1 privacy behavior

**Approved outcome:** Visitors may browse eligible public listings but must authenticate before initiating an in-app conversation. Authenticated contact remains subject to listing/account eligibility, seller `allow_in_app_contact`, blocking, moderation and safety rules. V1 does not expose protected phone/email or exact residential location to non-owners through the API or public web/SEO surfaces. Seller consent to messaging is not consent to disclose protected contact/location data.

### DOC-09 — CONTRACT DEFINED; VALIDATION STILL OPEN

Document 21 now defines V1 normalization and matching behavior: NFC, trim/collapse whitespace, case-insensitive Latin matching, preserve Devanagari, no automatic Romanized Nepali transliteration in V1, safe handling of short queries, no-results behavior, visibility filtering and required acceptance tests. Keep DOC-09 open until those tests pass on the supported MySQL version and actual evidence is recorded.

### Cross-document scope note

These updates are superseding decision addenda. Historical text and future-phase use cases may remain for audit history, but implementation and acceptance must follow the newest approved V1 decision. Do not treat addenda as evidence that MySQL runtime validation, OpenAPI generation, Whimsical diagram updates, admin MFA enforcement, operational restore tests or production configuration have passed.

## Technical Validation Gate Register — Execution Baseline (2026-10-18)

**Overall status: NOT IMPLEMENTATION-READY.** The current evidence supports documentation/static reconciliation only. Do not mark a runtime, security, or contract gate PASS until the specified command/test output or review artifact is attached or recorded here. Notion decisions are not substitutes for executable artifacts or test evidence.

### Gate TV-01 — Clean MySQL migration and schema verification

- **Status:** BLOCKED — execution evidence not available in this review.
- **Baseline:** Document 13 v1.4; 55 tables / 89 declared foreign-key relationships; MySQL 9.7.x; `user_push_devices.user_id` is BIGINT UNSIGNED referencing `users.id`.
- **Required evidence:** exact migration artifact/version and checksum; clean disposable database identity; successful migrate output; SQL inventory showing 55 expected tables and 89 expected FK relationships; enum/domain and unique-constraint checks; `migrate:rollback` and fresh migration results; representative seed/invariant tests; representative `EXPLAIN` plans.
- **Safety:** Never run destructive migration/rollback checks against the user's existing MySQL databases or any database containing valuable data. Use a new, explicitly named disposable validation database and verify its target before every destructive command.
- **Exit criterion:** all checks pass on the supported MySQL version and evidence is recorded. Static table counts alone are not a pass.

### Gate TV-02 — OpenAPI 3.1 contract artifact

- **Status:** BLOCKED — no final OpenAPI 3.1 YAML/JSON artifact or validator report was available in the accessible project files during this review.
- **Prerequisite:** TV-01 passes, or any database/API mismatches are resolved and explicitly approved first.
- **Required evidence:** versioned `openapi.yaml` or `openapi.json`; OpenAPI 3.1 validator PASS; route/operation inventory reconciled against Document 14; request/response schemas, auth/security schemes, error envelope, pagination, idempotency, concurrency, rate limits and examples validated; no undocumented endpoint or response field.
- **Exit criterion:** artifact and validator output are stored/linked, and Document 14 identifies the exact artifact version.

### Gate TV-03 — Search contract validation

- **Status:** SPECIFIED / TEST EVIDENCE PENDING.
- **Contract:** Unicode NFC; trim and collapse whitespace; case-insensitive Latin comparison; preserve Devanagari; no automatic Romanized Nepali transliteration in V1; empty query is a validation error; zero matches returns an empty result; public search must enforce publication, moderation, visibility, privacy and expiry rules.
- **Required evidence:** tests on pinned MySQL 9.7.x for English, Devanagari, mixed-script, case/whitespace normalization, two-character terms, punctuation, no-results, and visibility/expiry/moderation exclusions; record actual result and query plan for each case. Do not assume FULLTEXT supports every expected Nepali or short-query behavior.
- **Exit criterion:** agreed expected/actual results pass or a documented limitation/change is approved.

### Gate TV-04 — Location public slug resolver

- **Status:** BLOCKED — schema/API decision unresolved.
- **Required decision:** establish canonical stable, unique public slugs on the approved locality/municipality model or approve a dedicated slug registry; define uniqueness scope, Unicode/Latin transliteration policy, collision handling, rename/redirect behavior, and resolver contract. Update Documents 13, 14 and 23 together before implementing location SEO pages or including them in sitemaps.

### Gate TV-05 — Payment proof relational integrity

- **Status:** DECISION REQUIRED.
- **Current baseline:** `payment_intents.submitted_payment_proof_reference` is VARCHAR, not a media FK.
- **Required decision:** either approve a nullable FK to the canonical media record and regenerate/validate schema artifacts, or explicitly accept application-level ownership/purpose/exposure validation with the known absence of DB referential integrity. Do not store filesystem paths, storage keys or signed URLs as the public reference.

### Gate TV-06 — Admin MFA persistence and enforcement

- **Status:** BLOCKED — schema and runtime enforcement not proven.
- **Required evidence/decision:** define secure MFA enrollment, factor state, recovery-code lifecycle and reset/re-enrollment controls; use an approved encrypted/hashed persistence design; prove MFA is enforced for privileged Filament/admin access and cannot be bypassed through alternate routes. If durable state requires schema fields/tables, approve the schema change before implementation.

### Gate TV-07 — Media schema and processing security

- **Status:** BLOCKED for capabilities requiring absent durable fields.
- **Current limitation:** Document 13 does not establish every Document 20 concept, including generic classification/target resource, checksum, separately detected MIME, or dedicated quarantine state.
- **Required action:** map each V1 media guarantee to an existing physical column or approve schema changes. Test MIME/content sniffing, size/count/type limits, ownership, quarantine, processing failures, unsafe-file rejection, video processing, and private payment-proof access. Do not claim these guarantees from documentation alone.

### Gate TV-08 — Notification locale, expiry and deduplication

- **Status:** POLICY/SCHEMA REVIEW REQUIRED; runtime tests pending.
- **Current limitation:** no dedicated notification locale/classification/expiry/dedupe-key columns or templates table are established in Document 13.
- **Required action:** explicitly decide which attributes can be derived from event/outbox data and which need durable schema. For V1, templates may remain versioned code/config only if documented. Prove idempotent consumption and duplicate prevention; define locale selection independent of an unrelated request's `Accept-Language`.

### Gate TV-09 — Production and operational evidence

- **Status:** NOT VERIFIED.
- **Required evidence:** CI pipeline results; secret/access-control review; logging/monitoring and actionable alerts; backup configuration; successful restore drill; release/rollback rehearsal; production proxy/IP rate-limit test; real-device FCM tests; media and notification end-to-end tests. Attach dates, environment/version, result and evidence reference.

### Validation execution rule

For each gate, update status only to **PASS** when evidence is recorded; use **FAIL** for a reproducible failed test; use **BLOCKED** where a decision/artifact/dependency is missing; and **NOT RUN** where no execution occurred. Keep the overall project **NOT IMPLEMENTATION-READY** until all gates required for the intended MVP release are passed. Deferred Stage 4 subscription/paid-entitlement behavior is outside MVP acceptance and must not be accidentally treated as an MVP gate or implemented as required functionality.

### TV-04 Decision Update — 2026-10-18

**Decision:** Location SEO must remain disabled/non-indexable and excluded from sitemaps until the stable slug/public-identifier model, resolver and physical artifacts are approved and tested. No URLs may be synthesized from integer IDs. This closes the unsafe implementation ambiguity, but **does not close TV-04**: the physical schema and runtime tests remain blocked on review of the current Gate #14 artifact set.

### TV-07 Update — 2026-10-18

Document 13 and Document 20 now explicitly describe the media schema boundary and distinguish current columns from schema-gated capabilities. Durable quarantine, checksum, separately detected MIME, access classification and generic target-resource association are not established in the current physical model. TV-07 remains BLOCKED pending artifact reconciliation and runtime security tests; no runtime PASS is claimed.

### TV-09 Review Update — 2026-10-18

Documents 25–27 now explicitly distinguish target operating procedures from evidence of actual implementation. Required proof includes CI run and secret review, deployed infrastructure/security checks, actionable alert and log-redaction tests, backup plus successful restore drill, approved/measured RPO/RTO, release recovery rehearsal, trusted-proxy/IP rate-limit test, real-device FCM, and media/notification end-to-end tests. No operational evidence was supplied or executed in this review. **TV-09 remains NOT VERIFIED. Overall project remains NOT IMPLEMENTATION-READY.**

## Implementation-Readiness Evidence Inventory — 2026-10-18

**Audit scope:** connected KHOJ BHET Notion documentation and files discoverable through the current ChatGPT project/library context. This is an evidence-availability audit, not a claim that the live source repository, database, CI provider, or deployment environment has been inspected.

### A. Evidence inventory and findings

| Area | Evidence found in this review | Assessment | Required next action |
| --- | --- | --- | --- |
| Canonical source repository | Document 28's repository bootstrap gate was updated after the repository was created. The connected GitHub integration verified `yadavrabikrishna/khoj-bhet` as a private repository with default branch `main`; repository metadata reports size 0, and the branch listing is empty. Branch protection/rulesets could not be verified through the available connection/plan. No code, schema artifacts, tests, or CI workflows are present in the empty repository. | BLOCKED — live repository cannot yet be audited. | Identify the canonical repository URL or provide an accessible repository snapshot. Then inventory branch protections, workflows, dependency lockfiles, migrations, tests, secret scanning and release artifacts. |
| Database artifacts | Document 13 records the current approved decision baseline as 55 tables / 89 declared FKs and references the expected artifact names: `schema.dbml`, `2026_09_28_000000_create_khoj_bhet_schema.php`, `khoj-bhet-migration-validation.md`, and `database-schema-review.md`. However, Document 13 also states that DBML, Laravel migration, validation SQL, and review artifacts remain pending final regeneration after later Gate #11–#14 changes. The discoverable Library copy of `database-schema-review.md` (modified 2026-09-28) describes the earlier 47-table / 71-relationship baseline, so it is not safe to treat that file as the current canonical review. | STALE ARTIFACT FOUND — this older review is not evidence for the current 55/89 baseline and must not be treated as current runtime proof. The current DBML, migration and validation SQL could not be identified from the accessible file-search results. | Recover or regenerate the four named schema artifacts from the latest approved Document 13 decisions; confirm they all derive from the same revision and record hashes. Reconcile 55 tables / 89 declared FKs, PHP syntax, indexes, enums and constraints, then run TV-01 on a disposable supported MySQL 9.7.x instance. Never use an existing user database for destructive validation. |
| OpenAPI 3.1 | Notion specifies contract-first generation after schema/runtime validation. No final `openapi.yaml` / `openapi.json` or validator report was identified in accessible file-search results. | BLOCKED — no accessible artifact/evidence located; this does not prove no copy exists elsewhere. | After TV-01 passes or discrepancies are approved, generate and version the OpenAPI 3.1 artifact, validate it, reconcile operations against Doc 14 and retain validator output. |
| Automated tests / test harness | Doc 24 defines the QA baseline and requires supported-MySQL behavior. No current source repository or executable test-run report was available to inspect in this review. | NOT VERIFIED — test strategy is documentation, not test execution. | Inspect the real repository for backend unit/feature tests, MySQL integration tests, web/mobile checks, fixtures and CI invocation. Run tests and record exact commit, tool versions, commands, exit codes and failures. |
| CI/CD and repository protections | Docs 25 and 28 describe intended workflows and protections; actual workflow files, branch settings and successful run evidence were not available for verification. | NOT VERIFIED. | Inspect workflow configuration and live repository settings; verify least-privilege permissions, protected branches, secret handling, required checks and successful pipeline evidence. |
| Deployment, monitoring and recovery | Docs 26–27 define intended deployment, observability, backup and restore evidence; no live environment details, backup configuration or restore-drill output were supplied in the accessible context. | NOT VERIFIED. | Identify the real deployment target and collect configuration references, health/alert tests, backup evidence, successful restore drill, measured RPO/RTO and rollback/forward-recovery rehearsal. Do not record credentials or secret values in Notion. |
| Security-critical implementation gates | TV-04 location resolver, TV-06 admin MFA, TV-07 media schema/processing security and TV-08 notification locale/deduplication remain blocked or evidence-pending as recorded in their gate notes. | BLOCKED / TEST EVIDENCE PENDING. | Close each gate only after the physical schema/API decisions are reflected in the canonical artifacts and required tests pass. Keep Stage 4 monetization outside MVP acceptance unless scope is explicitly changed. |
| Search behavior | Doc 21 specifies normalization and visibility behavior, but supported-MySQL acceptance-test evidence is not recorded. | SPECIFIED / TEST EVIDENCE PENDING. | Run the TV-03 matrix for Latin, Devanagari, mixed script, NFC/NFD, case/whitespace, short terms, punctuation, no results and visibility/expiry/moderation filtering. |

### B. Audit result

- **Documentation architecture:** conditional pass, subject to remaining documentation and diagram checks already tracked elsewhere in this register.
- **Current executable artifact inventory:** incomplete in the accessible workspace; the old 47/71 review is stale relative to the current documented 55/89 baseline.
- **Live repository inspection:** not performed because the canonical repository location/access is not established in the available context.
- **Runtime validation:** no new MySQL migration, OpenAPI validation, test suite, CI run, deployment check, backup restore or end-to-end test was executed during this audit.
- **Overall implementation readiness: NOT IMPLEMENTATION-READY.**

### C. Prioritized next actions

1. **Establish source-of-truth access:** identify the canonical repository and current artifact revision. Do not infer repository existence, URL, settings or test results.
2. **Recover the exact current schema package:** DBML + Laravel migration + clean-MySQL validation SQL + schema review, all from the same revision. Reconcile 55 tables / 89 FK declarations before execution.
3. **Execute TV-01 safely:** use a disposable MySQL 9.7.x database; capture migration, inventory, constraints, seed/invariant, rollback/fresh migration and representative EXPLAIN results.
4. **Generate TV-02:** create the versioned OpenAPI 3.1 YAML/JSON only after schema/API mismatches are reconciled; validate and retain report.
5. **Inspect the real test/CI setup:** map test commands to Doc 24 and confirm a successful run on a known commit.
6. **Collect operational proof:** inspect the actual deployment, monitoring, backup and restore setup; execute a restore drill before claiming recovery readiness.
7. **Close capability-specific gates:** TV-03 through TV-08 according to their individual dependencies; keep TV-09 NOT VERIFIED until operational evidence is attached or referenced.

**Evidence rule:** mark PASS only when an observable artifact or reproducible execution result is recorded with revision, environment/tool version, command, date, outcome and evidence location. A Notion design statement or checklist is not runtime proof.

### GitHub Access Check — 2026-10-18

- **Connector access:** verified. The authenticated GitHub account is `yadavrabikrishna` (account ID `344270375`).
- **Repository inventory:** the connected account returned zero repositories visible to this integration at the time of the check.
- **Interpretation:** this confirms that no repository is currently available through the connected account/integration; it does not prove that no repository exists under another account or inaccessible organization.
- **Repository creation:** the available GitHub actions support working with existing repositories, but no repository-creation action is exposed in this connection. Create the repository through GitHub's UI, then provide its canonical `owner/repository` name or URL so the repository can be inspected and bootstrapped safely.
- **Next action:** establish the canonical repository before treating source-control, branch protection, CI, schema artifact inventory, or code inspection as verified. Overall implementation readiness remains **NOT IMPLEMENTATION-READY**.

### TV-01 Static Candidate Reconciliation Update — 2026-10-18

**Status: STATIC INVENTORY/REFERENCE CHECKS PASS; FULL SEMANTIC REVIEW AND RUNTIME VALIDATION PENDING.**

A corrected static candidate now exists outside GitHub. Static results: 55 DBML tables, 55 unique Laravel table declarations, 89 DBML references, 89 Laravel FK declarations, exact FK endpoint match, all DBML reference endpoints resolve, and PHP syntax lint passes in the review environment. Confirmed defects corrected: listing-type applicability had an integer type instead of the approved ENUM; composite-PK tables had conflicting per-column primary declarations; explicitly documented physical ENUMs and pricing-mode registry were incomplete/misaligned; unapproved `users.deleted_at` and a migration-level global string-length setting were removed. Clean-MySQL validation SQL was added. The candidate uses explicit RESTRICT FK delete actions as a conservative provisional policy; per-relationship semantics still require review.

**TV-01 remains BLOCKED / NOT RUNTIME VALIDATED.** The migration has not been run against MySQL. Full column/index/delete-action review, Laravel rollback/re-migrate, schema inventory, domain invariant tests and representative EXPLAIN plans remain outstanding. The package is not yet canonical and has not been committed to GitHub. Use a new disposable validation database only; never run destructive tests against other project databases.

## Follow-up Audit Pass — 2026-10-21

### Scope and result

- Re-fetched the canonical 13.1 Category & Attribute Catalogue and all 25 linked CAT detail pages.
- Preserved the approved taxonomy baseline: 25 categories, 372 subcategories, all existing CAT IDs unchanged; CAT-002 remains Mobile & Electronics and CAT-002-05 remains Television.
- The Phase 3B §43–§44 result is retained as a completed controlled-option/unit-policy milestone dated 2026-09-30. It is not a current production-seed validation or a blanket declaration that every detailed catalogue is seed-ready.
- CAT-002 is the only fetched detail page with explicit post-reconciliation field-level gaps found by this text-marker pass. CAT-001 and CAT-003–CAT-025 had no literal `UNRESOLVED`, `Decision required`, or `not specified in master` markers detected in the fetched content. This is a documentation-text check, not a substitute for automated seed-data validation.

### CAT-002 — current open items

The page enumerates all 96 attribute identifiers, including the 69 identifiers absent from the original detail tables. It remains **NOT seed-ready**. The audit recorded:

1. **48 flag cells across 16 attributes** still marked `Decision required` for required/filterable/searchable behavior: MOB-001, MOB-002, TAB-001, LAP-001, DESK-001, TV-001, CAM-001, CAM-002, MACC-001, MACC-002, AUD-001, AUD-002, GAME-001, GAME-002, CACC-001, and CACC-002.
2. **Eight product-specific option sets** remain undecided: TAB-001 Operating System, TAB-007 Network Type, LAP-004 RAM Unit, LAP-010 Operating System, DESK-003 Storage Type, DESK-006 Operating System, TV-005 Operating System, and AUD-006 Channels.
3. **Measurement semantics/ranges** remain open for RAM units (MOB-002, TAB-002, LAP-003, DESK-002), MOB-006 Battery Capacity, MOB-015 Battery Health, CAM-002 Sensor Resolution, CAM-006 Optical Zoom, and AUD-005 Wattage. Numeric ranges also remain to be specified for screen/monitor-size fields and TV-007 Refresh Rate, plus any other numeric measurements for which the catalogue has not established a validation range.
4. The audit applied §43 only where the semantic mapping is unambiguous: storage-unit options GB/TB for TAB-004, LAP-007 and GAME-004; length-unit family for MOB-005, TAB-005, LAP-009, TV-001 and DESK-008; GB/TB for DESK-004 storage capacity; Hz/kHz for TV-007 refresh-rate units; and the §43.2 Connectivity family for CACC-003. These resolutions do not close missing flags or numeric ranges.
5. Final subcategory applicability and attribute/option ordering still require validation. Do not generate production seeders, API filters, or UI forms until these decisions are closed.

### Historical registry sections

Sections 32–37 of 13.1 contain 2026-09-30 snapshots, including historical counts of 135 and 77 and literal `UNRESOLVED` table cells. Those counts are not current materialized-registry counts. §43 supersedes those snapshots for semantic option/unit policy; the current registry/materialized seed coverage remains unverified until the deterministic seed audit runs.

### Closure status

- **Phase 3B option/unit policy:** COMPLETE.
- **CAT-002 attribute metadata:** OPEN — catalogue-owner decisions required.
- **Current catalogue-wide option materialization and structural validation:** PENDING.
- **Production seed readiness / clean-MySQL execution:** NOT VERIFIED.

No taxonomy change is required.

## CAT-002 Decision Closure — 2026-10-21

The catalogue owner approved defaults rather than leaving the product choices open:

- Required = No by default; only essential listing fields should be required.
- Filterable = Yes and Searchable = Yes by default for all 96 CAT-002 attributes, using datatype-aware query behavior.
- Approved option sets: TAB-001 OS (Android, iPadOS, Windows, ChromeOS, Other); TAB-007 Network Type (2G, 3G, 4G, 5G, Wi-Fi Only, Other); LAP-004 RAM Unit (GB); LAP-010 OS (Windows, macOS, Linux, ChromeOS, Other); DESK-003 Storage Type (HDD, SSD, NVMe SSD, eMMC, Hybrid, Other); DESK-006 OS (Windows, macOS, Linux, Other); TV-005 OS (Android TV, Google TV, Tizen, webOS, Roku TV, Fire TV, VIDAA, Proprietary, Other); AUD-006 Channels (Mono, Stereo, 2.1, 5.1, 7.1, 9.1, Other).
- Measurement semantics: RAM in GB (>0); MOB-006 battery capacity in mAh (>0); MOB-015 battery health 0–100%; CAM-002 sensor resolution in MP (>0); CAM-006 optical zoom ratio ≥1.0×; AUD-005 wattage in W (>0); TV-007 refresh rate in Hz (>0); screen/monitor-size attributes use the §43 Length Unit family and positive values.

**Current disposition:** CAT-002 product-choice gaps are closed by documented owner-approved defaults. Taxonomy remains 25 categories / 372 subcategories. Production seed readiness remains **PENDING VALIDATION**, not blocked on further product decisions: the next gate is materialized attribute/applicability coverage, option slug uniqueness, type compatibility, duplicate/orphan checks, ordering/inheritance checks, and a clean-MySQL migration/seed test. The CAT-002 detail page and parent catalogue record the same decisions.

## Catalogue-Wide Static Audit & Runtime Gate — 2026-10-21

The 25 linked catalogue pages were fetched and checked for literal unresolved/decision-required/unspecified markers. CAT-001 and CAT-003 through CAT-025 had no such markers in this pass. CAT-002 decisions are documented in its detail page and parent §45; two stale RAM/sensor-resolution notes were corrected. This is a text-marker check, not proof of seed row coverage or runtime validity.

The catalogue owner approved Required = No by default and Filterable = Yes / Searchable = Yes by default for all 25 categories, with datatype-aware search semantics. Parent catalogue §46 is the effective policy authority.

**Runtime status: NOT EXECUTED / NOT VERIFIED.** The current GitHub develop branch remains a Laravel skeleton baseline; the expected approved-schema migration path did not exist at the checked path. A prior saved static reconciliation result reports 55 tables and 89 foreign keys for a reconstructed migration, but it is not evidence that this migration is committed or that clean MySQL succeeds.

Remaining execution work: reconcile approved DBML to the migration actually committed on develop; generate/validate the catalogue seed manifest; run PHP lint and static schema reconciliation; run migrations and seeders in a confirmed disposable Docker MySQL database; execute saved SQL inventory/FK checks, domain invariants, catalogue option/applicability assertions, and representative query-plan checks; then record captured output before changing the gate to PASS.