# 31. Release Management

| Field | Value |
| --- | --- |
| Document ID | KB-OPS-031 |
| Version | 1.0 |
| Status | Active — Release Management Baseline; validate all release steps against the actual repositories, CI/CD configuration, hosting provider, and deployed services before operational use |
| Owner | Engineering / Release Owner (role assignment to be confirmed by the project team) |
| Applies to | KHOJ BHET web, API/backend, admin panel, mobile applications, database schema, and supporting integrations |
| Last reviewed | 2026-10-18 |
| Classification | Internal project documentation |

## 1. Purpose

This document defines a controlled release-management baseline for KHOJ BHET. It establishes the evidence, checks, approval points, deployment coordination, post-release validation, and recovery considerations expected before a change is considered released.

This is a process standard, not evidence that automated CI/CD, staging, production deployment tooling, release approvals, feature flags, or monitoring are already configured. Confirm the actual implementation and record deviations before treating any procedure as executable.

## 2. Scope

This guide applies to:

- Laravel API/backend and FilamentPHP administration.
- Next.js web application.
- React Native / Expo mobile application and store submissions.
- MySQL schema and data migrations.
- Firebase Authentication integration and Bearer-token API authorization.
- Payment integrations, including eSewa, Khalti, connectIPS, PhonePay, and any manual approval flow that is actually enabled.
- Media/file handling, notifications, search, SEO, background jobs, configuration, and infrastructure changes.

Infrastructure-specific commands and provider-specific steps must live in the approved deployment runbook for the actual hosting environment. Do not infer commands, secret names, URLs, or service topology from this document.

## 3. Authority and related documentation

Use the following sources together, resolving conflicts before release:

1. Approved product requirements and architecture documents define intended behaviour and constraints.
2. Document 14, API Specification, and the generated OpenAPI 3.1 contract define the API surface. The final contract audit remains a release gate until its completion is evidenced.
3. Document 24, Testing & QA, defines test expectations and acceptance evidence.
4. Document 19, Security Architecture, defines security requirements.
5. Document 13, Database Architecture & Data Model, defines data ownership and persistence rules.
6. Document 26, Infrastructure & Deployment, defines the intended deployment model.
7. Document 28, Git & GitHub Workflow, defines source-control practices.
8. Documents 29, Developer Onboarding Guide, and 30, Admin & Operations Guide, define contributor and operational responsibilities.
9. Document 32, Incident & Troubleshooting Guide, defines incident handling and recovery coordination.

A passing checklist does not authorize release if an approved requirement, security rule, or architecture decision is violated.

## 4. Release principles

- **Traceability:** Every release must map to a known commit or immutable build artifact.
- **Reproducibility:** Record how the artifact was built and which source revision produced it.
- **Small, reviewable changes:** Prefer bounded releases over unrelated bundled changes.
- **Backward compatibility:** Keep old and new application versions compatible during rolling deployments and mobile-version overlap wherever feasible.
- **Data safety:** Treat database changes and data transformations as potentially irreversible.
- **Least privilege:** Use authorized release identities and narrowly scoped credentials.
- **Evidence over assumption:** Record test results, approvals, migration outcome, and post-release checks.
- **Recoverability:** Decide how to mitigate a failed release before deploying it.
- **No secret leakage:** Never put credentials, private keys, access tokens, or production personal data in source control, release notes, screenshots, or logs.

## 5. Roles and decision rights

Assign named people to these roles before a production release. One person may cover multiple roles in a small team, but the release decision and its evidence must still be explicit.

| Role | Responsibility |
| --- | --- |
| Release Owner | Coordinates scope, readiness evidence, release timing, communication, and final record |
| Change Author | Explains the change, links requirements/issues, provides tests, and documents risks |
| Reviewer | Reviews code, design impact, security implications, and maintainability |
| QA / Test Owner | Reports test scope, results, failures, and known gaps |
| Database Owner | Reviews migration safety, backup/restore assumptions, and data integrity checks |
| Operations / Deployment Owner | Executes the approved deployment runbook and verifies runtime health |
| Product / Business Approver | Accepts user-facing changes and business risks where required |
| Incident Lead | Coordinates mitigation or rollback when a release causes an incident |

Do not invent named approvers or imply a formal separation of duties exists until the project team confirms it.

## 6. Release types

### 6.1 Standard release

A planned, reviewed release that completes the normal readiness checks, approvals, deployment, and post-release verification.

### 6.2 Hotfix

A narrowly scoped urgent change used to address a confirmed production defect, security issue, data-integrity risk, or severe service degradation. It still requires a known source revision, appropriate review, focused tests, risk assessment, deployment authorization, and post-release verification. Any skipped check must be explicitly justified, approved by the authorized decision-maker, and followed by a recorded remediation plan.

### 6.3 Rollback or mitigation release

A controlled response to a release that is unsafe or unsuccessful. The response may be an application rollback, disabling a confirmed feature flag, reverting traffic, restoring a compatible artifact, or deploying a forward fix. Database rollback must not be assumed safe or automatic.

## 7. Release lifecycle

1. **Define scope:** Identify the issue, requirement, user impact, affected components, dependencies, and acceptance criteria.
2. **Prepare change:** Implement the change on the approved branch/workflow in Document 28.
3. **Review:** Obtain code/design review and security review proportional to risk.
4. **Validate:** Run the tests required by Document 24 and capture results.
5. **Prepare release candidate:** Identify the exact commit, version/tag where used, build artifact, and dependency/configuration changes.
6. **Assess risk:** Review migrations, API compatibility, auth, payments, media, notifications, background work, mobile compatibility, and recovery options.
7. **Approve:** Record readiness and the decision to proceed.
8. **Deploy:** Follow the verified environment-specific runbook; do not improvise production commands.
9. **Verify:** Run smoke tests and inspect health signals, logs, and critical business flows.
10. **Close out:** Record outcome, issues, release notes, migrations, approvals, and any follow-up work.

If a required stage is unavailable because the corresponding tool or environment does not exist, record the gap and the approved substitute evidence. Do not mark the stage as passed without evidence.

## 8. Readiness gates

Before a release, confirm and record the following:

- [ ]  Release scope, acceptance criteria, and affected components are identified.
- [ ]  Change is reviewed and traceable to the approved source revision.
- [ ]  Automated and/or manual test results satisfy Document 24; failures and exclusions are documented.
- [ ]  Security and dependency checks appropriate to the change are complete.
- [ ]  API changes are checked against Document 14 and the OpenAPI 3.1 contract; breaking changes are explicitly assessed.
- [ ]  Database migrations are reviewed, ordered, and tested against a representative clean or upgrade path as appropriate.
- [ ]  Firebase token validation, authorization boundaries, and access control remain correct.
- [ ]  Payment state transitions, callback/webhook validation where used, reconciliation, and duplicate handling are tested for affected flows.
- [ ]  Required environment configuration and secrets are available through the approved secret-handling mechanism.
- [ ]  Background jobs, scheduled tasks, queues, cache changes, and external integrations have a deployment plan where applicable.
- [ ]  Web and mobile compatibility, including supported older mobile app versions, has been assessed.
- [ ]  Media/file permissions, storage paths, and public/private exposure have been checked if affected.
- [ ]  Backup and recovery assumptions are verified for the affected data and service.
- [ ]  Monitoring/log access and post-release checks are available, or their absence is explicitly recorded as a risk.
- [ ]  Release notes and stakeholder/support communications are prepared where needed.
- [ ]  A release owner, deployment window, stop conditions, and recovery decision-maker are identified.
- [ ]  Required approvals are recorded.

A missing check is not automatically a blocker for every low-risk change, but any exception must be deliberate, documented, and approved at the appropriate risk level.

## 9. Component-specific checks

### 9.1 Laravel backend and Filament administration

- Verify application configuration, dependency lock files, and required runtime compatibility.
- Confirm authorization policies, validation, rate limits, and admin-only operations for changed paths.
- Ensure production debug output and development tooling are disabled or restricted as required.
- Review queue workers, scheduled commands, caches, and long-running processes where present.
- Confirm the deployment sequence for dependencies, configuration/cache refresh, and process restarts using the actual runbook.
- Avoid exposing internal exception details or secrets in responses and logs.

### 9.2 Next.js web application

- Verify production build output and runtime configuration.
- Check route behaviour, authentication flows, error states, metadata/SEO requirements, and API compatibility.
- Confirm any client-visible environment values are intentionally public; never expose server secrets through a client bundle.
- Check caching and static asset compatibility when deploying a new build.

### 9.3 React Native / Expo mobile application

- Distinguish a backend release, an over-the-air update where supported and appropriate, and a new native app-store build. These are not interchangeable.
- Confirm the exact Expo/runtime/native compatibility and release channel or distribution target used by the project.
- Test authentication, API compatibility, deep links, media upload, notifications, and payment handoffs where applicable.
- Consider the time required for store review and the fact that users may continue using older installed versions.
- Do not publish to a store or distribute an update until the authorized owner approves the release and its target audience.

### 9.4 MySQL schema and data

- Review migration order, lock or downtime risk, table/index size, data volume, and expected execution time.
- Test migrations on the supported upgrade path and on a clean database when applicable.
- Prefer additive, backward-compatible changes first. Use an expand–migrate–contract sequence for risky schema changes where practical.
- Deploy code that can tolerate the old/new schema during a transition; remove old columns or constraints only after dependent code and data are confirmed migrated.
- Define pre-migration backup or recovery measures and verify that the selected recovery point is usable.
- Do not assume that restoring a database is harmless: it may discard writes made after the backup.
- Do not run destructive data transformations without explicit review, recovery planning, and approval.

### 9.5 Firebase Authentication and API authorization

- Verify that clients continue to send Firebase ID tokens using the documented Bearer-token model.
- Verify server-side token validation and authorization for affected endpoints.
- Do not introduce application-session cookies or CSRF assumptions into the client API unless an approved architecture decision explicitly changes the model.
- Validate token expiry, invalid-token handling, role/ownership checks, and sensitive admin access as relevant to the change.

### 9.6 Payments and financial state

- Confirm the enabled provider and environment; never assume sandbox and production credentials are interchangeable.
- Verify payment status transitions, amount/currency validation, reference uniqueness, duplicate notifications, failure handling, and reconciliation.
- Keep secrets and provider signatures out of logs and release artifacts.
- Confirm a safe manual review/reconciliation path where the feature is enabled.
- Do not declare a payment integration production-ready solely because a redirect or sandbox test succeeds.

## 10. Environment promotion

Use only environments that actually exist and are documented in the deployment architecture. If the project uses development, test, staging, and production, promote the same identified release candidate through the required gates rather than rebuilding an untraceable variant at each stage.

- **Development:** Early integration and developer feedback.
- **Test / QA:** Repeatable validation against defined acceptance criteria.
- **Staging / pre-production:** Production-like verification where the environment exists and is sufficiently representative.
- **Production:** Authorized user-facing deployment with recovery and communication arrangements.

Production data must not be copied into lower environments without an approved privacy and security process. Environment-specific settings and credentials must remain separate. Passing a local test alone does not establish production readiness.

## 11. Deployment execution record

For each release, record at minimum:

- Release identifier and release type.
- Date/time and timezone.
- Release owner and deployment operator.
- Source repository and exact commit/tag or immutable artifact identifier.
- Included changes, linked issues, and release notes.
- Target environment and affected services.
- Test evidence and approvals.
- Configuration/secret changes by reference only (never record secret values).
- Migration identifiers and results.
- Backup/recovery reference and retention details where applicable.
- Start/end time, outcome, smoke-test results, and observed anomalies.
- Rollback/mitigation decision, if any.
- Follow-up actions, owners, and due dates.

Use the team's approved tracker or release record location once designated. Until then, do not assume a particular system is authoritative.

## 12. Post-release verification

Perform checks proportionate to release risk immediately after deployment and again after an appropriate observation period.

- [ ]  Application processes start and remain healthy.
- [ ]  Critical routes and API health checks respond as expected.
- [ ]  Authentication and role/ownership authorization work correctly.
- [ ]  Critical listing flows (create, edit, publish/moderate, view) work where affected.
- [ ]  Media upload and retrieval work where affected.
- [ ]  Payment initiation, status update, and reconciliation paths work where affected.
- [ ]  Search, notifications, and scheduled/background work function where affected.
- [ ]  Database connectivity, migrations, and data-integrity checks succeed.
- [ ]  Error rates, latency, resource use, and relevant logs show no unacceptable regression, where those signals are available.
- [ ]  Support channels and user-facing communications reflect the release outcome.

A deployment command finishing successfully is not sufficient proof that the release works. If checks fail, stop further rollout and follow Section 14.

## 13. Release notes and communication

Release notes should state:

- Release identifier/date.
- User-visible additions, changes, fixes, and known limitations.
- Breaking changes or required user action.
- API or mobile compatibility implications.
- Maintenance/downtime expectations, if any.
- Security-relevant changes at a safe level of detail.
- Recovery or mitigation status if the release was interrupted.

Communicate to affected stakeholders before a planned interruption and after completion. Avoid exposing vulnerability details or private user information in public notes.

## 14. Failure criteria, rollback, and forward recovery

### 14.1 Stop or rollback triggers

The Release Owner and Operations/Incident Owner should agree on thresholds before deployment. Examples include:

- Critical user journeys are unavailable or materially broken.
- Authentication or authorization is bypassed or unreliable.
- Payment or listing state can become incorrect, duplicated, or unreconciled.
- Data loss, corruption, or an unexpected destructive migration is detected.
- Error rates, latency, or service instability exceed the accepted release threshold.
- A serious security exposure or secret leak is identified.

### 14.2 Decision process

1. Pause rollout and preserve relevant logs/evidence.
2. Assess scope, severity, data integrity, and whether the issue is continuing.
3. Choose rollback, traffic/configuration mitigation, feature disablement (only if supported), or forward fix.
4. Confirm that the recovery action is compatible with current schema and data.
5. Execute the approved recovery runbook and verify critical flows.
6. Communicate status and record decisions, timestamps, and outcomes.
7. Open incident follow-up under Document 32 when incident criteria are met.

### 14.3 Database caution

Application rollback does not automatically mean database rollback. Reversing a migration can destroy valid data or make the previous application incompatible. Prefer a forward fix or compatible schema strategy when that is safer. Restore from backup only after assessing data-loss impact, required approvals, and the point-in-time recovery capability actually available.

## 15. Hotfix handling

- Record the incident/defect and impact.
- Limit the change to the smallest safe scope.
- Obtain review and run focused regression/security tests.
- Identify exact source revision and target environment.
- Record any waived readiness gate, approver, rationale, and follow-up validation.
- Verify the affected user journey after deployment.
- Merge or reconcile the fix into the normal development line so it is not lost.
- Complete a retrospective or incident review where warranted.

## 16. Release quality measures

Track measures only where reliable data can be collected. Useful measures include deployment frequency, lead time for changes, change failure rate, time to restore service, escaped defects, rollback/mitigation frequency, and completion of post-release checks. These metrics are intended for process improvement, not individual blame. Establish a baseline before setting numerical targets.

## 17. Release checklist

### Before release

- [ ]  Scope and risk reviewed.
- [ ]  Source revision and artifact identified.
- [ ]  Review, tests, security checks, and required approvals recorded.
- [ ]  API/OpenAPI compatibility assessed.
- [ ]  Database and configuration changes assessed.
- [ ]  Backup/recovery approach confirmed.
- [ ]  Deployment and post-release verification steps ready.
- [ ]  Stop conditions, owner, and communication plan agreed.

### During release

- [ ]  Approved runbook followed.
- [ ]  Actual steps, timings, and migration results recorded.
- [ ]  Unexpected results assessed before continuing.
- [ ]  No secrets or private user data exposed in logs or notes.

### After release

- [ ]  Smoke tests and critical journeys pass.
- [ ]  Logs/health signals reviewed where available.
- [ ]  Release notes and stakeholder updates completed.
- [ ]  Issues and follow-up tasks assigned.
- [ ]  Release record closed with outcome and evidence.

## 18. Document Status

**Active — Release Management Baseline.** This document establishes the expected release-control process. It does not certify that CI/CD, staging, production monitoring, backup automation, feature flags, or rollback tooling exists. The team must validate those capabilities against the live repository and deployment environment, identify the authoritative runbook and release-record location, and document approved exceptions before relying on environment-specific steps.

## 19. Document Control

| Field | Value |
| --- | --- |
| Document ID | KB-OPS-031 |
| Version | 1.0 |
| Created | 2026-10-18 |
| Status | Active baseline; operational implementation verification pending |
| Review trigger | Release workflow, hosting/deployment architecture, CI/CD, database strategy, authentication, payment provider, or approval responsibilities change |
| Change history | v1.0 — Initial release-management baseline |

## Related Documents

- 
    1. API Specification
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
    1. Incident & Troubleshooting Guide