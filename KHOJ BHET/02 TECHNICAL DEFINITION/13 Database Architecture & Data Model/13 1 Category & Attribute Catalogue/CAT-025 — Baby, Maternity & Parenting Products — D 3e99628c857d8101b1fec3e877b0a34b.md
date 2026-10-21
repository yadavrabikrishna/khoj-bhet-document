# CAT-025 — Baby, Maternity & Parenting Products — Detailed Catalogue

**Catalogue ID:** CAT-025

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope

CAT-025 covers physical products for pregnancy, maternity, newborn care, parenting, breastfeeding, postpartum care and early-childhood needs.

## Boundary

- CAT-012 covers general baby, kids and toys.
- CAT-015 covers general personal-care, health and wellness products.
- CAT-023 covers medical/diagnostic equipment.
- CAT-005 covers ordinary clothing/fashion.
- CAT-003 covers furniture; dedicated maternity/nursing furniture may remain CAT-025.
- CAT-006 covers home appliances.
- CAT-024 covers school supplies.
- CAT-009 covers maternity, childcare, doula, nursing and other human-delivered services.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-025-01 | Maternity Clothing &amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-025-02 | Pregnancy Support &amp; Comfort Products | Primary catalogue scope for this subcategory. |
| CAT-025-03 | Maternity &amp; Hospital Bags | Primary catalogue scope for this subcategory. |
| CAT-025-04 | Breastfeeding &amp; Nursing Products | Primary catalogue scope for this subcategory. |
| CAT-025-05 | Breast Pumps &amp; Milk Storage | Primary catalogue scope for this subcategory. |
| CAT-025-06 | Maternity &amp; Nursing Furniture | Primary catalogue scope for this subcategory. |
| CAT-025-07 | Pregnancy &amp; Parenting Books / Materials | Primary catalogue scope for this subcategory. |
| CAT-025-08 | Postpartum Care Products | Primary catalogue scope for this subcategory. |
| CAT-025-09 | Parenting &amp; Childcare Accessories | Primary catalogue scope for this subcategory. |
| CAT-025-10 | Prenatal &amp; Postpartum Support Equipment | Primary catalogue scope for this subcategory. |
| CAT-025-11 | Pregnancy Testing &amp; Monitoring Products | Primary catalogue scope for this subcategory. |
| CAT-025-12 | Maternity Recovery &amp; Comfort Products | Primary catalogue scope for this subcategory. |
| CAT-025-13 | Nursing Covers &amp; Breastfeeding Accessories | Primary catalogue scope for this subcategory. |
| CAT-025-14 | Parenting Organization &amp; Care Kits | Primary catalogue scope for this subcategory. |
| CAT-025-15 | Other Maternity &amp; Parenting Products | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| PARENT-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| PARENT-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| PARENT-ATTR-003 | Product Type | select | Yes | Yes | Yes | No |
| PARENT-ATTR-004 | Condition | select. | No | No | No | No |
| PARENT-ATTR-005 | Intended User Group | select | No | Yes | No | Yes |
| PARENT-ATTR-006 | Material | select | No | Yes | No | Yes |
| PARENT-ATTR-007 | Size | select. | No | No | No | No |
| PARENT-ATTR-008 | Color | select | No | Yes | No | Yes |
| PARENT-ATTR-009 | Quantity | decimal. | No | No | No | No |
| PARENT-ATTR-010 | Quantity Unit | select. | No | No | No | No |
| PARENT-ATTR-011 | Dimensions | text. | No | No | No | No |
| PARENT-ATTR-012 | Age / Stage Suitability | select. | No | No | No | No |
| PARENT-ATTR-013 | Warranty Status | select. | No | No | No | No |
| PARENT-ATTR-014 | Accessories Included | multi_select | No | Yes | No | Yes |
| PARENT-ATTR-015 | Original Packaging | boolean. | No | No | No | No |
| PARENT-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Open Box, Like New, Good, Fair, Used, Needs Repair, Refurbished.

Intended User Group: Pregnant Person, Postpartum Parent, Nursing Parent, Newborn, Infant, Baby, Parent / Caregiver, Family, Other.

Quantity Unit: Piece, Set, Pack, Pair, Bottle, Box, Dozen, Other.

## Subcategory Attributes

### 01 — Maternity Clothing & Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-01-ATTR-001 | Clothing Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-01-ATTR-002 | Pregnancy / Postpartum Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-01-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-01-ATTR-004 | Gender / Target Group | text | No | No | No | Yes | Free text |
| CAT-025-01-ATTR-005 | Material / Fabric | text | No | No | No | No | Free text |
| CAT-025-01-ATTR-006 | Season | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-01-ATTR-007 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-025-01-ATTR-008 | Nursing Friendly | text | No | No | No | No | Free text |
| CAT-025-01-ATTR-009 | Occasion | text | No | No | No | No | Free text |
| CAT-025-01-ATTR-010 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 02 — Pregnancy Support & Comfort Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-02-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-02-ATTR-002 | Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-02-ATTR-003 | Support Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-02-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-02-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-02-ATTR-006 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-025-02-ATTR-007 | Wearable | text | No | No | No | No | Free text |
| CAT-025-02-ATTR-008 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-025-02-ATTR-009 | Intended Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-02-ATTR-010 | Care Instructions | text | No | No | No | No | Free text |

### 03 — Maternity & Hospital Bags

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-03-ATTR-001 | Bag Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-03-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-03-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-03-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-03-ATTR-005 | Number of Compartments | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-03-ATTR-006 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-025-03-ATTR-007 | Shoulder / Carry Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-03-ATTR-008 | Included Organizer | boolean | No | Yes | No | No | true / false |
| CAT-025-03-ATTR-009 | Suitable Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-03-ATTR-010 | Dimensions | text | No | No | No | No | Free text |

### 04 — Breastfeeding & Nursing Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-04-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-04-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-025-04-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-04-ATTR-004 | Size / Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-04-ATTR-005 | BPA-Free | boolean | No | Yes | No | No | true / false |
| CAT-025-04-ATTR-006 | Sterilization Compatible | boolean | No | Yes | No | Yes | true / false |
| CAT-025-04-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-025-04-ATTR-008 | Portability | text | No | No | No | No | Free text |
| CAT-025-04-ATTR-009 | Accessories | text | No | No | No | Yes | Free text |
| CAT-025-04-ATTR-010 | Suitable Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 05 — Breast Pumps & Milk Storage

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-05-ATTR-001 | Pump Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-05-ATTR-002 | Manual / Electric | boolean | No | Yes | No | No | true / false |
| CAT-025-05-ATTR-003 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-05-ATTR-004 | Pumping Modes | text | No | No | No | No | Free text |
| CAT-025-05-ATTR-005 | Suction Levels | text | No | No | No | No | Free text |
| CAT-025-05-ATTR-006 | Bottle Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-05-ATTR-007 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-05-ATTR-008 | Battery Runtime | boolean | No | Yes | No | No | true / false |
| CAT-025-05-ATTR-009 | Sterilization Compatible | boolean | No | Yes | No | Yes | true / false |
| CAT-025-05-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 06 — Maternity & Nursing Furniture

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-06-ATTR-001 | Furniture Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-06-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-06-ATTR-003 | Dimensions | text | No | No | No | No | Free text |
| CAT-025-06-ATTR-004 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-025-06-ATTR-005 | Reclining | boolean | No | Yes | No | No | true / false |
| CAT-025-06-ATTR-006 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-025-06-ATTR-007 | Nursing Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-06-ATTR-008 | Storage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-06-ATTR-009 | Cushion / Mattress Included | boolean | No | Yes | No | No | true / false |
| CAT-025-06-ATTR-010 | Assembly Required | boolean | No | Yes | No | No | true / false |

### 07 — Pregnancy & Parenting Books / Materials

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-07-ATTR-001 | Material Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-07-ATTR-002 | Topic | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-07-ATTR-003 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-07-ATTR-004 | Author / Creator | text | No | No | No | No | Free text |
| CAT-025-07-ATTR-005 | Publisher | text | No | No | No | No | Free text |
| CAT-025-07-ATTR-006 | Edition | text | No | No | No | No | Free text |
| CAT-025-07-ATTR-007 | Publication Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-07-ATTR-008 | Format | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-07-ATTR-009 | Intended Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-07-ATTR-010 | ISBN / Catalog Number | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 08 — Postpartum Care Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-08-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-08-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-025-08-ATTR-003 | Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-08-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-08-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-08-ATTR-006 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-025-08-ATTR-007 | Disposable | text | No | No | No | No | Free text |
| CAT-025-08-ATTR-008 | Intended Postpartum Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-08-ATTR-009 | Care Instructions | text | No | No | No | No | Free text |
| CAT-025-08-ATTR-010 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 09 — Parenting & Childcare Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-09-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-025-09-ATTR-003 | Age / Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-09-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-09-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-09-ATTR-006 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-025-09-ATTR-007 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-025-09-ATTR-008 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-025-09-ATTR-009 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-09-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 10 — Prenatal & Postpartum Support Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-10-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-10-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-025-10-ATTR-003 | Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-10-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-10-ATTR-005 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-10-ATTR-006 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-025-10-ATTR-007 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-025-10-ATTR-008 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-025-10-ATTR-009 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-10-ATTR-010 | Safety Features | text | No | No | No | Yes | Free text |

### 11 — Pregnancy Testing & Monitoring Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-11-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-11-ATTR-002 | Measurement / Test Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-11-ATTR-003 | Detection / Measurement Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-11-ATTR-004 | Accuracy | text | No | No | No | No | Free text |
| CAT-025-11-ATTR-005 | Result Format | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-11-ATTR-006 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-025-11-ATTR-007 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-11-ATTR-008 | Connectivity | text | No | No | No | No | Free text |
| CAT-025-11-ATTR-009 | Accessories | text | No | No | No | Yes | Free text |

### 12 — Maternity Recovery & Comfort Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-12-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-12-ATTR-002 | Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-12-ATTR-003 | Intended Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-12-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-12-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-12-ATTR-006 | Support Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-12-ATTR-007 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-025-12-ATTR-008 | Wearable | text | No | No | No | No | Free text |
| CAT-025-12-ATTR-009 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-025-12-ATTR-010 | Heat / Cooling Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-12-ATTR-011 | Care Instructions | text | No | No | No | No | Free text |

### 13 — Nursing Covers & Breastfeeding Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-13-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-13-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-13-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-13-ATTR-004 | Coverage Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-13-ATTR-005 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-025-13-ATTR-006 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-025-13-ATTR-007 | Washable | boolean | No | Yes | No | No | true / false |
| CAT-025-13-ATTR-008 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-025-13-ATTR-009 | Accessories | text | No | No | No | Yes | Free text |
| CAT-025-13-ATTR-010 | Suitable Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 14 — Parenting Organization & Care Kits

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-14-ATTR-001 | Kit Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-14-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-025-14-ATTR-003 | Stage / Age Group | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-14-ATTR-004 | Contents | text | No | No | No | Yes | Free text |
| CAT-025-14-ATTR-005 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-025-14-ATTR-006 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-025-14-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-025-14-ATTR-008 | Storage Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-14-ATTR-009 | Organizer Included | boolean | No | Yes | No | No | true / false |

### 15 — Other Maternity & Parenting Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-025-15-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-15-ATTR-002 | Intended User | text | No | No | No | No | Free text |
| CAT-025-15-ATTR-003 | Intended Stage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-15-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-025-15-ATTR-005 | Intended Use | text | No | No | No | No | Free text |
| CAT-025-15-ATTR-006 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange (limited), Wanted, Free, Rent (limited), Offer. Lease, Service and Job are not ordinary listing types.

## Safety & Boundary Rules

- General baby clothing, toys, kids products and children's equipment belong to CAT-012 unless maternity/parenting lifecycle is the primary purpose.
- General personal-care products belong to CAT-015.
- Medical diagnostic or therapeutic equipment belongs to CAT-023.
- Pregnancy/maternity books belong to CAT-025 when specifically parenting/maternity-oriented; general books remain CAT-012.
- Ordinary furniture belongs to CAT-003; dedicated maternity/nursing furniture may remain CAT-025.
- Maternity and childcare services belong to CAT-009.
- Baby appliances such as sterilizers and dedicated electrical appliances belong to CAT-006 where appliance classification is primary.
- School/learning supplies belong to CAT-024.
- Safety claims are not automatically verified.
- “Medical grade,” “hospital grade” and similar claims are seller-provided unless independently verified.
- Feeding and milk-storage products require appropriate material and capacity information.
- Products intended for newborn sleep or infant safety may require stronger moderation.
- Age/stage suitability is explicit and should not be inferred from product title alone.
- Hygiene-sensitive used products may require additional moderation.
- Expired consumables should not remain active marketplace inventory.
- Health or medical treatment claims should not be treated as verified product capabilities.

## Implementation Rules

- Pregnancy stage, postpartum stage and infant age/stage remain distinct concepts where applicable.
- Capacity and capacity unit remain separate.
- Quantity and quantity unit remain separate.
- Age/stage suitability is structured where practical.
- Disposable versus reusable is explicit.
- Material remains separate from ingredients/material composition where relevant.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Baby, Maternity & Parenting Products is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

## Phase 3 Audit Correction

CAT-025 is restricted to pregnancy, maternity, breastfeeding/nursing, postpartum and parenting-lifecycle products. General baby/kids products remain CAT-011.