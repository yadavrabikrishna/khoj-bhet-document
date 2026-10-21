# 00.1 Documentation & SDLC Framework

**Project:** KHOJ BHET  

**Document:** Documentation & SDLC Framework  

**Document ID:** KB-DOC-001  

**Status:** Active  

**Version:** 1.1  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-10-15

---

# KHOJ BHET — Documentation & SDLC Framework

> This document defines the governance framework for how KHOJ BHET is documented and how the software progresses through its lifecycle. It explains the relationship between product, requirements, design, architecture, implementation, testing, deployment, and operations.
> 

> **This is a framework document. It does not define the actual product requirements or technical implementation. Those are maintained in their respective authoritative documents.**
> 

## 1. Purpose

KHOJ BHET is intended to be a long-term software product. The project therefore needs a repeatable framework for:

- Planning and developing the product.
- Maintaining product and technical knowledge.
- Making and recording important decisions.
- Controlling changes.
- Maintaining traceability from requirements to implementation and testing.
- Onboarding new team members.
- Keeping documentation and implementation aligned.

This framework establishes the rules used across the project lifecycle.

---

## 2. Scope

This framework applies to:

- Product documentation.
- Requirements documentation.
- UX/UI documentation.
- Business rules.
- Software architecture.
- Technology decisions.
- Database and API documentation.
- Frontend, backend, and mobile architecture.
- Security and authentication documentation.
- Testing and QA.
- DevOps and infrastructure.
- Operations and administration.
- Developer onboarding.
- Architecture Decision Records (ADRs).
- Significant project changes.

It does not replace the content of those documents.

---

## 3. Core Documentation Principles

### 3.1 Single Source of Truth

Each subject has one authoritative document.

Examples:

| Subject | Authoritative document |
| --- | --- |
| Product purpose | Product Vision & Mission |
| Product scope | Product Scope & Roadmap |
| Requirements | Requirements Specification |
| Users and access | Users, Roles & Permissions |
| User interaction | User Stories, Use Cases & User Flows |
| Product rules | Product & Business Rules |
| Architecture | Software Architecture |
| Technology choices | Technology Stack |
| Database | Database Architecture |
| API contract | API Specification |
| Security | Security Architecture |
| Testing | Testing & QA |
| Deployment | Infrastructure & Deployment |
| Development process | Development Methodology |
| Team coding rules | Engineering Standards |
| Architectural decisions | ADRs |

Related documents may reference one another, but important definitions should not be independently duplicated.

---

### 3.2 Document the Decision at the Correct Level

A product requirement should not contain an unnecessary implementation decision.

Example:

> Users must be able to search listings by location.
> 

This is a product/system requirement.

The choice between MySQL search, Typesense, Elasticsearch, or another solution belongs in technical documentation and, where significant, an ADR.

---

### 3.3 Do Not Turn Assumptions into Decisions

Unresolved choices must be explicitly marked. Document status, decision status, and implementation status are distinct dimensions; one must never be used as a proxy for another.

Allowed states include:

- Proposed
- Decision Pending
- Approved
- Active
- Superseded
- Deprecated
- Archived

Example:

> Mobile framework: **Decision Pending**
> 

This is different from:

> Mobile framework: **Flutter**
> 

until the project formally approves that choice.

---

### 3.4 Documentation Must Be Traceable

Important product capabilities should be traceable through the lifecycle:

```
Requirement
    ↓
User Story / Use Case
    ↓
User Flow / UX/UI
    ↓
Business Rule
    ↓
Architecture
    ↓
Implementation
    ↓
Test
    ↓
Release
```

The exact traceability mechanism may evolve, but the relationship must remain understandable.

---

## 4. SDLC Framework

KHOJ BHET follows a broad Software Development Life Cycle (SDLC).

The lifecycle is:

```
1. Initiation
      ↓
2. Product Definition
      ↓
3. Requirements
      ↓
4. Design
      ↓
5. Architecture
      ↓
6. Development
      ↓
7. Testing & QA
      ↓
8. Deployment
      ↓
9. Operations
      ↓
10. Maintenance & Evolution
```

These stages describe the overall lifecycle. They do not mean the entire project must be completed in one large sequential pass.

The project will use iterative development within this lifecycle.

---

## 5. Agile Development Framework

Agile is the development approach used to deliver and improve the product iteratively.

A typical iteration is:

```
Backlog
   ↓
Planning
   ↓
Development
   ↓
Testing
   ↓
Review
   ↓
Release
   ↓
Feedback
   ↓
Backlog Refinement
   ↓
Next Iteration
```

Agile does not replace:

- Requirements.
- Architecture.
- Documentation.
- Testing.
- Security.
- Deployment.
- Operations.

Instead, Agile provides the iterative working method inside the broader SDLC.

---

## 6. SDLC vs Agile

These concepts must remain distinct.

### SDLC answers:

> What is the overall lifecycle of the software?
> 

### Agile answers:

> How does the team repeatedly build, test, release, and improve the product?
> 

Therefore:

```
SDLC = overall lifecycle
Agile = iterative development approach
```

A sprint is an iteration within the Agile development process. Sprint length is a project-management decision and is not fixed by this framework.

---

## 7. Documentation Lifecycle

Major documentation follows:

```jsx
Proposed
  ↓
Draft
  ↓
Under Review
  ↓
Approved
  ↓
Active
  ↓
Superseded / Deprecated / Archived
```

### Draft

The document is being prepared and is not authoritative.

### Under Review

The document is ready for review and feedback.

### Approved

The proposed content has been accepted.

### Active

The document represents the current source of truth.

### Superseded

The document has been replaced by a newer decision or document.

### Deprecated

The document or information is no longer recommended for current use.

### Archived

The information is retained for historical reference.

---

## 8. Document Ownership

Important documents should have:

- Owner.
- Status.
- Version/revision.
- Last reviewed date.
- Related documents.
- Related ADRs where applicable.

The document owner is responsible for keeping the document accurate when the underlying product, technical, or operational decision changes.

Ownership does not require the owner to personally make every edit.

---

## 9. Documentation Review

A document should be reviewed when:

- A related requirement changes.
- A business rule changes.
- A user flow changes significantly.
- An architecture decision changes.
- A technology is replaced.
- A database or API contract changes.
- A security mechanism changes.
- A deployment process changes.
- A significant operational process changes.

Periodic review may also be used for important active documents.

During review, check:

1. Is the information still correct?
2. Is it consistent with authoritative documents?
3. Does it match the current implementation?
4. Are referenced documents still valid?
5. Are any decisions unresolved?
6. Is obsolete information clearly marked?

---

## 10. Change Management

A significant change should follow this general process:

```
Change Proposed
      ↓
Impact Analysis
      ↓
Identify Affected Documents
      ↓
Determine Decision / Approval Requirement
      ↓
Update ADR if Required
      ↓
Update Authoritative Documentation
      ↓
Update Dependent Documentation
      ↓
Implement
      ↓
Test
      ↓
Release
```

### Important rule

Documentation and implementation must not intentionally remain contradictory.

If the implementation differs from the approved documentation, the difference must be classified as one of:

- Implementation defect.
- Documentation defect.
- Deliberate approved change.
- Temporary implementation state.

---

## 11. Change Classification

Changes should be classified according to their impact.

### Product change

Changes what the product does.

Example:

> Adding saved searches.
> 

### Requirement change

Changes a system requirement.

Example:

> Increasing the maximum number of listing photos.
> 

### Business-rule change

Changes how the marketplace operates.

Example:

> Changing listing expiration rules.
> 

### Architecture change

Changes the structure or major technical direction of the system.

Example:

> Moving from a modular monolith toward independently deployable services.
> 

### Technology change

Changes a selected technology.

Example:

> Replacing one search engine with another.
> 

### Implementation change

Changes code without changing approved product behavior or architecture.

Example:

> Refactoring a controller for maintainability.
> 

Not every implementation change requires documentation changes.

---

## 12. Architecture Decision Records

Important architectural and technical decisions should be recorded as ADRs.

An ADR should normally document:

1. Decision ID.
2. Title.
3. Date.
4. Status.
5. Context.
6. Problem.
7. Options considered.
8. Decision.
9. Rationale.
10. Consequences.
11. Related documents.
12. Superseded/superseding decisions where applicable.

Examples of decisions that may require ADRs:

- Application architecture.
- Backend framework.
- Frontend framework.
- Mobile framework.
- Database technology.
- Search technology.
- Authentication architecture.
- File/media storage.
- Payment architecture.
- Notification infrastructure.
- Major infrastructure changes.
- Significant migration strategies.

Minor coding decisions normally do not require ADRs.

The authoritative ADR index is maintained in **00.3 Decision / ADR Register**.

---

## 13. Requirements-to-Implementation Traceability

The project should preserve traceability for important features.

Example:

```
Feature
  ↓
Requirement
  ↓
Use Case
  ↓
User Flow
  ↓
Business Rule
  ↓
API / Architecture
  ↓
Implementation
  ↓
Test Case
```

This allows the team to answer:

- Why does this feature exist?
- What requirement does it satisfy?
- Which user flow uses it?
- Which business rules apply?
- Which API supports it?
- Where is it implemented?
- How is it tested?

The exact IDs and tracking mechanism can be defined later in the relevant project-management and engineering documentation.

---

## 14. Product Documentation vs Technical Documentation

These must remain separate.

### Product documentation answers:

> What are we building, for whom, why, and what should it do?
> 

It includes:

- Product Vision & Mission.
- Product Scope & Roadmap.
- Requirements.
- Users/Roles.
- User Stories.
- Use Cases.
- User Flows.
- UX/UI.
- Business Rules.

### Technical documentation answers:

> How will the approved product be implemented and operated?
> 

It includes:

- Software Architecture.
- Technology Stack.
- Database Architecture.
- API Specification.
- Frontend Architecture.
- Backend Architecture.
- Mobile Architecture.
- Authentication.
- Security.
- Media/File Storage.
- Search.
- Notifications.
- SEO.
- DevOps.
- Infrastructure.
- Monitoring.

Product requirements should be defined before detailed technical implementation decisions wherever practical.

---

## 15. Architecture Terminology Policy

Architecture terminology must describe an intentional decision, not a trend.

For example, the project should not state:

> KHOJ BHET uses microservices because microservices are modern.
> 

Instead, an architecture decision should explain:

- Business requirements.
- Scale requirements.
- Team capability.
- Operational complexity.
- Cost.
- Maintainability.
- Reliability.
- Deployment requirements.
- Future evolution.

The initial architecture may use a modular monolith while maintaining module boundaries that could support future extraction if justified.

This is an architectural principle, not a final decision about every future service.

---

## 16. Database and API Dependency Rule

Database and API design should follow approved requirements and architecture.

The intended dependency is:

```
Product Requirements
       ↓
Business Rules
       ↓
Architecture
       ↓
Data / API Design
       ↓
Implementation
```

Therefore, the project should not begin detailed database modeling merely because database design is technically interesting.

The database must represent the approved product and architectural requirements.

---

## 17. Development Methodology and Engineering Standards

Development Methodology defines:

- How work is planned.
- How iterations are organized.
- How work moves from backlog to release.
- How feedback is incorporated.

Engineering Standards define:

- Coding standards.
- Naming conventions.
- Project structure.
- Error handling.
- Logging.
- Testing expectations.
- Code review standards.
- Security practices.
- Documentation expectations.

These are related but separate concerns.

---

## 18. Quality and Testing

Testing is part of the lifecycle, not an activity performed only at the end.

Testing should be considered from the requirement and design stages.

The general relationship is:

```
Requirement
   ↓
Acceptance Criteria
   ↓
Test Design
   ↓
Implementation
   ↓
Automated / Manual Testing
   ↓
Release Verification
```

The detailed testing strategy belongs in **Testing & QA**.

---

## 19. Security by Design

Security should be considered throughout the SDLC.

Relevant areas include:

- Authentication.
- Authorization.
- Input validation.
- Data protection.
- File uploads.
- API security.
- Abuse prevention.
- Rate limiting.
- Privacy.
- Logging.
- Secrets management.
- Administrative access.

Security requirements should not be added only after implementation.

Detailed controls belong in **Security Architecture** and related technical documents.

---

## 20. Deployment and Operations

Deployment and operations are part of the SDLC.

The project lifecycle continues after the first production release:

```
Development
   ↓
Testing
   ↓
Deployment
   ↓
Monitoring
   ↓
Maintenance
   ↓
Improvement
   ↓
Next Release
```

Operational documentation should cover:

- Deployment.
- Configuration.
- Monitoring.
- Logging.
- Backup.
- Recovery.
- Incident handling.
- Release procedures.

---

## 21. New Developer Documentation Path

The documentation system provides two levels of onboarding.

### Level 1 — Documentation navigation

A new team member starts with:

1. **00. Project Documentation Guide**
2. **00.1 Documentation & SDLC Framework**
3. **00.2 Terminology & Glossary**

Then they follow the product and technical documentation relevant to their role.

### Level 2 — Full developer onboarding

The detailed setup and working procedure belongs in:

**29. Developer Onboarding Guide**

That document will eventually cover:

- Development environment.
- Repository access.
- Local setup.
- Environment variables.
- Backend setup.
- Frontend setup.
- Mobile setup.
- Database setup.
- Running the application.
- Running tests.
- Git workflow.
- Branching.
- Pull requests.
- Code review.
- Debugging.
- Deployment workflow.
- Common issues.

The framework defines the reading principle; the onboarding guide defines the practical onboarding procedure.

---

## 22. Documentation and Source Control

Notion and Git/GitHub have different responsibilities.

### Notion

Used for:

- Product documentation.
- Requirements.
- Architecture.
- Decisions.
- Standards.
- Operational procedures.
- Onboarding.
- Knowledge management.

### Git/GitHub

Used for:

- Source code.
- Configuration files.
- Database migrations.
- Automated tests.
- Infrastructure code.
- Application assets.
- Code history.

Neither system replaces the other.

---

## 23. Documentation and Project Management

Documentation and project-management tasks are different.

### Documentation

Explains:

> What the product/system is and how it should work.
> 

### Task

Explains:

> What work must be performed.
> 

Example:

**Documentation:**

> Sellers can create property listings containing required location information.
> 

**Task:**

> Implement property listing creation endpoint.
> 

The task should implement the approved documentation rather than silently redefine it.

---

## 24. Handling Conflicting Documentation

When two documents conflict:

1. Identify the authoritative document.
2. Check each document's status.
3. Check versions/revisions.
4. Review related ADRs.
5. Determine the current approved decision.
6. Update the incorrect or outdated document.
7. Update dependent documentation.
8. Create or update an ADR if the conflict represents an architectural decision.

Conflicting documentation should not be left unresolved.

---

## 25. Documentation Status and Versioning

Each major document should maintain:

- Status.
- Version/revision.
- Owner.
- Last reviewed date.
- Change history where appropriate.

Suggested version convention:

```
1.0 = Initial approved version
1.1 = Minor clarification or additive change
1.2 = Additional non-breaking content
2.0 = Major structural or behavioral change
```

Exact versioning practices may be refined later.

Not every spelling or formatting correction requires a new major version.

---

## 26. What Requires Documentation?

### Usually requires documentation

- New product capability.
- Major requirement change.
- New business rule.
- New user role.
- Significant user-flow change.
- Architecture change.
- Technology selection.
- API contract change.
- Database design change.
- Security architecture change.
- Infrastructure change.
- Major operational procedure.

### Usually does not require a new project document

- Minor refactoring.
- Variable renaming.
- Formatting changes.
- Small bug fixes that do not change documented behavior.
- Routine code cleanup.

The relevant existing documentation should still be updated if these changes alter documented behavior.

---

## 27. What Must Never Be Stored in Project Documentation

Never store:

- Passwords.
- API keys.
- Authentication tokens.
- Private keys.
- Database credentials.
- Recovery codes.
- Production secrets.

Documentation may describe where credentials are managed, but must not contain the secret values.

---

## 28. Framework Completion Criteria

The Documentation & SDLC Framework is considered established when the project has clear rules for:

- Documentation lifecycle.
- Documentation ownership.
- Document status.
- Document dependencies.
- Product vs technical documentation.
- SDLC.
- Agile development.
- Change management.
- ADR usage.
- Traceability.
- Versioning.
- Documentation review.
- New-member documentation navigation.
- Relationship between Notion documentation and source control.

---

## 29. Relationship to Other Phase-0 Documents

This document works together with the other Phase-0 foundation documents:

| Document | Responsibility |
| --- | --- |
| **00. Project Documentation Guide** | Defines where information belongs and how to navigate the documentation system |
| **00.1 Documentation & SDLC Framework** | Defines lifecycle, governance, change, review, and documentation-management rules |
| **00.2 Terminology & Glossary** | Defines the authoritative meaning of important KHOJ BHET and technical terms |
| **00.3 Decision / ADR Register** | Indexes and tracks important architectural decisions |

Together these documents form the documentation foundation.

---

## 30. Next Phase

After the Phase-0 documentation foundation is established, KHOJ BHET moves into:

# Phase 1 — Product Definition

The next document is:

**01. Product Vision & Mission**

That document will define:

- What KHOJ BHET is.
- Why it exists.
- The problems it addresses.
- Target users.
- Product vision.
- Product mission.
- Core value proposition.
- Product principles.
- Long-term direction.

Detailed requirements, user flows, architecture, and database design will be developed from this product foundation rather than assumed in advance.

---

## Document Control

**Document ID:** KB-DOC-001  

**Document:** Documentation & SDLC Framework  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-20  

**Parent:** 00. Project Documentation Guide  

**Related:** 00.2 Terminology & Glossary, 00.3 Decision / ADR Register  

**Next:** 00.2 Terminology & Glossary

## Revision History

- **v1.1 — 2026-10-15:** Clarified that document status, ADR decision status, and implementation status are separate dimensions; added explicit governance rule to prevent status conflation.