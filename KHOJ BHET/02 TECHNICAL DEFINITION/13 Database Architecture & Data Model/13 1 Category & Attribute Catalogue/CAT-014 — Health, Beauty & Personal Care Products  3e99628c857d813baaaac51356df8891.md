# CAT-014 — Health, Beauty & Personal Care Products — Detailed Catalogue

**Catalogue ID:** CAT-014

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope Boundary

CAT-014 covers physical consumer health, beauty and personal-care products. Clinics, doctors, therapists, trainers, salons and other professional services remain under CAT-009 Services.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-014-01 | Personal Care &amp; Hygiene | Primary catalogue scope for this subcategory. |
| CAT-014-02 | Skin Care | Primary catalogue scope for this subcategory. |
| CAT-014-03 | Hair Care | Primary catalogue scope for this subcategory. |
| CAT-014-04 | Makeup &amp; Cosmetics | Primary catalogue scope for this subcategory. |
| CAT-014-05 | Fragrances &amp; Perfumes | Primary catalogue scope for this subcategory. |
| CAT-014-06 | Shaving &amp; Grooming | Primary catalogue scope for this subcategory. |
| CAT-014-07 | Dental &amp; Oral Care | Primary catalogue scope for this subcategory. |
| CAT-014-08 | Baby Personal Care | Primary catalogue scope for this subcategory. |
| CAT-014-09 | Fitness &amp; Wellness Products | Primary catalogue scope for this subcategory. |
| CAT-014-10 | Massage &amp; Relaxation Products | Primary catalogue scope for this subcategory. |
| CAT-014-11 | Vision &amp; Eye Care Products | Primary catalogue scope for this subcategory. |
| CAT-014-12 | Hearing &amp; Assistive Products | Primary catalogue scope for this subcategory. |
| CAT-014-13 | Beauty Equipment &amp; Salon Supplies | Primary catalogue scope for this subcategory. |
| CAT-014-14 | Other Health, Beauty &amp; Personal Care | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| CARE-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| CARE-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| CARE-ATTR-003 | Product Type | select | Yes | Yes | Yes | No |
| CARE-ATTR-004 | Condition | select | Yes | Yes | No | No |
| CARE-ATTR-005 | Intended User Group | select | No | Yes | No | Yes |
| CARE-ATTR-006 | Gender / Target Group | select. | No | No | No | No |
| CARE-ATTR-007 | Quantity / Pack Size | decimal. | No | No | No | No |
| CARE-ATTR-008 | Unit | select. | No | No | No | No |
| CARE-ATTR-009 | Expiry Date | date. | No | No | No | No |
| CARE-ATTR-010 | Manufacturing Date | date. | No | No | No | No |
| CARE-ATTR-011 | Ingredients / Materials | text | No | No | No | Yes |
| CARE-ATTR-012 | Warranty Status | select. | No | No | No | No |
| CARE-ATTR-013 | Certification / Compliance | text | No | No | No | Yes |
| CARE-ATTR-014 | Original Packaging | boolean. | No | No | No | No |
| CARE-ATTR-015 | Accessories Included | multi_select | No | Yes | No | Yes |
| CARE-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Open Box, Like New, Good, Fair, Used, Needs Repair, Refurbished.

Target Group: Newborn, Baby, Kids, Teen, Adult, Senior, All Ages.

Gender / Target Group: Male, Female, Unisex, All.

## Subcategory Attributes

### 01 — Personal Care & Hygiene

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-01-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-01-ATTR-002 | Skin / Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-014-01-ATTR-003 | Form | text | No | No | No | No | Free text |
| CAT-014-01-ATTR-004 | Pack Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-01-ATTR-005 | Fragrance | text | No | No | No | No | Free text |
| CAT-014-01-ATTR-006 | Intended Age | text | No | No | No | No | Free text |
| CAT-014-01-ATTR-007 | Ingredients | text | No | No | No | Yes | Free text |

### 02 — Skin Care

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-02-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-02-ATTR-002 | Skin Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-02-ATTR-003 | Skin Concern | text | No | No | No | No | Free text |
| CAT-014-02-ATTR-004 | SPF | text | No | No | No | No | Free text |
| CAT-014-02-ATTR-005 | Form | text | No | No | No | No | Free text |
| CAT-014-02-ATTR-006 | Ingredients | text | No | No | No | Yes | Free text |
| CAT-014-02-ATTR-007 | Intended Age | text | No | No | No | No | Free text |
| CAT-014-02-ATTR-008 | Fragrance-Free | text | No | No | No | No | Free text |

### 03 — Hair Care

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-03-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-03-ATTR-002 | Hair Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-03-ATTR-003 | Hair Concern | text | No | No | No | No | Free text |
| CAT-014-03-ATTR-004 | Form | text | No | No | No | No | Free text |
| CAT-014-03-ATTR-005 | Ingredients | text | No | No | No | Yes | Free text |
| CAT-014-03-ATTR-006 | Fragrance | text | No | No | No | No | Free text |
| CAT-014-03-ATTR-007 | Intended Age | text | No | No | No | No | Free text |

### 04 — Makeup & Cosmetics

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-04-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-04-ATTR-002 | Shade / Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-04-ATTR-003 | Skin Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-04-ATTR-004 | Finish | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-04-ATTR-005 | Coverage | text | No | No | No | No | Free text |
| CAT-014-04-ATTR-006 | Form | text | No | No | No | No | Free text |
| CAT-014-04-ATTR-007 | Ingredients | text | No | No | No | Yes | Free text |
| CAT-014-04-ATTR-008 | Expiry Date | text | No | No | No | No | Free text |

### 05 — Fragrances & Perfumes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-05-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-05-ATTR-002 | Brand | text | No | No | Yes | No | Free text |
| CAT-014-05-ATTR-003 | Fragrance Family | text | No | No | No | No | Free text |
| CAT-014-05-ATTR-004 | Gender | text | No | No | No | No | Free text |
| CAT-014-05-ATTR-005 | Volume | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-014-05-ATTR-006 | Concentration | text | No | No | No | No | Free text |
| CAT-014-05-ATTR-007 | Original / Tester | text | No | No | No | No | Free text |
| CAT-014-05-ATTR-008 | Packaging | text | No | No | No | No | Free text |

### 06 — Shaving & Grooming

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-06-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-06-ATTR-002 | Manual / Electric | boolean | No | Yes | No | No | true / false |
| CAT-014-06-ATTR-003 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-06-ATTR-004 | Battery / Runtime | boolean | No | Yes | No | No | true / false |
| CAT-014-06-ATTR-005 | Blade Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-06-ATTR-006 | Attachments | text | No | No | No | No | Free text |
| CAT-014-06-ATTR-007 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-014-06-ATTR-008 | Accessories | text | No | No | No | Yes | Free text |

### 07 — Dental & Oral Care

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-07-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-07-ATTR-002 | Brand | text | No | No | Yes | No | Free text |
| CAT-014-07-ATTR-003 | Electric / Manual | boolean | No | Yes | No | No | true / false |
| CAT-014-07-ATTR-004 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-07-ATTR-005 | Brush Head Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-07-ATTR-006 | Modes | text | No | No | No | No | Free text |
| CAT-014-07-ATTR-007 | Battery / Runtime | boolean | No | Yes | No | No | true / false |
| CAT-014-07-ATTR-008 | Accessories | text | No | No | No | Yes | Free text |

### 08 — Baby Personal Care

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-08-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-08-ATTR-002 | Intended Age | text | No | No | No | No | Free text |
| CAT-014-08-ATTR-003 | Skin / Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-014-08-ATTR-004 | Ingredients | text | No | No | No | Yes | Free text |
| CAT-014-08-ATTR-005 | Fragrance-Free | text | No | No | No | No | Free text |
| CAT-014-08-ATTR-006 | Hypoallergenic Claim | text | No | No | No | No | Free text |
| CAT-014-08-ATTR-007 | Pack Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-08-ATTR-008 | Expiry Date | text | No | No | No | No | Free text |

### 09 — Fitness & Wellness Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-09-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-014-09-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-09-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-09-ATTR-005 | Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-014-09-ATTR-006 | Resistance / Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-014-09-ATTR-007 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-014-09-ATTR-008 | Accessories | text | No | No | No | Yes | Free text |

### 10 — Massage & Relaxation Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-10-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-10-ATTR-002 | Massage Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-10-ATTR-003 | Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-014-10-ATTR-004 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-10-ATTR-005 | Heat Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-10-ATTR-006 | Intensity Levels | text | No | No | No | No | Free text |
| CAT-014-10-ATTR-007 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-014-10-ATTR-008 | Accessories | text | No | No | No | Yes | Free text |

### 11 — Vision & Eye Care Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-11-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-11-ATTR-002 | Lens Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-11-ATTR-003 | Prescription / Non-Prescription | text | No | No | No | No | Free text |
| CAT-014-11-ATTR-004 | Lens Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-11-ATTR-005 | Frame Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-11-ATTR-006 | Frame Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-11-ATTR-007 | UV Protection | text | No | No | No | No | Free text |
| CAT-014-11-ATTR-008 | Accessories | text | No | No | No | Yes | Free text |

### 12 — Hearing & Assistive Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-12-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-12-ATTR-002 | Assistive Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-12-ATTR-003 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-12-ATTR-004 | Battery / Runtime | boolean | No | Yes | No | No | true / false |
| CAT-014-12-ATTR-005 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-12-ATTR-006 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-014-12-ATTR-007 | Connectivity | text | No | No | No | No | Free text |
| CAT-014-12-ATTR-008 | Accessories | text | No | No | No | Yes | Free text |

### 13 — Beauty Equipment & Salon Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-13-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-13-ATTR-002 | Professional / Consumer | text | No | No | No | No | Free text |
| CAT-014-13-ATTR-003 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-13-ATTR-004 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-13-ATTR-005 | Temperature Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-014-13-ATTR-006 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-014-13-ATTR-007 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-13-ATTR-008 | Accessories | text | No | No | No | Yes | Free text |

### 14 — Other Health, Beauty & Personal Care

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-014-14-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-014-14-ATTR-002 | Intended User | text | No | No | No | No | Free text |
| CAT-014-14-ATTR-003 | Intended Use | text | No | No | No | No | Free text |
| CAT-014-14-ATTR-004 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange, Wanted, Free (limited), Rent (limited), Offer. Lease, Service and Job are not applicable.

## Implementation Rules

- Expiry is first-class for applicable products.
- Expired products must not be treated as normally sellable active inventory.
- Health-related product claims are not automatically verified.
- Certification/compliance information is seller-provided unless independently verified.
- Prescription-specific information must not be treated as ordinary metadata where it creates privacy or regulated-use concerns.
- Medical and mobility equipment may receive stronger moderation rules.
- Ingredients and accessories may be multi-value.
- Electrical attributes apply only to applicable products.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Health, Beauty & Personal Care is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

## Phase 3 Audit Correction

Health monitoring and mobility equipment are assigned to CAT-023. CAT-014 remains consumer health, beauty, personal-care and general wellness products. Sport/exercise equipment remains CAT-007.