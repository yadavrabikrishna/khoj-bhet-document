# 18. Authentication & Authorization

> **Implementation status clarification — 2026-10-15:** “Active” means this is the current authoritative design baseline, not that implementation is release-ready. Implementation sign-off remains gated by the final OpenAPI 3.1 contract, successful clean-MySQL migration/runtime validation, and the relevant component tests. Component-specific schema or provider gates documented below remain independently binding.
> 

Document ID: KB-TECH-018

Status: Active — Authentication & Authorization Baseline

Version: 1.0

Owner: KHOJ BHET Engineering

Last Reviewed: 2026-10-08

Parent: 02. TECHNICAL DEFINITION

Previous: 17. Mobile Application Architecture

Next: 19. Security Architecture

Related: 04. Users, Roles & Permissions, 09. Software Architecture, 10. Technology Stack, 12. Engineering Standards, 14. API Specification, 15. Frontend Architecture, 16. Backend Architecture, 17. Mobile Application Architecture, ADR-002 — Authentication Architecture, 19. Security Architecture

# 1. Document Purpose

This document defines the production authentication and authorization architecture for KHOJ BHET.

It translates the approved identity model and ADR-002 decision into implementation rules shared by the web application, mobile application, Laravel backend, Filament administration, API, database, verification workflows, subscriptions, and security controls.

The central architectural distinction is:

**Authentication answers: “Who is this identity?”**

**Authorization answers: “What is this identity allowed to do, to which resource, under which conditions?”**

Authentication does not grant marketplace permissions automatically.

Laravel remains authoritative for marketplace identity, account state, authorization, roles, permissions, ownership, entitlements, verification state, listing access, privacy, and business rules.

# 2. Architectural Decision

ADR-002 is accepted.

### Normal marketplace users

Firebase Authentication is the selected authentication mechanism for normal KHOJ BHET users.

Flow:

Firebase Authentication

→ Firebase ID Token

→ Laravel token verification

→ MySQL marketplace user lookup

→ Account-state evaluation

→ Authorization evaluation

→ API operation

### Administrative users

Administrative authentication is intentionally separate.

Laravel / Filament authentication

→ dedicated `admins` identity store

→ Laravel admin guard

→ admin authorization

→ administrative operation

Admin identities are not required to have a Firebase UID and are not represented by the marketplace `users` table.

# 3. Core Authority Rules

1. Firebase authenticates normal marketplace users.
2. Laravel verifies Firebase-issued identity tokens.
3. MySQL stores the authoritative marketplace user record.
4. Laravel decides marketplace authorization.
5. Subscription status is an entitlement, not a role.
6. Verification status is not equivalent to authorization.
7. Phone verification is not permission.
8. Identity verification is not permission.
9. Admin identity is separate from marketplace identity.
10. The client never becomes the authorization authority.
11. Hidden UI controls are not security controls.
12. Every protected API operation is authorized server-side.

# 4. Identity Model

A normal marketplace identity follows:

Firebase UID

↓

users.firebase_uid

↓

Marketplace User

↓

Roles / Capabilities / Ownership / Verification / Entitlements

The marketplace user record contains application identity and account state.

The application may maintain profile information, business relationships, verification records, permissions, and marketplace activity separately from the authentication provider.

Firebase is not the authoritative source for:

- marketplace roles;
- listing ownership;
- account suspension;
- subscription entitlement;
- business membership;
- moderation status;
- exact-location entitlement;
- marketplace verification decisions.

# 5. Identity Uniqueness

`users.firebase_uid` must be unique.

A Firebase identity must map to at most one active marketplace user identity.

The system must prevent accidental duplicate marketplace accounts when:

- the same Firebase user signs in from another device;
- a token is refreshed;
- the application is reinstalled;
- the user changes devices;
- the user changes authentication context supported by Firebase;
- account recovery occurs.

Account linking rules must be explicit and must not silently merge accounts.

# 6. Authentication Flow — Web

Browser

→ Firebase Authentication

→ Firebase ID Token

→ Laravel Authentication Boundary

→ Verify Token

→ Resolve users.firebase_uid

→ Evaluate Account Status

→ Send Firebase ID token as `Authorization: Bearer <token>` to Laravel API

→ Laravel verifies token and applies current MySQL account state, roles, permissions, and entitlement

→ Authorized API request

**V1 marketplace API authentication is bearer-only.** Laravel does not create an application session for marketplace web clients; the API does not use session cookies or CSRF tokens for this bearer-token flow. Next.js may perform server-side requests but must not silently introduce a Laravel cookie session. Any future cookie-based BFF/session design requires a separate accepted ADR and matching API/security contract. The browser must never send Firebase Admin credentials.

# 7. Authentication Flow — Mobile

React Native + Expo

→ Firebase Authentication

→ Firebase ID Token

→ Axios Authorization Header

→ Laravel API

→ Verify Firebase Token

→ Resolve Marketplace User

→ Authorize Request

The mobile application must refresh expired authentication credentials through the supported Firebase mechanism.

The mobile application must not implement its own competing authorization token format.

# 8. API Authentication

Protected API requests use:

Authorization: Bearer <Firebase ID Token>

Laravel must:

1. validate token authenticity;
2. validate token integrity and required claims;
3. determine the Firebase UID;
4. resolve the marketplace user;
5. evaluate account state;
6. continue to authorization;
7. reject invalid or unusable identities.

The API must not trust a client-provided user ID as proof of identity.

# 9. Token Validation

The backend must validate Firebase ID tokens using an authoritative server-side Firebase verification mechanism.

Validation must include the claims and conditions required by the Firebase authentication integration, including:

- signature;
- issuer;
- audience/project;
- expiration;
- issued-at constraints where applicable;
- subject/UID;
- revocation state where the selected implementation requires or supports it.

The backend must not decode a JWT and treat decoding alone as verification.

# 10. Token Lifetime and Refresh

Firebase controls normal Firebase ID-token issuance and refresh behavior.

The client must:

- use the Firebase SDK for token lifecycle;
- refresh credentials when required;
- avoid manually constructing tokens;
- avoid storing raw credentials in ordinary local storage;
- recover cleanly from authentication expiration.

Laravel must not assume that a token remains valid indefinitely.

# 11. Revocation and Session Invalidation

The architecture must support access invalidation when:

- account is suspended;
- account is deactivated;
- security compromise is detected;
- authentication provider state is revoked;
- user account is deleted/anonymized;
- required security state changes.

A valid Firebase token does not automatically mean the marketplace account remains authorized.

Laravel must evaluate current marketplace account state for protected operations.

# 12. Account Provisioning

When a valid Firebase identity reaches Laravel for the first time:

Verified Firebase UID

→ Find users.firebase_uid

→ If found: load user

→ If absent: controlled account provisioning

→ Apply default account state

→ Return authenticated marketplace context

Automatic provisioning must not grant privileged roles.

Initial marketplace capability should be the minimum required for a normal registered user.

# 13. Account Linking

Account linking is security-sensitive.

The system must not merge identities merely because:

- email addresses appear equal;
- phone numbers appear equal;
- names match;
- device identifiers match.

Any account-linking operation must require authenticated proof of control of the relevant identities and must follow an explicit recovery/linking workflow.

# 14. Authentication Methods

Firebase Authentication provides the normal-user authentication boundary.

The project may support approved Firebase authentication methods such as:

- phone authentication;
- email/password where enabled;
- approved future identity-provider methods.

The selected production methods must be documented in configuration and tested.

An authentication method identifies a user; it does not determine marketplace permissions.

# 15. Phone OTP

Phone OTP for marketplace sign-in/phone verification is handled by Firebase Authentication. Laravel does not receive or validate OTP codes and does not independently enforce Firebase OTP expiry, code-attempt limits, or resend throttling. Configure and monitor these controls through Firebase Authentication and its supported abuse-protection settings. Application-owned SMS notifications, if introduced, are a separate workflow and must not be confused with Firebase Authentication OTP.

It must not be treated as:

- seller authorization;
- business verification;
- identity verification;
- admin authorization;
- premium entitlement.

Firebase Authentication owns OTP expiration, verification attempt limits, resend throttling, and provider-level abuse controls. The application must configure the available Firebase protections, restrict allowed SMS destinations to Nepal (+977) where supported by the chosen Firebase configuration, monitor SMS spend/abuse, and apply Firebase App Check where supported for the client platform. Laravel must never implement a parallel OTP verifier or accept OTP codes as business API payloads.

The system must not expose OTP values through logs, analytics, API responses, or error messages.

# 16. Email Verification

Where email authentication/verification is enabled, email verification state may be used as an eligibility condition only where explicitly required by product rules.

It does not automatically grant:

- seller status;
- business status;
- moderator access;
- administrator access;
- subscription entitlement.

# 17. Identity Verification

Identity verification is distinct from authentication.

Conceptual model:

Authenticated User

→ Verification Workflow

→ Verification Record

→ Verification Type

→ Verification State

→ Product-specific eligibility

V1 approved verification subjects/types:

- User: phone;
- User: email;
- User: identity;
- Business: business.

Professional and standalone address verification remain deferred for V1.

Verification state must not be collapsed into a generic verified=true authorization flag.

# 18. Verification State

A verification record should distinguish the relevant lifecycle states exposed by the approved registry and implementation.

Examples may include:

- pending;
- approved;
- rejected;
- expired;
- revoked.

The exact public enum must follow the final public API enum registry.

A user must not receive a protected capability merely because a verification workflow exists.

# 19. Marketplace Roles

The product-level baseline from Document 04 includes:

- Visitor;
- User;
- Poster;
- Moderator;
- Administrator.

However, the technical authorization model must not depend on one permanent marketplace persona.

One authenticated user may simultaneously:

- buy;
- sell;
- rent;
- act as an owner;
- act as an agent;
- operate a business;
- perform other approved marketplace activities.

Capabilities are evaluated from the user's current authorization context.

# 20. Authorization Layers

Authorization should be evaluated in layers:

1. Is the request authenticated?
2. Is the account active and allowed to operate?
3. Does the user have the required capability?
4. Does the user have access to this resource?
5. Does ownership/delegation permit the operation?
6. Does listing/resource state permit the operation?
7. Does verification permit the operation where required?
8. Does entitlement permit the requested feature where required?
9. Does privacy policy permit the requested data?
10. Does safety/moderation policy impose a restriction?

A request succeeds only when all applicable checks pass.

# 21. Default Deny

Authorization is default-deny.

A permission must be explicitly granted or derived from an approved rule.

Adding a new endpoint must not automatically make the underlying operation available to every authenticated user.

# 22. Least Privilege

The system grants the minimum capability required for a task.

Examples:

- A user may edit their own listing without being able to edit another user's listing.
- A business manager may operate scoped listings without managing business members.
- A moderator may review reports without receiving unrestricted system configuration access.
- An administrator may manage configuration only through explicitly granted administrative permissions.

# 23. Resource Ownership

Ownership checks are mandatory for user-owned resources.

Examples:

- own profile;
- own listing;
- own favorite;
- own push-device registration;
- own preferences.

Conceptual rule:

authenticated_[user.id](http://user.id) == resource.owner_id

Where delegation exists, the authorization policy must additionally evaluate the delegation scope.

# 24. Listing Poster vs Owner

KHOJ BHET must not assume:

poster = owner

A listing may be represented by:

- owner;
- authorized agent;
- broker;
- dealer;
- property manager;
- authorized representative.

The authorization model must therefore evaluate the relationship between the authenticated user, business, poster, representative, and listing.

# 25. Business Authorization

V1 business roles are:

- owner;
- admin;
- manager;
- member.

Membership must be:

- active;
- associated with the target business;
- evaluated within the business scope.

Business roles never grant platform-wide administrative or moderation authority.

# 26. V1 Business Permission Matrix

| Capability | Owner | Admin | Manager | Member |
| --- | --- | --- | --- | --- |
| View business resources within scope | Yes | Yes | Yes | Yes |
| Edit business profile | Yes | Yes | No | No |
| Invite members | Yes | Yes | No | No |
| Change member role/status | Yes | Yes, except owner | No | No |
| Remove members | Yes | Yes, except owner | No | No |
| Create business listings | Yes | Yes | Yes | Yes |
| Edit business listings | Yes | Yes | Yes | Yes |
| Submit business listings | Yes | Yes | Yes | No |
| Pause business listings | Yes | Yes | Yes | No |
| Resume business listings | Yes | Yes | Yes | No |
| Archive business listings | Yes | Yes | No | No |
| Delete business listings | Yes | Yes | No | No |
| Act as business representative on authorized listings | Yes | Yes | Yes | Yes |
| Platform administration/moderation | No | No | No | No |

Additional rules:

1. Business Admin cannot modify, remove, or demote the Business Owner.
2. Manager cannot manage members.
3. Member cannot submit, pause, resume, archive, or delete listings.
4. All business listing operations remain subject to listing lifecycle, moderation, privacy, consent, entitlement, account-state, and safety rules.
5. Ownership transfer is not implied by business membership.

# 27. Scoped Authorization

Authorization must support scope.

Possible scopes:

- platform;
- business;
- listing;
- conversation;
- resource.

A scoped permission must not accidentally become global.

Example:

business:123

manager

→ listing:456

→ listing:789

does not imply access to business:999 or platform administration.

# 28. Subscription and Entitlement

Subscription is not authorization.

Conceptual chain:

User / Business

→ Subscription

→ Entitlement

→ Feature Access

Entitlements may control approved premium features such as:

- additional listing limits;
- featured placement;
- advanced analytics;
- business tools;
- restricted-information access where explicitly approved.

Entitlements never override:

- security;
- moderation;
- account suspension;
- administrator-only access;
- legal restrictions;
- privacy restrictions.

# 29. Restricted Information Authorization

Sensitive marketplace information must have explicit authorization.

Examples:

- exact location;
- direct contact information;
- additional seller information;
- premium facilities.

The API must determine whether the requester is entitled to receive the information.

The client must not infer access from:

- subscription UI;
- cached content;
- previous access;
- listing ownership assumptions;
- URL parameters.

# 30. Authorization for Listing Lifecycle

Listing actions must be state-aware.

Conceptual:

Draft

→ submit

→ Review / Validation

→ Published

→ pause

→ Paused

→ resume

→ Published

→ expire/archive

Each command must check:

- authenticated actor;
- actor capability;
- ownership/representation;
- current lifecycle state;
- moderation state;
- applicable business rules;
- entitlement where relevant.

The client must never directly set arbitrary lifecycle state.

# 31. Administrative Authentication

Administrative access is isolated from normal marketplace authentication.

Admin architecture:

Admin User

→ Laravel / Filament Authentication

→ Admin Guard

→ admins identity store

→ Admin Authorization

→ Admin Resource

Admin accounts:

- do not require Firebase UID;
- are not ordinary marketplace users;
- must use stronger operational controls;
- must have explicitly assigned administrative permissions.

# 32. Admin Role Separation

Administrative responsibilities should be separated where practical.

Potential administrative roles:

- Platform Administrator;
- Content Moderator;
- Support Operator;
- Verification Operator;
- Technical Operator.

Administrative roles must follow least privilege.

A support operator should not automatically gain:

- database administration;
- security configuration;
- unrestricted moderation;
- payment configuration;
- platform-wide role management.

# 33. Admin MFA

**MFA is required for all privileged administrative access**, consistent with Documents 10 and 19. Enforce the approved MFA mechanism at the admin authentication boundary; do not describe MFA as optional or defer the requirement to deployment policy.

# 34. Authorization Middleware and Policies

Laravel authorization should be implemented through consistent server-side mechanisms.

Conceptual request pipeline:

HTTP Request

→ Authentication Middleware

→ Account-State Check

→ Route/Capability Check

→ Resource Policy

→ Ownership / Scope Check

→ Business Rules

→ Controller / Action

Authorization logic must not be duplicated inconsistently across controllers.

Laravel Policies, Gates, middleware, domain services, or equivalent mechanisms should have clear ownership of each authorization decision.

# 35. API Authorization

Document 14 defines public API endpoints and authorization requirements.

Every protected endpoint must specify:

- authentication requirement;
- permission/capability requirement;
- resource scope;
- ownership requirement;
- role requirement if applicable;
- verification requirement if applicable;
- entitlement requirement if applicable;
- privacy restrictions;
- expected forbidden behavior.

A client must not infer authorization merely from HTTP route visibility.

# 36. HTTP Authorization Outcomes

The API should distinguish relevant cases according to the public API contract.

Typical outcomes:

- 401 — authentication missing/invalid;
- 403 — authenticated but not authorized;
- 404 — resource not found or intentionally undisclosed;
- 409 — state/conflict condition;
- 422 — validation failure;
- 429 — rate limited.

The exact status/error envelope must follow Document 14.

The system must avoid leaking whether a sensitive resource exists when policy requires indistinguishable not-found behavior.

# 37. Insecure Direct Object Reference Protection

Never authorize a request solely because a resource ID is syntactically valid.

Bad pattern:

PATCH /listings/123

→ load listing 123

→ update

Required pattern:

authenticate actor

→ load resource

→ evaluate policy

→ evaluate ownership/delegation

→ evaluate state

→ update only if authorized

Resource IDs are identifiers, not permissions.

# 38. Account Status

Account state can restrict authorization.

Potential states:

- active;
- pending verification;
- restricted;
- suspended;
- deactivated;
- deletion_pending (normal marketplace access disabled while a cancellable deletion request is processed);
- deleted/anonymized.

`deletion_pending` is not the same as `deactivated`: it represents an active deletion workflow with a defined cancellation window and retention/finalization rules. Exact transitions, cancellation eligibility, and provider-side Firebase identity deletion remain governed by the approved account-deletion workflow.

Examples:

- suspended accounts may be prevented from publishing;
- deactivated accounts may lose normal interactive access;
- restricted accounts may retain limited read access;
- deleted/anonymized accounts must not retain ordinary authenticated access.

Exact state transitions remain governed by product/business and security rules.

# 39. Permission Revocation

Authorization changes must take effect promptly enough for the security requirement.

Examples:

- moderator role removed;
- business membership revoked;
- account suspended;
- entitlement expires;
- listing delegation removed.

The backend must not depend exclusively on long-lived client-side cached permission state.

# 40. Client Authorization State

Web and mobile clients may cache authorization state for UX.

Examples:

- show/hide controls;
- route guards;
- feature presentation.

However:

**Client authorization state is advisory only.**

Every protected operation must be re-authorized by Laravel.

A user who manipulates the client must not gain additional capability.

# 41. Session and Device Management

Normal-user session/device management must support:

- multiple devices;
- token refresh;
- sign-out;
- account suspension handling;
- credential invalidation where supported;
- push-device registration independently from authorization.

Push-device registration is a user-owned resource.

A user may have multiple active devices.

The user may manage only their own registrations.

# 42. Push Device and Authorization

Push registration does not grant:

- a role;
- verification;
- entitlement;
- administrative capability.

Notification infrastructure may invalidate a device token based on provider feedback.

Raw push tokens are infrastructure-sensitive data and are not ordinary marketplace information.

# 43. Account Recovery

Account recovery must preserve the identity model.

Recovery must:

- prove control of the approved authentication factor/provider;
- avoid account enumeration;
- respect rate limits;
- preserve marketplace authorization boundaries;
- not silently transfer ownership;
- not grant administrative privileges.

A recovery event does not automatically modify:

- business membership;
- listing ownership;
- verification status;
- subscription;
- administrator status.

# 44. Sensitive Account Operations

High-impact operations should require appropriate authentication state and, where defined by security policy, recent authentication or additional verification.

Examples:

- account deletion;
- security-factor changes;
- sensitive identity changes;
- payment-related account changes;
- privileged business membership changes.

Exact requirements are finalized in Document 19.

# 45. Authorization Auditability

Important authorization events should be attributable.

Examples:

- admin role changes;
- business membership changes;
- privileged listing actions;
- moderation actions;
- verification decisions;
- account suspension;
- entitlement changes;
- sensitive access grants.

Audit records should identify:

- actor;
- action;
- target/resource;
- timestamp;
- relevant scope;
- outcome;
- request/correlation identifier where appropriate.

Do not log secrets or unnecessary sensitive payloads.

# 46. Authorization Caching

Authorization decisions may be cached only where:

- the cache key includes all relevant identity/scope dimensions;
- invalidation is defined;
- stale authorization cannot create unacceptable security exposure.

Core authorization should prefer current authoritative state for sensitive operations.

Redis is infrastructure for controlled caching and queues; it is not a client-accessible authorization store.

# 47. Service-to-Service Authorization

Internal services/workers must use explicit service authentication/authorization.

Examples:

- Laravel queue worker;
- notification worker;
- payment adapter;
- media processing;
- scheduled jobs.

A background job must not impersonate an arbitrary marketplace user merely because it contains a user ID.

Service identity and user identity must remain distinguishable.

# 48. Queue and Job Authorization

Queued jobs must carry only the information required to perform their approved operation.

Before executing sensitive operations, jobs should verify that the referenced state remains valid where the operation is security-sensitive.

Examples:

- notification job must not disclose a revoked protected resource;
- entitlement job must not grant access without verified payment state;
- moderation job must use the recorded moderation authority.

# 49. Web and Mobile Consistency

The web and mobile applications must consume the same authorization semantics.

They may differ in:

- UI;
- navigation;
- device capability;
- local state.

They must not differ in:

- role meaning;
- permission meaning;
- ownership rules;
- entitlement meaning;
- verification meaning;
- protected-data rules.

# 50. Security Boundaries

The following are security boundaries:

Firebase Authentication

↓

Laravel Authentication Boundary

↓

Marketplace User Identity

↓

Authorization

↓

Resource / Scope / Ownership

↓

Entitlement / Verification / Privacy

↓

Business Operation

Breaking any boundary must result in denial rather than implicit permission.

# 51. Threats Addressed

This architecture specifically addresses:

- forged authentication tokens;
- expired tokens;
- revoked accounts;
- privilege escalation;
- IDOR;
- horizontal privilege escalation;
- vertical privilege escalation;
- stale entitlement;
- unauthorized business access;
- unauthorized listing edits;
- admin identity mixing;
- account enumeration;
- token leakage;
- insecure client-side authorization;
- unauthorized protected-data access;
- replay of sensitive mutations where idempotency is required.

Detailed threat modeling and security controls belong to Document 19.

# 52. Testing Strategy

Authentication tests must include:

- valid token;
- expired token;
- invalid token;
- wrong Firebase project/audience;
- revoked identity where supported;
- unknown Firebase UID;
- inactive marketplace account;
- suspended account;
- deactivated account;
- account provisioning;
- duplicate UID prevention.

Authorization tests must include:

- own resource;
- another user's resource;
- authorized business member;
- unauthorized business member;
- manager versus admin;
- business owner protection;
- moderator boundary;
- administrator boundary;
- expired entitlement;
- missing verification;
- restricted information;
- lifecycle-state violations;
- IDOR attempts;
- privilege escalation attempts.

# 53. Acceptance Test Examples

### User listing edit

Firebase-authenticated user

→ Laravel resolves user

→ listing policy checks ownership

→ listing state permits edit

→ request succeeds

### Another user's listing

Firebase-authenticated user

→ Laravel resolves user

→ listing policy fails ownership/delegation

→ request denied

### Business manager

Authenticated business member

→ membership active

→ role = manager

→ listing belongs to scoped business

→ operation = pause

→ allowed if lifecycle permits

### Business member

Authenticated business member

→ membership active

→ role = member

→ operation = delete listing

→ denied

### Suspended account

Valid Firebase token

→ marketplace user = suspended

→ protected mutation

→ denied

A valid authentication token must not override marketplace account state.

# 54. Implementation Rules

### Rule 1

Firebase Authentication is for normal marketplace authentication.

### Rule 2

Laravel is authoritative for marketplace authorization.

### Rule 3

The users.firebase_uid mapping is unique.

### Rule 4

Admin identities remain separate in admins.

### Rule 5

Authentication and authorization remain separate concepts.

### Rule 6

Verification is not authorization.

### Rule 7

Subscription entitlement is not authorization.

### Rule 8

Client-side permission state is never a security boundary.

### Rule 9

Every protected resource operation requires server-side policy evaluation.

### Rule 10

Ownership and delegated business scope must be evaluated.

### Rule 11

Business roles are scoped to the business.

### Rule 12

Admin privileges are isolated from marketplace roles.

### Rule 13

Protected data must be authorized at request time.

### Rule 14

Push-device registration does not grant authorization.

### Rule 15

Resource identifiers never imply permission.

# 55. Relationship to Other Documents

| Area | Authority |
| --- | --- |
| Product user/role model | 04. Users, Roles & Permissions |
| User stories/use cases | 05. User Stories & Use Cases |
| Business access rules | 08. Product & Business Rules |
| System architecture | 09. Software Architecture |
| Technology baseline | 10. Technology Stack |
| Engineering rules | 12. Engineering Standards |
| Database identity model | 13. Database Architecture & Data Model |
| Public API authentication/authorization contract | 14. API Specification |
| Web authentication integration | 15. Frontend Architecture |
| Laravel authorization implementation | 16. Backend Architecture |
| Mobile authentication integration | 17. Mobile Application Architecture |
| Authentication & authorization | 18. Authentication & Authorization |
| Security controls and threat model | 19. Security Architecture |

# 56. Implementation Readiness Checklist

Before production implementation:

- [ ]  Firebase Authentication project/configuration is defined.
- [ ]  Firebase UID → MySQL user mapping is unique.
- [ ]  Laravel token verification is implemented.
- [ ]  Token claims are validated server-side.
- [ ]  Account-state checks are implemented.
- [ ]  Marketplace authorization policies are defined.
- [ ]  Ownership checks are implemented.
- [ ]  Business-scoped authorization is implemented.
- [ ]  V1 business member matrix is implemented.
- [ ]  Admin identity store is separate.
- [ ]  Admin guard is separate.
- [ ]  Admin MFA is enforced and tested before privileged admin access is granted.
- [ ]  Verification states are represented separately from authorization.
- [ ]  Entitlements are represented separately from roles.
- [ ]  Protected-information policies are implemented.
- [ ]  Push-device ownership rules are implemented.
- [ ]  Account recovery is defined.
- [ ]  Permission revocation behavior is defined.
- [ ]  Audit events are defined.
- [ ]  Authentication/authorization contract tests are implemented.
- [ ]  IDOR and privilege-escalation tests are implemented.
- [ ]  Web and mobile authorization semantics are aligned.
- [ ]  Security review is completed.

# 57. Status

**Active — Authentication & Authorization Baseline.**

This document operationalizes ADR-002 and the approved product-level permission model.

The architecture deliberately separates:

- Firebase authentication;
- Laravel marketplace identity;
- authorization;
- ownership/delegation;
- verification;
- subscription entitlement;
- administrative identity.

The next technical-definition document is:

**19. Security Architecture.**