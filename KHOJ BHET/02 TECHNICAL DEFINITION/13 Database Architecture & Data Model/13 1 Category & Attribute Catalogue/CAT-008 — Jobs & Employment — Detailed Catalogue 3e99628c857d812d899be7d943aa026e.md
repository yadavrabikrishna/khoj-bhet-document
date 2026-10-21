# CAT-008 — Jobs & Employment — Detailed Catalogue

**Catalogue ID:** CAT-008

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-008-01 | Full-Time Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-02 | Part-Time Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-03 | Contract / Temporary Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-04 | Freelance Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-05 | Internship / Trainee | Primary catalogue scope for this subcategory. |
| CAT-008-06 | Work From Home / Remote | Primary catalogue scope for this subcategory. |
| CAT-008-07 | Government / Public Sector Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-08 | Teaching &amp; Education Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-09 | Healthcare Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-10 | IT &amp; Technology Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-11 | Sales &amp; Marketing Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-12 | Hospitality &amp; Tourism Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-13 | Construction &amp; Skilled Trades | Primary catalogue scope for this subcategory. |
| CAT-008-14 | Driver &amp; Delivery Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-15 | Domestic &amp; Household Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-16 | Other Jobs | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| JOB-ATTR-001 | Employer / Organization | text | Yes | No | Yes | No |
| JOB-ATTR-002 | Job Title | text | Yes | Yes | Yes | No |
| JOB-ATTR-003 | Employment Type | select | Yes | Yes | Yes | No |
| JOB-ATTR-004 | Work Mode | select | Yes | Yes | No | No |
| JOB-ATTR-005 | Experience Level | select | No | Yes | No | No |
| JOB-ATTR-006 | Experience Required | decimal | No | Yes | No | No |
| JOB-ATTR-007 | Experience Unit | select | No | Yes | No | No |
| JOB-ATTR-008 | Education Level | select | No | Yes | No | No |
| JOB-ATTR-009 | Skills | option | No | Yes | Yes | Yes |
| JOB-ATTR-010 | Salary Minimum | decimal | No | Yes | No | No |
| JOB-ATTR-011 | Salary Maximum | decimal | No | Yes | No | No |
| JOB-ATTR-012 | Salary Period | select | No | Yes | No | No |
| JOB-ATTR-013 | Salary Currency | select | No | Yes | No | No |
| JOB-ATTR-014 | Vacancy Count | integer | No | Yes | No | No |
| JOB-ATTR-015 | Application Deadline | date | No | Yes | No | No |
| JOB-ATTR-016 | Gender Preference | select | No | Yes | No | No |
| JOB-ATTR-017 | Age Requirement | text | No | No | No | No |
| JOB-ATTR-018 | Benefits | option | No | No | No | Yes |
| JOB-ATTR-019 | Required Languages | option | No | Yes | Yes | Yes |
| JOB-ATTR-020 | Job Description | text | Yes | Yes | Yes | No |
| JOB-ATTR-021 | Application Instructions | text | Yes | No | No | No |
| JOB-ATTR-022 | Seller / Employer Notes | text | No | No | Yes | No |

## Controlled Values

Employment Type: Full-Time, Part-Time, Contract, Temporary, Freelance, Internship, Apprenticeship, Volunteer, Seasonal, Other.

Work Mode: On-site, Remote, Hybrid, Field Work, Other.

Experience Level: No Experience, Entry Level, Junior, Mid Level, Senior, Manager, Executive, Other.

Experience Unit: Months, Years.

Education Level: No Formal Education, SEE / Equivalent, +2 / Intermediate, Diploma, Bachelor, Master, MPhil, PhD, Professional Certification, Other.

Salary Period: Hourly, Daily, Weekly, Monthly, Annual, Project Based, Negotiable.

Salary Currency: NPR, USD, INR, Other.

Gender Preference: Any, Male, Female, Other.

Benefits: Provident Fund, Insurance, Health Insurance, Accident Insurance, Paid Leave, Festival Allowance, Dashain Bonus, Transportation, Food / Meal, Accommodation, Training, Communication Allowance, Internet Allowance, Performance Bonus, Other.

Required Languages: Nepali, Maithili, Bhojpuri, Newari, Tamang, Tharu, Hindi, English, Urdu, Other.

## Subcategory Attributes

### 01 — ull-Time

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-01-ATTR-001 | Job Category | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-01-ATTR-002 | Work Schedule | text | No | No | No | No | Free text |
| CAT-008-01-ATTR-003 | Probation Period | text | No | No | No | No | Free text |
| CAT-008-01-ATTR-004 | Office Location | text | No | No | No | No | Free text |
| CAT-008-01-ATTR-005 | Relocation Required | boolean | No | Yes | No | No | true / false |
| CAT-008-01-ATTR-006 | Benefits | text | No | No | No | Yes | Free text |

### 02 — Part-Time

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-02-ATTR-001 | Hours Per Week | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-008-02-ATTR-002 | Work Schedule | text | No | No | No | No | Free text |
| CAT-008-02-ATTR-003 | Shift | text | No | No | No | No | Free text |
| CAT-008-02-ATTR-004 | Duration | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-008-02-ATTR-005 | Duration Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Contract / Temporary

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-03-ATTR-001 | Contract Duration | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-008-03-ATTR-002 | Duration Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-03-ATTR-003 | Contract Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-03-ATTR-004 | Renewable | text | No | No | No | No | Free text |
| CAT-008-03-ATTR-005 | Project Name | text | No | No | Yes | No | Free text |

### 04 — Freelance

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-04-ATTR-001 | Project Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-04-ATTR-002 | Project Duration | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-008-04-ATTR-003 | Duration Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-04-ATTR-004 | Payment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-04-ATTR-005 | Remote Allowed | boolean | No | Yes | No | No | true / false |
| CAT-008-04-ATTR-006 | Deliverables | text | No | No | No | No | Free text |
| CAT-008-04-ATTR-007 | Required Portfolio | boolean | No | Yes | No | No | true / false |

### 05 — Internship / Trainee

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-05-ATTR-001 | Internship Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-05-ATTR-002 | Duration | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-008-05-ATTR-003 | Duration Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-05-ATTR-004 | Paid / Unpaid | text | No | No | No | No | Free text |
| CAT-008-05-ATTR-005 | Stipend | text | No | No | No | No | Free text |
| CAT-008-05-ATTR-006 | Training Provided | text | No | No | No | No | Free text |
| CAT-008-05-ATTR-007 | Potential Employment | text | No | No | No | No | Free text |

### 06 — Work From Home / Remote

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-06-ATTR-001 | Remote Type | boolean | No | Yes | Yes | No | true / false |
| CAT-008-06-ATTR-002 | Required Time Zone | boolean | No | Yes | No | No | true / false |
| CAT-008-06-ATTR-003 | Required Internet | boolean | No | Yes | No | No | true / false |
| CAT-008-06-ATTR-004 | Equipment Provided | text | No | No | No | No | Free text |
| CAT-008-06-ATTR-005 | Communication Platform | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-06-ATTR-006 | Location Restriction | text | No | No | No | No | Free text |

### 07 — Government / Public Sector

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-07-ATTR-001 | Government Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-07-ATTR-002 | Organization | text | No | No | No | No | Free text |
| CAT-008-07-ATTR-003 | Position Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-07-ATTR-004 | Exam Required | boolean | No | Yes | No | No | true / false |
| CAT-008-07-ATTR-005 | Application Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-07-ATTR-006 | Official Notice Reference | text | No | No | No | No | Free text |

### 08 — Teaching & Education

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-08-ATTR-001 | Teaching Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-08-ATTR-002 | Subject | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-08-ATTR-003 | Teaching Qualification | text | No | No | No | No | Free text |
| CAT-008-08-ATTR-004 | Classroom / Online | text | No | No | No | No | Free text |
| CAT-008-08-ATTR-005 | Certification Required | boolean | No | Yes | No | No | true / false |
| CAT-008-08-ATTR-006 | Institution Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 09 — Healthcare

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-09-ATTR-001 | Profession | text | No | No | No | No | Free text |
| CAT-008-09-ATTR-002 | Specialization | text | No | No | No | No | Free text |
| CAT-008-09-ATTR-003 | Qualification | text | No | No | No | No | Free text |
| CAT-008-09-ATTR-004 | License Required | boolean | No | Yes | No | No | true / false |
| CAT-008-09-ATTR-005 | Experience | text | No | No | No | No | Free text |
| CAT-008-09-ATTR-006 | Shift Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-09-ATTR-007 | Institution Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 10 — IT & Technology

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-10-ATTR-001 | Technology Role | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-10-ATTR-002 | Technical Skills | text | No | No | No | Yes | Free text |
| CAT-008-10-ATTR-003 | Programming Languages | text | No | No | No | Yes | Free text |
| CAT-008-10-ATTR-004 | Frameworks / Platforms | text | No | No | No | No | Free text |
| CAT-008-10-ATTR-005 | Certification | text | No | No | No | No | Free text |
| CAT-008-10-ATTR-006 | Portfolio Required | boolean | No | Yes | No | No | true / false |
| CAT-008-10-ATTR-007 | Remote Availability | boolean | No | Yes | No | No | true / false |

### 11 — Sales & Marketing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-11-ATTR-001 | Sales / Marketing Role | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-11-ATTR-002 | Industry | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-11-ATTR-003 | Target / Commission | text | No | No | No | Yes | Free text |
| CAT-008-11-ATTR-004 | Travel Required | boolean | No | Yes | No | No | true / false |
| CAT-008-11-ATTR-005 | Field Work | text | No | No | No | No | Free text |
| CAT-008-11-ATTR-006 | Communication Skills | text | No | No | No | Yes | Free text |

### 12 — Hospitality & Tourism

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-12-ATTR-001 | Job Role | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-12-ATTR-002 | Establishment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-12-ATTR-003 | Shift Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-12-ATTR-004 | Accommodation Provided | text | No | No | No | No | Free text |
| CAT-008-12-ATTR-005 | Food Provided | text | No | No | No | No | Free text |
| CAT-008-12-ATTR-006 | Tourism Experience Required | boolean | No | Yes | No | No | true / false |

### 13 — Construction & Skilled Trades

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-13-ATTR-001 | Trade Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-13-ATTR-002 | Skill Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-13-ATTR-003 | Certification Required | boolean | No | Yes | No | No | true / false |
| CAT-008-13-ATTR-004 | Tools Provided | text | No | No | No | No | Free text |
| CAT-008-13-ATTR-005 | Accommodation | text | No | No | No | No | Free text |
| CAT-008-13-ATTR-006 | Field Location | text | No | No | No | No | Free text |

### 14 — Driver & Delivery

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-14-ATTR-001 | Driver Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-14-ATTR-002 | License Category | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-14-ATTR-003 | Vehicle Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-14-ATTR-004 | Experience Required | boolean | No | Yes | No | No | true / false |
| CAT-008-14-ATTR-005 | Commercial License Required | boolean | No | Yes | No | No | true / false |
| CAT-008-14-ATTR-006 | Own Vehicle Required | boolean | No | Yes | No | No | true / false |
| CAT-008-14-ATTR-007 | Route / Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-008-14-ATTR-008 | Accommodation | text | No | No | No | No | Free text |

### 15 — Domestic & Household

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-15-ATTR-001 | Job Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-15-ATTR-002 | Live-in / Live-out | text | No | No | No | No | Free text |
| CAT-008-15-ATTR-003 | Working Hours | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-008-15-ATTR-004 | Accommodation | text | No | No | No | No | Free text |
| CAT-008-15-ATTR-005 | Food Provided | text | No | No | No | No | Free text |
| CAT-008-15-ATTR-006 | Experience Required | boolean | No | Yes | No | No | true / false |
| CAT-008-15-ATTR-007 | Number of Persons / Household | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 16 — Other Jobs

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-008-16-ATTR-001 | Job Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-16-ATTR-002 | Industry | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-16-ATTR-003 | Required Skills | boolean | No | Yes | No | Yes | true / false |
| CAT-008-16-ATTR-004 | Intended Role | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-008-16-ATTR-005 | Key Requirements | text | No | No | No | No | Free text |

## Listing Types

Job and Wanted only. Sale, Exchange, Rent, Lease, Free, Offer, and Service are not applicable.

## Implementation Rules

- Employer/organization and job poster identity are separate concepts.
- A business may publish jobs through authorized business members.
- Salary minimum, maximum, period, and currency are modeled independently.
- Salary may be negotiable without requiring numeric values.
- Skills and languages are multi-value.
- Application deadline is distinct from listing expiration.
- Government/public-sector listings support an official source/reference.
- Qualification and licensing requirements are seller/employer-provided unless independently verified.
- Sensitive applicant information is not stored as ordinary listing attributes.
- Job listings follow review-before-publication lifecycle.
- Expired jobs are not searchable as active opportunities.
- Other Jobs is a controlled fallback.