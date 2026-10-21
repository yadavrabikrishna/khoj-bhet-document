# 29. Developer Onboarding Guide

**Project:** KHOJ BHET  

**Document ID:** KB-OPS-029  

**Section:** 04. TEAM & OPERATIONS  

**Status:** Active — Developer Onboarding Baseline; repository URLs, CI enforcement, and machine-specific setup must be verified against the actual implementation  

**Version:** 1.0  

**Owner:** KHOJ BHET Engineering  

**Last Reviewed:** 2026-10-18  

**Previous:** 28. Git & GitHub Workflow  

**Next:** 30. Admin & Operations Guide

---

## 1. Purpose

This guide gives a new developer a consistent path from project orientation to a first reviewed contribution. It explains what to read, how to request access, how to prepare a local environment, how to validate a change, and how to get that change reviewed and merged.

This is an onboarding baseline, not proof that every repository, environment, CI check, permission, or deployment process is already configured. Follow live repository instructions and approved project decisions. Where a setup detail is unverified, confirm it with the maintainer rather than inventing values.

## 2. Scope and authority

This guide applies to contributors working on:

- Laravel 13 backend API and FilamentPHP 5 administration.
- Next.js public web application.
- React Native with Expo mobile application.
- MySQL schema, migrations, seeders, and database-backed tests.
- Firebase Authentication and Bearer-token API integration.
- OpenAPI 3.1 contract and API validation.
- Build, test, CI/CD, infrastructure, monitoring, and operational documentation.

Use project sources according to their authority:

1. **Notion:** canonical product, requirements, architecture, business rules, and team/process documentation.
2. **Git repository:** implementation, tests, migrations, dependency lockfiles, executable configuration, and repository-specific contributor instructions.
3. **ADR Register and accepted ADRs:** recorded technical decisions and rationale. A proposal or pending ADR is not an accepted decision.
4. **Figma / Whimsical:** authoritative design and diagram artifacts for the areas they cover.
5. **GitHub issues and pull requests:** implementation discussion, review evidence, work tracking, and change history.

If sources conflict, do not silently choose whichever is easiest to implement. Check document status and relevant ADR, identify the conflict, and raise it with the maintainer. Update the canonical source after a decision is made.

## 3. Before starting

A maintainer should provide or confirm:

- [ ]  Access to the canonical GitHub repository and the correct account.
- [ ]  Access to relevant Notion documents, design files, issue tracker, and team communication channels.
- [ ]  The approved repository URL and default branch.
- [ ]  Current supported runtime and package-manager versions.
- [ ]  The approved local development and test setup for the assigned component.
- [ ]  Access to required non-production services or test credentials through an approved secure channel.
- [ ]  A named reviewer or technical contact for the assigned area.
- [ ]  The first task, acceptance criteria, and related requirement/story/issue.
- [ ]  Role-specific access required for the task, with least privilege.

Do not request production credentials or real customer data simply to complete onboarding. Use local services, synthetic data, and designated development/test credentials wherever possible.

## 4. Read the project documentation in order

Read the canonical numbered documents under **Documentation Sequence**. This path provides the shared foundation before role-specific reading.

### 4.1 Product foundation — understand what is being built

Read:

1. **01. Product Vision & Mission**
2. **02. Product Scope & Roadmap**
3. **03. Requirements Specification**
4. **04. Users, Roles & Permissions**
5. **05. User Stories & Use Cases**
6. **06. User Flows**
7. **07. UX/UI Specification**
8. **08. Product & Business Rules**

You should be able to explain target users, marketplace capabilities, role boundaries, core journeys, acceptance criteria, and relevant business constraints before implementing a feature.

### 4.2 Technical foundation — understand how the system is designed

Read:

1. **09. Software Architecture**
2. **10. Technology Stack**
3. **11. Development Methodology**
4. **12. Engineering Standards**
5. **13. Database Architecture & Data Model**
6. **14. API Specification**
7. **15. Frontend Architecture**
8. **16. Backend Architecture**
9. **17. Mobile Application Architecture**
10. **18. Authentication & Authorization**
11. **19. Security Architecture**
12. **20. Media & File Storage**
13. **21. Search Architecture**
14. **22. Notification System**
15. **23. SEO Architecture**

Reading a design does not prove that the corresponding feature is implemented or runtime-validated. Check implementation status and evidence separately.

### 4.3 Engineering and quality foundation

Read:

1. **24. Testing & QA**
2. **25. DevOps & CI/CD**
3. **26. Infrastructure & Deployment**
4. **27. Monitoring, Logging & Backup**
5. **28. Git & GitHub Workflow**

Also review **00. Project Documentation Guide**, **00.1 Documentation & SDLC Framework**, **00.2 Terminology & Glossary**, **00.3 Decision / ADR Register**, and relevant requirements/traceability registers. Check the current status of any ADR that affects your task.

### 4.4 Role-specific reading

- **Backend / API:** Documents 13, 14, 16, 18, 19, 20, 21, and 22, plus relevant business rules and database catalogues.
- **Web frontend:** Documents 07, 14, 15, 18, 19, and 23, plus relevant flows and the API contract.
- **Mobile:** Documents 07, 14, 17, 18, 19, and 22, plus client/server compatibility requirements.
- **Database-focused:** Documents 08, 13, 14, 19, and 24, plus schema, migration, integrity, and recovery guidance.
- **DevOps / infrastructure:** Documents 19 and 24–28, plus deployment, secrets, monitoring, backup, and incident guidance.
- **QA / test engineering:** Documents 03–08, 12–14, 18–24, and 28.
- **Administration / operations:** Documents 04, 08, 18–22, 26, and 27, plus the operational guides relevant to the assigned duties.

Role-specific lists supplement rather than replace the shared foundation.

## 5. Development environment setup

Exact commands depend on the actual repository layout and approved tooling. Follow the repository README, contributor guide, lockfiles, and component-specific setup instructions. Do not invent a clone URL, package script, environment variable, secret, or service name.

### 5.1 Prepare the workstation

1. Install supported Git and the runtimes/toolchains required by the assigned component.
2. Install the repository's approved package managers.
3. Configure Git author name and work email for your own account.
4. Authenticate to the approved Git remote using SSH or the organization's approved credential manager.
5. Confirm that credentials are not embedded in remote URLs or saved in scripts.
6. Install dependencies using the documented, reproducible process.
7. Start local infrastructure using the documented development configuration.

Use exact versions stated in repository runtime files, lockfiles, CI configuration, or approved technology documentation. If these sources disagree, ask the maintainer to resolve the mismatch before upgrading tools.

### 5.2 Obtain the repository

After the maintainer confirms the canonical repository URL and default branch:

1. Clone the repository using the approved URL.
2. Read the root README and any applicable package-level README or contributor guide.
3. Check the current branch and working tree before making changes.
4. Create a task-specific branch according to **28. Git & GitHub Workflow**.

Do not create a second canonical repository, rename the default branch, or restructure the project based only on an illustrative example in documentation.

### 5.3 Configure environment variables and secrets

1. Locate the documented example environment file for the relevant application.
2. Copy it to the documented local environment filename.
3. Fill in local-only values using approved instructions.
4. Obtain test credentials through the designated secure process.
5. Verify that local environment files and secrets are excluded from version control.

Never commit real environment files, production application keys, database passwords, Firebase service-account private keys, payment gateway secrets, webhook signing keys, GitHub tokens, SSH private keys, mobile signing keys, production data, or private uploads. An ignore rule is not a substitute for checking staged changes.

If a required variable is undocumented or a secret is unavailable, stop and ask the maintainer. Do not place credentials in Notion pages, issues, pull requests, screenshots, chat, or logs.

### 5.4 Start local services

Use the approved local service configuration. Depending on the assigned component, this may include MySQL, a local API, a web development server, Expo tooling, a queue worker, cache/search services, or object/media-storage emulation.

- Use isolated development/test databases and synthetic data.
- Do not point a local application at production systems unless explicitly authorized through an approved safe procedure.
- Do not assume SQLite is an equivalent substitute for MySQL-backed validation.
- Do not run destructive migrations or reset commands until the target connection has been positively verified.
- Confirm service health checks and ports from actual configuration rather than guessing defaults.

### 5.5 Verify the initial setup

Complete the checks applicable to your component:

- [ ]  Git reports the expected repository and branch.
- [ ]  The working tree is clean before your changes.
- [ ]  Dependencies install using the committed lockfile and approved command.
- [ ]  Required local services start and pass health checks.
- [ ]  The application starts using the documented local command.
- [ ]  Existing relevant tests can be executed.
- [ ]  Documented lint, format, type-check, or static-analysis commands run.
- [ ]  No real secrets or production data are present in the working tree or staged changes.
- [ ]  Setup failures and exact error output are recorded without credentials or sensitive payloads.

Record tool versions and blockers that prevent a clean baseline. Do not mark the environment verified if key checks have not run.

## 6. Project-specific implementation rules

### 6.1 API authentication

The current client API baseline uses a Firebase ID token in the Authorization Bearer header. Do not introduce Laravel session-cookie or CSRF assumptions into this client API without an approved architecture change.

Follow **18. Authentication & Authorization** and **19. Security Architecture** for token verification, authorization, ownership checks, role boundaries, and error handling. Never trust a user ID, role, listing owner, payment state, or moderation decision supplied by the client without server-side verification.

### 6.2 Database changes

MySQL is the authoritative transactional data store in the current architecture baseline. Follow **13. Database Architecture & Data Model** and relevant domain rules.

- Use version-controlled migrations for schema changes.
- Include tests for constraints, relationships, ownership, and relevant edge cases.
- Validate against the supported MySQL version and a clean test database.
- Review foreign keys, indexes, unique constraints, nullability, defaults, and data migrations.
- Never modify an already-applied shared migration as a replacement for a new corrective migration.
- Explain deployment compatibility and recovery implications for destructive or high-risk changes.
- Do not allow seeders to overwrite real marketplace records.

### 6.3 API contracts and clients

The Laravel API is shared by the Next.js web and React Native + Expo clients. Keep request validation, response shape, status/error behavior, authorization, tests, and the canonical OpenAPI 3.1 contract aligned where that contract is maintained.

Before changing an API field, enum, pagination rule, or error response, identify affected clients and compatibility risks. Prefer additive changes when practical. Do not remove or reinterpret a field that a released mobile client may depend on without a migration plan.

The final OpenAPI artifact and clean-MySQL runtime validation have been tracked as project audit gates. Do not claim either is complete unless the current repository and validation evidence demonstrate it.

### 6.4 Security and privacy

- Enforce authorization on the server, including resource ownership and administrative actions.
- Validate and normalize untrusted input at the appropriate boundary.
- Apply documented controls to uploads, file access, public media URLs, and metadata.
- Avoid logging authentication tokens, passwords, private contact details, payment secrets, or unnecessary personal data.
- Use synthetic fixtures and redact logs before sharing them.
- Treat payment callbacks/webhooks as untrusted until signature and state-transition checks pass.
- Add regression tests for security-sensitive behavior.
- Report suspected secret exposure or security incidents promptly through the designated channel.

### 6.5 Documentation and decisions

Update canonical documentation when implementation changes a contract, architecture boundary, business rule, operational procedure, or team workflow. Keep implementation-specific details in the repository where developers need them during builds and reviews, and link back to the Notion source of truth.

Use the ADR process for material technical decisions. A pending ADR is not permission to implement its proposal as a settled standard. Record unresolved questions and blockers rather than silently converting assumptions into decisions.

## 7. First contribution workflow

Follow **28. Git & GitHub Workflow** for detailed source-control and review rules.

1. **Understand the task.** Locate its requirement, user story/use case, flow, business rule, acceptance criteria, and related technical documents.
2. **Confirm scope.** Identify affected components, data, APIs, roles, tests, and documentation. Ask about ambiguous behavior before implementation.
3. **Check existing work.** Review relevant code, open issues/PRs, current tests, and applicable ADRs.
4. **Create a branch.** Use the approved naming convention and current target branch.
5. **Implement narrowly.** Keep the change focused; avoid unrelated refactors and generated-file churn.
6. **Add or update tests.** Cover expected behavior, failure paths, authorization, edge cases, and regressions.
7. **Run checks.** Execute relevant formatters, linters, static analysis, type checks, tests, builds, and database/API validation.
8. **Review the diff.** Inspect staged files, migrations, lockfiles, generated artifacts, logs, and environment files before committing.
9. **Commit clearly.** Use the convention from Document 28, for example: feat(listings): add category filter validation.
10. **Open a pull request.** Explain reason, scope, implementation, test evidence, data/API/security impacts, deployment considerations, and known limitations.
11. **Respond to review.** Resolve comments, rerun affected checks, and request re-review where needed.
12. **Merge through the approved process.** Do not bypass required review or checks without explicit authorization and a recorded exception.
13. **Close the loop.** Confirm documentation and traceability are updated, and identify release or follow-up work.

Do not self-approve a pull request as a substitute for independent review. If repository protections or CI checks are not configured, report that gap; this document does not enable them.

## 8. Definition of ready and done

### 8.1 Ready to start

A task is ready when:

- Its expected behavior and acceptance criteria are clear.
- Relevant requirements, user flows, business rules, and technical decisions have been checked.
- Dependencies and affected components are understood.
- Required access and test data are available.
- Known architecture conflicts and blockers are resolved or explicitly documented.
- A reviewer or owner can be identified.

If these conditions are not met, ask for clarification instead of making a consequential product or security decision by assumption.

### 8.2 Done for a normal code change

A change is ready for merge when:

- Acceptance criteria are met.
- Implementation follows relevant architecture and engineering standards.
- Appropriate tests have been added or updated and run.
- Required local and CI checks pass, or an authorized exception is recorded.
- The diff contains no secrets, production data, accidental generated output, or unrelated changes.
- API, database, security, compatibility, and operational impacts are documented.
- Relevant Notion/repository documentation and traceability links are updated.
- Required reviewers approve and review conversations are resolved.
- The pull request describes remaining limitations and follow-up work honestly.

A merged change is not automatically deployed, released, or runtime-validated in production. Use the release and operations procedures for those activities.

## 9. Communication and escalation

- Raise blockers early and include the task link, affected component, expected versus observed behavior, reproduction steps, and relevant redacted logs.
- Ask a focused question and identify the decision needed; do not share secrets or unnecessary personal data.
- Use the designated team channel or issue/PR thread for decisions so the rationale remains discoverable.
- Record durable architecture decisions through the ADR process rather than leaving them only in chat.
- Notify the relevant owner before breaking API, database, deployment, security, or release changes.
- Distinguish observed behavior, a hypothesis, a proposal, and verified evidence.
- For authentication, authorization, payments, sensitive data, availability, or possible secret exposure, escalate promptly using the applicable incident process.

## 10. Onboarding plan and checkpoints

| Stage | Activities | Exit checkpoint |
| --- | --- | --- |
| Before access | Receive repository/workspace access, role assignment, first task, and secure credential instructions. | Access is least-privilege and the task owner is known. |
| Orientation | Read product foundation and shared project/engineering documentation; identify unresolved decisions relevant to the role. | Developer can explain user value, constraints, and architecture boundary. |
| Environment | Follow repository setup instructions, configure local-only environment, start required services, and run baseline checks. | Setup is reproducible or blockers are recorded with actionable evidence. |
| First change | Make a small scoped change, add tests, run checks, and inspect the diff. | Change satisfies acceptance criteria and is ready for independent review. |
| Review and merge | Open a PR, respond to feedback, satisfy required checks, and update traceability/documentation. | PR is approved and merged through the approved workflow. |
| Role handoff | Review release/operations procedures applicable to the role and confirm ownership boundaries. | Developer knows where to find operational guidance and when to escalate. |

Timings depend on the contributor's role, task complexity, and environment. Completion is judged by these checkpoints, not an arbitrary number of days.

## 11. Common onboarding mistakes to avoid

- Treating archived pages as current authority instead of using canonical numbered documents.
- Treating a document marked Active as proof that its implementation is deployed or tested.
- Treating a pending ADR, illustrative folder path, or proposed workflow as an approved implementation decision.
- Using SQLite as the only validation for MySQL-dependent behavior.
- Introducing session-cookie/CSRF assumptions into the Firebase Bearer-token client API.
- Changing shared API behavior without checking web/mobile compatibility and OpenAPI alignment.
- Editing applied migrations instead of adding a corrective migration.
- Committing secrets, production dumps, private uploads, or unredacted logs.
- Merging without independent review or required checks.
- Updating code but leaving requirements traceability or canonical documentation inconsistent.
- Claiming setup, test, CI, security, or deployment success without evidence.

## 12. Completion checklist

- [ ]  I have read the shared product, architecture, engineering, and Git workflow foundations.
- [ ]  I know which sources are authoritative and how to resolve conflicts.
- [ ]  I have reviewed role-specific documents and relevant ADRs.
- [ ]  I have confirmed the canonical repository and default branch with a maintainer.
- [ ]  I have configured my own Git identity and secure authentication.
- [ ]  I have set up a local environment without committing secrets or production data.
- [ ]  I have run documented baseline checks or recorded blockers.
- [ ]  I understand the task acceptance criteria and its data/API/security impact.
- [ ]  My first contribution includes appropriate tests and a clear pull request.
- [ ]  Required review and checks are complete before merge.
- [ ]  Relevant documentation and traceability are synchronized.
- [ ]  I know the escalation path for blockers and incidents.

## 13. Maintenance and change control

The Engineering owner should review this guide when the technology stack, repository topology, authentication model, API contract, development workflow, security requirements, or onboarding access process materially changes.

Changes must remain consistent with Documents 00–28 and accepted ADRs. When a source document changes, review this guide for stale references and update cross-links. **Active** means this is the current onboarding baseline; it does not certify that all described tools, permissions, CI checks, or deployment controls have been implemented or verified.

## 14. Related documents

- **00. Project Documentation Guide** — documentation authority and governance.
- **00.1 Documentation & SDLC Framework** — lifecycle, review, and change control.
- **00.2 Terminology & Glossary** — canonical project terms.
- **00.3 Decision / ADR Register** — decision status and rationale.
- **00.4 Requirements–Use Cases–User Flows Traceability Matrix** — end-to-end traceability.
- **12. Engineering Standards** — coding and implementation standards.
- **13. Database Architecture & Data Model** — schema and data integrity.
- **14. API Specification** — client/server contract.
- **18. Authentication & Authorization** and **19. Security Architecture** — identity, permissions, and security controls.
- **24. Testing & QA** — validation expectations.
- **25. DevOps & CI/CD**, **26. Infrastructure & Deployment**, and **27. Monitoring, Logging & Backup** — delivery and operations.
- **28. Git & GitHub Workflow** — branches, commits, pull requests, reviews, and repository governance.
- **30. Admin & Operations Guide**, **31. Release Management**, and **32. Incident & Troubleshooting Guide** — operational follow-through.

## 15. Change history

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-10-18 | Created the canonical developer onboarding baseline under 04. TEAM & OPERATIONS; aligned with Documents 00–28 and separated documented standards from implementation evidence. |