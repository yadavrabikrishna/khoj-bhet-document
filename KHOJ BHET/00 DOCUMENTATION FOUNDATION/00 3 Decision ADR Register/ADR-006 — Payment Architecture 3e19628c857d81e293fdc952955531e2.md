# ADR-006 — Payment Architecture

# ADR Metadata

- **ADR ID:** ADR-006
- **Status:** Accepted
- **Date:** 2026-09-20
- **Decision Owner:** KHOJ BHET Project Team
- **Area:** Payments
- **Related ADRs:** ADR-005, ADR-007
- **Implementation Status:** Not started

# 1. Context

KHOJ BHET may eventually process payments for subscriptions, featured listings, promotional services, managed rental workflows, marketplace orders, and other paid services.

Payment processing introduces financial, security, reconciliation, refund, dispute, and regulatory requirements.

# 2. Decision Drivers

- Nepal payment ecosystem
- Provider coverage
- User experience
- API quality
- Security
- Webhooks
- Reliability
- Reconciliation
- Refunds
- Failed payments
- Fees
- Regulatory requirements
- Operational support
- Future expansion

# 3. Alternatives

Potential approaches include direct integration with one provider, multiple providers behind an abstraction, an external checkout platform, or manual/off-platform payment for early non-transactional features.

# 4. Decision

**Accepted decision:** KHOJ BHET will use a provider-agnostic payment abstraction supporting multiple gateway adapters plus **manual/admin-approved payment as the initial product path**. No online payment gateway is required for the initial implementation. Business logic must not be coupled directly to one provider.

Payment persistence will use a **provider-neutral relational core plus structured metadata**. Common fields include provider, provider reference, transaction reference, payment method, amount, currency, status, idempotency key, failure code/message, and timestamps. Provider-specific payloads and additional fields belong in structured metadata rather than provider-specific core columns.

# 5. Required Payment Concepts

The eventual architecture should distinguish payment intent, payment attempt, transaction, provider reference, success, failure, pending, cancellation, refund, reconciliation, webhook/event, and invoice/receipt where applicable.

A client-side success response must not be treated as authoritative financial confirmation.

# 6. Security and Reliability

Address provider authentication, secret management, webhook verification, idempotency, duplicate callbacks, transaction state transitions, refunds, reconciliation, audit logs, and failure recovery.

# 7. Acceptance Criteria

Evaluate applicable Nepal providers, fees, settlement, API/webhook behavior, refund support, regulatory requirements, transaction states, and accounting/reconciliation needs when payment scope is activated.

# 8. Related Documentation

- 
    1. Product & Business Rules
- 
    1. API Specification
- 
    1. Security Architecture
- 
    1. Infrastructure & Deployment
- ADR-005 — File Storage Strategy

# 9. Status History

- 2026-09-20 — Created as Decision Pending.
- 2026-09-28 — Accepted; payment abstraction with multiple gateway adapters and manual/admin-approved payment selected as the architecture baseline.