# ADR-002 — Authentication Architecture

> ## Accepted Authentication Contract Addendum — 2026-10-09
> 

> This addendum closes the previously open marketplace web session strategy for V1. Normal marketplace clients (Next.js web and React Native/Expo) authenticate to the Laravel API with Firebase Authentication ID tokens in the Authorization: Bearer header. Laravel verifies the Firebase token and applies authoritative MySQL account state, roles, permissions, restrictions, and entitlements. The Laravel marketplace API does not create or require a Laravel application session, session cookie, or CSRF token for this bearer-token API contract. Any future cookie-based BFF/session design requires a separate accepted ADR and matching API/security updates.
> 

> 
> 

> Firebase Authentication owns marketplace phone OTP verification and its supported expiry, attempt, resend and abuse controls. Laravel must not accept OTP codes as business API payloads or implement a second OTP verifier. Configure Firebase App Check and restrict SMS destinations to Nepal (+977) where supported by the chosen Firebase configuration; verify these settings in the actual project.
> 

> 
> 

> MFA is required for all privileged administrative access. Admin authentication remains separate from Firebase marketplace-user authentication through the dedicated Laravel/Filament admins identity store and admin guard.
> 

# ADR Metadata

- **ADR ID:** ADR-002
- **Status:** Accepted
- **Date:** 2026-09-20
- **Decision Owner:** KHOJ BHET Project Team
- **Area:** Security / Identity
- **Related ADRs:** ADR-001
- **Implementation Status:** Not started

# 1. Context

KHOJ BHET needs authentication for public marketplace users and separate administrative access. One user may act as buyer, seller, owner, landlord, tenant, agent, dealer, business, employer, or worker.

The architecture must support phone verification, future identity verification, sessions, account recovery, authorization, and stronger administrative security.

# 2. Decision Drivers

- Security
- Simplicity
- User experience
- Nepal-focused phone verification
- Session management
- Authorization flexibility
- Admin isolation
- Cost
- Provider dependency
- Account recovery
- Web and mobile support
- Auditability

# 3. Alternatives Considered

## Option A — Application-Owned Authentication

The backend owns application identity, sessions/tokens, verification workflows, and authorization. External SMS providers may be used only for OTP delivery.

## Option B — External Identity Provider

A managed identity provider handles authentication while the backend consumes verified identity information.

## Option C — Hybrid

An external provider handles authentication while the application remains authoritative for marketplace profiles, roles, permissions, verification state, and business rules.

# 4. Proposed Decision

**Accepted decision:** Firebase Authentication is the selected authentication mechanism for normal KHOJ BHET users. Laravel remains authoritative for the application's user record, authorization, roles/permissions, account state, entitlement, and marketplace identity. The backend validates Firebase-issued identity tokens and maps the Firebase identity to the MySQL user record.

Phone OTP is an authentication/verification mechanism, not an authorization mechanism.

A separate admin authentication boundary is maintained through Laravel/Filament authentication using a dedicated `admins` identity store and Laravel admin guard. Admin identities are not required to have a Firebase UID and are not represented by the marketplace `users` table.

# 5. Important Distinctions

### Authentication

Who is this user?

### Authorization

What is this user allowed to do?

### Phone Verification

Confirms control of a phone number.

### Identity Verification

A stronger process that may require government-issued or business documentation.

### Admin Authentication

A higher-security access path for administrative users.

These concepts must not be collapsed into one generic verification flag.

# 6. Proposed Identity Model

The application should maintain an authoritative marketplace user record containing marketplace identity and account state. Normal marketplace users map Firebase UID → `users.firebase_uid`. Administrative identities are maintained separately in `admins` under the Laravel/Filament authentication boundary; they are not forced into the marketplace user identity model.

Sensitive authentication data must not be exposed through ordinary marketplace APIs.

# 7. Authorization Model

Authorization should support permissions and multiple capabilities rather than permanently assigning one marketplace identity. A single account may buy a mobile, sell a bike, rent a room, and operate a business profile.

# 8. Consequences

### Benefits

- Clear separation of identity and authorization
- Flexible marketplace roles
- Stronger admin isolation
- Easier web/mobile support
- Clearer verification model

### Trade-offs

- More explicit security design
- OTP provider dependency
- Additional privacy controls for identity verification
- Careful account recovery design

# 9. Security Requirements

The final implementation should address password handling if applicable, session/token expiration, revocation, OTP expiration, OTP attempt limits, rate limiting, device/session management, account recovery, admin MFA where appropriate, audit logging, secret management, and personal-data protection.

# 10. Acceptance Criteria

Finalize the primary authentication mechanism, web session strategy, mobile authentication strategy, OTP provider, account recovery, admin authentication, authorization model, verification model, and security controls.

# 11. Related Documentation

- 
    1. Users, Roles & Permissions
- 
    1. API Specification
- 
    1. Authentication & Authorization
- 
    1. Security Architecture
- ADR-001 — Application Architecture

# 12. Status History

- 2026-09-20 — Created as Proposed.
- 2026-09-28 — Accepted; Firebase Authentication selected for normal users, with Laravel/Filament plus a dedicated admin identity store and guard for administrative users.