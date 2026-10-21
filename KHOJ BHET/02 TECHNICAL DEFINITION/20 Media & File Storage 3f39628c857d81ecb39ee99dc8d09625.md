# 20. Media & File Storage

> **Implementation status clarification — 2026-10-15:** “Active” means this is the current authoritative design baseline, not that implementation is release-ready. Implementation sign-off remains gated by the final OpenAPI 3.1 contract, successful clean-MySQL migration/runtime validation, and the relevant component tests. Component-specific schema or provider gates documented below remain independently binding.
> 

> ## Schema Compatibility Gate — 2026-10-09
> 

> Document 13 currently defines media metadata such as public_id, owner_user_id, storage_provider, storage_key, media_type, mime_type, file_size, width/height, duration_seconds, processing_status, moderation_status, timestamps, media_variants, and listing_media. It does not yet establish dedicated columns for a media access classification, checksum, separately detected MIME, generic target-resource association, or explicit quarantine state. Do not assume these fields already exist or rely on undocumented free-form metadata for security-critical policy.
> 

> 
> 

> Before implementing private verification/property documents, file quarantine, checksums, or generic resource targeting, either extend Document 13 through an approved schema gate or constrain V1 to relationships and states that the current schema supports. Validate the required V1 video workflow against the existing processing_status model and add durable processing/failure state only through an approved schema change if needed.
> 

## Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-TECH-020 |
| Status | Active — Media & File Storage Baseline |
| Version | 1.0 |
| Owner | KHOJ BHET Engineering |
| Last Reviewed | 2026-10-08 |
| Parent | 02. TECHNICAL DEFINITION |
| Previous | 19. Security Architecture |
| Next | 21. Search Architecture |
| Related | 08 Product & Business Rules; 09 Software Architecture; 10 Technology Stack; 12 Engineering Standards; 13 Database Architecture & Data Model; 14 API Specification; 15 Frontend Architecture; 16 Backend Architecture; 17 Mobile Application Architecture; 18 Authentication & Authorization; 19 Security Architecture |

# 1. Purpose

This document defines the authoritative architecture for media and file handling in KHOJ BHET.

It covers listing images and galleries, user/profile media, business media, verification documents, private/restricted media, upload and validation, processing, storage, retrieval, replacement, deletion, lifecycle management, quotas, cleanup, moderation, abuse controls, and disaster recovery.

The architecture uses a local-storage-first abstraction: application code depends on a storage contract rather than a specific provider.

# 2. Core Architectural Decision

KHOJ BHET uses an application-level Media Storage Service between Laravel and physical/object storage.

**Web/Mobile Client → Laravel API → Media Service → Storage Adapter → Physical/Object Storage**

MySQL stores authoritative media metadata and relationships. Storage holds binary content.

Neither the client nor storage provider is authoritative for ownership, publication state, permissions, listing association, moderation state, or entitlement.

# 3. Authoritative Responsibilities

| Concern | Authority |
| --- | --- |
| Media ownership | Laravel + MySQL |
| Resource association | Laravel + MySQL |
| Publication state | Laravel + MySQL |
| Moderation state | Laravel + MySQL |
| Access authorization | Laravel |
| Media metadata | MySQL |
| Binary file | Storage adapter/provider |
| Image variants | Media processing pipeline |
| Temporary upload state | Laravel/storage workflow |
| Public URL generation | Storage service |
| Restricted-media access | Laravel authorization + controlled delivery |
| Cleanup eligibility | Laravel + scheduled workers |
| Storage implementation | Configured storage adapter |

# 4. Media Categories

## 4.1 Listing Media

Property, room, vehicle, mobile/electronics, furniture, land, clothing, and other category-specific gallery media.

Listing media is normally visible according to listing publication and privacy rules.

## 4.2 Profile Media

Examples include user avatar/profile images, business logos, and business cover images.

## 4.3 Verification Media

Identity or business verification documents, when enabled. Verification media is private by default and never follows public listing-media access rules.

## 4.4 Private/Restricted Media

Documents, moderation evidence, private conversation attachments, and other confidential files require explicit authorization.

# 5. Media Classification

Every stored object has an application-level classification.

| Classification | Default Exposure |
| --- | --- |
| Public | Publicly retrievable after publication rules permit |
| Protected | Authenticated and authorized access |
| Private | Explicit owner/business/admin authorization |
| Restricted | Highly sensitive; dedicated policy required |
| Quarantined | Not user-accessible until validation/moderation completes |
| Deleted | No application access; pending physical cleanup |

A storage path or URL is never a substitute for classification.

# 6. Media Lifecycle

Canonical lifecycle:

**Multipart Request → Uploaded → Validating → Processing → Ready/Rejected → Published/Attached → Replaced/Unpublished → Deleted → Purged** (V1 direct-multipart flow; no upload-intent endpoint)

## 6.1 Future Upload-Intent Model (Not V1)

Upload-intent/complete endpoints are not part of V1. The following is a future design option only and must not be implemented unless Document 14 is formally amended.

May contain authenticated actor, target resource, media category, expected content type, maximum size, expiry, and upload identifier.

## 6.2 Uploaded

The binary has reached temporary or permanent storage but is not automatically user-visible.

## 6.3 Validation

Validate file type, signature, size, dimensions, integrity, ownership, target authorization, supported format, and security policy.

## 6.4 Processing

Processing may include decoding, orientation normalization, resizing, WebP/AVIF generation, metadata normalization, optimization, and malware/content scanning where supported.

## 6.5 Ready

Only validated and successfully processed media may enter the normal usable state.

## 6.6 Published/Attached

Media becomes available through the relevant resource visibility policy.

## 6.7 Deleted/Purged

Application deletion removes access immediately. Physical deletion may be asynchronous after retention requirements are satisfied.

# 7. Upload Architecture

**V1 upload contract: direct multipart upload through Laravel**, as approved by Document 14 AD-API-03. Do not implement upload-intent/complete endpoints in V1 unless Document 14 is explicitly amended.

1. Client authenticates with Firebase and sends the Bearer token.
2. Client uploads multipart media to the canonical Document 14 endpoint.
3. Laravel authenticates and authorizes the actor and target resource.
4. Laravel validates file signature, detected MIME, extension, byte size, count, and media category before accepting the file.
5. Laravel stores the object under a collision-resistant ULID-based storage key and records metadata in MySQL.
6. Expensive image/video processing and public-variant publication run asynchronously through the transactional outbox/queue workflow.
7. The multipart request completes; Laravel records media metadata and processing status.
8. The outbox relay/queue worker performs asynchronous validation and image/video processing. V1 does not create a separate upload-intent/complete API.
9. Completion is reported to Laravel.
10. Laravel validates the uploaded object.
11. Processing/scanning occurs.
12. Media metadata is committed.
13. Media is attached to the resource.
14. API returns the canonical media representation.

The client cannot decide that an upload is published.

# 8. Direct-to-Storage Uploads

Direct or signed uploads may be used for large files.

If used:

- Laravel creates the authorization-controlled upload intent.
- The upload capability is short-lived.
- The upload is bound to the intended object.
- Size/type constraints are enforced.
- Client cannot change application ownership.
- Completion must be confirmed by Laravel.
- Unconfirmed objects are cleaned up.
- Public access is not enabled automatically.

A signed upload URL is an upload capability, not an application authorization grant.

# 9. Storage Abstraction

Application code must not depend directly on provider-specific SDK behavior.

The storage contract should support operations conceptually equivalent to create/write/read/stream, generate temporary access, copy/move, delete, existence check, metadata, and public URL generation where appropriate.

Laravel services use a storage contract/interface and adapter implementation.

Initial implementation may use local filesystem storage. Future adapters may support S3-compatible storage, Cloudflare R2, or other approved providers.

Changing providers must not require rewriting marketplace business logic.

# 10. Storage Layout

Storage paths are generated by the application and never use user-provided filenames as authoritative paths.

Recommended logical structure:

environment / media-class / resource-type / resource-public-id / media-ulid / variant.extension

Examples:

- production / listings / property / {listing-public-id-ulid} / {media-ulid} / original.webp
- production / listings / mobile / {listing-public-id-ulid} / {media-ulid} / large.webp
- production / profiles / user / {user-public-id-ulid} / {media-ulid} / avatar.webp
- production / verification / user / {user-public-id-ulid} / {media-ulid} / document.pdf

Examples are logical placeholders, not literal storage paths. Do not place sequential BIGINT database IDs in public URLs or externally visible storage paths. Exact private storage keys should remain server-side and may be opaque random/ULID-based keys behind the storage abstraction.

# 11. Object Naming

Object identifiers must be generated by the application.

Requirements:

- collision-resistant IDs;
- no unnecessary exposure of sequential database IDs;
- original filenames are not object identifiers;
- original filename may be retained only as metadata;
- extension follows validated content;
- path traversal is prevented;
- user-controlled directory traversal is impossible;
- private object paths are not predictable.

# 12. Database Metadata

The media model must represent at least:

- media ID;
- owner/actor context where required;
- classification;
- media type/category;
- target resource type;
- target resource ID;
- storage disk/provider;
- storage object key/path;
- original filename where required;
- MIME type;
- detected MIME type;
- extension;
- byte size;
- checksum/content hash where supported;
- width;
- height;
- duration for future supported media;
- processing state;
- publication state;
- moderation state;
- sort/order position;
- variant relationship;
- upload intent/reference;
- timestamps;
- deletion/purge timestamps where required.

Exact schema remains aligned with Document 13 and the final migration.

# 13. Media Relationships

A media record may belong to a User, Business, Listing, Conversation/Message where supported, Verification Submission, Moderation/Report Evidence, or another approved domain resource.

The relationship must be explicit.

Do not infer authorization from the storage path.

A listing's media relationship does not automatically mean every listing viewer can access every media variant.

# 14. Image Variants

Original uploads should generally not be used directly for normal delivery.

| Variant | Purpose |
| --- | --- |
| Original | Controlled archival/source copy |
| Large | Listing detail/full gallery |
| Medium | Cards/search results |
| Thumbnail | Small previews |
| Blur/placeholder | Loading/privacy UX where needed |

Variant dimensions and quality are implementation configuration.

# 15. Image Processing Rules

For image uploads:

- validate actual file signature;
- normalize orientation;
- strip unnecessary metadata;
- remove potentially sensitive EXIF/GPS metadata unless explicitly required;
- enforce maximum dimensions;
- generate controlled variants;
- normalize supported formats;
- reject malformed or decompression-bomb-like files;
- enforce processing resource limits.

Exact location/property media must not accidentally expose GPS coordinates through EXIF.

# 16. Supported Formats

Accepted input formats must be explicitly configured.

V1 image inputs are limited to JPEG, PNG, and WebP, matching Document 14. HEIC/HEIF is not accepted in V1 unless the API contract and validation suite are explicitly updated. Canonical delivery may use WebP variants generated by the approved processing pipeline.

Unsupported or unsafe formats must be rejected.

# 17. File Size and Dimension Limits

Limits must exist at multiple layers:

1. API request limit.
2. Upload-intent limit.
3. Storage/upload limit.
4. Processing limit.
5. Resource-level media count limit.

Limits must be category-aware.

Approved V1 listing-media limits are **20 images per listing, 21 total media items including at most one video, and 10 MB maximum per image**. The separately approved video limit is one MP4 (H.264/AAC) file up to 50 MB and 60 seconds. Enforce these limits consistently at the API, PHP, reverse-proxy, processing worker, and storage layers; reject rather than silently truncate.

# 18. Media Count and Quotas

Media limits are enforced server-side.

Enforce the fixed V1 per-listing media limits independent of subscription tier; subscription plans do not increase the approved media count or per-file size. Apply abuse-oriented request-frequency, concurrency, and processing-resource controls separately. Do not introduce tier-based media quotas without an approved contract change.

Client UI may mirror these limits but is not authoritative.

# 19. Public Media Delivery

V1 supports one listing video as well as images. Video processing is asynchronous and must validate MP4 container and H.264 video/AAC audio, enforce the 50 MB/60-second limits, generate a poster frame and approved playback derivative, and publish only after processing succeeds. Delivery must support HTTP byte-range requests for seeking; verify Range/206 behavior end-to-end through the reverse proxy and application/storage adapter. Configure matching PHP and Nginx request-body limits with safe headroom above the 50 MB maximum, and test timeouts, temporary storage, worker resource limits, failed transcodes, and cleanup.

Public media may use CDN-backed public URLs, optimized image endpoints, or application-controlled media URLs.

Public delivery is permitted only when:

1. media classification is public;
2. target resource permits public visibility;
3. moderation/publication rules permit access;
4. media is not deleted/restricted.

Changing a listing from public to private/unpublished must disable access according to the delivery architecture.

# 20. Protected Media Delivery

Protected media should use authenticated streaming, short-lived signed URLs after authorization, or controlled proxy delivery.

Long-lived public URLs must not be used for sensitive media.

Authorization occurs before issuing access. Temporary URLs must have bounded lifetimes.

# 21. Verification and Highly Sensitive Files

Verification documents are private by default.

Requirements:

- never expose through public CDN paths;
- never include raw storage keys in normal API responses;
- restrict access to authorized verification/admin roles;
- log sensitive access where required;
- use short-lived controlled access;
- encrypt at rest where appropriate;
- apply strict retention/deletion policies;
- avoid unnecessary duplication.

Verification media must not become listing media merely because the same user owns both resources.

# 22. Media Security Controls

Media handling implements the controls defined in Document 19:

- untrusted-input treatment;
- MIME/content validation;
- size limits;
- malware/content scanning where available;
- path traversal protection;
- controlled storage;
- least-privilege access;
- secret isolation;
- safe deletion;
- auditability for sensitive access.

A file extension alone is never sufficient proof of file type.

# 23. Content Moderation

Listing media may require moderation before publication.

Moderation state remains separate from technical processing state.

Example:

**Uploaded → Validated → Processed → Moderation Pending → Approved/Rejected**

A technically valid image can still be rejected for business or safety reasons.

Moderators do not automatically receive unrelated private or verification media.

# 24. Malware and Unsafe File Handling

All uploaded files are potentially malicious.

Controls include MIME/signature validation, size limits, decompression/resource limits, malware scanning where available, isolated processing, non-executable storage, safe image decoding, controlled document handling, and quarantine/rejection on scan failure.

Unscanned or failed-scan objects must not become publicly accessible.

# 25. Client Caching

Clients may cache media for performance.

Private media must not be cached indefinitely. Protected-media cache lifetimes must reflect sensitivity. Logout/account switching must clear relevant private caches. Revoked access must not depend solely on client cache expiry. Cached media URLs must never be treated as current authorization.

# 26. Media Replacement

Replacement is an authorized mutation:

1. Authenticate actor.
2. Authorize target resource.
3. Validate new media.
4. Process new variants.
5. Update canonical association.
6. Preserve required audit/history.
7. Mark old media for deletion.
8. Asynchronously purge obsolete objects when safe.

Replacement must not create accessible orphan files.

# 27. Media Deletion

Deletion distinguishes application deletion, logical deletion, physical object deletion, and backup retention.

After application deletion, media is excluded from normal API queries.

Physical purge may be asynchronous.

Sensitive deleted media must not remain unnecessarily accessible through old public URLs.

# 28. Orphan and Temporary Object Cleanup

Scheduled cleanup must identify:

- abandoned upload intents;
- expired temporary uploads;
- storage objects without media records;
- media records without valid objects;
- obsolete variants;
- replaced/deleted objects awaiting purge.

Cleanup jobs must be idempotent and safe to retry.

Cleanup must not delete active objects because of stale indexes.

# 29. Storage Integrity

Where supported, maintain content hashes/checksums.

They may be used to detect corruption, accidental duplication, upload completion, migration validation, and reconciliation.

A checksum is an integrity mechanism, not an authorization mechanism.

# 30. Duplicate Media

Deduplication may be introduced later.

If implemented:

- authorization remains resource-specific;
- one physical object may serve multiple authorized media records only when safe;
- deleting one reference must not delete a shared object still in use;
- reference counting or equivalent lifecycle management is required.

Deduplication must never expose private media through another resource.

# 31. Upload Abuse Protection

Upload endpoints enforce authentication where required, resource authorization, file count/byte limits, rate limits, concurrency limits, processing limits, storage quotas, and suspicious-pattern detection where available.

Abuse controls should run before expensive processing whenever possible.

# 32. API Contract

Document 14 remains authoritative for public API naming, request/response envelopes, error semantics, and enum values.

V1 media APIs use direct multipart uploads through the documented Laravel endpoints. After acceptance, asynchronous validation and processing are dispatched through the transactional outbox. A future version may add upload-intent/complete endpoints only through a coordinated API and schema change.

- attach media;
- list resource media;
- reorder media;
- replace media;
- delete media;
- retrieve authorized media metadata;
- obtain controlled access URL where required.

Exact endpoint paths and public enum names remain defined by Document 14.

# 33. Error Handling

Typical failures include unsupported type, file too large, dimensions too large, expired upload, invalid intent, unauthorized resource, forbidden access, validation failure, processing failure, moderation rejection, missing object, stale/replaced media, quota exceeded, and rate limit exceeded.

Responses follow Document 14's canonical error envelope.

Do not expose storage keys, provider errors, scanning internals, or filesystem paths.

# 34. Performance Architecture

Media performance should use resized variants, CDN delivery where available, HTTP caching for public assets, appropriate cache headers, lazy loading, thumbnails, progressive loading, background processing, asynchronous cleanup, and bounded image-processing resources.

The API should avoid embedding large binary payloads in ordinary JSON responses.

# 35. Observability

Track operational metrics for upload success/failure, validation failure, processing duration/failure, scan failure, storage failure, controlled URL generation, media deletion, orphan cleanup, quota rejection, and abuse/rate-limit events.

Metrics and logs must not contain sensitive file contents or secrets.

# 36. Backup and Disaster Recovery

Media and metadata have different recovery characteristics.

Backups must account for MySQL media metadata, storage objects, required object versions, configuration, and storage-adapter settings.

Recovery must preserve the relationship between database records and stored objects.

A database restore without required media objects, or media restore without matching metadata, is incomplete recovery.

# 37. Migration Between Storage Providers

Provider migration follows:

1. Coordinate writes where required.
2. Inventory media records and objects.
3. Copy objects.
4. Validate checksums/counts.
5. Validate metadata.
6. Validate representative public/protected access.
7. Switch adapter/configuration.
8. Monitor.
9. Retain rollback capability.
10. Remove old objects only after validation and retention requirements are satisfied.

Application business logic remains unchanged.

# 38. Local Development and Environment Separation

Development, staging, and production storage must be logically separated.

Development may use filesystem storage.

Staging uses an isolated namespace/bucket.

Production uses production-specific credentials and access controls.

Development data must never accidentally point to production media.

# 39. Security Invariants

1. Storage paths never grant application authorization.
2. The client never decides whether media is public.
3. Upload permission does not imply publication permission.
4. Listing visibility does not automatically grant verification/private media access.
5. A signed URL is temporary access, not ownership.
6. User filenames are never trusted storage paths.
7. Unvalidated uploads are never publicly accessible.
8. Deleted media is immediately removed from normal application access.
9. Sensitive media is never placed in a public storage namespace.
10. Media processing cannot change ownership or authorization.
11. Moderation and technical processing states remain distinct.
12. Storage-provider changes must not change authorization semantics.
13. Media cleanup must be safe and idempotent.
14. Public media must respect resource publication/moderation state.
15. Exact-location/privacy rules apply to media as they apply to structured data.

# 40. Cross-Document Contracts

| Document | Media Contract |
| --- | --- |
| 08 Product & Business Rules | Defines listing/media business rules and visibility |
| 09 Software Architecture | Defines service boundaries |
| 10 Technology Stack | Defines storage/processing technology choices |
| 12 Engineering Standards | Defines implementation/testing standards |
| 13 Database Architecture & Data Model | Defines authoritative media metadata/relationships |
| 14 API Specification | Defines public media API contract |
| 15 Frontend Architecture | Defines web media presentation and public SEO boundaries |
| 16 Backend Architecture | Defines Laravel storage-service implementation |
| 17 Mobile Application Architecture | Defines mobile capture/upload/cache behavior |
| 18 Authentication & Authorization | Defines actor identity and authorization |
| 19 Security Architecture | Defines media security, trust boundaries, and threat controls |
| 20 Media & File Storage | Defines end-to-end media/file architecture |

# 41. Implementation Rules

1. Implement media access through a storage abstraction.
2. Keep binary storage separate from authoritative media metadata.
3. Never authorize from a storage path.
4. Treat all uploads as untrusted.
5. Validate content rather than trusting extensions.
6. Use generated object identifiers.
7. Separate public, protected, private, restricted, and quarantined semantics.
8. Generate controlled image variants.
9. Remove unnecessary EXIF/GPS metadata.
10. Keep verification media private.
11. Use short-lived controlled access for protected media.
12. Make cleanup jobs idempotent.
13. Keep expensive processing asynchronous.
14. Enforce quotas and limits server-side.
15. Record sensitive media access where required.
16. Keep provider-specific behavior behind adapters.
17. Keep API media semantics aligned with Document 14.
18. Keep schema aligned with Document 13.
19. Add negative-path security tests for every media access path.
20. Record material storage/security architecture changes through an ADR.

# 42. Acceptance Checklist

- [ ]  Media storage abstraction exists.
- [ ]  MySQL media metadata is authoritative.
- [ ]  Direct multipart uploads are authorized against the actor, target resource, media type and approved limits.
- [ ]  Upload limits are enforced.
- [ ]  File signatures/MIME types are validated.
- [ ]  Unsafe uploads are quarantined/rejected.
- [ ]  Image variants are generated.
- [ ]  EXIF/GPS metadata handling is defined.
- [ ]  Public/protected/private/restricted classifications are enforced.
- [ ]  Verification media is isolated.
- [ ]  Signed/temporary access is used where appropriate.
- [ ]  Storage paths are application-generated.
- [ ]  Client cannot publish media directly.
- [ ]  Media replacement is authorized.
- [ ]  Deleted media is removed from normal application access.
- [ ]  Orphan cleanup exists.
- [ ]  Upload abuse/rate limits exist.
- [ ]  Storage quotas are enforced.
- [ ]  Media operations are observable.
- [ ]  Backup/recovery covers metadata and binary objects.
- [ ]  Provider migration is reproducible.
- [ ]  Development/staging/production storage is isolated.
- [ ]  Security regression tests exist.
- [ ]  Document 13 and Document 14 remain authoritative for schema/API contracts.

# 43. Status

**Active — Media & File Storage Baseline**

This document is the authoritative architectural baseline for KHOJ BHET media and file handling. Implementation details may evolve, but storage abstraction, authorization boundaries, media classification, lifecycle, privacy, and security invariants must remain intact unless changed through the appropriate architecture/ADR process.

**Next document: 21. Search Architecture.**

## TV-07 Media Schema & Processing Gate — V1 Capability Boundary (2026-10-18)

The current physical `media` baseline includes `public_id`, `owner_user_id`, `storage_provider`, `storage_key`, `media_type`, `mime_type`, `file_size`, optional dimensions/duration, `processing_status`, `moderation_status`, timestamps and soft deletion; `media_variants` and `listing_media` provide variant/listing relationships. The schema does not establish dedicated access classification, checksum, separately detected MIME, generic target-resource association, or explicit quarantine state. Do not treat those as existing columns or rely on undocumented JSON for security-critical controls.

**Controls implementable without new columns:** authenticated upload; server-side owner/target authorization; allowlisted media type and size/count limits; content-signature/MIME consistency checks in the processing pipeline; generated storage names; non-executable private storage; safe image/video processing; authorization-controlled delivery; processing/moderation state transitions using only supported values; structured logs that exclude sensitive storage details. These controls still require code and runtime evidence before being claimed as implemented.

**Schema-gated capabilities:** durable quarantine lifecycle, checksum persistence, separate detected-MIME audit, generic resource targeting, and durable access classification require either approved physical fields/relationships or an explicit narrowed V1 contract. Payment proof remains outside MVP unless scope is changed; if enabled later, it must use private delivery and its own integrity gate.

**TV-07 remains BLOCKED** until each approved V1 media requirement is mapped to an existing column or a schema change, the DBML/migrations/validation SQL are reconciled, and tests cover spoofed MIME, malformed files, size/count boundaries, unauthorized ownership/attachment, processing failure, unsafe-file rejection, video limits/derivatives, and private-access denial. This is a design boundary, not evidence of runtime security.