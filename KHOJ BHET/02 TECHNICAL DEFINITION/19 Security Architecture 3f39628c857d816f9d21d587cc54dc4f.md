# 19. Security Architecture

> **Implementation status clarification — 2026-10-15:** “Active” means this is the current authoritative design baseline, not that implementation is release-ready. Implementation sign-off remains gated by the final OpenAPI 3.1 contract, successful clean-MySQL migration/runtime validation, and the relevant component tests. Component-specific schema or provider gates documented below remain independently binding.
> 

> ## Admin MFA Implementation Gate — 2026-10-09
> 

> MFA is required for all privileged administrative access. Document 13's current admins table does not define explicit MFA-secret/recovery-code columns. Before implementation, select and verify a Laravel/Filament-compatible MFA mechanism that securely persists enrollment, recovery and challenge state (through its supported schema/package), or approve a dedicated schema migration. Do not store MFA secrets in plaintext, generic logs, or undocumented JSON. The admin guard must deny privileged access until MFA is completed, and tests must cover enrollment, challenge failure, recovery, revocation, and administrator offboarding.
> 

## Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-TECH-019 |
| Status | Active — Security Architecture Baseline |
| Version | 1.0 |
| Owner | KHOJ BHET Engineering |
| Last Reviewed | 2026-10-08 |
| Parent | 02. TECHNICAL DEFINITION |
| Previous | 18. Authentication & Authorization |
| Next | 20. Media & File Storage |
| Related | 04 Users, Roles & Permissions; 08 Product & Business Rules; 09 Software Architecture; 10 Technology Stack; 12 Engineering Standards; 13 Database Architecture & Data Model; 14 API Specification; 15 Frontend Architecture; 16 Backend Architecture; 17 Mobile Application Architecture; 18 Authentication & Authorization; ADR-002 — Authentication Architecture |

# 1. Purpose

This document defines the production security architecture for KHOJ BHET.

It establishes the security controls, trust boundaries, threat model, data-protection rules, secure-development requirements, runtime protections, observability requirements, and incident-response expectations that apply across the web application, React Native/Expo mobile application, Laravel API/backend, Filament administration, MySQL, Firebase services, Redis, object/media storage, notification providers, payment providers, and external integrations.

This document answers **how KHOJ BHET is secured**. Architectural decisions that explain **why** a particular security boundary or control was selected remain in the ADR register.

# 2. Security Objectives

1. Protect user identity and account credentials.
2. Prevent unauthorized access to listings, private information, business resources, conversations, payments, and administration.
3. Prevent privilege escalation and insecure direct object reference (IDOR).
4. Protect restricted information such as exact location and direct contact details.
5. Protect payment and subscription state from client-side manipulation.
6. Preserve integrity of listings, catalogue data, moderation state, business membership, and ownership relationships.
7. Prevent abuse of OTP, authentication, messaging, media, search, listing, and payment endpoints.
8. Maintain confidentiality and integrity of operational and administrative data.
9. Minimize the blast radius of compromised credentials, devices, providers, or services.
10. Provide sufficient auditability to investigate security-sensitive actions.
11. Support privacy-aware data retention, deletion, anonymization, and access controls.
12. Make secure behavior the server-side default rather than depending on client behavior.

# 3. Security Principles

- **Zero trust between clients and the API.**
- **Default deny** for authentication, authorization, privileged operations, and protected data.
- **Least privilege** for users, business members, administrators, services, and infrastructure.
- **Server-side authority** for every security-sensitive decision.
- **Explicit trust boundaries** between Firebase, Laravel, clients, providers, and data stores.
- **Defense in depth** rather than reliance on one control.
- **Fail closed** when a security decision cannot be established safely.
- **Separation of duties** for administration, moderation, verification, payments, and technical operations where practical.
- **Secure by design** for new features and APIs.
- **No secrets in source control, client bundles, logs, URLs, or ordinary telemetry.**
- **Minimize sensitive data collection and exposure.**
- **Consistent security semantics** across web and mobile clients.

# 4. System Trust Boundaries

The principal security boundary is:

**Client → API authentication boundary → Laravel application → authorization/policy boundary → resource/data boundary → external provider boundary**

Primary trust zones:

| Zone | Examples | Trust Level |
| --- | --- | --- |
| Public | Public listing data, public catalogue metadata | Untrusted input / publicly readable |
| Client | Web browser, React Native/Expo app | Fully untrusted |
| Identity provider | Firebase Authentication | External trusted security service |
| Application | Laravel API/backend | Primary application authority |
| Administration | Filament/admin application | Highly privileged |
| Primary data | MySQL | Authoritative data store |
| Infrastructure | Redis, queues, workers | Trusted infrastructure; never client authority |
| Media | Object/file storage | Controlled data service |
| External providers | FCM, SMS, payment providers, maps | Limited third-party trust |
| Operations | Logs, metrics, audit records | Security-sensitive operational zone |

The client is never a trusted authority even when it is an official KHOJ BHET build.

# 5. Identity and Authentication Security

Authentication follows Document 18:

- Firebase Authentication authenticates normal marketplace users.
- Laravel verifies the Firebase ID token.
- Laravel maps Firebase UID to the authoritative MySQL marketplace user.
- Laravel evaluates account state and authorization.
- Admin identities use the separate Laravel/Filament administrative authentication boundary.

A valid authentication token does not itself grant access to any marketplace resource.

# 6. Authorization Security

Authorization is enforced in Laravel through:

1. Authentication.
2. Account-state evaluation.
3. Capability/permission evaluation.
4. Resource policy.
5. Ownership or delegation.
6. Business scope.
7. Resource lifecycle.
8. Verification requirements.
9. Entitlement/subscription requirements.
10. Privacy and restricted-data rules.
11. Moderation/safety/legal restrictions.

All protected operations are denied unless the complete policy permits the operation.

# 7. Data Security

MySQL is the authoritative application datastore.

Sensitive information must be protected through restricted database credentials, encrypted transport, controlled backups, least-privilege service accounts, secret management, limited administrative access, audit logging of privileged operations, and data minimization/retention controls.

Application authorization must not be delegated to database visibility alone.

# 8. Media Security

Media uploads are untrusted input.

The backend must validate:

- authenticated uploader;
- authorization to attach media to the target resource;
- MIME/type;
- file signature where applicable;
- size limits;
- image dimensions;
- extension consistency;
- malware/content scanning where supported;
- storage path ownership;
- access policy.

Original filenames must not be treated as storage identifiers.

Executable content must never be accepted into an executable web-serving location.

Private/restricted media must use controlled access rather than public permanent URLs.

# 9. Threat Model

| Threat | Primary Control |
| --- | --- |
| Forged/invalid token | Firebase token verification |
| Expired/revoked session | Token/account-state checks |
| IDOR | Resource policies and ownership checks |
| Privilege escalation | Capability-based authorization and default deny |
| Business-scope escalation | Explicit business membership scope |
| Admin privilege abuse | Separate admin boundary and MFA |
| Client-side price/subscription manipulation | Server-side entitlement/payment verification |
| OTP abuse | Rate limiting, attempt limits, expiry |
| Account enumeration | Generic responses and throttling |
| Credential/token leakage | Secure storage, transport, log redaction |
| Malicious uploads | Validation, scanning, storage isolation |
| XSS | Output encoding, sanitization, CSP where applicable |
| CSRF | Appropriate framework/browser protections |
| SQL injection | Parameterized queries/query builder/ORM |
| Mass assignment | Explicit fillable/validated fields and DTO/request validation |
| Replay/double mutation | Idempotency and state validation |
| Webhook forgery | Provider signature verification |
| Webhook replay | Timestamp/event-ID/idempotency controls |
| Denial of service | Edge protections, rate limits, queue isolation, resource limits |

# 10. Input Validation and Output Security

Every externally supplied value is untrusted.

Validation is required for query parameters, path identifiers, JSON bodies, multipart uploads, headers used by application logic, webhook payloads, payment callbacks, notification-provider callbacks, and imported catalogue/configuration data.

Validation must be allowlist-oriented where possible, type-aware, length-bounded, range-bounded, normalized consistently, and applied server-side.

The API must return only fields the caller is authorized to receive.

Never expose internal secrets, raw authentication tokens, password hashes, OTPs, provider credentials, internal security configuration, unrestricted database records, private moderation notes, or hidden exact location/contact data.

# 11. API Security

All protected /api/v1 endpoints must conform to Document 14.

Required controls include:

- HTTPS/TLS in production;
- bearer-token verification where authentication is required;
- explicit endpoint authorization;
- request validation;
- rate limiting;
- idempotency for applicable mutations;
- consistent error envelopes;
- safe pagination limits;
- resource-level authorization;
- restricted-field response shaping;
- audit logging for security-sensitive actions.

The API must not trust client-supplied user IDs, owner IDs, business IDs as proof of membership, roles, admin/verification/subscription flags, payment state, or unauthorized lifecycle transitions.

# 12. Web Security

The web frontend must use HTTPS, avoid storing privileged secrets in browser storage, avoid exposing server credentials in JavaScript bundles, use secure cookie attributes where cookies are used, use appropriate CSRF protection for cookie-authenticated state-changing requests, use content security policy where compatible, sanitize/encode user-generated content, prevent open redirects, validate external URLs, protect privileged routes server-side, and treat SEO/public rendering as separate from authorization.

Search-engine visibility must never bypass API authorization.

# 13. Mobile Security

The React Native/Expo application must use HTTPS only in production, use platform-secure mechanisms for sensitive local credentials/tokens, avoid embedding server secrets, treat local state as potentially compromised, avoid logging authentication tokens or sensitive user data, validate deep-link targets, re-check authorization after app resume where necessary, handle token/session expiry safely, avoid relying on local role/entitlement state for access decisions, and use certificate/public-key pinning only if justified and operationally supportable.

Rooted/jailbroken devices are not assumed trustworthy.

# 14. Authentication, Session, and Token Security

Firebase Authentication owns marketplace OTP verification and its supported expiry, attempt, resend, and provider abuse controls, as defined in Document 18. KHOJ BHET must configure and monitor those provider controls rather than implement a second OTP verifier in Laravel.

Additional requirements:

- OTP values must never be logged by the application.
- Laravel business APIs must never accept OTP codes as business payloads.
- Apply Firebase App Check where supported and restrict SMS destinations to Nepal (+977) where supported by the chosen Firebase configuration.
- Monitor SMS spend and abuse indicators; provider configuration must be verified in the deployed Firebase project.
- Authentication endpoints must resist enumeration.
- Account recovery must not silently change ownership.
- Authentication-provider linking requires proof of control.
- Authentication credentials must never be stored by KHOJ BHET unless a future architecture explicitly requires it.
- Admin authentication remains separate from marketplace authentication.
- Privileged admin access requires MFA.
- Firebase ID tokens are bearer credentials and must be treated as secrets.
- Tokens must never appear in URLs, logs, analytics events, or unnecessary third-party requests.
- Backend authorization must be evaluated on every protected operation.
- Account suspension/deactivation overrides stale client session state.

# 15. Sensitive Data Protection

Sensitive or potentially sensitive data includes authentication identifiers, phone numbers, email addresses, exact property/location information, direct contact information, identity-verification information, business membership information, private conversations, payment references, subscription state where commercially sensitive, push-device identifiers, moderation/admin records, security/audit records, and provider credentials/secrets.

Restricted information must be exposed only through explicit server-side policy.

Premium access does not override privacy, moderation, legal, suspension, or account restrictions.

# 16. Encryption

## 16.1 Data in Transit

Production traffic must use TLS for web-to-API, mobile-to-API, Laravel-to-provider APIs, payment-provider communication, webhook endpoints, administrative interfaces, and storage operations where supported.

Plain HTTP must not be used for authenticated production traffic.

## 16.2 Data at Rest

Sensitive infrastructure data should use provider/disk/database encryption at rest where available.

Application-level encryption should be used when required beyond storage-level encryption.

Encryption keys must be managed separately from encrypted data and never committed to source control.

# 17. Secrets Management

Secrets include Firebase service credentials, API keys, payment credentials, webhook secrets, database passwords, Redis credentials, SMTP/SMS credentials, storage credentials, admin integration secrets, and CI/CD deployment credentials.

Rules:

- never commit secrets to Git;
- never place server secrets in web/mobile bundles;
- use environment/secret-management mechanisms;
- rotate compromised credentials immediately;
- maintain separate development/staging/production credentials;
- restrict secret access by service;
- redact secrets from logs and error reports.

Production .env files containing secrets must never be committed.

# 18. Database Security

MySQL security baseline:

- dedicated application DB user;
- minimum required privileges;
- separate administrative credentials;
- no application use of root;
- network access restricted to required services;
- encrypted backups;
- tested restore procedures;
- migration-controlled schema changes;
- parameterized queries;
- database connection secrets managed outside source control.

Destructive production database operations require controlled deployment/administrative procedures.

# 19. Redis, Queues, and Workers

Redis is infrastructure, not an authorization authority.

Rules:

- Redis must not be publicly exposed.
- Require authentication where supported/configured.
- Restrict network access.
- Do not store plaintext secrets unnecessarily.
- Queue payloads contain only necessary data.
- Sensitive queued jobs revalidate current authorization/state when executed.
- Workers run with least-privilege service credentials.
- Background jobs must not impersonate a user merely by carrying a user ID.
- Security-sensitive jobs must be idempotent.

# 20. Webhook and Provider Security

Every provider callback is untrusted until verified.

Payment, notification, storage, or other webhooks must:

1. Validate request authenticity/signature.
2. Validate event type.
3. Validate required identifiers.
4. Validate timestamp/replay constraints where supported.
5. Apply idempotency.
6. Reconcile state against authoritative internal records.
7. Record the outcome.
8. Never trust client-provided payment/subscription status.

A successful client redirect is not proof of payment.

# 21. Rate Limiting and Abuse Prevention

Rate limiting is required for abuse-sensitive operations including authentication, OTP, recovery, listing creation/editing, messaging, search, media upload, favorites, reporting, payment initiation, verification submission, admin endpoints, and public high-cost API operations.

Limits should be scoped appropriately by identity, IP, resource, endpoint, and operation. IP-only controls are insufficient for authenticated abuse.

# 22. Business and Marketplace Abuse Controls

Controls must cover fake/spam listings, repeated listing creation, fraudulent contact behavior, prohibited content, abusive messaging, payment manipulation, subscription entitlement abuse, business membership abuse, impersonation, malicious media, location/contact scraping, and automated harvesting of restricted information.

Moderation and security controls must work together without granting moderators unrestricted technical privileges.

# 23. Administrative Security

Administration is a high-risk trust zone.

Required baseline:

- separate admin identity boundary;
- MFA;
- least-privilege admin roles;
- explicit capability grants;
- secure session management;
- administrative audit logging;
- restricted production database access;
- no shared administrator accounts;
- strong re-authentication for highly sensitive operations;
- controlled emergency/break-glass access.

Administrative actions affecting roles, permissions, verification, moderation, payments, entitlements, or account state must be auditable.

# 24. Logging, Monitoring, and Audit

Security telemetry must distinguish application logs, operational metrics, security events, and auditable administrative actions.

Security-sensitive events include authentication failures, account recovery, suspicious token/session events, privilege changes, business membership changes, listing ownership/delegation changes, moderation actions, verification decisions, subscription/entitlement changes, payment reconciliation, account suspension/deactivation, admin authentication events, and sensitive-data access where required.

Never log passwords, OTP values, bearer tokens, provider secrets, full payment credentials, or unnecessary sensitive personal data.

Use correlation/request IDs to connect API, worker, and provider events.

# 25. Privacy and Data Lifecycle

Security and privacy requirements apply across:

**collect → validate → store → use → expose → retain → archive/delete/anonymize**

Principles:

- collect only necessary information;
- define retention requirements by data class;
- restrict access;
- avoid unnecessary replication;
- support account deactivation/deletion according to product rules;
- anonymize or delete data when required;
- consider backups and replicas in deletion/retention design;
- prevent deleted/deactivated identities from retaining unintended privileges.

# 26. Dependency and Supply-Chain Security

Backend and frontend dependencies must use controlled package manifests and lockfiles.

Required practices include reviewing dependency advisories, updating deliberately, avoiding abandoned/high-risk packages where practical, using lockfiles, reviewing critical transitive dependencies, scanning dependencies in CI, pinning deployment/runtime versions appropriately, and reviewing untrusted package installation scripts.

# 27. Secure Development Lifecycle

For each new feature:

1. Identify assets.
2. Identify trust boundaries.
3. Identify abuse cases.
4. Define authorization rules.
5. Define sensitive data exposure.
6. Validate inputs.
7. Define rate limits.
8. Define audit requirements.
9. Define failure behavior.
10. Add security tests.
11. Review dependencies and secrets.
12. Verify API contract and client behavior.

Security review is required for changes involving authentication, authorization, payments, restricted information, admin capabilities, external webhooks, media, or data exports.

# 28. Security Testing

Automated testing must cover valid/expired/invalid tokens, wrong Firebase project/audience, unknown UID, suspended/deactivated accounts, provisioning races, own/other resources, business roles, cross-business access, moderator/admin boundaries, expired entitlement, missing verification, restricted fields, IDOR, privilege escalation, injection, XSS, CSRF where applicable, replay, rate-limit bypass, webhook forgery/replay, path traversal, malicious uploads, open redirects, safe 401/403/404 behavior, validation failures, concurrency conflicts, and idempotent retries.

# 29. Incident Response

Security incidents follow:

**Detect → Triage → Contain → Preserve evidence → Eradicate → Recover → Verify → Communicate → Root-cause analysis → Preventive action**

Potential containment actions include credential rotation, account suspension, integration disablement, session invalidation where supported, abusive-traffic blocking, vulnerable-feature disablement, provider-secret rotation, and infrastructure isolation.

Incident response procedures must not depend solely on a potentially compromised application component.

# 30. Backup and Recovery Security

Backups must be access controlled, encrypted, monitored, retained according to policy, separated from ordinary application credentials, and tested through restoration exercises.

A backup that cannot be restored is not a reliable recovery control.

Recovery procedures must preserve security controls and must not restore compromised credentials or unauthorized privileges.

# 31. Production Security Configuration Baseline

Production baseline:

- HTTPS enforced;
- debug disabled;
- sanitized production errors;
- secure headers configured;
- admin MFA enabled;
- secrets externalized;
- database access restricted;
- Redis access restricted;
- queue workers isolated appropriately;
- rate limiting enabled;
- backups enabled;
- monitoring enabled;
- audit logging enabled;
- dependency/security checks enabled;
- development/test credentials prohibited;
- default accounts/passwords removed or disabled.

# 32. Security Headers and Browser Controls

The web/API deployment should configure appropriate security headers, including where applicable:

- Content-Security-Policy;
- Strict-Transport-Security;
- X-Content-Type-Options;
- Referrer-Policy;
- frame/embedding restrictions;
- appropriate Permissions-Policy.

Header configuration must be validated against the final frontend, analytics, payment, map, authentication, and media integrations.

# 33. Error Handling

Security errors must fail safely.

Rules:

- do not expose stack traces in production;
- do not expose SQL errors;
- do not reveal provider credentials/configuration;
- avoid account/resource enumeration;
- use consistent API error envelopes;
- provide enough correlation information for support without exposing internal details.

Detailed diagnostics belong in controlled server-side logs.

# 34. Security Invariants

1. The client is never the authorization authority.
2. A Firebase UID alone is not a marketplace permission.
3. A subscription is not a role.
4. Verification is not authorization.
5. Listing ownership is not automatically seller/business authority.
6. Business membership is scoped.
7. Resource identifiers do not grant access.
8. Admin identity is separate from normal marketplace identity.
9. Payment redirects do not prove payment.
10. Webhooks are untrusted until verified.
11. Push-device registration grants no permissions.
12. Redis/cache state cannot override authoritative security state.
13. Hidden UI cannot substitute for backend authorization.
14. Exact location/contact access is server-controlled.
15. Security-sensitive mutations must be idempotent or otherwise protected against duplicate execution where applicable.
16. Privilege changes must be auditable.
17. Secrets never belong in source control or client applications.

# 35. Cross-Document Security Contracts

| Document | Security Contract |
| --- | --- |
| 04 Users, Roles & Permissions | Defines user/role concepts; this document defines security enforcement |
| 08 Product & Business Rules | Business constraints must be enforced server-side |
| 09 Software Architecture | Defines service boundaries and system-level structure |
| 10 Technology Stack | Defines security-relevant platform choices |
| 12 Engineering Standards | Defines secure coding/testing standards |
| 13 Database Architecture & Data Model | Defines authoritative data structures and integrity |
| 14 API Specification | Defines public API contract and security requirements |
| 15 Frontend Architecture | Defines web-side security behavior and SEO/public boundaries |
| 16 Backend Architecture | Defines Laravel enforcement mechanisms |
| 17 Mobile Application Architecture | Defines mobile trust and secure-storage boundaries |
| 18 Authentication & Authorization | Defines identity, authentication, roles, capabilities, and authorization |
| 19 Security Architecture | Defines cross-system security controls and threat model |

# 36. Implementation Rules

1. Every new protected endpoint requires an explicit authorization definition before implementation.
2. Every new sensitive field requires an exposure classification.
3. Every new external integration requires a trust-boundary review.
4. Every webhook requires authenticity and replay protection.
5. Every privileged admin capability requires explicit permission and auditability.
6. Every upload path requires validation and storage isolation.
7. Every security-sensitive mutation must define replay/idempotency behavior.
8. Every authentication/recovery flow must define abuse limits.
9. Every client-visible permission must have an authoritative server-side equivalent.
10. Every new secret must have a defined storage and rotation mechanism.
11. Every security-sensitive feature must have negative-path tests.
12. Production configuration must fail closed when security prerequisites are missing.
13. Security-sensitive logs must be structured and redacted.
14. Security controls must be applied consistently across web and mobile API consumers.
15. Security-sensitive trust-boundary changes require an ADR.

# 37. Acceptance Checklist

- [ ]  Firebase authentication boundary implemented.
- [ ]  Laravel authorization is authoritative.
- [ ]  Admin authentication is isolated.
- [ ]  Default-deny authorization is enforced.
- [ ]  Resource ownership/delegation policies are implemented.
- [ ]  Business scope is enforced.
- [ ]  Restricted fields have explicit policies.
- [ ]  Rate limits exist for abuse-sensitive endpoints.
- [ ]  OTP/recovery abuse controls exist.
- [ ]  Webhooks use authenticity verification and idempotency.
- [ ]  Media validation and storage isolation exist.
- [ ]  Secrets are externalized.
- [ ]  Production TLS is enforced.
- [ ]  Database and Redis are network restricted.
- [ ]  Admin MFA is enforced.
- [ ]  Security audit events are captured.
- [ ]  Sensitive logs are redacted.
- [ ]  Dependency/security scanning is included in CI.
- [ ]  Security regression tests exist.
- [ ]  Backup/restore procedures are tested.
- [ ]  Incident-response procedure is documented.
- [ ]  Security-sensitive changes have ADR coverage where required.

# 38. Status

**Active — Security Architecture Baseline**

This document is the authoritative cross-system security baseline for KHOJ BHET. Detailed implementation may evolve, but implementation must not weaken the security invariants defined here without an explicit architecture/security review.

**Next document: 20. Media & File Storage.**

## TV-06 Admin MFA Gate — Decision Baseline (2026-10-18)

**Required V1 security outcome:** all privileged Filament/admin access must complete MFA. Enforce this on the server-side admin authentication path, not only in UI navigation. Deny privileged access when enrollment or challenge is incomplete; cover alternate routes, session persistence, recovery and offboarding.

**Recommended implementation direction:** select a maintained Laravel/Filament-compatible TOTP or WebAuthn implementation only after checking compatibility with the pinned stack. Prefer per-admin encrypted MFA secret storage and hashed, single-use recovery codes; never log secrets or recovery codes. Require re-authentication for enrollment changes, factor reset and recovery-code regeneration. Audit enrollment, successful/failed challenges, recovery, factor reset and admin disablement without logging factor material.

**Schema boundary:** the current `admins` baseline has no explicit MFA enrollment/recovery fields. Use the chosen implementation's documented migration if appropriate, or approve a dedicated migration; do not assume fields exist or store MFA state in undocumented JSON. TV-06 remains BLOCKED until implementation, schema review and bypass/recovery tests are evidenced.

## TV-07 Media Security Verification Matrix — 2026-10-18

Before media release, verify upload authentication and target authorization; allowlisted extension, detected MIME and file signature consistency; strict file-size/count/dimension/duration limits; generated storage identifiers; storage isolation from executable web roots; processing sandbox and failure handling; ownership checks on attach, replace, delete and deliver; private-media access denial to unauthorized users; safe image derivatives and video poster/playback outputs; and logs that exclude credentials, signed URLs and sensitive storage paths. Do not claim durable quarantine, checksum persistence, access-classification persistence, or generic target-resource persistence until supported by the physical schema or explicitly implemented with an approved alternative. TV-07 remains BLOCKED pending reproducible tests.