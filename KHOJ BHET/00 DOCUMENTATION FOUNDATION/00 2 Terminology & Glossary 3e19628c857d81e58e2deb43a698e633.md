# 00.2 Terminology & Glossary

**Project:** KHOJ BHET  

**Document:** Terminology & Glossary  

**Document ID:** KB-DOC-002  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-20  

**Parent:** 00. DOCUMENTATION FOUNDATION  

**Related:** 00. Project Documentation Guide, 00.1 Documentation & SDLC Framework  

**Next:** 00.3 Decision / ADR Register

---

> This glossary is the authoritative reference for important KHOJ BHET product, marketplace, software-engineering, architecture, and documentation terminology. Terms should be used consistently across requirements, design, code, APIs, database models, and team communication.
> 

## 1. Purpose

The glossary exists to:

- Establish a shared vocabulary for the project.
- Prevent the same concept from being described using conflicting terms.
- Help new team members understand KHOJ BHET documentation.
- Provide precise definitions before requirements and architecture are finalized.
- Define KHOJ BHET-specific meanings where common industry terms may be ambiguous.

### Glossary rule

When a KHOJ BHET document introduces an important term that already exists here, it should use the glossary definition unless a more specific domain definition is explicitly documented.

---

## 2. Product & Marketplace Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **KHOJ BHET** | The Nepal-focused marketplace product being developed by the project. | The overall product and platform. |
| **Marketplace** | A platform connecting people or organizations that offer something with people seeking it. | KHOJ BHET connects buyers, sellers, landlords, tenants, employers, workers, and service providers. |
| **User** | A person or organization that interacts with KHOJ BHET. | A user may have multiple marketplace roles. |
| **Buyer** | A user seeking to purchase something. | Can browse and contact sellers. |
| **Seller** | A user or organization offering something for sale. | Seller is a marketplace role, not necessarily the legal owner. |
| **Owner** | The person or organization that owns the listed asset/property. | A listing may be posted by an owner or by another authorized party. |
| **Landlord** | A person or organization offering property for rent. | Used primarily for rental property. |
| **Tenant** | A person seeking or occupying a rental property. | May be a renter or prospective renter. |
| **Agent** | A person acting on behalf of another party. | May publish listings for owners or businesses. |
| **Dealer** | A business or person regularly selling a category of goods or vehicles. | Useful for vehicle and commercial sellers. |
| **Broker** | An intermediary connecting parties for a transaction or service. | Must not be assumed to be the owner. |
| **Business** | An organization or commercial entity operating on the marketplace. | May have a business profile and multiple listings. |
| **Listing** | A marketplace record representing an item, property, service, job, or other offering/wanted request. | Core universal marketplace entity. |
| **Listing Owner** | The user account that owns/manages the listing record in KHOJ BHET. | May differ from the real-world asset owner. |
| **Listing Type** | The commercial or marketplace action associated with a listing. | Examples: sale, rent, lease, wanted, exchange, free, service, job. |
| **Category** | A classification used to organize listings. | Property, Vehicles, Electronics, Furniture, etc. |
| **Subcategory** | A more specific classification within a category. | Room, Flat, House, Land, Bike, Car, Mobile, etc. |
| **Attribute** | A category-specific property describing a listing. | RAM, storage, bedrooms, mileage, land area, etc. |
| **Facility** | A user-facing amenity or included feature associated with a listing. | Parking, Wi-Fi, water supply, furnished, etc. |
| **Condition** | The physical or functional state of a listed item. | New, used, refurbished, or other defined states where applicable. |
| **Price** | The monetary amount associated with a listing. | Must be interpreted together with currency and listing type. |
| **Currency** | The monetary unit used for a price. | Nepalese Rupee (NPR) is expected to be the primary marketplace currency. |
| **Favorite** | A listing saved by a user for later access. | Supports personal saved listings. |
| **Saved Search** | A stored search configuration that a user can reuse or receive alerts for. | Planned marketplace feature. |
| **Contact Seller** | A controlled mechanism for a buyer or interested user to communicate with a listing's seller. | May expose phone/chat/contact methods according to product rules. |
| **Report** | A user-submitted complaint about a listing or user. | Used for moderation and trust/safety. |
| **Moderation** | The process of reviewing marketplace content or behavior against platform rules. | Includes listing review, reports, rejection, and enforcement. |
| **Verification** | A process for confirming a user, business, listing, or submitted information. | May include phone, identity, business, or listing verification. |
| **Featured Listing** | A listing given additional visibility through a marketplace feature. | Planned monetization/visibility capability. |
| **Subscription** | A time-bound commercial entitlement associated with a user or business account. | May unlock marketplace features. |
| **Entitlement** | A specific capability granted to a user by plan, subscription, role, or other rule. | Used instead of hardcoding every feature to a single paid/free state. |
| **Managed Rental** | A future model where KHOJ BHET may participate more directly in rental operations. | Outside the initial marketplace scope. |

---

## 3. Property & Location Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Property** | Real estate such as land, a room, flat, house, building, or apartment. | A major marketplace category. |
| **Room** | An individual room offered for rent or another supported transaction. | Property subcategory. |
| **Flat / Apartment** | A residential unit within a building or complex. | Property subcategory. |
| **House** | A standalone or otherwise separately offered residential building/property. | Property subcategory. |
| **Land** | A parcel of real property offered through the marketplace. | Property subcategory. |
| **Address** | A structured or human-readable description identifying a location. | Built from geographic hierarchy plus optional locality/landmark information. |
| **Country** | The highest geographic level in the marketplace location hierarchy. | Nepal is the primary launch country. |
| **Province** | Administrative division below country level. | Nepal's provincial administrative level. |
| **District** | Administrative division below province level. | Used for location filtering and organization. |
| **Municipality** | Local government administrative area, including applicable urban and rural municipalities. | Important marketplace search/location level. |
| **Ward** | Administrative division within a municipality. | Important for Nepal addresses and filtering. |
| **Locality** | A local settlement, neighborhood, Tole, village, or commonly recognized area. | More precise local address information. |
| **Tole** | A locally recognized neighborhood or small settlement area. | May be represented as a locality or related local place. |
| **Chowk** | A locally recognized junction, square, intersection, or named area. | Optional location reference because multiple Chowks can exist within one ward. |
| **Landmark** | A recognizable local place used to describe or locate an area. | Can include Chowk, market, temple, school, hospital, bus park, bridge, etc. |
| **Postal Code** | A postal addressing code associated with a geographic service area. | Stored separately from the full address hierarchy; it does not by itself uniquely identify a property. |
| **Latitude** | Geographic north/south coordinate. | Used for mapping, proximity search, and location services. |
| **Longitude** | Geographic east/west coordinate. | Used with latitude for geographic positioning. |
| **Approximate Location** | A location representation intentionally less precise than the exact property position. | Used for privacy and public listing display. |
| **Exact Location** | A sufficiently precise geographic location that can identify the actual property or premises. | Access should be controlled and should not automatically be exposed merely because a user has a paid subscription. |
| **Location Hierarchy** | The structured geographic levels used to represent a place. | Country → Province → District → Municipality → Ward → Locality → optional Landmark/Chowk. |

---

## 4. User & Access Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Role** | A defined set of responsibilities or capabilities associated with a user. | A user may perform different marketplace roles. |
| **Permission** | An authorization to perform a particular action. | Example: publish a listing, moderate a report, manage a business profile. |
| **Authentication** | Establishing that a user is who they claim to be. | Login/identity verification mechanism. |
| **Authorization** | Determining what an authenticated user is allowed to do. | Controls access to protected actions and resources. |
| **Session** | A period during which an authenticated client is recognized by the system. | Web/mobile authentication context. |
| **Identity Verification** | Verification of a person's identity using an approved verification process. | A future trust feature; exact provider/process remains a project decision. |
| **Business Profile** | A profile representing a business rather than only an individual marketplace account. | Planned feature for dealers, agencies, and other businesses. |
| **Public Data** | Information intentionally available to users without special authorization. | Example: broad listing location and public listing details. |
| **Restricted Data** | Information available only under defined authorization or product rules. | Example: protected contact or exact-location information. |
| **Privacy Rule** | A rule controlling collection, storage, processing, or disclosure of personal information. | Important for addresses, contact details, identity information, and user data. |

---

## 5. Listing Lifecycle Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Draft** | A listing being prepared and not yet publicly published. | Initial listing state. |
| **Pending** | A listing awaiting an action such as moderation or approval. | May be used when review is required. |
| **Published** | A listing currently available to the intended marketplace audience. | Public active state, subject to visibility rules. |
| **Paused** | A listing temporarily hidden or made inactive by its owner or authorized system process. | Used when the seller does not want the listing actively promoted. |
| **Sold** | A listing whose offered item has been sold. | Terminal commercial state unless relisted. |
| **Rented** | A rental listing whose available property has been rented. | Rental completion state. |
| **Expired** | A listing that is no longer active because its validity period ended. | Can potentially be renewed according to product rules. |
| **Rejected** | A listing rejected by moderation or another defined rule. | Not publicly publishable until corrected/reviewed. |
| **Deleted** | A listing removed from normal marketplace use. | Deletion policy and retention rules will be defined later. |

---

## 6. Software & Engineering Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Software** | The programs, configuration, data structures, and supporting components that implement the product. | The complete technical implementation. |
| **Application** | A software system that provides functionality to users or other systems. | KHOJ BHET web/mobile applications and backend systems. |
| **Frontend** | The client-facing software through which users interact with the product. | Web or mobile user interface. |
| **Backend** | Server-side software responsible for business logic, APIs, authentication, data access, and related services. | Primary application server. |
| **API** | A defined interface through which software components communicate. | Backend API consumed by web/mobile clients and integrations. |
| **REST API** | An HTTP-based API style using resources, methods, representations, and standard web semantics. | Candidate/expected API style for KHOJ BHET. |
| **Endpoint** | A specific API route through which a client can perform an operation. | Example: listing creation endpoint. |
| **Request** | Data sent to an API or application operation. | HTTP request from a client. |
| **Response** | Data returned by an API or operation. | API response containing status/data/errors. |
| **Database** | Persistent structured storage for application data. | MySQL is the planned primary database technology, subject to formal technical decisions. |
| **Database Schema** | The structural definition of database tables, columns, relationships, constraints, and related objects. | Defines persistent KHOJ BHET data. |
| **Migration** | A version-controlled change to the database schema. | Used to evolve database structure safely. |
| **ORM** | Object-Relational Mapping layer for interacting with relational data through application models. | Laravel Eloquent is the planned ORM. |
| **Model** | An application representation of a domain/data entity. | Example: Listing model. |
| **Controller** | Application component responsible for handling an incoming request and coordinating the relevant operation. | Backend request handling. |
| **Service** | Application component encapsulating reusable business/application logic. | Used where logic should not be concentrated in controllers. |
| **Module** | A logically bounded area of application functionality. | Marketplace domains can be organized as modules inside the backend. |
| **Modular Monolith** | A single deployable application organized into clearly separated internal modules. | Initial backend architecture direction, subject to formal architecture approval. |
| **Microservice** | An independently deployable service focused on a bounded capability. | Possible future architecture if justified by project needs. |
| **Dependency** | A relationship where one component, document, or decision relies on another. | Requirements depend on product scope; implementation depends on approved design. |
| **Integration** | A connection between KHOJ BHET and another software/system/service. | Example: SMS, payment, maps, notification, or identity provider. |
| **Third-party Service** | An externally operated service used by KHOJ BHET. | Any external provider used for infrastructure or product functionality. |
| **Repository** | A version-controlled project storage location containing source and related files. | Git repository for KHOJ BHET code. |
| **Branch** | An independent line of development in a version-control repository. | Used for feature, fix, release, or other development work. |
| **Pull Request (PR)** | A proposed set of repository changes submitted for review and integration. | Used for collaborative code review. |
| **Code Review** | Examination of proposed code changes before integration. | Quality and maintainability control. |
| **Refactoring** | Changing internal code structure without intentionally changing externally observed behavior. | Routine engineering activity. |

---

## 7. Architecture Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Architecture** | The significant structure and relationships of a software system and the principles guiding its evolution. | Defines how KHOJ BHET components are organized. |
| **System Architecture** | High-level structure of the complete system, including major applications and infrastructure. | Covers web, mobile, backend, database, storage, search, and integrations. |
| **Application Architecture** | Internal organization of a particular application. | Covers frontend/backend/mobile structure. |
| **Domain** | A distinct business area with its own concepts and rules. | Examples may include Listings, Users, Messaging, Moderation, and Subscriptions. |
| **Bounded Context** | A boundary within which a domain model and terminology have a specific consistent meaning. | May be used if domain complexity justifies formal boundaries. |
| **Layer** | A logical separation of responsibilities within an application. | Example: presentation, application, domain, infrastructure. |
| **Component** | A distinct software unit with a defined responsibility and interface. | May exist within modules or applications. |
| **Scalability** | The ability of a system to handle increased workload while maintaining acceptable behavior. | Considered in architecture and infrastructure decisions. |
| **Maintainability** | The ease with which a system can be understood, changed, tested, and operated. | Core long-term engineering concern. |
| **Availability** | The degree to which a system is operational and accessible when needed. | Infrastructure and reliability concern. |
| **Reliability** | The ability of a system to perform required functions consistently under stated conditions. | Quality and operations concern. |
| **Technical Debt** | Future cost created by expedient technical choices that make later change or maintenance harder. | Should be identified and managed rather than hidden. |

---

## 8. Product Development & SDLC Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **SDLC** | Software Development Life Cycle: the overall lifecycle through which software is conceived, defined, designed, built, tested, deployed, operated, and evolved. | Project-level lifecycle framework. |
| **Agile** | An iterative development approach emphasizing incremental delivery, feedback, and adaptation. | Development approach within the SDLC. |
| **Iteration** | A repeated development cycle producing a defined increment of work. | Used for incremental product delivery. |
| **Sprint** | A fixed-length Agile development iteration. | Length will be decided by the development process. |
| **Backlog** | An ordered collection of work items, ideas, requirements, bugs, or improvements. | Product and engineering work management. |
| **Epic** | A large body of work that can be divided into smaller deliverable items. | Useful for major marketplace capabilities. |
| **Feature** | A user-visible or system capability that provides defined value. | Example: listing creation or saved searches. |
| **User Story** | A concise statement of a user's need or desired capability from the user's perspective. | Used to express product needs. |
| **Use Case** | A structured description of interactions between an actor and the system to achieve a goal. | Example: Create Listing. |
| **Acceptance Criteria** | Conditions that must be satisfied for a requirement or work item to be considered acceptable. | Used to verify behavior. |
| **User Flow** | The sequence of actions, decisions, and screens through which a user completes a goal. | Example: Login → Create Listing → Preview → Publish. |
| **UX** | User Experience: the overall experience of using the product. | Covers usability, clarity, interaction, and journey. |
| **UI** | User Interface: the visual and interactive interface presented to the user. | Screens, components, controls, and layouts. |
| **Requirement** | A documented capability, constraint, quality, or condition the system must satisfy. | Defines what the system must provide. |
| **Functional Requirement** | A requirement describing a specific behavior or capability. | Example: user can create a listing. |
| **Non-functional Requirement** | A requirement describing quality attributes or constraints rather than a specific feature. | Performance, security, availability, accessibility, etc. |
| **Business Rule** | A rule governing how the marketplace or product must behave. | Example: required information must exist before publication. |
| **Scope** | The defined boundaries of what is included and excluded from a release or project. | Prevents uncontrolled feature expansion. |
| **MVP** | Minimum Viable Product: the smallest product version that can test the core value proposition with real users. | A product-development concept, not automatically the entire V1. |
| **Release** | A version of the software made available to a defined audience. | May be development, staging, beta, or production. |
| **Production** | The live environment serving real users. | Public KHOJ BHET environment. |

---

## 9. Testing & Quality Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **QA** | Quality Assurance: activities used to establish and improve confidence in product quality. | Includes testing and quality processes. |
| **Test Case** | A defined set of inputs, conditions, and expected results used to verify behavior. | Used for systematic verification. |
| **Unit Test** | Test of a small isolated unit of code. | Used for business/application logic where appropriate. |
| **Integration Test** | Test verifying interaction between multiple components. | Example: API + database behavior. |
| **End-to-End Test** | Test covering a complete user or system workflow. | Example: create listing through publication. |
| **Regression Test** | Test intended to detect unintended breakage caused by changes. | Required as the product evolves. |
| **Bug / Defect** | A deviation between actual behavior and expected/approved behavior. | Tracked and resolved through engineering workflow. |
| **Acceptance Test** | Verification that a feature satisfies its acceptance criteria. | Confirms requirements from a user/business perspective. |

---

## 10. DevOps & Operations Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **DevOps** | Practices combining development, deployment, infrastructure, and operations responsibilities and automation. | Covers delivery and operational lifecycle. |
| **CI** | Continuous Integration: automatically integrating and validating code changes. | Build/test automation. |
| **CD** | Continuous Delivery or Continuous Deployment, depending on project definition, for automated software delivery. | Deployment automation. |
| **CI/CD Pipeline** | Automated sequence used to build, test, validate, and potentially deploy software. | Engineering delivery mechanism. |
| **Environment** | A distinct runtime context with its own configuration and purpose. | Development, staging, production, etc. |
| **Development Environment** | Environment used by developers to build and test changes. | Local or shared development setup. |
| **Staging** | Pre-production environment used for release validation. | Should resemble production where practical. |
| **Infrastructure** | Computing, networking, storage, and supporting resources required to operate the system. | Servers, databases, storage, networking, etc. |
| **Deployment** | Process of making a software version available in an environment. | Includes release and configuration steps. |
| **Monitoring** | Continuous observation of system health, performance, and behavior. | Detects operational problems. |
| **Logging** | Recording structured application/system events for debugging, auditing, and operations. | Supports troubleshooting and observability. |
| **Backup** | A retained copy of data or configuration used for recovery. | Required for important production data. |
| **Recovery** | Process of restoring service or data after failure or loss. | Covered by operational procedures. |
| **Incident** | An event that causes or risks service degradation, outage, security impact, or other operational harm. | Managed through incident procedures. |
| **Rollback** | Reverting a deployment or change to a previous known-good state. | Used when a release causes unacceptable problems. |

---

## 11. Security Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Security** | Protection of systems, data, users, and operations against unauthorized or harmful activity. | Cross-cutting engineering concern. |
| **Authentication** | Verifying identity. | Login/identity process. |
| **Authorization** | Verifying permission to perform an action or access a resource. | Role/permission enforcement. |
| **Access Control** | Mechanisms controlling who can access which resources and perform which operations. | Applies to users, admins, listings, contact data, and restricted information. |
| **Least Privilege** | Giving an actor only the access required to perform its legitimate function. | Security principle for users, services, and administrators. |
| **Personal Data** | Information that can identify or relate to an individual. | Includes applicable account/contact information and other protected data. |
| **Sensitive Data** | Data requiring stronger protection because unauthorized disclosure or alteration could cause significant harm or risk. | Exact classification will be defined in security/privacy documentation. |
| **Secret** | Confidential credential or value used to authenticate or authorize systems. | Passwords, API keys, tokens, private keys, etc.; never stored in documentation. |
| **Encryption** | Transformation of data so it can only be read or used by authorized parties with the required cryptographic mechanism. | Used where required by security architecture. |
| **Rate Limiting** | Restricting how frequently an actor can perform an operation. | Used to reduce abuse and protect services. |
| **Abuse Prevention** | Controls intended to reduce fraud, spam, scraping, harassment, or other misuse. | Important marketplace trust/safety area. |

---

## 12. Documentation Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Documentation** | Structured information explaining the product, system, decisions, processes, or operations. | Maintained primarily in the project knowledge base. |
| **Authoritative Document** | The document that is the current source of truth for a particular subject. | Other documents should defer to it. |
| **Single Source of Truth** | Principle that a subject should have one authoritative definition/location. | Prevents conflicting copies of important information. |
| **Document Lifecycle** | The progression of documentation through statuses such as Draft, Review, Approved, Active, and Archived. | Defined in the Documentation & SDLC Framework. |
| **Draft** | Documentation that is being prepared and is not authoritative. | Initial writing state. |
| **Review** | Documentation ready for evaluation and feedback. | Pre-approval state. |
| **Approved** | Documentation accepted as a project decision. | Accepted state before or when made active. |
| **Active** | Current authoritative documentation. | Current source of truth. |
| **Superseded** | Replaced by a newer document or decision. | Historical but no longer current. |
| **Deprecated** | No longer recommended for current use. | Retained where historical context matters. |
| **Archived** | Retained primarily for historical reference. | Not current guidance. |
| **Traceability** | Ability to connect a requirement or decision to related design, implementation, and verification artifacts. | Used for important features and changes. |
| **Document Owner** | Person/team responsible for maintaining a document's accuracy. | Assigned to important documents. |
| **Revision** | A recorded change to an existing document. | Used for document history/versioning. |
| **ADR** | Architecture Decision Record: a document recording an important architectural decision and its rationale. | Used for significant technical/architectural choices. |
| **Decision Pending** | A documented choice that has not yet been formally decided. | Prevents proposals from becoming accidental requirements. |

---

## 13. Data & Search Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Entity** | A distinct business or data object with an identity. | Examples: User, Listing, Category, Subscription. |
| **Record** | A stored representation of an entity or event in a data store. | Database row representing application data. |
| **Field / Attribute** | A named piece of data describing an entity or record. | Listing title, price, condition, etc. |
| **Relationship** | A defined association between entities. | User owns listings; listing belongs to category. |
| **Relational Database** | Database organized around structured tables and relationships. | MySQL. |
| **Index** | Data structure used to improve lookup/query performance. | Database indexes for common marketplace queries. |
| **Query** | A request to retrieve or manipulate data. | Search/filter database operation. |
| **Search** | Process of finding listings or other records matching user criteria. | Core marketplace capability. |
| **Filter** | A constraint applied to reduce search results. | Price, location, category, condition, attributes. |
| **Sort** | Ordering search or listing results according to a selected criterion. | Price, date, relevance, etc. |
| **Pagination** | Dividing a large result set into smaller pages/chunks. | Used for listing/search results. |
| **Full-Text Search** | Search mechanism that matches terms within textual content. | May be used for listing titles/descriptions. |
| **Geospatial Search** | Search based on geographic coordinates or distance. | Useful for nearby listings and map-based discovery. |
| **Search Engine** | Specialized system for indexing and retrieving searchable data. | A dedicated search engine may be introduced as scale requires. |

---

## 14. Web, Mobile & API Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Web Application** | Browser-accessible software application. | KHOJ BHET web marketplace. |
| **Mobile Application** | Application designed for mobile operating systems. | Android/iOS client planned for a later implementation stage. |
| **Responsive Design** | Interface design that adapts to different screen sizes and devices. | Required for the web experience. |
| **SSR** | Server-Side Rendering: generating web content on the server before delivering it to the browser. | Relevant to marketplace SEO and initial page rendering. |
| **Client** | Software that requests or consumes services from another system. | Web/mobile application consuming the backend API. |
| **HTTP** | Protocol used for web communication. | API and web traffic. |
| **JSON** | Common structured data interchange format. | Expected API payload format where applicable. |
| **HTTP Method** | Standard operation type such as GET, POST, PUT, PATCH, or DELETE. | Used by REST-style API endpoints. |
| **Status Code** | HTTP response code describing request outcome. | Example: 200 success, 400 client error, 401 unauthenticated, 404 not found, 500 server error. |

---

## 15. Monetization Terms

| Term | Definition | KHOJ BHET usage |
| --- | --- | --- |
| **Free Tier** | Product access available without payment, subject to defined limits. | Supports marketplace liquidity and user acquisition. |
| **Paid Plan** | Commercial plan providing defined additional capabilities or limits. | Potential seller/business/buyer monetization. |
| **Subscription Plan** | A predefined collection of subscription features and limits. | Example: listing limits, visibility, analytics, or business capabilities. |
| **Feature Entitlement** | A specific capability granted by a plan or other rule. | More flexible than checking only whether a user is "paid". |
| **Listing Limit** | Maximum number of listings a user can maintain or publish under a defined rule. | Potential subscription feature. |
| **Featured Placement** | Additional marketplace visibility provided under a defined rule or paid feature. | Future monetization mechanism. |

---

## 16. Project-Specific Terminology Rules

The following rules apply throughout KHOJ BHET:

### 16.1 Listing vs Product

**Listing** means the marketplace record.

**Product/Item** means the underlying thing being offered, where applicable.

Example:

> A user creates a **listing** for a **mobile phone**.
> 

The listing is not automatically the same conceptual object as the physical mobile phone.

### 16.2 User vs Seller

A **user** is the account/person interacting with the platform.

A **seller** is the marketplace role of offering something.

One user can be:

- Buyer in one interaction.
- Seller in another.
- Landlord for a property.
- Tenant for another property.
- Employer for a job.
- Worker/service provider in another context.

### 16.3 Seller vs Owner

Do not use these terms interchangeably.

A seller may be:

- Owner.
- Agent.
- Dealer.
- Broker.
- Tenant.
- Business.
- Other authorized party.

### 16.4 Address vs Location

**Address** is the structured/human-readable place description.

**Location** is the broader concept that may include administrative hierarchy, coordinates, landmarks, approximate positioning, and privacy-controlled exact positioning.

### 16.5 Category vs Attribute

**Category** determines what kind of listing something is.

**Attribute** describes characteristics of that listing.

Example:

> Category = Mobile
> 

> Attribute = RAM: 8 GB
> 

### 16.6 Facility vs Attribute

A **facility** is generally a user-facing amenity or included feature.

An **attribute** is a broader category-specific characteristic.

The final data-model rules will define when a property belongs to attributes versus facilities.

---

## 17. Terms That Must Not Be Used as Unresolved Synonyms

The following pairs should remain conceptually distinct:

| Do not casually merge | Distinction |
| --- | --- |
| User / Seller | Account/person vs marketplace role |
| Seller / Owner | Marketplace offerer vs underlying owner |
| Listing / Item | Marketplace record vs underlying thing |
| Category / Attribute | Classification vs characteristic |
| Address / Location | Human/structured address vs broader geographic concept |
| Authentication / Authorization | Identity verification vs permission checking |
| Requirement / Task | What the system must satisfy vs work required to implement it |
| Use Case / User Flow | Goal-oriented interaction specification vs sequence of user/system steps |
| UX / UI | Overall experience vs interface |
| Architecture / Technology Stack | System structure/principles vs selected technologies |
| Database / ORM | Persistent data store vs application abstraction for accessing it |
| SDLC / Agile | Overall software lifecycle vs iterative development approach |
| Documentation / Task | Knowledge about the system vs work to be performed |
| ADR / Requirement | Architectural decision record vs system/product need |
| Verification / Moderation | Confirmation of defined information/identity vs review/enforcement process |

---

## 18. Naming Consistency Rules

The project should:

1. Prefer one canonical English term in technical documentation.
2. Use local/Nepali terminology where it improves user-facing clarity.
3. Define domain-specific terms before using them in requirements or schema design.
4. Avoid creating multiple names for the same concept without a documented reason.
5. Preserve a term's meaning across product, API, database, and UI unless a translation/localization layer intentionally changes the presentation.
6. Record new important terminology in this glossary when it becomes part of the project's shared vocabulary.

---

## 19. Glossary Governance

This glossary is itself an authoritative document.

When introducing a new important domain term:

1. Check whether an existing term already covers the concept.
2. Reuse the existing term if appropriate.
3. If a new term is necessary, define it clearly.
4. Check related requirements and documents for conflicting terminology.
5. Update dependent documentation if the terminology change affects meaning.
6. Consider an ADR when terminology is tied to a significant architectural or domain-model decision.

The glossary should evolve with the product, but changes should preserve conceptual consistency.

---

## Document Control

**Document ID:** KB-DOC-002  

**Document:** Terminology & Glossary  

**Status:** Active  

**Version:** 1.0  

**Owner:** KHOJ BHET Project Team  

**Last Reviewed:** 2026-09-20  

**Parent:** 00. DOCUMENTATION FOUNDATION  

**Related:** 00. Project Documentation Guide, 00.1 Documentation & SDLC Framework  

**Next:** 00.3 Decision / ADR Register