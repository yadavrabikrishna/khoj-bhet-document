# CAT-015 — Home & Garden — Detailed Catalogue

**Catalogue ID:** CAT-015

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope Boundary

CAT-015 covers household goods, gardening products, décor, lighting, household tools, outdoor/home-improvement products. Furniture remains CAT-003; electrical home appliances remain CAT-006; sports/gym equipment remains CAT-007; commercial equipment remains CAT-010; agricultural products remain CAT-013.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-015-01 | Home Décor &amp; Decorative Items | Primary catalogue scope for this subcategory. |
| CAT-015-02 | Lighting &amp; Lamps | Primary catalogue scope for this subcategory. |
| CAT-015-03 | Kitchenware &amp; Dining | Primary catalogue scope for this subcategory. |
| CAT-015-04 | Bedding &amp; Linens | Primary catalogue scope for this subcategory. |
| CAT-015-05 | Bathroom Accessories | Primary catalogue scope for this subcategory. |
| CAT-015-06 | Storage &amp; Organization | Primary catalogue scope for this subcategory. |
| CAT-015-07 | Cleaning &amp; Household Supplies | Primary catalogue scope for this subcategory. |
| CAT-015-08 | Curtains, Blinds &amp; Window Coverings | Primary catalogue scope for this subcategory. |
| CAT-015-09 | Carpets, Rugs &amp; Mats | Primary catalogue scope for this subcategory. |
| CAT-015-10 | Garden &amp; Gardening Supplies | Primary catalogue scope for this subcategory. |
| CAT-015-11 | Plants, Pots &amp; Planters | Primary catalogue scope for this subcategory. |
| CAT-015-12 | Outdoor Furniture &amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-015-13 | Home Improvement &amp; Building Supplies | Primary catalogue scope for this subcategory. |
| CAT-015-14 | Hand Tools &amp; Household Tools | Primary catalogue scope for this subcategory. |
| CAT-015-15 | Other Home &amp; Garden | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| HOMEG-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| HOMEG-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| HOMEG-ATTR-003 | Product Type | select | Yes | Yes | Yes | No |
| HOMEG-ATTR-004 | Condition | select | Yes | Yes | No | No |
| HOMEG-ATTR-005 | Material | select | No | Yes | No | Yes |
| HOMEG-ATTR-006 | Color | select. | No | No | No | No |
| HOMEG-ATTR-007 | Size / Dimensions | text. | No | No | No | No |
| HOMEG-ATTR-008 | Weight | decimal. | No | No | No | No |
| HOMEG-ATTR-009 | Weight Unit | select. | No | No | No | No |
| HOMEG-ATTR-010 | Quantity | integer. | No | No | No | No |
| HOMEG-ATTR-011 | Purchase Year | integer. | No | No | No | No |
| HOMEG-ATTR-012 | Warranty Status | select. | No | No | No | No |
| HOMEG-ATTR-013 | Power Source | select. | No | No | No | No |
| HOMEG-ATTR-014 | Assembly Required | boolean. | No | No | No | No |
| HOMEG-ATTR-015 | Accessories Included | multi_select | No | Yes | No | Yes |
| HOMEG-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Weight Unit: g, kg, lb.

Power Source: Electricity, Battery, Solar, Manual, Gas, LPG, Hybrid, Other.

Warranty: None, Active, Expired, Seller Warranty, Manufacturer Warranty.

## Subcategory Attributes

### 01 — Home Décor & Decorative Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-01-ATTR-001 | Décor Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-01-ATTR-002 | Style | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-01-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-01-ATTR-004 | Room / Placement | text | No | No | No | No | Free text |
| CAT-015-01-ATTR-005 | Handmade | text | No | No | No | No | Free text |
| CAT-015-01-ATTR-006 | Theme | text | No | No | No | No | Free text |
| CAT-015-01-ATTR-007 | Dimensions | text | No | No | No | No | Free text |

### 02 — Lighting & Lamps

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-02-ATTR-001 | Lighting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-02-ATTR-002 | Bulb Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-02-ATTR-003 | Wattage | text | No | No | No | No | Free text |
| CAT-015-02-ATTR-004 | Voltage | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-02-ATTR-005 | Light Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-02-ATTR-006 | Fixture Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-02-ATTR-007 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-015-02-ATTR-008 | Dimmable | boolean | No | Yes | No | No | true / false |
| CAT-015-02-ATTR-009 | Smart / Connected | boolean | No | Yes | No | No | true / false |

### 03 — Kitchenware & Dining

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-03-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-03-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-03-ATTR-003 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-03-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-03-ATTR-005 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-03-ATTR-006 | Dishwasher Safe | text | No | No | No | No | Free text |
| CAT-015-03-ATTR-007 | Microwave Safe | text | No | No | No | No | Free text |
| CAT-015-03-ATTR-008 | Food Safe | text | No | No | No | No | Free text |
| CAT-015-03-ATTR-009 | Heat Resistance | text | No | No | No | No | Free text |

### 04 — Bedding & Linens

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-04-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-04-ATTR-002 | Bed Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-04-ATTR-003 | Material / Fabric | text | No | No | No | No | Free text |
| CAT-015-04-ATTR-004 | Thread Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-04-ATTR-005 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-04-ATTR-006 | Pattern | text | No | No | No | No | Free text |
| CAT-015-04-ATTR-007 | Set Components | text | No | No | No | Yes | Free text |
| CAT-015-04-ATTR-008 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 05 — Bathroom Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-05-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-05-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-05-ATTR-003 | Installation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-05-ATTR-004 | Room / Placement | text | No | No | No | No | Free text |
| CAT-015-05-ATTR-005 | Water Resistant | boolean | No | Yes | No | No | true / false |
| CAT-015-05-ATTR-006 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-05-ATTR-007 | Dimensions | text | No | No | No | No | Free text |

### 06 — Storage & Organization

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-06-ATTR-001 | Storage Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-06-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-06-ATTR-003 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-06-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-06-ATTR-005 | Number of Compartments | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-06-ATTR-006 | Stackable | text | No | No | No | No | Free text |
| CAT-015-06-ATTR-007 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-015-06-ATTR-008 | Lockable | boolean | No | Yes | No | No | true / false |
| CAT-015-06-ATTR-009 | Dimensions | text | No | No | No | No | Free text |

### 07 — Cleaning & Household Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-07-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-07-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-07-ATTR-003 | Intended Surface / Use | text | No | No | No | No | Free text |
| CAT-015-07-ATTR-004 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-015-07-ATTR-005 | Pack Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-07-ATTR-006 | Concentration / Form | text | No | No | No | No | Free text |
| CAT-015-07-ATTR-007 | Accessories | text | No | No | No | Yes | Free text |

### 08 — Curtains, Blinds & Window Coverings

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-08-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-08-ATTR-002 | Material / Fabric | text | No | No | No | No | Free text |
| CAT-015-08-ATTR-003 | Window Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-08-ATTR-004 | Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-08-ATTR-005 | Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-08-ATTR-006 | Mounting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-08-ATTR-007 | Light Blocking | text | No | No | No | No | Free text |
| CAT-015-08-ATTR-008 | Pattern | text | No | No | No | No | Free text |
| CAT-015-08-ATTR-009 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 09 — Carpets, Rugs & Mats

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-09-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-09-ATTR-003 | Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-09-ATTR-004 | Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-09-ATTR-005 | Thickness | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-09-ATTR-006 | Pattern | text | No | No | No | No | Free text |
| CAT-015-09-ATTR-007 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-015-09-ATTR-008 | Washable | boolean | No | Yes | No | No | true / false |
| CAT-015-09-ATTR-009 | Non-Slip | boolean | No | Yes | No | No | true / false |

### 10 — Garden & Gardening Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-10-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-10-ATTR-002 | Gardening Use | text | No | No | No | No | Free text |
| CAT-015-10-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-10-ATTR-004 | Tool Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-10-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-10-ATTR-006 | Manual / Powered | boolean | No | Yes | No | No | true / false |
| CAT-015-10-ATTR-007 | Handle Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-10-ATTR-008 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 11 — Plants, Pots & Planters

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-11-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-11-ATTR-002 | Plant Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-11-ATTR-003 | Species | text | No | No | No | No | Free text |
| CAT-015-11-ATTR-004 | Variety | text | No | No | No | No | Free text |
| CAT-015-11-ATTR-005 | Plant Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-11-ATTR-006 | Pot Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-11-ATTR-007 | Pot Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-11-ATTR-008 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-015-11-ATTR-009 | Sunlight Requirement | text | No | No | No | No | Free text |
| CAT-015-11-ATTR-010 | Water Requirement | text | No | No | No | No | Free text |

### 12 — Outdoor Furniture & Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-12-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-12-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-12-ATTR-003 | Seating Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-12-ATTR-004 | Weather Resistant | boolean | No | Yes | No | No | true / false |
| CAT-015-12-ATTR-005 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-015-12-ATTR-006 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-015-12-ATTR-007 | Cushion Included | boolean | No | Yes | No | No | true / false |
| CAT-015-12-ATTR-008 | Dimensions | text | No | No | No | No | Free text |

### 13 — Home Improvement & Building Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-13-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-13-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-13-ATTR-003 | Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-13-ATTR-004 | Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-13-ATTR-005 | Dimensions | text | No | No | No | No | Free text |
| CAT-015-13-ATTR-006 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-015-13-ATTR-007 | Coverage | text | No | No | No | No | Free text |
| CAT-015-13-ATTR-008 | Brand | text | No | No | Yes | No | Free text |
| CAT-015-13-ATTR-009 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 14 — Hand Tools & Household Tools

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-14-ATTR-001 | Tool Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-14-ATTR-002 | Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-14-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-14-ATTR-004 | Manual / Powered | boolean | No | Yes | No | No | true / false |
| CAT-015-14-ATTR-005 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-14-ATTR-006 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-14-ATTR-007 | Professional / Consumer | text | No | No | No | No | Free text |
| CAT-015-14-ATTR-008 | Compatible Accessories | boolean | No | Yes | No | Yes | true / false |

### 15 — Other Home & Garden

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-015-15-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-15-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-015-15-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-015-15-ATTR-004 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange, Wanted, Free, Rent (limited), Lease (limited), Offer. Service and Job are not applicable.

## Implementation Rules

- Dimensions should be structured where practical rather than stored only as free text.
- Weight and weight unit remain separate.
- Power attributes apply only to applicable products.
- Indoor/outdoor suitability is independent from product category.
- Safety/certification claims are seller-provided unless independently verified.
- Plants support species and variety separately.
- Rental/lease applies only to suitable reusable products.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Home & Garden is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.