# 30. Admin & Operations Guide

**Project:** KHOJ BHET  

**Document ID:** KB-OPS-030  

**Section:** 04. TEAM & OPERATIONS  

**Status:** Active — Operations Baseline; access controls, production tooling, and runbooks must be verified against the deployed environment  

**Version:** 1.0  

**Owner:** KHOJ BHET Operations / Engineering  

**Last Reviewed:** 2026-10-18  

**Previous:** 29. Developer Onboarding Guide  

**Next:** 31. Release Management

---

## 1. Purpose

This guide defines how authorized administrators and operators manage the day-to-day health, access, configuration, data integrity, moderation, support, and operational records of KHOJ BHET. It establishes safe operating principles and repeatable procedures while directing detailed release and incident response to Documents 31 and 32.

This is an operational baseline. It does not assert that a production deployment, specific admin account, monitoring alert, backup schedule, approval workflow, or access-control configuration exists unless verified in the actual system. Operators must confirm the live deployment's runbooks and permissions before taking action.

## 2. Scope

This guide covers operational responsibilities for:

- User, role, and administrator access governance.
- Marketplace listings and content moderation.
- Categories and catalogue data governance.
- Payment-status review and reconciliation support.
- Media/file access and reported content.
- Application health, configuration, logs, and routine checks.
- Database integrity, backup verification, and recovery coordination.
- Customer/support requests and operational record keeping.
- Escalation, privacy, auditability, and change control.

It does not replace the product requirements, security architecture, release procedure, or incident-response procedure.

## 3. Authority and source of truth

Use these sources in order for their respective areas:

1. **Notion's canonical numbered documents** define approved product requirements, business rules, architecture, security policy, and operating procedures.
2. **The deployed application's configuration and version-controlled repository** show what is actually implemented. Verify environment and release version before operating.
3. **Accepted ADRs** govern decisions within their scope. Pending proposals are not approved standards.
4. **Operational records, deployment evidence, monitoring, and audit logs** provide evidence of what occurred.
5. **Support reports and operator observations** are inputs to investigation, not by themselves proof of root cause.

If a written procedure conflicts with the deployed behavior, stop any risky action, preserve evidence, and escalate to the responsible owner. Do not improvise a change to production business rules to make the system appear consistent. Resolve the decision and update the canonical documentation.

## 4. Roles and responsibility boundaries

Exact staffing, names, approval thresholds, and on-call coverage must be assigned by project governance; do not infer them from this guide.

| Role | Core responsibility | Boundary |
| --- | --- | --- |
| Product owner / authorized business owner | Approves product policy, user-facing decisions, and business exceptions. | Does not bypass technical security or audit controls. |
| Operations administrator | Performs authorized routine administration, reviews queues, and records actions. | Uses only granted permissions; does not share accounts or bypass approval rules. |
| Engineering owner | Owns application behavior, technical diagnosis, migrations, and corrective code changes. | Production changes follow the release process. |
| Security/privacy owner | Coordinates access, suspected exposure, privacy requests, and security investigations. | Sensitive incidents use the restricted escalation path. |
| Finance/payment reviewer | Reconciles payment evidence and follows approved payment-state procedures, where this role exists. | Does not mark a payment successful solely on a user screenshot or unsupported claim. |
| Support operator | Receives reports, records facts, communicates approved guidance, and escalates. | Does not disclose another user's private information or promise unapproved outcomes. |

One person may hold multiple roles in an early-stage team, but sensitive actions should still receive independent review where feasible. Role combinations and segregation-of-duties exceptions should be explicitly approved and recorded.

## 5. Access control and administrator lifecycle

### 5.1 Granting access

1. Confirm the person's identity and operational need through the approved process.
2. Identify the minimum role and resources needed for their responsibilities.
3. Obtain approval from the designated owner where required.
4. Grant access using the application's supported role/permission mechanism and the relevant infrastructure provider's access controls.
5. Verify the assigned access and record the request, approver, scope, and date in the approved access register.
6. Explain the secure handling of credentials, personal data, support cases, and audit records.

Do not grant broad administrator or database-superuser access for routine support if a narrower role can perform the task. Never share administrator accounts, passwords, Firebase private keys, API tokens, or recovery codes.

### 5.2 Changing or removing access

Review access when a person changes duties, leaves the project, loses a business need, or when an account is suspected compromised.

- Revoke unnecessary application and infrastructure permissions promptly.
- Revoke or rotate relevant sessions, tokens, credentials, and keys using the supported controls.
- Transfer ownership of tasks, integrations, and operational records.
- Preserve required audit evidence without retaining unnecessary personal data.
- Record the completion and any remaining dependency.

For suspected compromise, use the incident process in **32. Incident & Troubleshooting Guide** rather than treating the event as a routine access update.

### 5.3 Privileged actions

Administrative actions that affect accounts, permissions, listing visibility, moderation, payments, categories, configuration, or data exports should be attributable to an authorized operator. Where the application supports audit logs, verify that the actor, action, target, timestamp, outcome, and reason are recorded appropriately.

Never disable authorization, edit production records directly, or use another person's account as a shortcut. If the interface cannot safely perform a necessary action, escalate to Engineering and use a reviewed, auditable procedure.

## 6. Routine operational checks

The operator or assigned owner should use the deployed environment's actual monitoring and runbooks. A suggested checklist is below; frequency and ownership must be assigned according to service criticality and actual capabilities.

### 6.1 Service health

- [ ]  Confirm the public web application and API health indicators.
- [ ]  Check for sustained error-rate increases, latency, failed requests, or unexpected traffic patterns.
- [ ]  Confirm database and required dependent services are reachable through supported health checks.
- [ ]  Review queue/worker, search, notification, and scheduled-job status where those services are enabled.
- [ ]  Review storage capacity, upload failures, and media access errors.
- [ ]  Review actionable alerts and ensure each has an owner or escalation.
- [ ]  Record unresolved degradation and hand over open work.

A successful homepage request alone does not prove that authentication, listing creation, search, uploads, payments, notifications, or administrative actions work.

### 6.2 Logs and metrics

- Use approved, access-controlled logging and monitoring systems.
- Search by time range, request/correlation identifier, component, and error class where available.
- Compare the event with recent deployments and known dependencies before assigning a cause.
- Redact access tokens, passwords, private keys, payment secrets, and unnecessary personal information before sharing evidence.
- Do not enable verbose or debug logging in production without authorization, a defined time limit, and a safe data-handling plan.
- Do not delete or alter audit logs to hide an action or make a dashboard appear healthy.

### 6.3 Scheduled tasks and integrations

For scheduled jobs, queues, notifications, search indexing, storage providers, and external payment integrations:

1. Confirm the integration is configured for the correct environment.
2. Check the latest execution time, outcome, retry behavior, and backlog where observable.
3. Investigate repeated failures before manually replaying jobs.
4. Determine whether the operation is idempotent and whether replay can create duplicate notifications, payment records, or other side effects.
5. Record any approved manual retry and verify the resulting state.

Do not assume an integration is enabled just because its architecture document describes it.

## 7. User and marketplace administration

All user-facing decisions must follow **04. Users, Roles & Permissions**, **08. Product & Business Rules**, **18. Authentication & Authorization**, and **19. Security Architecture**.

### 7.1 User account support

- Verify the support request and the minimum information needed to investigate it.
- Use the supported account-recovery and authentication flows.
- Do not ask a user to send a password, one-time code, bearer token, or private key.
- Verify identity before changing account access or disclosing account-specific information.
- Apply restrictions, suspensions, or reinstatements only with the authority and evidence required by approved policy.
- Record the reason and relevant reference for consequential actions.
- Escalate suspected account takeover, impersonation, or unauthorized access.

### 7.2 Listing and content moderation

For a listing report or moderation request:

1. Capture the listing identifier/URL, report reason, time, and available supporting evidence.
2. Check the relevant catalogue category, listing rules, prohibited-content policy, and any prior moderation history that the operator is authorized to view.
3. Apply only the permitted action and threshold defined by the approved business rules.
4. Record the decision, reason, operator, time, and follow-up required.
5. Communicate only the information the requester is authorized to receive.
6. Escalate legal threats, credible safety concerns, suspected fraud, or ambiguous policy cases to the designated owner.

Do not delete evidence prematurely or make irreversible decisions solely on an unverified allegation. Preserve only the information needed under the approved retention and privacy policy.

### 7.3 Categories and catalogue changes

The **13.1 Category & Attribute Catalogue** is the authoritative catalogue reference. Before changing category or attribute data:

- Confirm the requested change against the approved catalogue and business rules.
- Check existing listings, filters, validation rules, search behavior, analytics, and mobile/web compatibility.
- Preserve canonical identifiers and the approved hierarchy.
- Identify whether the change requires a migration, backfill, reindex, or coordinated release.
- Obtain the required product and engineering approvals.
- Test the change in a non-production environment and document rollback or correction steps.
- Verify results after the approved release.

Do not create duplicate categories, repurpose an existing identifier for a different meaning, or make an untracked direct database edit.

## 8. Payment operations and reconciliation

Payment handling must follow the approved payment architecture, business rules, and provider requirements. This guide does not authorize manual payment approval or define provider-specific settlement rules.

- Use provider transaction references and server-verified callback/webhook evidence.
- Treat screenshots, messages, and client-submitted payment status as supporting claims, not authoritative confirmation.
- Confirm amount, currency, transaction identity, intended order/listing, current state, and duplicate-processing safeguards through approved systems.
- Do not mark a transaction successful unless the required server-side verification and business conditions have been satisfied.
- For manual payment methods, follow the documented evidence, reviewer, approval, and audit requirements.
- Investigate pending, duplicated, reversed, failed, or mismatched transactions through the designated reconciliation procedure.
- Do not request, store, or transmit card security codes, passwords, OTPs, or payment-provider secrets.
- Escalate discrepancies and suspected fraud to the assigned payment/business owner and Engineering as appropriate.

Never perform a direct database update to force a payment state. If a correction is necessary, use an approved, reviewed, auditable correction procedure that preserves the transaction history.

## 9. Media, files, and privacy requests

Follow **20. Media & File Storage**, **19. Security Architecture**, and the approved retention/privacy policy.

- Verify reported media using authorized access and the relevant listing/user context.
- Do not expose private uploads through public URLs or change access controls without authorization.
- Treat uploaded files, filenames, metadata, and embedded content as untrusted input.
- Use the documented malware/content checks and file-access controls where implemented.
- Handle requests to correct, export, or delete personal information through the approved verification and retention process.
- Check legal holds, transactional/audit requirements, and references before deletion.
- Record what was requested, the verification/approval outcome, what was changed, and any justified limitation.
- Escalate suspected data exposure immediately through the incident procedure.

Do not promise complete erasure from backups or third-party systems unless the actual retention and deletion process has been verified.

## 10. Configuration and operational changes

Configuration changes can affect authentication, API behavior, payments, media access, availability, privacy, and data integrity. Treat material production changes as controlled changes.

1. State the purpose, owner, target environment, scope, risk, and expected outcome.
2. Check the relevant architecture document, accepted ADR, and current deployed version.
3. Review the proposed change and dependencies with the appropriate owner.
4. Test in development/staging where available.
5. Confirm backup/recovery or rollback options when data or availability could be affected.
6. Obtain required approval and schedule the change under the release process.
7. Apply the change using the approved deployment/configuration mechanism; avoid undocumented manual edits.
8. Verify expected behavior and monitor for regressions.
9. Record the change, evidence, outcome, and any follow-up.

Secrets must be managed through the approved secret/configuration mechanism, not committed to the repository or copied into Notion. Do not change production environment variables, access policies, payment configuration, DNS, database permissions, or firewall rules without the relevant authorization.

## 11. Database, backup, and recovery responsibilities

Database administration and recovery must follow **13. Database Architecture & Data Model**, **19. Security Architecture**, and **27. Monitoring, Logging & Backup**.

- Use approved, least-privilege database accounts for routine operations.
- Prefer application-supported interfaces and reviewed migrations over direct production SQL changes.
- Confirm the environment, host, database, and intended records before any query that changes data.
- Review migration impact, locking, data volume, compatibility, and recovery options before execution.
- Verify that backups completed and that their integrity and restoration procedure are tested according to the approved plan.
- Protect backups with access controls and encryption where required; do not download production backups to unmanaged devices.
- Record restore tests, failures, recovery decisions, and exceptions.
- Coordinate restoration with Engineering and the incident lead when service integrity or availability is affected.

A backup job reporting success is not by itself proof that a usable restore can be completed. Never run a destructive reset, restore, or bulk update against an uncertain target.

## 12. Support queue and operational records

Each support or operations case should contain enough information for another authorized operator to continue safely:

- Unique case or issue reference.
- Time received and affected feature/component.
- Reporter identity only to the extent required and authorized.
- Clear description, expected behavior, and observed behavior.
- Relevant listing, transaction, or request reference, avoiding unnecessary personal data.
- Priority/severity according to the approved policy.
- Actions taken, evidence reviewed, and outcome.
- Current owner, next action, and follow-up deadline if one is defined.
- Escalation, approval, and closure reference where applicable.

Use the designated issue tracker or operational record system. Do not create a parallel spreadsheet or chat-only process if an approved system exists. Restrict case access according to sensitivity and retention policy.

## 13. Escalation and incident boundary

Routine operations must stop and transition to the incident process when there is evidence or credible suspicion of:

- Unauthorized administrator or user access.
- Secret, credential, or personal-data exposure.
- Payment manipulation, unexplained financial discrepancies, or suspected fraud.
- Widespread service outage or material degradation.
- Data corruption, unintended deletion, or failed recovery.
- Security-control bypass or unexpected privilege escalation.
- Repeated failed deployments or changes causing significant user impact.

Preserve relevant timestamps, request IDs, change/deployment identifiers, and redacted evidence. Avoid speculative public statements, unapproved remediation, or actions that destroy evidence. Follow **32. Incident & Troubleshooting Guide** for severity, communications, containment, investigation, recovery, and post-incident review.

For a planned deployment or rollback, follow **31. Release Management**. This guide does not replace either procedure.

## 14. Daily and periodic checklist

Use this as a baseline and assign actual frequency and ownership in the operational schedule.

### Routine review

- [ ]  Review application/API health and active alerts.
- [ ]  Check critical dependencies and failed scheduled jobs where applicable.
- [ ]  Review moderation and support queues according to policy.
- [ ]  Review payment exceptions/reconciliation queues if payment operations are assigned.
- [ ]  Record material actions, unresolved issues, and handover items.
- [ ]  Escalate security or availability risks rather than leaving them in a routine queue.

### Periodic governance review

- [ ]  Review administrator and privileged access.
- [ ]  Verify backup job evidence and recent restoration-test results.
- [ ]  Review alert routing, log access, and sensitive-data redaction.
- [ ]  Check external integrations and expiring credentials/certificates through approved tooling.
- [ ]  Review outstanding operational risks and stale runbooks.
- [ ]  Confirm that access removal and role changes are complete.
- [ ]  Review recurring incidents and propose preventive engineering work.

The exact daily, weekly, or monthly schedule must be set by the owner based on the actual service and team coverage; this guide does not invent service-level objectives or a backup frequency.

## 15. Operational handover

At shift change, leave a concise handover with:

- Current service status and active alerts.
- Open support, moderation, payment, or access cases.
- Actions performed and evidence/record references.
- Pending approvals, scheduled changes, and known risks.
- Incident references and the responsible incident owner, if applicable.
- Next actions, owners, and deadlines where assigned.

Transfer work through the approved shared system. Never transfer personal passwords or shared account credentials as part of a handover.

## 16. Completion criteria

An operational task is complete when:

- The requester and authority for the action have been verified as required.
- The correct environment and target were confirmed.
- The action complied with approved product, security, and data-handling rules.
- Required approvals and independent checks were completed.
- The result was verified rather than assumed.
- The action and evidence were recorded in the appropriate system.
- Any side effects, unresolved risks, and follow-up work have an owner.
- Related documentation or runbooks were updated when the procedure changed.

A ticket marked resolved is not proof that the underlying technical defect is fixed; link engineering work or an incident record when follow-up is required.

## 17. Maintenance and change control

The Operations and Engineering owners should review this guide when administrator capabilities, moderation/payment policy, deployment architecture, privacy requirements, data retention, monitoring, or backup/recovery procedures materially change.

The guide is the current operating baseline, not evidence that every suggested control exists. Maintain an explicit list of unimplemented controls and assign an owner before treating them as operationally available. Changes must remain consistent with accepted ADRs and canonical documents; resolve conflicts before applying risky actions.

## 18. Related documents

- **00. Project Documentation Guide** — documentation authority and governance.
- **00.1 Documentation & SDLC Framework** — change control and lifecycle.
- **00.3 Decision / ADR Register** — accepted decisions and pending proposals.
- **04. Users, Roles & Permissions** — role and permission boundaries.
- **08. Product & Business Rules** — moderation, marketplace, and payment rules.
- **13. Database Architecture & Data Model** and **13.1 Category & Attribute Catalogue** — data integrity and catalogue governance.
- **14. API Specification** — API behavior and contract.
- **18. Authentication & Authorization** and **19. Security Architecture** — access and security controls.
- **20. Media & File Storage** — media and file operations.
- **22. Notification System** — notification behavior and failure handling.
- **24. Testing & QA** — validation requirements.
- **26. Infrastructure & Deployment** and **27. Monitoring, Logging & Backup** — operational health, recovery, and evidence.
- **28. Git & GitHub Workflow** and **29. Developer Onboarding Guide** — engineering collaboration and onboarding.
- **31. Release Management** — controlled releases and rollback.
- **32. Incident & Troubleshooting Guide** — incident response and recovery.

## 19. Change history

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-10-18 | Created the canonical operations baseline covering access governance, routine health checks, marketplace administration, payment reconciliation, privacy, configuration changes, backup responsibilities, handover, and escalation. |