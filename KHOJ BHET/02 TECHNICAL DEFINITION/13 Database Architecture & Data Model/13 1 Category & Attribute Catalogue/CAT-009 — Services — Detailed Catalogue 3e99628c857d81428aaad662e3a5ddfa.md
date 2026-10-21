# CAT-009 — Services — Detailed Catalogue

**Catalogue ID:** CAT-009

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-009-01 | Home &amp; Domestic Services | Primary catalogue scope for this subcategory. |
| CAT-009-02 | Repair &amp; Maintenance | Primary catalogue scope for this subcategory. |
| CAT-009-03 | Construction &amp; Renovation Services | Primary catalogue scope for this subcategory. |
| CAT-009-04 | Automotive Services | Primary catalogue scope for this subcategory. |
| CAT-009-05 | IT &amp; Digital Services | Primary catalogue scope for this subcategory. |
| CAT-009-06 | Business &amp; Professional Services | Primary catalogue scope for this subcategory. |
| CAT-009-07 | Education &amp; Training | Primary catalogue scope for this subcategory. |
| CAT-009-08 | Health &amp; Wellness Services | Primary catalogue scope for this subcategory. |
| CAT-009-09 | Beauty &amp; Personal Care | Primary catalogue scope for this subcategory. |
| CAT-009-10 | Photography &amp; Videography | Primary catalogue scope for this subcategory. |
| CAT-009-11 | Events &amp; Entertainment | Primary catalogue scope for this subcategory. |
| CAT-009-12 | Travel &amp; Tourism Services | Primary catalogue scope for this subcategory. |
| CAT-009-13 | Delivery &amp; Moving Services | Primary catalogue scope for this subcategory. |
| CAT-009-14 | Financial &amp; Legal Services | Primary catalogue scope for this subcategory. |
| CAT-009-15 | Agricultural Services | Primary catalogue scope for this subcategory. |
| CAT-009-16 | Other Services | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| SERV-ATTR-001 | Service Provider | text | Yes | Yes | Yes | No |
| SERV-ATTR-002 | Service Title | text | Yes | Yes | Yes | No |
| SERV-ATTR-003 | Service Type | select | Yes | Yes | Yes | No |
| SERV-ATTR-004 | Service Description | text | Yes | Yes | Yes | No |
| SERV-ATTR-005 | Service Area | json | Yes | Yes | Yes | Yes |
| SERV-ATTR-006 | Availability | select | No | Yes | No | No |
| SERV-ATTR-007 | Pricing Type | select | No | Yes | Yes | No |
| SERV-ATTR-008 | Starting Price | decimal | No | Yes | No | No |
| SERV-ATTR-009 | Price Unit | select | No | Yes | No | No |
| SERV-ATTR-010 | Experience | decimal | No | Yes | No | No |
| SERV-ATTR-011 | Experience Unit | select | No | Yes | No | No |
| SERV-ATTR-012 | Skills / Expertise | option | No | Yes | Yes | Yes |
| SERV-ATTR-013 | Languages | option | No | Yes | Yes | Yes |
| SERV-ATTR-014 | Service Delivery Mode | select | No | Yes | Yes | No |
| SERV-ATTR-015 | Emergency Service | boolean | No | Yes | Yes | No |
| SERV-ATTR-016 | Home Visit | boolean | No | Yes | No | No |
| SERV-ATTR-017 | Booking Required | boolean | No | Yes | No | No |
| SERV-ATTR-018 | Warranty / Service Guarantee | text | No | Yes | Yes | No |
| SERV-ATTR-019 | Certifications | option | No | No | No | Yes |
| SERV-ATTR-020 | Provider Notes | text | No | No | Yes | No |

## Controlled Values

Availability: Available Now, By Appointment, Weekdays, Weekends, Evenings, Flexible, Seasonal, Other.

Pricing Type: Fixed Price, Starting From, Hourly, Daily, Monthly, Per Visit, Per Project, Negotiable, Free.

Price Unit: Hour, Day, Visit, Project, Item, Month, Other.

Experience Unit: Months, Years.

Service Delivery Mode: On-site, At Customer Location, Provider Location, Remote / Online, Mobile, Hybrid.

## Subcategory Attributes

### 01 — ome & Domestic

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-01-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-01-ATTR-002 | Household Task | text | No | No | No | No | Free text |
| CAT-009-01-ATTR-003 | Frequency | text | No | No | No | No | Free text |
| CAT-009-01-ATTR-004 | Number of Persons / Rooms | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-009-01-ATTR-005 | Live-in / Live-out | text | No | No | No | No | Free text |
| CAT-009-01-ATTR-006 | Supplies Provided | text | No | No | No | No | Free text |
| CAT-009-01-ATTR-007 | Equipment Provided | text | No | No | No | No | Free text |

### 02 — Repair & Maintenance

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-02-ATTR-001 | Repair Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-02-ATTR-002 | Equipment / Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-02-ATTR-003 | Brand Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-02-ATTR-004 | Parts Included | boolean | No | Yes | No | No | true / false |
| CAT-009-02-ATTR-005 | Parts Cost Included | boolean | No | Yes | No | No | true / false |
| CAT-009-02-ATTR-006 | Diagnosis Available | boolean | No | Yes | No | No | true / false |
| CAT-009-02-ATTR-007 | Warranty Period | text | No | No | No | No | Free text |

### 03 — Construction & Renovation

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-03-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-03-ATTR-002 | Construction Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-03-ATTR-003 | Property Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-03-ATTR-004 | Work Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-009-03-ATTR-005 | Materials Provided | text | No | No | No | No | Free text |
| CAT-009-03-ATTR-006 | Labor Only | text | No | No | No | No | Free text |
| CAT-009-03-ATTR-007 | Site Visit Available | boolean | No | Yes | No | No | true / false |
| CAT-009-03-ATTR-008 | Estimated Duration | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 04 — Automotive Services

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-04-ATTR-001 | Vehicle Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-04-ATTR-002 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-04-ATTR-003 | Compatible Brands | boolean | No | Yes | Yes | Yes | true / false |
| CAT-009-04-ATTR-004 | Mobile Service | text | No | No | No | No | Free text |
| CAT-009-04-ATTR-005 | Parts Provided | text | No | No | No | No | Free text |
| CAT-009-04-ATTR-006 | Diagnostic Service | text | No | No | No | No | Free text |
| CAT-009-04-ATTR-007 | Emergency Roadside Service | text | No | No | No | No | Free text |

### 05 — IT & Digital

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-05-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-05-ATTR-002 | Technology / Platform | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-05-ATTR-003 | Programming Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-05-ATTR-004 | Framework / CMS | text | No | No | No | No | Free text |
| CAT-009-05-ATTR-005 | Project Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-05-ATTR-006 | Remote Available | boolean | No | Yes | No | No | true / false |
| CAT-009-05-ATTR-007 | Portfolio Available | boolean | No | Yes | No | No | true / false |
| CAT-009-05-ATTR-008 | Maintenance Included | boolean | No | Yes | No | No | true / false |

### 06 — Business & Professional

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-06-ATTR-001 | Professional Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-06-ATTR-002 | Industry | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-06-ATTR-003 | Business Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-06-ATTR-004 | Consultation Available | boolean | No | Yes | No | No | true / false |
| CAT-009-06-ATTR-005 | On-site / Remote | boolean | No | Yes | No | No | true / false |
| CAT-009-06-ATTR-006 | Certification | text | No | No | No | No | Free text |
| CAT-009-06-ATTR-007 | Deliverable Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 07 — Education & Training

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-07-ATTR-001 | Subject / Skill | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-07-ATTR-002 | Education Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-07-ATTR-003 | Training Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-07-ATTR-004 | Class Mode | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-07-ATTR-005 | Class Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-07-ATTR-006 | Course Duration | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-009-07-ATTR-007 | Certification Provided | text | No | No | No | No | Free text |
| CAT-009-07-ATTR-008 | Trial Class | text | No | No | No | No | Free text |

### 08 — Health & Wellness

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-08-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-08-ATTR-002 | Specialty | text | No | No | No | No | Free text |
| CAT-009-08-ATTR-003 | Consultation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-08-ATTR-004 | Location Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-08-ATTR-005 | Appointment Required | boolean | No | Yes | No | No | true / false |
| CAT-009-08-ATTR-006 | Certification | text | No | No | No | No | Free text |
| CAT-009-08-ATTR-007 | Emergency Availability | text | No | No | No | No | Free text |

### 09 — Beauty & Personal Care

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-09-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-09-ATTR-002 | Gender / Customer Group | text | No | No | No | No | Free text |
| CAT-009-09-ATTR-003 | Home Service | text | No | No | No | No | Free text |
| CAT-009-09-ATTR-004 | Appointment Required | boolean | No | Yes | No | No | true / false |
| CAT-009-09-ATTR-005 | Product Included | boolean | No | Yes | No | No | true / false |
| CAT-009-09-ATTR-006 | Package Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-09-ATTR-007 | Duration | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 10 — Photography & Videography

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-10-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-10-ATTR-002 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-10-ATTR-003 | Photography / Video | text | No | No | No | No | Free text |
| CAT-009-10-ATTR-004 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-10-ATTR-005 | Editing Included | boolean | No | Yes | No | No | true / false |
| CAT-009-10-ATTR-006 | Number of Hours | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-009-10-ATTR-007 | Deliverables | text | No | No | No | No | Free text |
| CAT-009-10-ATTR-008 | Album Included | boolean | No | Yes | No | No | true / false |
| CAT-009-10-ATTR-009 | Drone Service | text | No | No | No | No | Free text |

### 11 — Events & Entertainment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-11-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-11-ATTR-002 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-11-ATTR-003 | Guest Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-009-11-ATTR-004 | Performance Duration | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-009-11-ATTR-005 | Equipment Included | boolean | No | Yes | No | No | true / false |
| CAT-009-11-ATTR-006 | Setup Included | boolean | No | Yes | No | No | true / false |
| CAT-009-11-ATTR-007 | Travel Available | boolean | No | Yes | No | No | true / false |

### 12 — Travel & Tourism

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-12-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-12-ATTR-002 | Destination | text | No | No | No | No | Free text |
| CAT-009-12-ATTR-003 | Tour Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-12-ATTR-004 | Number of Persons | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-009-12-ATTR-005 | Duration | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-009-12-ATTR-006 | Transportation Included | boolean | No | Yes | No | No | true / false |
| CAT-009-12-ATTR-007 | Accommodation Included | boolean | No | Yes | No | No | true / false |
| CAT-009-12-ATTR-008 | Guide Included | boolean | No | Yes | No | No | true / false |
| CAT-009-12-ATTR-009 | Package Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 13 — Delivery & Moving

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-13-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-13-ATTR-002 | Vehicle Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-13-ATTR-003 | Maximum Load | text | No | No | No | No | Free text |
| CAT-009-13-ATTR-004 | Service Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-009-13-ATTR-005 | Loading / Unloading | text | No | No | No | No | Free text |
| CAT-009-13-ATTR-006 | Packing Included | boolean | No | Yes | No | No | true / false |
| CAT-009-13-ATTR-007 | Insurance Available | boolean | No | Yes | No | No | true / false |
| CAT-009-13-ATTR-008 | Same-Day Service | text | No | No | No | No | Free text |

### 14 — Financial & Legal

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-14-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-14-ATTR-002 | Professional Specialty | text | No | No | No | No | Free text |
| CAT-009-14-ATTR-003 | Consultation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-14-ATTR-004 | Certification / License | text | No | No | No | No | Free text |
| CAT-009-14-ATTR-005 | Remote Consultation | boolean | No | Yes | No | No | true / false |
| CAT-009-14-ATTR-006 | Appointment Required | boolean | No | Yes | No | No | true / false |
| CAT-009-14-ATTR-007 | Document Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 15 — Agricultural Services

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-15-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-15-ATTR-002 | Crop Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-15-ATTR-003 | Farm Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-15-ATTR-004 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-15-ATTR-005 | Labor / Equipment | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-15-ATTR-006 | Seasonal Availability | text | No | No | No | No | Free text |
| CAT-009-15-ATTR-007 | Service Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 16 — Other Services

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-009-16-ATTR-001 | Service Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-009-16-ATTR-002 | Industry / Activity | text | No | No | No | No | Free text |
| CAT-009-16-ATTR-003 | Intended Use | text | No | No | No | No | Free text |
| CAT-009-16-ATTR-004 | Key Features | text | No | No | No | Yes | Free text |

## Listing Types

Service and Wanted are applicable. Offer may be used for explicitly modeled promotional/service offers. Sale, Exchange, Rent, Lease, Free, and Job are not applicable.

## Implementation Rules

- Service provider identity and listing poster identity remain separate.
- Businesses may publish services through authorized business members.
- Service area uses the existing structured location model and supports multiple areas.
- Pricing is optional because many services require quotation.
- Starting Price is not interpreted as a guaranteed final price.
- Skills, languages, certifications, and compatible brands can be multi-value.
- Service-specific technical attributes remain scoped to the relevant subcategory.
- Health, legal, financial, and other regulated professional claims remain provider-supplied unless independently verified.
- Emergency availability is explicit and never inferred from category.
- Service listings follow the standard Draft → Review → Published ↔ Paused → Expired → Archived lifecycle.
- Other Services is the controlled fallback.