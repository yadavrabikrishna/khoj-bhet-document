# 28. Git & GitHub Workflow

**Project:** KHOJ BHET  

**Document ID:** KB-ENG-028  

**Section:** 03. ENGINEERING & QUALITY  

**Status:** Active — Git & GitHub Workflow Baseline; repository settings and enforcement must be verified in the actual GitHub repository  

**Version:** 1.0  

**Owner:** KHOJ BHET Engineering  

**Last Reviewed:** 2026-10-15  

**Previous:** 27. Monitoring, Logging & Backup  

**Next:** 29. Developer Onboarding Guide

---

## 1. Purpose

This document defines the source-control, collaboration, review, and repository-governance workflow for KHOJ BHET. It establishes how changes move from a developer's working tree into reviewed, tested, traceable branches and releases.

The workflow supports the project's Laravel 13 backend and FilamentPHP 5 administration, Next.js public web application, React Native + Expo mobile application, MySQL schema and migration files, API/OpenAPI artifacts, automated tests, and deployment/configuration code where applicable.

This is the agreed working baseline, not a claim that every GitHub setting, branch protection rule, or automation has already been configured.

## 2. Scope and authority

Git is the version-control system. GitHub is the proposed canonical remote collaboration and review platform, subject to confirmation of the actual repository and account settings.

Git-managed artifacts include:

- Application source code and tests.
- Database migrations, seeders, schema definitions, and approved validation scripts.
- API contracts and implementation-relevant specifications that belong with the code.
- Dependency manifests and lockfiles.
- Build, test, CI/CD, deployment, and infrastructure configuration.
- Non-secret environment examples and operational runbooks.
- Versioned engineering documentation that is intended to evolve with implementation.

Not every planning artifact must be duplicated in the repository. Notion remains the primary home for project-level product and architecture documentation; the repository should link to the canonical Notion documents where useful. Figma and Whimsical remain authoritative for their respective design and diagram artifacts.

## 3. Core principles

1. **One canonical remote:** use the designated GitHub repository as the shared source-of-truth for code.
2. **Review before integration:** normal changes enter protected integration branches through pull requests.
3. **Small, focused changes:** keep pull requests reviewable and avoid mixing unrelated refactors, features, and formatting changes.
4. **Automated gates:** required checks must pass before merge.
5. **Traceability:** connect commits and pull requests to requirements, issues, decisions, tests, and releases where applicable.
6. **Security by default:** never commit secrets, production data, private keys, signing credentials, or user uploads.
7. **Reproducibility:** commit lockfiles for application dependencies and document runtime/tool versions.
8. **Compatibility:** coordinate API, database, web, and mobile changes so deployed clients and servers remain compatible.
9. **No silent bypasses:** exceptions to review or checks require explicit authorization and a recorded reason.
10. **Status honesty:** proposed workflow rules are not considered implemented until the repository configuration and evidence confirm them.

## 4. Repository strategy

### 4.1 Recommended repository model

Start with a clearly documented repository boundary. A monorepo is suitable if backend, web, mobile, shared contracts, and infrastructure are developed together and ownership remains manageable. Separate repositories may be chosen if independent permissions, release cycles, or tooling require them.

The final repository topology is an explicit project decision. Do not create multiple repositories or move code solely because this document describes an option.

If a monorepo is selected, use clear top-level boundaries, for example:

- `apps/api` — Laravel API and Filament administration, if they share one Laravel application.
- `apps/web` — Next.js public web application.
- `apps/mobile` — React Native + Expo application.
- `packages/contracts` — shared API schemas or generated client artifacts, only if the project adopts this approach.
- `infra/` — deployment and infrastructure configuration.
- `docs/` — repository-specific engineering instructions and implementation documentation.

These are illustrative paths, not mandatory paths until the repository structure is approved.

### 4.2 Repository ownership

- Keep one canonical remote URL and document it in onboarding material.
- Use GitHub teams or repository roles to grant the minimum access required.
- Restrict administrative access and review changes to repository settings.
- Keep production deployment permissions separate from ordinary write access where supported.
- Use CODEOWNERS for sensitive areas when ownership has been assigned.
- Review access when a contributor joins, changes responsibilities, or leaves.

## 5. Branching model

Use a simple, pull-request-based model. The default baseline is:

| Branch/pattern | Purpose | Merge/deployment rule |
| --- | --- | --- |
| `main` | Production-ready or release-ready history | Protected; changes through reviewed PRs; production release only through approved release process |
| `feature/<short-name>` | New user-facing or technical capability | PR into the selected integration branch |
| `fix/<short-name>` | Non-emergency defect fix | PR with regression coverage |
| `hotfix/<short-name>` | Urgent production correction | Expedited review, required tests, and post-release follow-up |
| `chore/<short-name>` | Tooling, dependency, or maintenance work | PR with relevant checks |
| `docs/<short-name>` | Documentation-only change | PR; lightweight checks where appropriate |

A long-lived `develop` branch is optional, not required. Prefer direct PRs into `main` for a small team if it supports the release model. Introduce `develop` only when multiple parallel changes need a stable integration branch and the team accepts the extra merge and release complexity.

Use lowercase, hyphen-separated branch names. Include an issue or task identifier when the project has an established tracker, for example `feature/KB-142-listing-filters`.

## 6. Git setup and line-ending policy

Each developer should configure an identifiable commit author name and email associated with their work account. Do not share credentials or impersonate another contributor.

Recommended baseline:

- Commit a repository `.editorconfig` for consistent editor behavior.
- Commit `.gitattributes` to define text normalization and binary-file handling.
- Use LF for text files where practical; configure Windows checkouts intentionally rather than allowing accidental line-ending churn.
- Keep executable scripts and shell files with appropriate line endings.
- Avoid global Git settings that unexpectedly override repository conventions.
- Use SSH keys or GitHub's approved credential manager/token flow; never place access tokens in remote URLs or scripts.

A contributor should verify the active identity and remote before pushing, particularly when multiple GitHub accounts are used.

## 7. Commit conventions

Use imperative, specific commit subjects. Recommended format:

`type(scope): concise description`

Common types:

- `feat` — user-visible or functional capability.
- `fix` — defect correction.
- `test` — test-only change.
- `docs` — documentation.
- `refactor` — behavior-preserving restructuring.
- `perf` — performance improvement.
- `build` — build tooling or dependency configuration.
- `ci` — CI workflow changes.
- `chore` — maintenance.
- `security` — security-related correction, when useful and consistent with team convention.

Examples:

- `feat(listings): add category filter validation`
- `fix(auth): reject expired Firebase tokens`
- `test(payments): cover duplicate callback handling`
- `docs(api): clarify listing pagination contract`
- `build(mobile): update Expo dependency lockfile`

Commits should be atomic where practical. Do not use vague messages such as `updates`, `final fix`, `new code`, or `changes`. Avoid rewriting shared history after other contributors have based work on it. Signed commits may be required by repository policy, but that setting must be explicitly decided and enabled rather than assumed.

## 8. Pull request lifecycle

1. Confirm the requirement, acceptance criteria, and relevant architecture/business rules.
2. Create a branch from the current target branch.
3. Implement a focused change and add/update tests.
4. Run the applicable local quality checks.
5. Commit and push the branch.
6. Open a pull request using the repository template.
7. Allow required CI checks to complete.
8. Obtain the required review(s), resolve comments, and update the PR.
9. Merge using the repository's approved merge strategy.
10. Delete the branch when it is no longer needed, unless retention is required for a documented reason.
11. Confirm the change has been included in the intended release and that documentation is synchronized.

Draft pull requests may be used early to share work or expose CI results, but must not bypass the required review and merge gates.

## 9. Pull request template

Every non-trivial pull request should state:

- **Summary:** what changed.
- **Reason:** the requirement, defect, or technical need.
- **Scope:** affected backend, web, mobile, database, API, or infrastructure areas.
- **Related work:** issue, user story, or requirement link where available.
- **Implementation:** notable design choices and trade-offs.
- **Database impact:** migrations, indexes, data backfills, compatibility, and recovery considerations.
- **API impact:** request/response, validation, authorization, enum, pagination, or contract changes.
- **Security/privacy impact:** authentication, authorization, ownership, sensitive data, uploads, secrets, or abuse controls.
- **Tests:** commands or CI jobs run and their results.
- **UI evidence:** screenshots/video for meaningful UI changes where useful.
- **Deployment/operations:** configuration, queue, cache, monitoring, or rollout changes.
- **Known limitations:** unresolved issues and follow-up work.

Do not include credentials, personal data, production payloads, or sensitive logs in the PR description.

## 10. Review requirements

At least one qualified reviewer other than the author should approve ordinary changes when team size and repository permissions allow. The author must not approve their own pull request as a substitute for independent review.

High-risk changes require a reviewer with appropriate domain knowledge. These include:

- Authentication, Firebase token verification, authorization policies, and account recovery.
- Listing ownership, moderation, visibility, and personal/contact/location data exposure.
- Payment initiation, gateway callbacks/webhooks, payment state transitions, refunds, and reconciliation.
- MySQL migrations, data deletion, backfills, and constraint/index changes.
- File upload, media processing, storage permissions, and public URL behavior.
- Secrets, CI/CD, deployment permissions, infrastructure, and security controls.
- API contract changes that affect mobile or web compatibility.

Reviewers should check correctness, maintainability, architecture boundaries, data integrity, security, test quality, operational behavior, and documentation alignment. A successful CI run does not replace review.

## 11. GitHub repository protections

Configure the following on protected branches where the GitHub plan and repository capabilities support them:

- Require pull requests before merging.
- Require the defined number of approvals.
- Dismiss stale approvals when new commits materially change the reviewed diff, if appropriate.
- Require all designated status checks to pass.
- Require branch to be up to date with the target branch when justified by the chosen merge strategy.
- Block force pushes and branch deletion for protected branches.
- Restrict bypass permissions to a small, named administrator/release group.
- Require conversation resolution before merge.
- Use CODEOWNERS for sensitive paths when maintainers are assigned.
- Enable secret scanning, push protection, dependency alerts, and security updates where available and appropriate.
- Review repository Actions/workflow permissions and third-party action usage.

The team must verify the actual settings in GitHub. This document alone does not prove that branch protection or security features are enabled. If a capability is unavailable on the selected plan, record the limitation and the compensating control.

## 12. Required checks before merge

The exact workflow names depend on the adopted CI provider and repository structure. Required checks should cover the affected component and the integration boundary.

Baseline checks, as applicable:

- Dependency installation from committed lockfiles.
- Formatting and linting.
- Static analysis and type checking.
- Unit and component tests.
- Laravel feature/API tests.
- MySQL-backed migration and integration tests.
- API/OpenAPI 3.1 validation when the canonical contract is available.
- Web production build.
- Expo configuration validation and mobile build checks appropriate to the changed code.
- Authorization, ownership, and privacy regression tests for sensitive changes.
- Dependency vulnerability and secret scanning.
- Infrastructure/deployment configuration validation where relevant.

Tests that depend on MySQL behavior must not rely only on SQLite substitutes. CI must use synthetic or approved test data and must not receive production secrets from untrusted pull-request workflows. A check may be waived only through a documented, authorized exception with a reason and expiry/review date.

## 13. Database and migration workflow

Database changes must be committed with application changes when they are part of the same feature.

Required practices:

- Use ordered, version-controlled Laravel migrations.
- Test migrations against a clean MySQL database using the supported project version.
- Review indexes, unique constraints, foreign keys, nullability, defaults, and data transformations.
- Consider existing production data volume, lock duration, and deployment compatibility.
- Prefer expand-and-contract migration patterns for changes that must coexist with old and new application versions.
- Separate large or risky backfills from schema changes when necessary.
- Never edit an already-applied shared migration as a substitute for a new corrective migration.
- Never assume a down migration safely restores deleted or transformed production data.
- Keep seeders safe for repeat execution and ensure they do not overwrite real user or marketplace data.
- Include a recovery/backup plan for destructive or high-risk operations.

A pull request that changes the database must describe deployment order, compatibility requirements, and rollback or forward-recovery strategy.

## 14. API and client compatibility

The Laravel REST API is the shared contract for the Next.js web and React Native + Expo clients. The current client API uses a Firebase ID token in the Bearer Authorization header; do not introduce Laravel session-cookie or CSRF assumptions into this API workflow unless the architecture is deliberately revised and documented.

For contract changes:

- Update the canonical OpenAPI 3.1 contract when it is maintained as a versioned artifact.
- Update request validation, response schemas, enums, error behavior, and tests consistently.
- Identify affected web/mobile versions and backward-compatibility risks.
- Prefer additive changes where possible.
- Do not remove or reinterpret fields that deployed clients may still depend on without a migration plan.
- Coordinate API deployment and mobile release timing; mobile clients can remain in use after a server release.
- Keep generated clients or schemas reproducible and document their generation command if adopted.

Any material change to authentication, API conventions, database ownership, or architecture should be reconciled with the corresponding Notion specification and ADR process.

## 15. Dependency and lockfile policy

Commit the lockfiles used by each application package manager. Install dependencies in CI using the package manager's reproducible/lockfile mode.

Examples include Composer's lockfile for Laravel and the selected npm/pnpm/yarn lockfile for web/mobile packages. Do not mix package managers in the same package without an explicit decision.

When updating dependencies:

- Explain significant framework, runtime, or security-related updates.
- Run the relevant test/build suites.
- Review release notes and breaking changes for major upgrades.
- Avoid unrelated mass upgrades in a feature PR.
- Do not commit generated caches, local vendor directories, node_modules, build output, or environment-specific files unless a specific artifact is intentionally tracked and justified.
- Pin or constrain runtime/tool versions according to the project's approved compatibility policy.

## 16. Secret and sensitive-data prevention

Never commit:

- `.env` files containing real credentials.
- Laravel production `APP_KEY`, database passwords, or cloud/storage credentials.
- Firebase service-account private keys or private credentials.
- Payment gateway secrets, webhook signing keys, or private API tokens.
- GitHub tokens, deploy keys, SSH private keys, certificates, or mobile signing keys.
- Production database dumps, real user data, payment records, private uploads, or unredacted logs.
- Real push notification credentials or signing material.

Commit safe templates such as `.env.example` with placeholders only. Add appropriate exclusions to `.gitignore`, but do not treat ignore rules as a substitute for secret scanning or review.

If a secret is committed or pushed:

1. Revoke/rotate it immediately; deleting the file or rewriting Git history does not make the exposed secret safe.
2. Assess whether it was accessed or used.
3. Remove the secret from current files and, when necessary, clean repository history using an approved procedure.
4. Review forks, clones, logs, CI artifacts, and caches where exposure is possible.
5. Record and handle the event through the incident process.
6. Add a regression control to prevent recurrence.

## 17. .gitignore baseline

The repository should exclude local secrets, dependencies, generated outputs, caches, editor/OS noise, logs, and temporary files appropriate to each component. Review the final ignore rules against the actual repository before adopting them.

Common examples to evaluate include:

- `.env` and environment-specific secret files, while allowing safe example templates.
- `vendor/`, `node_modules/`, and package-manager caches.
- Framework caches, logs, temporary files, and local runtime output.
- `.next/`, Expo/Metro caches, build output, and generated artifacts not intended for version control.
- IDE-specific local settings and operating-system metadata.
- Test artifacts and coverage output where they are reproducible.
- Local database files, dumps, uploaded media, and secrets.

Do not blanket-ignore source artifacts needed for reproducible builds, migrations, lockfiles, test fixtures, or approved generated contracts. Review ignore changes carefully to avoid accidentally excluding required files.

## 18. Merge strategy and history

Choose one repository-wide merge strategy and document it in the repository settings. Squash merge is a reasonable default for short-lived feature branches because it keeps the target branch history compact; merge commits or rebase-based policies may be chosen if preserving individual commits is important.

Whichever strategy is selected:

- Use consistent PR titles and commit conventions.
- Do not force-push protected branches.
- Avoid rewriting history that other contributors may have fetched.
- Resolve conflicts locally and rerun relevant tests after conflict resolution.
- Do not merge code solely to clear a queue or meet a calendar target while required gates fail.

## 19. Release tags and versioning

Releases must be traceable to a specific reviewed commit and release record.

- Use annotated tags for approved release points.
- Select a versioning convention appropriate to the product and mobile store requirements.
- Keep backend/web release identifiers traceable to the source commit and deployment record.
- Manage Android/iOS version and build numbers independently as required by their distribution platforms.
- Protect release-tag creation and signing credentials where applicable.
- Do not treat a tag as proof that deployment succeeded; deployment evidence belongs in the release/CI/CD record.

The exact versioning convention and release authority remain project decisions until approved.

## 20. Hotfix workflow

For a production-critical incident:

1. Confirm incident severity and appoint the authorized incident/release owner.
2. Branch from the deployed release or protected production branch using the agreed hotfix convention.
3. Implement the smallest safe correction and add a regression test.
4. Run mandatory targeted tests and security checks; do not omit critical checks without an explicit emergency exception.
5. Obtain expedited independent review where possible.
6. Deploy using the approved release procedure and verify the critical user journey.
7. Merge or otherwise reconcile the fix into all active branches that need it.
8. Document the incident, cause, decision, and follow-up actions.

Emergency procedures must not become a routine path around review or testing.

## 21. Documentation and decision synchronization

When a code change alters documented behavior, update the relevant specification or record the follow-up owner and deadline. Potentially affected sources include:

- Requirements, user stories, use cases, and business rules.
- Software architecture and technology stack.
- Database architecture and schema artifacts.
- API specification and OpenAPI contract.
- Frontend, backend, mobile, authentication, security, media, search, notification, and SEO architecture.
- Testing, CI/CD, infrastructure, monitoring, backup, and operational runbooks.
- ADR Register when a material technical decision changes.

Notion documents should remain the project-level specification source; repository files should remain authoritative for implementation and executable configuration. Avoid maintaining conflicting copies of the same artifact.

## 22. Repository automation and bots

- Grant GitHub Actions or other automation only the permissions needed by each workflow.
- Pin third-party workflow actions to reviewed versions or immutable commit references according to the project's security policy.
- Do not expose secrets to untrusted fork pull requests.
- Restrict who can modify workflows that have deployment or release privileges.
- Use bots for dependency updates only with review and CI gates.
- Review automated changes like human changes, especially for major upgrades, generated files, database migrations, and lockfiles.
- Keep bot-generated commits and pull requests traceable.

## 23. Collaboration and conflict handling

- Pull or fetch the latest target branch before starting substantial work.
- Keep branches short-lived and rebase/merge regularly according to the chosen policy.
- Do not commit another developer's uncommitted work without coordination.
- Resolve conflicts deliberately; never choose an entire side of a conflict without understanding its effect.
- After resolving conflicts, rerun tests relevant to both sides of the change.
- Coordinate simultaneous edits to API contracts, database schema, shared types, and dependency lockfiles.
- Use issues or task records to make ownership and intended outcomes visible.

## 24. Repository backup and recovery

GitHub is not a complete backup strategy for every project asset or external configuration. Follow Document 27 for the overall backup and restore policy.

At minimum:

- Ensure critical source code, migration history, workflow configuration, and release tags are recoverable from a trusted remote or approved backup.
- Protect repository administrators and account recovery methods.
- Preserve important release artifacts and build provenance according to retention policy.
- Store secrets in an approved secret manager, not in the repository as a backup method.
- Document recovery access and test restoration of critical repository content when required.
- Keep GitHub configuration, branch rules, environments, and deployment secrets documented securely enough to rebuild controls without publishing secret values.

## 25. Metrics and workflow health

Use metrics to improve the process rather than punish individuals. Useful indicators include:

- Pull request lead time and time to first review.
- Review turnaround and PR size.
- CI pass/failure rate and flaky-test frequency.
- Change failure rate and hotfix frequency.
- Defects found after merge or release.
- Dependency/security alert age.
- Frequency of policy exceptions and failed deployments.

Establish targets only after observing a reliable baseline. Do not set arbitrary metrics that encourage bypassing review or splitting work artificially.

## 26. Definition of Done for a pull request

A pull request is ready to merge when all applicable conditions are satisfied:

- [ ]  Scope and acceptance criteria are clear.
- [ ]  Change is focused and reviewed.
- [ ]  Required CI checks pass.
- [ ]  Relevant automated tests are added or updated.
- [ ]  Authorization, ownership, privacy, and security implications are addressed.
- [ ]  Database and API compatibility impacts are documented.
- [ ]  No secrets or production data are included.
- [ ]  Dependencies and lockfiles are consistent.
- [ ]  Documentation and ADRs are updated when required.
- [ ]  Deployment, observability, and recovery implications are considered.
- [ ]  Required approvals and conversation resolutions are complete.

## 27. Decisions to confirm

The following must be confirmed against the actual project setup rather than inferred from this document:

1. Canonical GitHub organization/account and repository URL.
2. Monorepo versus multi-repository structure.
3. Default branch and whether a long-lived `develop` branch is needed.
4. Required approval count and CODEOWNERS assignments.
5. Required CI provider, status-check names, and merge queue policy.
6. Merge strategy and commit-signing requirements.
7. Versioning convention and release-tag authority.
8. GitHub plan availability for branch rules, secret scanning, and other security controls.
9. Repository backup/retention expectations and responsible owner.
10. Issue/task tracker and link conventions.

Until confirmed, these remain open configuration decisions, not completed implementation claims.

## 28. Related documents

- [Documentation Sequence](https://app.notion.com/p/3e19628c857d8052b46fe5ad5bdb76ba?pvs=21)
- [11. Development Methodology](../02%20TECHNICAL%20DEFINITION/11%20Development%20Methodology%203e59628c857d8147a202d17b99dd3377.md)
- [12. Engineering Standards](../02%20TECHNICAL%20DEFINITION/12%20Engineering%20Standards%203e59628c857d815e93a9fb1facd0a97e.md)
- [14. API Specification](../02%20TECHNICAL%20DEFINITION/14%20API%20Specification%203ed9628c857d81a6b7e7ea0697cef4d1.md)
- [24. Testing & QA](24%20Testing%20&%20QA%203fa9628c857d81d7870dd25fec40a0db.md)
- [25. DevOps & CI/CD](25%20DevOps%20&%20CI%20CD%203fa9628c857d8121a3fcd748fc06f698.md)
- [26. Infrastructure & Deployment](26%20Infrastructure%20&%20Deployment%203fa9628c857d811bb075e4a90712af72.md)
- [27. Monitoring, Logging & Backup](27%20Monitoring,%20Logging%20&%20Backup%203fa9628c857d812c97ddcea2cc689613.md)
- 
    1. Developer Onboarding Guide — planned next document in the documentation sequence.

## 29. Repository Bootstrap Gate — 2026-10-18

**Status: REPOSITORY CREATED; BOOTSTRAP NOT STARTED — verified 2026-10-18.** Canonical repository: [https://github.com/yadavrabikrishna/khoj-bhet](https://github.com/yadavrabikrishna/khoj-bhet) (private; default branch configured as `main`; repository currently empty, with no commits or branches returned by the connected GitHub integration). This section defines the remaining bootstrap checklist; repository creation does not prove that branch protection, CI, code, schema artifacts, or other controls are active.

### 29.1 Before creating the repository

- Confirm whether the project will use a monorepo for Laravel API, Next.js web, and Expo mobile, or separate repositories. Default recommendation: a monorepo for the initial team unless independent deployment/access needs justify separation.
- Confirm the GitHub account/organization that will own the repository and who will administer it.
- Keep Notion as the product/architecture specification source; keep source code, migrations, tests, OpenAPI artifact, lockfiles, CI workflows, and executable configuration in Git.
- Recover/regenerate the current schema package before application feature work: `schema.dbml`, `2026_09_28_000000_create_khoj_bhet_schema.php`, `khoj-bhet-migration-validation.md`, and `database-schema-review.md`. The latest approved decision baseline is 55 tables / 89 declared FKs, but Document 13 records that the artifact package requires regeneration after later gate changes. These files must share one revision and be reconciled before TV-01.

### 29.2 Initial repository safeguards

- Create the repository as private during initial development unless the owner explicitly approves public visibility.
- Use `main` as the protected default branch; do not add a permanent `develop` branch without a clear workflow need.
- Require pull requests for changes to `main`, independent review where team size permits, passing CI checks, and resolution of review conversations.
- Add a `CODEOWNERS` file when maintainers/ownership areas are known.
- Add `.gitignore` before importing project files. Exclude `.env*` except documented safe examples, credentials, private keys, local databases/dumps, uploads, build outputs, dependency directories, editor caches, and machine-specific files.
- Add `.env.example` containing placeholder names only; never real credentials, tokens, Firebase service-account keys, database passwords, signing keys, or production values.
- Grant GitHub Actions least privilege; do not expose deployment secrets to untrusted pull requests. Protect environment secrets and release permissions.
- Choose and document the merge strategy, commit convention, release-tag policy, issue/task tracker, and backup/recovery owner.

### 29.3 Minimum initial repository layout

The layout is a proposal until the monorepo decision is approved:

```
khoj-bhet/
  apps/
    api/                 # Laravel 13 API and Filament administration
    web/                 # Next.js public web client
    mobile/              # Expo / React Native client
  packages/              # Shared TypeScript contracts/utilities only where justified
  docs/
    api/openapi.yaml     # generated/validated OpenAPI 3.1 contract
    architecture/        # implementation-facing diagrams/artifact notes
  database/
    schema.dbml
    validation/          # clean-MySQL validation SQL and instructions
  .github/
    workflows/
    CODEOWNERS
  .gitignore
  README.md
```

Do not create empty app folders merely to imply those applications are initialized. If the owner chooses separate repositories, revise the layout and cross-repository contract/versioning plan before bootstrap.

### 29.4 Exit criteria

- Repository exists and the canonical URL is recorded in the project documentation.
- Monorepo/multi-repo decision, default branch, visibility, maintainers and merge strategy are approved.
- Initial `.gitignore`, safe `.env.example`, README and branch protections are present and verified.
- Current schema artifact package is regenerated/reconciled; TV-01 remains open until disposable MySQL runtime evidence passes.
- CI workflow is present and a first run is captured against a known commit. Repository creation alone does not pass TV-01, TV-02 or TV-09.

## 30. Change history

- **v1.0 — 2026-10-15:** Initial Git and GitHub workflow baseline created. Repository-specific choices and enforcement settings remain to be verified and approved.
- **v1.1 — 2026-10-18:** Added repository bootstrap gate after confirming no GitHub repository exists; clarified schema artifact regeneration prerequisite and separated proposed repository controls from verified state.