# 32. Incident & Troubleshooting Guide

| Field | Value |
| --- | --- |
| Document ID | KB-OPS-032 |
| Version | 1.0 |
| Status | Active — Incident Response & Troubleshooting Baseline; validate contact paths, alerting, access, and recovery procedures against the actual environment |
| Owner | Operations / Incident Lead (named owner to be confirmed) |
| Applies to | KHOJ BHET web, API/backend, admin panel, mobile applications, database, authentication, payments, media, notifications, and supporting infrastructure |
| Last reviewed | 2026-10-18 |
| Classification | Internal — may contain operationally sensitive details when completed |

## 1. Purpose

This guide establishes a consistent way to report, assess, contain, investigate, recover from, and learn from incidents affecting KHOJ BHET. It also provides a structured troubleshooting method for recurring technical faults.

This is an operational baseline, not proof that on-call coverage, alerting, observability, incident tooling, service-level objectives, or disaster-recovery automation is already configured. Confirm actual capabilities and populate the operational details before relying on them during an incident.

## 2. Scope

Use this guide for events that materially affect or may compromise:

- Availability, latency, stability, or correctness of the web application, API, or admin panel.
- Listing creation, editing, publication, moderation, search, or user account access.
- Firebase Authentication, ID-token validation, Bearer-token authorization, or access boundaries.
- MySQL availability, schema migrations, data integrity, backups, or recovery.
- Payment initiation, provider callbacks/webhooks where used, payment state, reconciliation, or manual approval.
- Media uploads, storage permissions, file exposure, notifications, scheduled work, and background jobs.
- Secrets, personal information, administrative access, dependencies, deployment pipelines, or infrastructure.
- Mobile releases, API compatibility, and client versions.

Routine development errors with no user, security, data, or service impact can follow normal defect triage. Escalate immediately if impact is uncertain and a security or data-integrity risk is plausible.

## 3. Operating principles

1. **Protect people, users, and data first.** Contain active harm before pursuing a complete root-cause explanation.
2. **Establish facts.** Record timestamps, scope, symptoms, evidence, and actions. Separate confirmed facts from hypotheses.
3. **Use least privilege.** Only authorized personnel should access production systems, personal data, secrets, and recovery controls.
4. **Preserve evidence.** Avoid deleting logs, resetting systems, or changing multiple variables before capturing relevant evidence, unless delay increases harm.
5. **Prefer reversible actions.** Choose the smallest safe containment or recovery step and verify its result.
6. **Avoid destructive guesswork.** Never drop tables, delete persistent volumes, wipe media, reset credentials, or restore backups without understanding impact and obtaining the required authorization.
7. **Communicate clearly.** State what is affected, what is known, what is being done, and when the next update is expected.
8. **Learn without blame.** Review contributing system and process conditions, not just individual actions.

## 4. Severity and prioritization

Use this baseline to assign severity. The project team must confirm final thresholds, notification paths, and response targets; do not interpret this table as an existing SLA.

| Severity | Typical indicators | Initial response |
| --- | --- | --- |
| SEV-1 — Critical | Confirmed or strongly suspected active compromise; material data loss/corruption; widespread outage; severe payment integrity failure; critical authentication/authorization bypass | Start incident coordination immediately; contain active harm; notify authorized decision-makers; provide frequent status updates |
| SEV-2 — High | Major user journey unavailable for many users; sustained API/database failure; significant payment or listing workflow disruption; serious degradation with no safe workaround | Assign an incident lead promptly; mitigate; communicate impact and next update |
| SEV-3 — Moderate | Limited feature failure, partial degradation, or a subset of users affected with a viable workaround | Triage, assign an owner, document workaround and follow-up |
| SEV-4 — Low | Minor defect, cosmetic issue, or isolated failure with no meaningful security, data, or service impact | Record and prioritize through normal work intake |

When uncertain, choose the safer severity and reassess as evidence improves. Raise severity immediately for potential credential exposure, unauthorized data access, data corruption, or incorrect financial state.

## 5. Roles and responsibilities

Assign actual names and backup contacts in the team's operational contact register.

| Role | Responsibility |
| --- | --- |
| Incident Lead | Owns severity, coordination, action priorities, status updates, and closure decision |
| Technical Lead | Directs diagnosis and recovery for the affected component |
| Operations / Deployment Owner | Executes authorized infrastructure, deployment, and recovery procedures |
| Security Owner | Leads credential compromise, unauthorized access, vulnerability, and privacy investigations |
| Database Owner | Assesses database health, migration impact, backup integrity, and data recovery |
| Product / Business Owner | Assesses user/business impact and approves business decisions where required |
| Communications Owner | Coordinates internal and user-facing messages when warranted |
| Scribe / Recorder | Maintains the timeline, decisions, actions, evidence references, and follow-up items |

For a small team, one person may hold several roles. During a serious incident, explicitly name the incident lead and action owner so recovery tasks do not conflict.

## 6. Incident response lifecycle

### 6.1 Detect and report

Record the first known observation, who reported it, affected service, environment, time and timezone, visible symptoms, recent changes, and any immediate safety/security concern.

### 6.2 Triage

- Determine whether the issue is ongoing and user-facing.
- Estimate affected users, features, data, payments, and environments.
- Check whether there is evidence of unauthorized access, exposed secrets, or destructive data changes.
- Assign severity, an incident lead, and a technical owner.
- Decide whether to pause deployments, jobs, payment processing, or other risky operations.

### 6.3 Contain

Choose a proportionate action that limits further impact. Examples include pausing a rollout, restricting a compromised credential, disabling an affected integration through an existing supported control, or temporarily limiting a failing workflow. Confirm that the chosen action will not create a greater data-integrity or safety risk.

Do not assume feature flags, traffic switching, or automated isolation controls exist. Use only verified controls and approved access.

### 6.4 Diagnose

Build a timeline and test one hypothesis at a time. Correlate application errors, deployment changes, infrastructure health, database state, authentication/provider responses, and user reports. Preserve relevant evidence before making changes that could erase it.

### 6.5 Recover

Use the approved component-specific runbook. Validate the recovery action in the affected environment, then test critical user journeys and data integrity. A service process starting is not sufficient proof of recovery.

### 6.6 Communicate and close

Publish a concise status update, confirm service stability, record residual risk and follow-up work, and decide whether a post-incident review is required. Do not close a high-severity incident solely because a dashboard is green; validate user-facing behaviour and data state.

## 7. Incident communication

Use the team's approved communication channel and escalation contacts once confirmed. Avoid posting secrets, full access tokens, passwords, payment credentials, or unnecessary personal data in incident messages.

A useful update includes:

- Incident ID and severity.
- Start time and last updated time, with timezone.
- Affected services and user-visible impact.
- Confirmed facts versus current hypotheses.
- Containment/recovery actions taken.
- Current status and known workaround, if safe.
- Next action, owner, and expected next update.
- Whether security, privacy, payment, or data-integrity review is required.

Do not promise a resolution time without a credible basis. For a suspected security or privacy incident, follow the organization's approved legal, privacy, provider, and regulatory notification requirements; confirm the applicable requirements rather than assuming a universal deadline.

## 8. General troubleshooting workflow

1. **Confirm the symptom:** Capture exact error text, time, frequency, request/trace identifier if available, and reproduction steps.
2. **Confirm scope:** One user or many? One client or all clients? One endpoint or the entire service? One environment or multiple?
3. **Check recent changes:** Releases, migrations, configuration, secrets, certificates, DNS, provider status, dependency updates, and access changes.
4. **Check dependencies:** Network/DNS, application process, database connectivity, Firebase, payment provider, storage, queue/worker, and notification services as relevant.
5. **Inspect evidence:** Logs, metrics, health checks, database status, deployment records, and external provider responses where available.
6. **Form one testable hypothesis:** State what evidence would confirm or disprove it.
7. **Apply a bounded change:** Prefer reversible actions; record the exact change and result.
8. **Verify recovery:** Retest the failed path and adjacent critical flows.
9. **Record the outcome:** Cause or leading hypothesis, resolution, workaround, risks, and follow-up actions.

Do not repeatedly restart services as a substitute for diagnosis. Avoid running commands copied from unverified sources against production.

## 9. Troubleshooting guide by symptom

The following are diagnostic directions, not environment-specific commands. Use the actual approved runbooks, installed tooling, and access model.

### 9.1 Web or API unavailable

**Check**

- Whether the issue affects all users, a route, a region/network, or a single client.
- Recent release/configuration/DNS/TLS changes.
- Application process health, reverse proxy/web server, resource exhaustion, and upstream dependency failures.
- HTTP status patterns and timestamps in available logs.

**Safe response**

- Pause further rollout if the incident aligns with a new release.
- Confirm whether a known-good artifact or provider-supported mitigation is available.
- Avoid changing DNS, certificates, proxy settings, and application config simultaneously.
- Verify critical web routes and API flows after mitigation.

### 9.2 High latency or intermittent failures

**Check**

- Error/latency trends and resource saturation, if metrics exist.
- Database connection pressure, slow queries, locks, queue backlog, and external provider timeouts.
- Recent traffic, batch jobs, migrations, or expensive code paths.
- Whether retries are amplifying load.

**Safe response**

- Identify the dominant dependency before scaling or restarting.
- Avoid unbounded retries or increasing connection limits without understanding capacity.
- Preserve representative slow-request/query evidence while respecting privacy.

### 9.3 MySQL connection or migration failure

**Check**

- Database service availability, host/port configuration, credentials and grants, connection limits, disk capacity, and logs.
- Whether the application is using the intended environment/database.
- Migration status, partial DDL/data changes, locks, and compatibility between current code and schema.
- Backup freshness and restore feasibility before any recovery operation.

**Safe response**

- Do not delete database files or initialize a fresh data directory to “repair” an existing database.
- Do not rerun or reverse a failed migration blindly; determine whether it partially applied and inspect the actual schema/data.
- Do not restore over current data until the impact and recovery point are understood and authorized.
- Verify read/write operations and application-critical queries after recovery.

### 9.4 Firebase authentication or API authorization failures

**Check**

- Whether the client sends the documented Firebase ID token as a Bearer token.
- Token expiry, issuer/audience/project configuration, server-side token verification, clock skew, and Firebase service availability.
- Whether the failure is authentication (identity cannot be established) or authorization (identity is valid but action is not permitted).
- Recent changes to middleware, token verification, role/ownership policies, or project configuration.

**Safe response**

- Do not log or paste full tokens into tickets or chat.
- Do not bypass token verification or relax authorization to restore service.
- Preserve the API contract's Bearer-token model unless an approved architecture decision changes it.
- Test valid, expired/invalid, and unauthorized cases after a fix.

### 9.5 Payment mismatch, duplicate, or stuck status

**Check**

- Provider/environment, merchant reference, transaction identifier, amount/currency, event timestamps, and current internal state.
- Whether provider notifications/callbacks were delivered, authenticated, retried, duplicated, or processed out of order.
- Provider dashboard/settlement evidence and internal reconciliation records.
- Whether manual approval or reconciliation is enabled and who is authorized to use it.

**Safe response**

- Do not manually mark a payment as successful solely because a user reports success or a redirect page appears.
- Do not replay callbacks or modify financial records without idempotency checks and authorization.
- Preserve transaction references and evidence, but redact credentials and sensitive data.
- Escalate discrepancies to the payment/business owner and reconcile before declaring closure.

### 9.6 Listing, search, or moderation workflow failure

**Check**

- Whether the record exists and its status/ownership is correct.
- API validation, authorization policies, category/attribute constraints, search indexing or cache lag, and moderation rules.
- Whether the failure began after a schema/catalogue/content change.

**Safe response**

- Do not edit production records directly without an approved correction procedure and audit trail.
- Distinguish source-of-truth database state from search/index/cache state.
- Validate create, edit, view, search, and moderation paths as applicable.

### 9.7 Media upload or retrieval failure

**Check**

- Storage availability, permissions, configured paths/buckets, upload size/type limits, signed/public URL expiry, and disk capacity.
- Whether the upload completed but metadata persistence or thumbnail/processing failed.
- Whether an access-control change exposed private media.

**Safe response**

- Treat unintended public exposure as a potential security/privacy incident.
- Do not recursively change permissions or delete media directories as a first response.
- Preserve affected object identifiers and validate authorized and unauthorized retrieval after recovery.

### 9.8 Notifications, queues, or scheduled work delayed

**Check**

- Whether jobs are being enqueued, workers are running, failed-job counts/backlog, scheduler execution, retries, and provider limits.
- Recent deployment/configuration changes and queue connection settings.
- Whether the job is safe to retry and whether it is idempotent.

**Safe response**

- Confirm duplicate effects before replaying a batch.
- Avoid purging queues or failed-job records before preserving evidence.
- Verify delivery and business state, not just queue drain.

### 9.9 Mobile-only failure

**Check**

- App version/build, platform, OS, Expo/runtime/native compatibility, API version, network, authentication state, and crash evidence.
- Whether backend changes remain compatible with older installed app versions.
- Whether the issue is limited to an OTA update, store build, deep link, notification, media, or payment handoff.

**Safe response**

- Record exact build/version and reproduction steps.
- Do not assume every user can update immediately.
- Prefer backward-compatible backend mitigation where possible and follow the approved mobile distribution process.

### 9.10 Deployment or configuration failure

**Check**

- Exact commit/artifact, target environment, release log, configuration references, secret availability, dependency compatibility, and migration result.
- Whether the deployed artifact differs from the reviewed release candidate.
- Whether cache, worker, or process restart steps were omitted or failed.

**Safe response**

- Stop promotion to further environments.
- Compare actual deployment steps with Document 31, Release Management, and the verified environment runbook.
- Choose rollback or forward fix only after checking schema/data compatibility.

## 10. Security, privacy, and credential incidents

Treat suspected secret exposure, account takeover, unauthorized admin access, data exfiltration, malware, or unexplained privilege changes as security incidents, even if service availability is unaffected.

1. Notify the designated Security Owner and Incident Lead through the approved private channel.
2. Preserve relevant timestamps, logs, account/session identifiers, source revision, and access evidence while limiting unnecessary access to personal data.
3. Contain exposure using approved controls: revoke/rotate affected credentials, disable compromised access, or restrict a vulnerable path as appropriate.
4. Identify which systems, accounts, records, and integrations may have been affected.
5. Rotate secrets through the approved process and update dependent services; never paste the new secret into the incident record.
6. Validate access boundaries and review for persistence or repeated unauthorized activity.
7. Follow applicable contractual, provider, privacy, and legal notification obligations through authorized decision-makers.
8. Document remediation and monitor for recurrence.

Do not destroy evidence, publicly disclose exploit details, or contact a suspected attacker outside the approved incident process.

## 11. Data corruption, loss, and recovery

Data incidents require a database owner and explicit recovery decision.

- Stop or limit writes if continuing writes could worsen corruption and the containment action is safe.
- Identify affected tables/records, time range, transactions, and likely source of corruption.
- Preserve current state and logs where feasible before repair.
- Establish the latest known-good backup/recovery point and verify the documented restore procedure.
- Estimate data loss between the recovery point and incident detection.
- Decide whether to repair specific records, replay verified events, perform point-in-time recovery (only if supported), or restore a broader dataset.
- Obtain required authorization before destructive restoration or data rewriting.
- Reconcile payments and other external side effects separately; restoring the database does not reverse external transactions.
- Validate integrity constraints, row counts/samples, critical business workflows, and consistency with external providers.
- Record any unrecoverable loss and required user/business follow-up.

A backup is not considered proven recoverable solely because a backup file exists. Restore testing and recovery objectives must be verified against the actual infrastructure.

## 12. Relationship to release management

When an incident may be related to a release:

1. Pause further rollout or promotion.
2. Identify the exact release artifact and source revision.
3. Compare symptoms with deployment, configuration, and migration timelines.
4. Apply Document 31, Release Management, to decide whether to roll back, mitigate, or forward-fix.
5. Treat database schema/data compatibility as a separate decision from application rollback.
6. Run post-recovery checks and record the release/incident linkage.
7. Add the missing test, deployment safeguard, monitoring, or review step to prevent recurrence.

## 13. Incident timeline and record template

Create one record per material incident in the team's approved tracking location. Until that location is designated, this template is the required minimum content.

| Field | Record |
| --- | --- |
| Incident ID | Unique identifier assigned by the team |
| Severity / status | SEV-1–SEV-4; investigating, contained, recovering, monitoring, or closed |
| Start / detected / resolved times | Include timezone |
| Reporter / incident lead / technical owner | Names or approved team identifiers |
| Affected systems and users | Scope, environment, and impact |
| Symptoms and evidence | Error messages, relevant log/trace references, screenshots redacted as needed |
| Recent changes | Release, migration, configuration, access, provider or infrastructure changes |
| Timeline | Timestamped observations, decisions, and actions |
| Root cause / contributing factors | Confirmed cause or leading hypothesis clearly labeled |
| Containment and recovery | Action, executor, time, and verification evidence |
| Data/security/payment impact | Known scope and any uncertainty |
| Communications | Status updates and authorized notification decisions |
| Follow-up actions | Action, owner, priority, due date, and completion evidence |
| Review decision | Whether a post-incident review is required and when |

Keep sensitive evidence in an access-controlled location and link to it rather than copying secrets or unnecessary personal data into a broadly visible page.

## 14. Post-incident review

Conduct a review for SEV-1 and SEV-2 incidents, security/privacy events, material data/payment integrity issues, repeated failures, and any incident where the Incident Lead decides a review will improve reliability. Confirm exact review thresholds with the team.

Review:

- What happened and the user/business impact.
- Detection method and time to detect.
- Response timeline and decision points.
- Root cause and contributing technical/process conditions.
- What worked, what delayed recovery, and what evidence was missing.
- Whether communication and escalation were effective.
- Whether backups, access controls, tests, deployment gates, or monitoring performed as expected.
- Corrective and preventive actions with named owners and due dates.

Keep the review blameless and evidence-based. Avoid closing the review with only “be more careful”; define an actionable control, test, alert, runbook change, or ownership improvement.

## 15. Readiness and recurring checks

### Per incident

- [ ]  Severity, incident lead, and technical owner assigned.
- [ ]  Scope, timeline, and evidence captured.
- [ ]  Security, privacy, data, or payment impact considered.
- [ ]  Containment and recovery actions authorized and recorded.
- [ ]  Critical workflows and data integrity verified before closure.
- [ ]  Stakeholder updates and follow-up actions recorded.

### Periodically, according to the confirmed operations schedule

- [ ]  Verify incident contacts and escalation paths.
- [ ]  Review access to logs, production consoles, and backup locations.
- [ ]  Test restore/recovery procedures under an approved plan.
- [ ]  Review repeated incidents, failed jobs, capacity trends, and unresolved actions.
- [ ]  Confirm that deployment and troubleshooting runbooks match the actual environment.
- [ ]  Exercise an incident scenario where feasible and record gaps.

Do not assign an unconfirmed frequency or mark checks complete without evidence.

## 16. Operational details to complete before production use

The project team must fill in and verify:

- Primary and backup incident contacts and escalation channel.
- Production environments, hosting/provider consoles, and access owners.
- Approved log/metric/error-tracking locations and retention.
- Current service dependencies and provider status links.
- Backup locations, retention, restore owner, and tested recovery procedure.
- Deployment runbook and release-record location.
- Security/privacy escalation and notification decision-makers.
- Any agreed service objectives, severity response targets, and user communication channel.

Store credentials only in the approved secrets manager or credential system, never in this document.

## 17. Document Status

**Active — Incident Response & Troubleshooting Baseline.** This guide defines expected response practices and diagnostic directions. It does not confirm that an on-call rota, alerting, centralized logs, monitoring, tested backups, point-in-time recovery, or automated rollback is configured. Verify those capabilities, complete Section 16, and link approved environment-specific runbooks before relying on this guide during a production incident.

## 18. Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-OPS-032 |
| Version | 1.0 |
| Created | 2026-10-18 |
| Status | Active baseline; operational implementation verification pending |
| Review trigger | Incident workflow, infrastructure, observability, security escalation, backup/recovery, release process, or provider integration changes |
| Change history | v1.0 — Initial incident response and troubleshooting baseline |

## Related Documents

- 
    1. Testing & QA Strategy
- 
    1. Security Architecture
- 
    1. Database Architecture
- 
    1. Deployment & Infrastructure Architecture
- 
    1. Git & GitHub Workflow
- 
    1. Developer Onboarding Guide
- 
    1. Admin & Operations Guide
- 
    1. Release Management