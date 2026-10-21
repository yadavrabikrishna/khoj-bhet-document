# 27. Monitoring, Logging & Backup

**Project:** KHOJ BHET  

**Document ID:** KB-ENG-027  

**Section:** 03. ENGINEERING & QUALITY  

**Status:** Active — Monitoring, Logging & Backup Baseline; implementation and provider choices require approval  

**Version:** 1.0  

**Owner:** KHOJ BHET Engineering  

**Last Reviewed:** 2026-10-15  

**Previous:** 26. Infrastructure & Deployment  

**Next:** 28. Git & GitHub Workflow

---

# 1. Purpose

Define the operational observability, application and infrastructure logging, alerting, backup, restore, and recovery requirements for KHOJ BHET.

The goal is to detect user-impacting failures, investigate them without exposing sensitive data, preserve recoverable copies of important state, and prove that recovery procedures work. This document defines the target operating standard; it does not claim that monitoring, backups, or production alerting are already deployed.

# 2. Scope

This document applies to the complete KHOJ BHET system:

- Laravel 13 backend, REST API, and business workflows.
- FilamentPHP 5 administration and privileged actions.
- Next.js public web application and SEO-critical public routes.
- React Native + Expo mobile clients and supported release channels.
- MySQL transactional data, schema, migrations, and database operations.
- Firebase Authentication integration and token-verification dependencies.
- Listing media, uploaded files, derivatives, and media metadata.
- Search indexes or external search services, if adopted.
- Queue workers, scheduled tasks, notifications, email/SMS, and push delivery.
- Payments: V1 is manual proof submission with admin approval. Gateway integrations such as eSewa, Khalti, connectIPS and Fonepay are future-phase; the callback and reconciliation monitoring below applies only once a gateway is approved.
- Infrastructure, deployment events, TLS/DNS, external providers, and CI/CD release evidence.

Monitoring provider, log platform, backup product, cloud provider, and hosting topology remain explicit implementation decisions until recorded and approved.

# 3. Operational Principles

1. **User impact first:** alerts must focus on availability, data integrity, security, payment correctness, and critical user journeys.
2. **Actionable telemetry:** every alert has severity, owner, response guidance, and a runbook or documented next step.
3. **No secrets in logs:** tokens, passwords, signing keys, payment credentials, and unnecessary personal data must never be logged.
4. **Backups must be restorable:** a successful backup job is not proof of recoverability.
5. **Separate failure domains:** backup copies must not all depend on the same account, host, disk, or failure domain as production.
6. **Least privilege:** monitoring and backup identities receive only the permissions needed for their tasks.
7. **Environment separation:** production telemetry and backups are isolated from development and staging.
8. **Evidence and auditability:** incidents, restores, backup tests, and material operational changes are recorded.
9. **Measured objectives:** RPO, RTO, retention, SLOs, and alert thresholds are approved based on business impact and actual workload, not invented values.
10. **Derived data can be rebuilt only if proven:** search indexes, caches, and media derivatives are recoverable only when their source-of-truth and rebuild procedure are documented and tested.

# 4. Service Inventory and Criticality

Maintain an operational inventory for each production component. Each entry must include owner, environment, purpose, dependencies, health signal, alert route, backup/recovery classification, runbook, and external support contact where relevant.

| Component | Primary signals | Recovery consideration |
| --- | --- | --- |
| Public web / Next.js | Availability, latency, 4xx/5xx trends, build/runtime errors, SEO route checks | Redeploy a known-good artifact; preserve public routing and metadata behavior |
| Laravel API | Request rate, latency, 5xx, validation/auth failures, dependency latency | Restore service with compatible artifact/configuration; verify business workflows |
| MySQL | Availability, connections, slow queries, locks, replication/backup status if applicable, disk growth | Point-in-time or backup restore if configured; validate schema and data integrity |
| Firebase Authentication integration | Token verification errors, provider errors/latency, configuration failures | Check provider status/configuration; never log raw ID tokens |
| Media/object storage | Upload/download failures, storage capacity, unauthorized access, missing objects | Restore objects and metadata; validate permissions and media references |
| Queue workers | Queue depth/age, failed jobs, retries, worker liveness | Restart safely; retry idempotent jobs and reconcile side effects |
| Scheduled tasks | Last successful execution, duration, missed/duplicate runs | Rerun safely after checking idempotency and impact |
| Notifications | Accepted/sent/delivered/failure states where available, provider errors, invalid device tokens | Retry within policy; avoid duplicate or excessive sends |
| Payments | Callback verification failures, pending/failed reconciliation, duplicate events, amount/status mismatches | Reconcile against verified provider records; do not blindly replay financial actions |
| Search | Query errors/latency, indexing lag, stale or missing records | Rebuild/reindex from authoritative database data if the index is derived |
| DNS/TLS/edge | Probe failures, certificate expiry, routing errors, rate-limit/WAF events | Correct records/certificates/rules and verify public reachability |
| Backup pipeline | Last successful backup, age, size anomalies, integrity/restore-test result | Escalate missed backups; restore-test and document gaps |

Assign criticality based on the approved service objectives. Do not treat every warning as a production incident; establish thresholds and response expectations appropriate to each component.

# 5. Observability Model

Use four complementary signal classes:

- **Metrics:** numeric time series such as request latency, error rate, database connections, queue depth, disk usage, and backup age.
- **Logs:** structured events for requests, failures, security-relevant actions, background jobs, provider callbacks, and operational changes.
- **Traces/correlation:** request or job identifiers that help connect web/API operations, database calls, queue work, and external calls where supported.
- **Synthetic checks:** scheduled checks of public endpoints and critical journeys from outside the application process.

Observability must cover both component health and user-visible outcomes. A green process-health check does not prove that login, listing creation, image delivery, search, payment reconciliation, or notification delivery is working.

# 6. Application Logging Standards

## 6.1 Structured fields

Where practical, application logs should be structured and include:

- UTC timestamp and severity.
- Environment and application/service name.
- Release/version identifier and source commit where available.
- Event name and safe error category.
- Request/correlation ID and job ID where applicable.
- Route or operation name, HTTP status, and duration.
- Provider/service name and safe outcome code for external calls.
- Actor type and internal identifier only when necessary and permitted.
- Exception class and sanitized stack/context for server-side debugging.

Do not place full request/response bodies into logs by default. Use allowlisted fields and explicit redaction for any diagnostic payloads.

## 6.2 Sensitive data prohibited from logs

Never log:

- Passwords, password reset secrets, OTP values, session secrets, or private keys.
- Firebase ID tokens, refresh tokens, authorization headers, or service-account credentials.
- Database passwords, application encryption keys, webhook signing secrets, or CI/CD tokens.
- Full payment credentials or sensitive provider payloads not required for safe reconciliation.
- Unnecessary personal data, private messages, precise location, identity documents, or uploaded file contents.
- Full signed media URLs if they contain access-bearing query parameters.

For authentication failures, log the reason category and request/correlation ID—not the credential or bearer token. For payment events, log a safe internal transaction reference and verified state transitions, not secret credentials.

## 6.3 Severity levels

- **DEBUG:** temporary development diagnostics; disabled or tightly controlled in production.
- **INFO:** meaningful expected events, lifecycle milestones, and successful operational actions.
- **WARNING:** unexpected but recoverable conditions, retries, degraded dependencies, or approaching capacity thresholds.
- **ERROR:** failed operation requiring investigation, but not necessarily a broad outage.
- **CRITICAL:** severe service outage, data-integrity risk, security incident, or failure requiring urgent response.

Severity must reflect operational impact, not merely the fact that an exception occurred.

# 7. Audit Logging for Privileged and Sensitive Actions

Maintain auditable events for actions such as:

- Administrator sign-in/access denials and changes to administrative permissions.
- Listing moderation, suspension, removal, or restoration.
- Payment approval/rejection, refunds or reversals if supported, and manual transaction corrections.
- Changes to critical configuration, integrations, and access controls.
- Data export, bulk operations, account restrictions, and other high-impact administrative actions.
- Production deployment, migration, backup policy, restore, and secret rotation events.

Audit records should identify the actor, action, target reference, timestamp, outcome, and a safe reason or change reference. Avoid storing unnecessary copies of personal or payment data in the audit record. Restrict alteration/deletion of audit events and define retention according to security, legal, and operational requirements.

# 8. Metrics and Service-Level Objectives

Define service-level indicators (SLIs) and service-level objectives (SLOs) for production before launch. Proposed indicators include:

- Public web availability and successful rendering of key public listing routes.
- API availability, latency percentiles, and server-error rate.
- Login/token-verification success and provider dependency health.
- Listing create/update/publish flows and moderation processing.
- Media upload and authorized delivery success.
- Search latency and indexing freshness, if a separate index is used.
- Payment callback processing and reconciliation lag.
- Notification queue age and provider failure rate.
- Queue processing latency, failed-job rate, and scheduled-task completion.
- Database availability, connection saturation, query latency, storage growth, and backup freshness.
- Backup restore-test success and achieved recovery time.

For each SLO, record the target, measurement window, exclusions, owner, alert policy, and corrective action. Set numeric targets only after product criticality, hosting capability, expected traffic, and support coverage are agreed. Avoid reporting a single aggregate uptime figure that hides failures in critical workflows.

# 9. Alerting and Escalation

Each production alert must specify:

- Alert name and condition.
- Severity and user/business impact.
- Evaluation window and anti-flapping policy.
- Responsible owner and escalation path.
- Runbook or initial diagnostic steps.
- Recovery objective or response expectation where approved.
- Required post-incident evidence.

## 9.1 Initial alert categories

- **Availability:** public site/API unreachable, repeated 5xx spikes, failed readiness checks.
- **Latency/capacity:** sustained latency increase, database connection saturation, disk/storage nearing an approved threshold, memory/CPU pressure.
- **Data integrity:** payment status/amount mismatch, migration failure, unexpected database constraint failures, missing media references.
- **Asynchronous processing:** queue age/depth above approved limits, repeated failed jobs, missed scheduled work.
- **Security:** suspicious authentication/authorization patterns, repeated admin access denials, unexpected privileged changes, secret exposure indicators.
- **External providers:** sustained Firebase, payment, notification, or storage failures.
- **Backup/recovery:** missed backup, unexpected backup-size change, stale recovery point, failed integrity or restore test.
- **DNS/TLS:** certificate expiry approaching policy threshold, DNS resolution failures, edge routing errors.

Thresholds must be calibrated from baseline behavior and tested in staging. Route critical alerts to a monitored channel; an alert that nobody owns is not an operational control.

# 10. Health Checks and Synthetic Monitoring

Implement safe health endpoints appropriate to the deployment platform:

- **Liveness:** confirms the process is alive and not irrecoverably stuck.
- **Readiness:** confirms the instance can safely receive traffic, including required startup/configuration checks.
- **Dependency health:** checks critical dependencies with bounded timeouts and without exposing credentials or internal diagnostics.

Do not make every optional provider outage cause all application instances to fail readiness. Define which dependencies are essential for serving requests and degrade gracefully where safe.

Synthetic checks should cover public availability and selected critical flows using test accounts and sandbox providers. They must not create real payments, send messages to real customers, publish unintended listings, or expose test credentials. Keep staging and synthetic test data isolated.

# 11. Backup Strategy and Coverage

The following are backup candidates; the final policy must explicitly classify each as **backed up**, **replicated**, **rebuildable**, or **not retained**, with a rationale.

| Data or artifact | Source of truth / recovery approach | Required control |
| --- | --- | --- |
| MySQL transactional data | Authoritative database backup; point-in-time recovery if supported and approved | Automated backups, retention, integrity checks, restore rehearsal |
| Database schema and migrations | Version-controlled migrations and schema artifacts | Repository protection and release/version traceability |
| Listing media and uploaded files | Durable object/file storage | Independent backup/versioning or documented equivalent recovery |
| Media metadata and object references | MySQL plus storage inventory | Restore consistency checks between database and objects |
| Search index | Usually derived from authoritative records, if architecture defines it as rebuildable | Documented and tested reindex procedure; preserve required synonyms/configuration |
| Cache | Usually transient/derived | Document cache semantics and invalidation/repopulation procedure |
| Queues and failed-job records | Depends on queue technology and business criticality | Define durability, recovery, and safe replay policy |
| Configuration and infrastructure definitions | Version-controlled sanitized configuration and approved secret references | Repository backup/access controls; do not put secret values in backups unnecessarily |
| Secrets and encryption keys | Approved secret-management/recovery process | Restricted escrow/recovery, rotation procedure, and separation of duties |
| CI/CD release artifacts | Artifact registry or reproducible build process | Retain approved production artifacts and provenance |
| Operational/audit logs | Approved logging destination and retention policy | Access control, tamper resistance where required, and export/recovery policy |
| Mobile signing credentials | Protected credential storage and controlled recovery | Very restricted access; tested recovery procedure; never commit keys |

Backups must cover the data needed to restore a coherent service, not only the MySQL database. The exact approach depends on selected hosting and storage providers.

# 12. Recovery Objectives: RPO and RTO

- **Recovery Point Objective (RPO):** maximum tolerable amount of data loss measured in time.
- **Recovery Time Objective (RTO):** target maximum time to restore an agreed service level after disruption.

RPO and RTO must be set separately where appropriate for transactional database data, media, and whole-service recovery. Payment and account data may require stricter objectives than rebuildable caches or search indexes.

Before production approval, record:

- Approved RPO and RTO by data/service class.
- Backup frequency and retention that can meet those objectives.
- Recovery dependencies and restore order.
- Who can authorize a restore or failover.
- Whether point-in-time recovery, replication, or a secondary environment is available and tested.
- Evidence that the measured recovery time and recovered data point meet the objective.

Do not publish numeric RPO/RTO promises before the deployment and backup capabilities are selected and tested.

# 13. MySQL Backup and Restore Controls

MySQL is the authoritative transactional database for KHOJ BHET.

- Use a backup method compatible with the selected MySQL version, database size, transaction workload, and recovery objectives.
- Document whether backups are logical, physical, snapshots, point-in-time recovery logs, or a combination.
- Encrypt backup data in transit and at rest and restrict access to the backup identity.
- Monitor backup age, completion, duration, size, and errors.
- Include required database objects and configuration in the recovery plan, including schema, indexes, constraints, and required routines/events if adopted.
- Define how consistency is maintained between database backups and media/object storage.
- Use least-privilege backup and restore accounts; production restore privileges must be tightly controlled.
- Validate restores against schema expectations, row/record sanity checks, and representative application queries.
- Keep production restore tests isolated so they cannot overwrite or expose the live database.
- Document the exact recovery point and any data-loss window when restoring from a backup.

A database dump or snapshot that has never been restored is an unverified recovery artifact.

# 14. Media, Search, and Derived Data Recovery

## 14.1 Media

Listing images and user-uploaded files are user-visible data. Define the backup/versioning strategy for original uploads, processed derivatives, metadata, access permissions, and deletion lifecycle. After restore, verify object existence, expected ownership/visibility, and database references. Do not make private or moderated media public as a side effect of restoration.

## 14.2 Search

If a separate search index is used, MySQL remains the authoritative source unless a later approved architecture explicitly says otherwise. Define a repeatable reindex process, batch sizing, progress monitoring, consistency checks, and safe cutover. Track indexing lag and failed indexing jobs. Rebuilding an index must not change listing visibility or authorization rules.

## 14.3 Cache and queues

Document which cache entries are disposable and which queue records represent important pending work. After a cache flush, monitor repopulation load. Before replaying jobs, check idempotency and external side effects. Never blindly replay payment, notification, or provider-callback jobs without reconciliation rules.

# 15. Payment, Notification, and External Event Observability

Payment and notification workflows require event-level visibility without logging sensitive provider credentials or payloads.

For payment processing:

- Track internal transaction reference, provider, amount/currency where policy permits, state transition, timestamps, callback verification result, and reconciliation status.
- Alert on verified callback failures, repeated pending states, duplicate events, unexpected amount/status mismatch, and reconciliation lag.
- Preserve sufficient evidence to investigate disputes while following data minimization and retention rules.
- Reconcile with provider records before manually changing state or replaying a payment event.

For notifications:

- Track safe internal notification reference, channel, enqueue time, attempt count, provider outcome, and final state where available.
- Monitor invalid device tokens, provider throttling, sustained failures, and backlog.
- Avoid logging message bodies or recipient details unless specifically required and approved.
- Make retry behavior bounded and prevent duplicate notifications where feasible.

For Firebase and other external dependencies, record safe error categories, latency, and correlation identifiers. Never log raw tokens or credentials. Define degraded-mode behavior and operator checks for provider outages.

# 16. Log Retention, Access, and Privacy

Define log retention by purpose and risk, including application logs, security/audit logs, infrastructure logs, CI/CD logs, payment reconciliation evidence, and backup logs.

- Restrict log access by role and environment.
- Use separate production access permissions from development access.
- Protect audit/security logs from unauthorized alteration or deletion where feasible.
- Apply retention and deletion policies consistently; do not keep logs indefinitely by default.
- Avoid collecting sensitive data that is not needed for troubleshooting or accountability.
- Sanitize user-provided strings before rendering them in log viewers or incident reports to prevent log injection.
- Review whether third-party logging services store data outside approved regions or retain data longer than intended.
- Ensure support exports and incident attachments follow the same access and redaction rules.

Exact retention durations must be approved after legal, privacy, security, provider, and cost requirements are reviewed.

# 17. Backup Security and Separation

- Encrypt backups in transit and at rest.
- Keep backup copies separate from the primary production account or failure domain where feasible.
- Restrict deletion and retention-policy changes to specifically authorized identities.
- Use MFA and approval controls for destructive backup administration where available.
- Monitor for unexpected backup deletion, encryption changes, access-policy changes, or unusual download activity.
- Do not store backup encryption keys only alongside the backups they protect.
- Test recovery of required secrets and keys without exposing them in logs or documentation.
- Protect backups from ransomware, accidental deletion, compromised production credentials, and unauthorized exports.

# 18. Restore and Disaster-Recovery Exercises

Run restore exercises on a defined schedule approved before production launch and after material changes to the database, storage, backup system, or deployment topology.

A restore exercise should:

1. Record the exercise owner, date, scope, and selected recovery point.
2. Confirm authorization and isolate the recovery environment.
3. Retrieve backup data and required keys/configuration securely.
4. Restore database, media, and required dependencies in documented order.
5. Validate schema, referential integrity, representative records, media references, access permissions, and critical workflows.
6. Rebuild derived indexes/caches or recover queues according to documented policy.
7. Measure elapsed time and determine the recovered data point.
8. Compare actual results with approved RPO/RTO.
9. Record failures, gaps, remediation owner, and due date.
10. Clean up temporary recovery resources safely and retain evidence without exposing sensitive data.

A failed exercise must create tracked remediation work. Do not mark disaster recovery as ready solely because a runbook exists.

# 19. Incident Detection and Operational Response

When an alert indicates an incident:

1. Confirm the signal and assess customer, data, security, and payment impact.
2. Assign an incident owner and severity using the approved incident process.
3. Preserve relevant logs, deployment IDs, metrics, and audit events.
4. Mitigate safely; avoid destructive recovery steps before understanding their effect on persisted data.
5. Communicate status through the approved channel and escalate when thresholds are met.
6. Restore service using the documented runbook and validate critical journeys.
7. Reconcile data and external side effects, especially payment and notification state.
8. Close only after service health and data integrity are checked.
9. Complete a post-incident review with timeline, cause, impact, detection gaps, and corrective actions.

Detailed roles, communications, and incident lifecycle belong in **32. Incident & Troubleshooting Guide**. This document defines the monitoring, logging, and backup evidence those procedures depend on.

# 20. Deployment and Change Monitoring

For each release, retain or link:

- Release version, source commit, artifact identifier/digest, and deployment time.
- Approval and deployment outcome.
- Migration status and safe error summary.
- Smoke-test results and key health signals.
- Relevant alert changes, rollback/forward-fix events, and post-deploy observations.

Compare baseline and post-release metrics for API error rate/latency, web route availability, queue processing, database load, media failures, and critical workflow outcomes. Material regressions should block promotion or trigger the documented recovery process.

Alert-rule, logging-schema, backup-policy, retention, credential, and monitoring-agent changes must be reviewed and tested. Avoid untracked manual changes that create configuration drift.

# 21. Operational Runbooks

Maintain version-controlled or otherwise access-controlled runbooks for:

- API/web outage and elevated error rate.
- Database saturation, failed migration, corruption suspicion, or unavailable database.
- Backup failure, stale recovery point, and restore procedure.
- Missing/corrupt media and object-storage outage.
- Queue backlog, failed jobs, and scheduler failure.
- Payment callback failure and transaction reconciliation.
- Firebase authentication/provider outage.
- Notification provider outage or invalid device-token spike.
- Search indexing lag or index rebuild.
- TLS certificate expiry, DNS failure, and edge routing issues.
- Suspected credential exposure or unauthorized privileged action.
- Deployment rollback, forward-fix, and post-deployment regression.

Every runbook must state prerequisites, authorization, safe diagnostic commands/actions, impact warnings, verification steps, escalation route, and evidence to retain. Commands that could delete data or affect production must be clearly marked and require explicit confirmation/approval.

# 22. Ownership and Operational Review

Assign named roles in the operational roster (names may be recorded in the appropriate internal access-controlled location):

- **Service owner:** accountable for health objectives and operational readiness.
- **On-call/incident owner:** responds to actionable alerts and coordinates mitigation.
- **Database owner:** backup policy, database health, restore testing, and data-integrity checks.
- **Security/privacy owner:** log access, sensitive-data redaction, audit controls, and incident evidence.
- **Release owner:** deployment telemetry and post-release verification.
- **Backup/restore approver:** authorizes production restore and validates completion.

Review dashboards, alert noise, backup status, storage growth, incident trends, and restore-test findings at a defined cadence. Review immediately after a material incident or architecture change.

# 23. Production Readiness Checklist

- [ ]  Service inventory lists owners, dependencies, criticality, health signals, and runbooks.
- [ ]  Logs are structured and contain correlation identifiers where practical.
- [ ]  Tokens, credentials, signing keys, and unnecessary personal/payment data are redacted.
- [ ]  Privileged administrative and sensitive business actions produce auditable records.
- [ ]  Production SLIs/SLOs and alert thresholds have approved values and owners.
- [ ]  Critical public routes and API endpoints have external synthetic checks.
- [ ]  Liveness/readiness checks are safe and do not leak internal details.
- [ ]  Database, media, queues, payment workflows, notifications, and external dependencies have relevant monitoring.
- [ ]  Backup coverage explicitly classifies every critical data/artifact type.
- [ ]  Backup encryption, retention, access, separation, and deletion controls are documented.
- [ ]  RPO/RTO are approved and achievable with the selected platform.
- [ ]  Database and media backups have been restored and validated in an isolated environment.
- [ ]  Search/cache/queue rebuild or recovery procedures are tested where applicable.
- [ ]  Restore exercise results and remediation actions are recorded.
- [ ]  Alert escalation routes are tested and staffed.
- [ ]  Operational runbooks exist for major failure modes.
- [ ]  Release events are correlated with post-deployment health checks.
- [ ]  Retention, privacy, and production telemetry access policies are approved.
- [ ]  Incident response handoff to Document 32 is documented.

# 24. Decisions Required Before Production

The following must be approved and recorded rather than guessed:

- Monitoring, metrics, log aggregation, error tracking, and alerting providers.
- Production SLOs, alert thresholds, and response coverage.
- RPO/RTO by data/service class.
- MySQL backup method, frequency, retention, and point-in-time recovery capability.
- Media/object storage backup/versioning and recovery strategy.
- Log and audit retention durations and access policy.
- Backup storage location, encryption/key recovery, and deletion protection.
- Restore-test cadence and approval authority.
- Search/queue/cache recovery classification and rebuild procedures.
- Incident severity model, on-call ownership, and escalation channel.

# 25. Related Documents

- **13. Database Architecture & Data Model** — schema, authoritative data, and integrity constraints.
- **14. API Specification** — API behavior and critical endpoint contracts.
- **16. Backend Architecture** — Laravel runtime and background processing responsibilities.
- **17. Mobile Application Architecture** — mobile release and client compatibility considerations.
- **18. Authentication & Authorization** — Firebase token validation and authorization boundaries.
- **19. Security Architecture** — security controls, threat model, and incident/security requirements.
- **20. Media & File Storage** — uploaded files, derivatives, permissions, and lifecycle.
- **21. Search Architecture** — indexing, freshness, and rebuild requirements.
- **22. Notification System** — notification lifecycle and delivery outcomes.
- **23. SEO Architecture** — public route and crawler availability requirements.
- **24. Testing & QA** — test evidence and recovery/operational validation.
- **25. DevOps & CI/CD** — release telemetry, artifact traceability, and deployment gates.
- **26. Infrastructure & Deployment** — hosting topology, persistence, environment, and deployment operations.
- **28. Git & GitHub Workflow** — repository protection and version-controlled runbooks.
- **30. Admin & Operations Guide** — routine operational actions.
- **31. Release Management** — release approvals and coordination.
- **32. Incident & Troubleshooting Guide** — incident roles, communications, and resolution lifecycle.

# 26. Changelog

- **2026-10-15 — v1.0:** Created the KHOJ BHET monitoring, logging, backup, restore, and operational readiness baseline. Separated target controls from implemented capabilities and listed production decisions requiring approval.

## TV-09 Operational Proof Matrix — 2026-10-18

For each control, retain date, environment, version/commit, command or procedure, outcome, evidence reference, owner, and unresolved gaps. Required proof: (1) CI/release traceability and secret-access review; (2) alert delivery test with severity, owner and runbook; (3) log review proving tokens, passwords, keys, signed URLs and unnecessary personal data are redacted; (4) backup job success plus a restore drill covering MySQL, uploaded media and critical configuration; (5) recorded RPO/RTO and measured restore time/data-integrity checks; (6) release/rollback or forward-recovery rehearsal; (7) trusted-proxy/IP rate-limit test; (8) real-device FCM test; (9) media and notification end-to-end tests. A configured backup without a successful restore is not PASS. **TV-09 remains NOT VERIFIED until evidence is attached; this checklist is not operational proof.**