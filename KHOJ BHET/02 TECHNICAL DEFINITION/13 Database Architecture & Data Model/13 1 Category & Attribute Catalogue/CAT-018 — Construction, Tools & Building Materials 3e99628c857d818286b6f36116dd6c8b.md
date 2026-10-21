# CAT-018 — Construction, Tools & Building Materials — Detailed Catalogue

**Catalogue ID:** CAT-018

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope Boundary

CAT-018 covers physical construction materials, hardware, tools, plumbing, electrical supplies, renovation products and construction-site supplies. Household/garden tools remain CAT-016; commercial/industrial equipment remains CAT-010; construction, repair, plumbing and electrical labor/services remain CAT-009.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-018-01 | Cement, Concrete &amp; Aggregates | Primary catalogue scope for this subcategory. |
| CAT-018-02 | Bricks, Blocks &amp; Pavers | Primary catalogue scope for this subcategory. |
| CAT-018-03 | Steel, Metal &amp; Structural Materials | Primary catalogue scope for this subcategory. |
| CAT-018-04 | Wood, Timber &amp; Boards | Primary catalogue scope for this subcategory. |
| CAT-018-05 | Roofing &amp; Waterproofing Materials | Primary catalogue scope for this subcategory. |
| CAT-018-06 | Doors, Windows &amp; Frames | Primary catalogue scope for this subcategory. |
| CAT-018-07 | Flooring &amp; Tiles | Primary catalogue scope for this subcategory. |
| CAT-018-08 | Paint, Wall Finishes &amp; Coatings | Primary catalogue scope for this subcategory. |
| CAT-018-09 | Plumbing &amp; Sanitary Materials | Primary catalogue scope for this subcategory. |
| CAT-018-10 | Electrical &amp; Wiring Materials | Primary catalogue scope for this subcategory. |
| CAT-018-11 | Hardware, Fasteners &amp; Fittings | Primary catalogue scope for this subcategory. |
| CAT-018-12 | Hand Tools | Primary catalogue scope for this subcategory. |
| CAT-018-13 | Power Tools | Primary catalogue scope for this subcategory. |
| CAT-018-14 | Safety Equipment &amp; Workwear | Primary catalogue scope for this subcategory. |
| CAT-018-15 | Construction Equipment &amp; Site Supplies | Primary catalogue scope for this subcategory. |
| CAT-018-16 | Other Construction &amp; Building Materials | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| BUILD-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| BUILD-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| BUILD-ATTR-003 | Product Type | select | Yes | Yes | Yes | No |
| BUILD-ATTR-004 | Condition | select | Yes | Yes | No | No |
| BUILD-ATTR-005 | Material | select | No | Yes | No | Yes |
| BUILD-ATTR-006 | Grade / Specification | text. | No | No | No | No |
| BUILD-ATTR-007 | Size / Dimensions | text. | No | No | No | No |
| BUILD-ATTR-008 | Quantity | decimal. | No | No | No | No |
| BUILD-ATTR-009 | Quantity Unit | select. | No | No | No | No |
| BUILD-ATTR-010 | Weight | decimal. | No | No | No | No |
| BUILD-ATTR-011 | Weight Unit | select. | No | No | No | No |
| BUILD-ATTR-012 | Application / Compatibility | text | No | No | No | Yes |
| BUILD-ATTR-013 | Purchase / Manufacture Year | integer. | No | No | No | No |
| BUILD-ATTR-014 | Warranty Status | select. | No | No | No | No |
| BUILD-ATTR-015 | Accessories Included | multi_select | No | Yes | No | Yes |
| BUILD-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Quantity Units: Piece, Set, Box, Pack, Bag, Sack, kg, Ton, Meter, Square Meter, Cubic Meter, Liter, Other.

Weight Unit: g, kg, Ton, lb.

## Subcategory Attributes

### 01 — Cement, Concrete & Aggregates

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-01-ATTR-001 | Material Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-01-ATTR-002 | Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-01-ATTR-003 | Cement Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-01-ATTR-004 | Aggregate Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-01-ATTR-005 | Particle Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-01-ATTR-006 | Bag Weight | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-01-ATTR-007 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-01-ATTR-008 | Manufacturer | text | No | No | No | No | Free text |
| CAT-018-01-ATTR-009 | Production Date | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 02 — Bricks, Blocks & Pavers

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-02-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-02-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-02-ATTR-003 | Dimensions | text | No | No | No | No | Free text |
| CAT-018-02-ATTR-004 | Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-02-ATTR-005 | Compressive Strength | text | No | No | No | No | Free text |
| CAT-018-02-ATTR-006 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-02-ATTR-007 | Finish | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-02-ATTR-008 | Quantity per Pack | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 03 — Steel, Metal & Structural Materials

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-03-ATTR-001 | Material Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-03-ATTR-002 | Steel / Metal Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-03-ATTR-003 | Shape / Profile | text | No | No | No | No | Free text |
| CAT-018-03-ATTR-004 | Thickness | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-03-ATTR-005 | Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-03-ATTR-006 | Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-03-ATTR-007 | Diameter | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-03-ATTR-008 | Weight per Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-03-ATTR-009 | Surface Finish | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 04 — Wood, Timber & Boards

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-04-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-04-ATTR-002 | Wood Species | text | No | No | No | No | Free text |
| CAT-018-04-ATTR-003 | Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-04-ATTR-004 | Thickness | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-04-ATTR-005 | Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-04-ATTR-006 | Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-04-ATTR-007 | Moisture / Treatment | text | No | No | No | No | Free text |
| CAT-018-04-ATTR-008 | Finish | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-04-ATTR-009 | Intended Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 05 — Roofing & Waterproofing Materials

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-05-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-05-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-05-ATTR-003 | Thickness | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-05-ATTR-004 | Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-05-ATTR-005 | Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-05-ATTR-006 | Coverage Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-05-ATTR-007 | Waterproofing Type | boolean | No | Yes | Yes | No | true / false |
| CAT-018-05-ATTR-008 | UV Resistance | text | No | No | No | No | Free text |
| CAT-018-05-ATTR-009 | Installation Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 06 — Doors, Windows & Frames

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-06-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-06-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-06-ATTR-003 | Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-06-ATTR-004 | Height | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-06-ATTR-005 | Frame Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-06-ATTR-006 | Glass Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-06-ATTR-007 | Opening Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-06-ATTR-008 | Lock Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-06-ATTR-009 | Security Features | text | No | No | No | Yes | Free text |

### 07 — Flooring & Tiles

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-07-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-07-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-07-ATTR-003 | Tile / Board Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-07-ATTR-004 | Thickness | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-07-ATTR-005 | Surface Finish | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-07-ATTR-006 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-018-07-ATTR-007 | Slip Resistance | text | No | No | No | No | Free text |
| CAT-018-07-ATTR-008 | Coverage per Box | text | No | No | No | No | Free text |
| CAT-018-07-ATTR-009 | Pattern | text | No | No | No | No | Free text |

### 08 — Paint, Wall Finishes & Coatings

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-08-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-08-ATTR-002 | Surface Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-08-ATTR-003 | Finish | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-08-ATTR-004 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-08-ATTR-005 | Volume | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-08-ATTR-006 | Coverage | text | No | No | No | No | Free text |
| CAT-018-08-ATTR-007 | Application Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-08-ATTR-008 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-018-08-ATTR-009 | Drying Time | text | No | No | No | No | Free text |

### 09 — Plumbing & Sanitary Materials

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-09-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-09-ATTR-003 | Diameter | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-09-ATTR-004 | Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-09-ATTR-005 | Pressure Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-09-ATTR-006 | Connection Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-09-ATTR-007 | Thread Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-09-ATTR-008 | Compatible System | boolean | No | Yes | No | Yes | true / false |
| CAT-018-09-ATTR-009 | Indoor / Outdoor | text | No | No | No | No | Free text |

### 10 — Electrical & Wiring Materials

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-10-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-10-ATTR-002 | Cable / Wire Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-10-ATTR-003 | Conductor Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-10-ATTR-004 | Core Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-10-ATTR-005 | Cross Section | text | No | No | No | No | Free text |
| CAT-018-10-ATTR-006 | Voltage Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-10-ATTR-007 | Current Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-10-ATTR-008 | Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-10-ATTR-009 | Insulation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-10-ATTR-010 | Certification | text | No | No | No | No | Free text |

### 11 — Hardware, Fasteners & Fittings

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-11-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-11-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-11-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-11-ATTR-004 | Thread Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-11-ATTR-005 | Finish | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-11-ATTR-006 | Strength / Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-11-ATTR-007 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-11-ATTR-008 | Compatible Material | boolean | No | Yes | No | Yes | true / false |
| CAT-018-11-ATTR-009 | Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 12 — Hand Tools

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-12-ATTR-001 | Tool Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-12-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-12-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-12-ATTR-004 | Handle Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-12-ATTR-005 | Professional / Consumer | text | No | No | No | No | Free text |
| CAT-018-12-ATTR-006 | Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-12-ATTR-007 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-12-ATTR-008 | Compatible Accessories | boolean | No | Yes | No | Yes | true / false |

### 13 — Power Tools

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-13-ATTR-001 | Tool Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-13-ATTR-002 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-13-ATTR-003 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-13-ATTR-004 | Voltage | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-13-ATTR-005 | Battery Type | boolean | No | Yes | Yes | No | true / false |
| CAT-018-13-ATTR-006 | Battery Included | boolean | No | Yes | No | No | true / false |
| CAT-018-13-ATTR-007 | Speed | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-13-ATTR-008 | Chuck / Bit Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-13-ATTR-009 | Professional / Consumer | text | No | No | No | No | Free text |
| CAT-018-13-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 14 — Safety Equipment & Workwear

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-14-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-14-ATTR-002 | Safety Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-14-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-14-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-14-ATTR-005 | Protection Standard | text | No | No | No | No | Free text |
| CAT-018-14-ATTR-006 | Certification | text | No | No | No | No | Free text |
| CAT-018-14-ATTR-007 | PPE Category | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-14-ATTR-008 | Gender / Fit | text | No | No | No | No | Free text |
| CAT-018-14-ATTR-009 | Intended Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 15 — Construction Equipment & Site Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-15-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-15-ATTR-002 | Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-15-ATTR-003 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-15-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-15-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-15-ATTR-006 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-15-ATTR-007 | Dimensions | text | No | No | No | No | Free text |
| CAT-018-15-ATTR-008 | Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-018-15-ATTR-009 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-018-15-ATTR-010 | Assembly Required | boolean | No | Yes | No | No | true / false |

### 16 — Other Construction & Building Materials

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-018-16-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-16-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-16-ATTR-003 | Grade / Specification | text | No | No | No | No | Free text |
| CAT-018-16-ATTR-004 | Intended Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-16-ATTR-005 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-018-16-ATTR-006 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange, Wanted, Free, Rent (limited), Lease (limited), Offer. Service and Job are not applicable.

## Boundary Rules

- Household hand/garden tools primarily for ordinary consumers belong to CAT-016.
- Industrial machinery and commercial equipment belong to CAT-010.
- Construction, renovation, plumbing and electrical labor belong to CAT-009.
- Construction materials and physical tools belong to CAT-018.
- Professional construction equipment can remain CAT-018 when primarily construction-site equipment rather than general commercial machinery.

## Implementation Rules

- Quantity and quantity unit remain separate.
- Dimensions should be structured where practical.
- Material grade/specification remains distinct from material type.
- Construction standards and certifications are seller-provided unless independently verified.
- Electrical products support applicable voltage/current/specification attributes.
- Safety equipment distinguishes seller claims from verified certification.
- Used power tools/equipment may require functional-status information.
- Expiration/production dates are supported for applicable consumables such as cement, coatings and other time-sensitive products.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Construction & Building Materials is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.