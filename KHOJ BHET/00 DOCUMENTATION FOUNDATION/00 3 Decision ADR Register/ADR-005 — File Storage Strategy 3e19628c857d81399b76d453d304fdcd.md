# ADR-005 — File Storage Strategy

> ## V1 Media Processing Addendum — 2026-10-09
> 

> This addendum closes the V1 video-processing direction referenced by Document 14 Gate #06. V1 supports at most one listing video per listing: MP4 container, H.264 video, AAC audio, up to 50 MB and 60 seconds. Video processing is asynchronous; a video is not publicly playable until validation/transcoding succeeds. Generate a poster frame and an approved playback derivative, retain processing/failure state, and make retries idempotent.
> 

> 
> 

> V1 keeps local application/server storage behind the provider-agnostic storage abstraction. A CDN is not required for V1 and remains a later operational decision. Public video delivery must support HTTP byte-range requests; verify 206 responses and seeking through the actual Nginx/PHP/storage path. Configure reverse-proxy and PHP upload limits with safe headroom above the 50 MB maximum, bounded temporary storage, timeouts, and worker resource limits. Private media remains authorization-protected and must never be exposed through predictable public URLs.
> 

> 
> 

> **Schema gate remains open:** confirm the existing media.processing_status, media.moderation_status, media.duration_seconds and media_variants model can represent the required workflow. If not, extend Document 13 through a reviewed migration gate before implementation. This addendum does not itself prove that the processing pipeline or delivery path has been implemented or tested.
> 

# ADR Metadata

- **ADR ID:** ADR-005
- **Status:** Accepted
- **Date:** 2026-09-20
- **Decision Owner:** KHOJ BHET Project Team
- **Area:** Infrastructure / Media
- **Related ADRs:** ADR-001
- **Implementation Status:** Not started

# 1. Context

Marketplace listings depend heavily on media: images, thumbnails, videos, floor plans, documents, vehicle documents, land/property documents, and business profile media.

Media volume can grow much faster than normal relational data.

# 2. Decision Drivers

- Cost
- Storage capacity
- Upload reliability
- Image processing
- Thumbnail generation
- Video handling
- CDN delivery
- Access control
- Backup
- Retention
- Scalability
- Migration capability

# 3. Alternatives

## Local Server Storage

Store files on application/infrastructure disks.

## Object Storage

Store media in object storage while keeping metadata in the application database.

## Hybrid

Use local storage during early stages while designing a storage abstraction that can later move to object storage.

# 4. Decision

**Accepted decision:** KHOJ BHET will **start with local application/server storage** for V1, while maintaining a provider-agnostic **media storage abstraction** so the physical backend can later move to object storage without changing marketplace business logic.

The database stores media metadata and storage references, not large binary media as ordinary relational records. The initial implementation must keep storage operations behind the abstraction boundary.

No specific future object-storage provider is selected by this ADR.

# 5. Proposed Media Abstraction

Conceptually manage media ID, listing ID, media type, storage key, visibility, MIME type, size, dimensions, duration, thumbnail reference, processing status, sort order, primary-media flag, and timestamps.

The storage provider should be replaceable without changing marketplace business logic.

# 6. Security Considerations

Distinguish public listing media, restricted media, verification documents, and administrative documents. Sensitive documents must not become publicly accessible merely because a URL exists.

# 7. Consequences

Local storage is simple initially but creates scaling, backup, migration, and large-media delivery concerns. Object storage improves separation and scalability but adds provider configuration and operational dependencies.

# 8. Acceptance Criteria

Decide initial storage type, image processing, thumbnail generation, video processing, CDN strategy, backup, private-media access, retention, and migration strategy.

# 9. Related Documentation

- 
    1. Security Architecture
- 
    1. Media & File Storage
- 
    1. Infrastructure & Deployment
- ADR-001 — Application Architecture

# 10. Status History

- 2026-09-20 — Created as Decision Pending.
- 2026-09-28 — Accepted: local storage for V1 with a replaceable storage abstraction for future object storage.