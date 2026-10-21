# CAT-011 — Baby, Kids & Toys — Detailed Catalogue

**Catalogue ID:** CAT-011

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-011-01 | Baby Clothing &amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-011-02 | Baby Gear &amp; Carriers | Primary catalogue scope for this subcategory. |
| CAT-011-03 | Strollers &amp; Prams | Primary catalogue scope for this subcategory. |
| CAT-011-04 | Baby Furniture | Primary catalogue scope for this subcategory. |
| CAT-011-05 | Feeding &amp; Nursing | Primary catalogue scope for this subcategory. |
| CAT-011-06 | Diapering &amp; Baby Care | Primary catalogue scope for this subcategory. |
| CAT-011-07 | Toys | Primary catalogue scope for this subcategory. |
| CAT-011-08 | Educational Toys &amp; Learning | Primary catalogue scope for this subcategory. |
| CAT-011-09 | Outdoor &amp; Ride-On Toys | Primary catalogue scope for this subcategory. |
| CAT-011-10 | Video Games &amp; Kids Electronics | Primary catalogue scope for this subcategory. |
| CAT-011-11 | Kids Books &amp; Educational Materials | Primary catalogue scope for this subcategory. |
| CAT-011-12 | Party &amp; Kids Event Supplies | Primary catalogue scope for this subcategory. |
| CAT-011-13 | Safety &amp; Childproofing | Primary catalogue scope for this subcategory. |
| CAT-011-14 | Baby Health &amp; Wellness Products | Primary catalogue scope for this subcategory. |
| CAT-011-15 | Kids Sports &amp; Activity Equipment | Primary catalogue scope for this subcategory. |
| CAT-011-16 | Other Baby, Kids &amp; Toys | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| KIDS-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| KIDS-ATTR-002 | Product Name / Model | text. | No | Yes | Yes | No |
| KIDS-ATTR-003 | Condition | select. | No | No | No | No |
| KIDS-ATTR-004 | Age Group | select. | No | No | No | No |
| KIDS-ATTR-005 | Recommended Age | select. | No | No | No | No |
| KIDS-ATTR-006 | Material | select. | No | No | No | No |
| KIDS-ATTR-007 | Color | select. | No | No | No | No |
| KIDS-ATTR-008 | Size | select. | No | No | No | No |
| KIDS-ATTR-009 | Gender / Target Group | select. | No | No | No | No |
| KIDS-ATTR-010 | Quantity | integer. | No | No | No | No |
| KIDS-ATTR-011 | Purchase Year | integer. | No | No | No | No |
| KIDS-ATTR-012 | Warranty Status | select. | No | No | No | No |
| KIDS-ATTR-013 | Accessories Included | multi_select | No | Yes | No | Yes |
| KIDS-ATTR-014 | Original Packaging | boolean. | No | No | No | No |
| KIDS-ATTR-015 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Age Group: Newborn, 0–3 Months, 3–6 Months, 6–12 Months, 1–2 Years, 2–3 Years, 3–5 Years, 5–8 Years, 8–12 Years, 12+ Years, All Ages.

Target Group: Boys, Girls, Unisex, All.

## Subcategory Attributes

### 01 — Baby Clothing & Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-01-ATTR-001 | Clothing Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-01-ATTR-002 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-01-ATTR-003 | Fabric | text | No | No | No | No | Free text |
| CAT-011-01-ATTR-004 | Season | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-01-ATTR-005 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-01-ATTR-006 | Gender | text | No | No | No | No | Free text |
| CAT-011-01-ATTR-007 | Occasion | text | No | No | No | No | Free text |

### 02 — Baby Gear & Carriers

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-02-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-02-ATTR-002 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-02-ATTR-003 | Weight Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-02-ATTR-004 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-011-02-ATTR-005 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-011-02-ATTR-006 | Safety Harness | text | No | No | No | No | Free text |
| CAT-011-02-ATTR-007 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Strollers & Prams

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-03-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-03-ATTR-002 | Age Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-03-ATTR-003 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-03-ATTR-004 | Reclining | boolean | No | Yes | No | No | true / false |
| CAT-011-03-ATTR-005 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-011-03-ATTR-006 | Wheel Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-03-ATTR-007 | Safety Harness | text | No | No | No | No | Free text |
| CAT-011-03-ATTR-008 | Storage Basket | text | No | No | No | No | Free text |
| CAT-011-03-ATTR-009 | Rain Cover | text | No | No | No | No | Free text |

### 04 — Baby Furniture

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-04-ATTR-001 | Furniture Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-04-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-04-ATTR-003 | Dimensions | text | No | No | No | No | Free text |
| CAT-011-04-ATTR-004 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-011-04-ATTR-005 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-011-04-ATTR-006 | Safety Rail | text | No | No | No | No | Free text |
| CAT-011-04-ATTR-007 | Mattress Included | boolean | No | Yes | No | No | true / false |
| CAT-011-04-ATTR-008 | Assembly Required | boolean | No | Yes | No | No | true / false |

### 05 — Feeding & Nursing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-05-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-05-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-05-ATTR-003 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-05-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-05-ATTR-005 | BPA-Free | boolean | No | Yes | No | No | true / false |
| CAT-011-05-ATTR-006 | Sterilization Compatible | boolean | No | Yes | No | Yes | true / false |
| CAT-011-05-ATTR-007 | Age Suitability | text | No | No | No | No | Free text |

### 06 — Diapering & Baby Care

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-06-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-06-ATTR-002 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-06-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-06-ATTR-004 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-06-ATTR-005 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-011-06-ATTR-006 | Fragrance-Free | text | No | No | No | No | Free text |
| CAT-011-06-ATTR-007 | Intended Age | text | No | No | No | No | Free text |

### 07 — Toys

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-07-ATTR-001 | Toy Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-07-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-07-ATTR-003 | Recommended Age | text | No | No | No | No | Free text |
| CAT-011-07-ATTR-004 | Battery Required | boolean | No | Yes | No | No | true / false |
| CAT-011-07-ATTR-005 | Battery Included | boolean | No | Yes | No | No | true / false |
| CAT-011-07-ATTR-006 | Educational | text | No | No | No | No | Free text |
| CAT-011-07-ATTR-007 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-011-07-ATTR-008 | Number of Pieces | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 08 — Educational Toys & Learning

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-08-ATTR-001 | Learning Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-08-ATTR-002 | Subject | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-08-ATTR-003 | Skill Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-08-ATTR-004 | Age Group | text | No | No | No | No | Free text |
| CAT-011-08-ATTR-005 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-08-ATTR-006 | Number of Pieces | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-08-ATTR-007 | Battery / Electronic | boolean | No | Yes | No | No | true / false |

### 09 — Outdoor & Ride-On Toys

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-09-ATTR-002 | Age Group | text | No | No | No | No | Free text |
| CAT-011-09-ATTR-003 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-09-ATTR-004 | Electric / Manual | boolean | No | Yes | No | No | true / false |
| CAT-011-09-ATTR-005 | Battery Voltage | boolean | No | Yes | No | No | true / false |
| CAT-011-09-ATTR-006 | Maximum Speed | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-09-ATTR-007 | Safety Equipment | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-09-ATTR-008 | Assembly Required | boolean | No | Yes | No | No | true / false |

### 10 — Video Games & Kids Electronics

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-10-ATTR-001 | Device Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-10-ATTR-002 | Platform | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-10-ATTR-003 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-10-ATTR-004 | Storage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-10-ATTR-005 | Screen Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-10-ATTR-006 | Parental Controls | text | No | No | No | No | Free text |
| CAT-011-10-ATTR-007 | Accessories | text | No | No | No | Yes | Free text |
| CAT-011-10-ATTR-008 | Age Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 11 — Kids Books & Educational Materials

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-11-ATTR-001 | Material Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-11-ATTR-002 | Subject | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-11-ATTR-003 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-11-ATTR-004 | Age Group | text | No | No | No | No | Free text |
| CAT-011-11-ATTR-005 | Grade Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-11-ATTR-006 | Author / Publisher | text | No | No | No | No | Free text |
| CAT-011-11-ATTR-007 | Edition | text | No | No | No | No | Free text |

### 12 — Party & Kids Event Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-12-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-12-ATTR-002 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-12-ATTR-003 | Age Group | text | No | No | No | No | Free text |
| CAT-011-12-ATTR-004 | Theme | text | No | No | No | No | Free text |
| CAT-011-12-ATTR-005 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-011-12-ATTR-006 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-011-12-ATTR-007 | Decoration Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 13 — Safety & Childproofing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-13-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-13-ATTR-002 | Installation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-13-ATTR-003 | Compatible Location | boolean | No | Yes | No | Yes | true / false |
| CAT-011-13-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-13-ATTR-005 | Safety Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-13-ATTR-006 | Age Suitability | text | No | No | No | No | Free text |
| CAT-011-13-ATTR-007 | Certification | text | No | No | No | No | Free text |

### 14 — Baby Health & Wellness Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-14-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-14-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-011-14-ATTR-003 | Age Suitability | text | No | No | No | No | Free text |
| CAT-011-14-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-14-ATTR-005 | Measurement Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-14-ATTR-006 | Battery Required | boolean | No | Yes | No | No | true / false |
| CAT-011-14-ATTR-007 | Certification | text | No | No | No | No | Free text |

### 15 — Kids Sports & Activity Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-15-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-15-ATTR-002 | Sport / Activity | select | No | Yes | No | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-15-ATTR-003 | Age Group | text | No | No | No | No | Free text |
| CAT-011-15-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-15-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-15-ATTR-006 | Safety Equipment Included | boolean | No | Yes | No | No | true / false |
| CAT-011-15-ATTR-007 | Skill Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 16 — Other Baby, Kids & Toys

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-011-16-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-011-16-ATTR-002 | Intended Age | text | No | No | No | No | Free text |
| CAT-011-16-ATTR-003 | Intended Use | text | No | No | No | No | Free text |
| CAT-011-16-ATTR-004 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange, Wanted, Free. Rent may apply to appropriate reusable products. Lease, Service, and Job are not applicable. Offer may be used where explicitly modeled.

## Implementation Rules

- Age suitability is independently filterable from category.
- Safety-related attributes do not imply certification unless verified.
- Battery/electrical attributes apply only to relevant products.
- Multi-value attributes use separate attribute rows; single-value attributes allow at most one.
- Used baby products may require additional condition/safety information.
- Safety-sensitive products may receive additional moderation restrictions.
- Other Baby, Kids & Toys is the controlled fallback.
- Rental applies only to appropriate reusable products such as selected baby gear, toys, and event supplies.
- All listings follow the standard review-before-publication lifecycle.