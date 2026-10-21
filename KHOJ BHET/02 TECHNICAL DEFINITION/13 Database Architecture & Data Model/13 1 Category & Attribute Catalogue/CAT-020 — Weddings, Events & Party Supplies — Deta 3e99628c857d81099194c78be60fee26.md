# CAT-020 — Weddings, Events & Party Supplies — Detailed Catalogue

**Catalogue ID:** CAT-020

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope Boundary

CAT-020 covers physical products used for weddings, parties, celebrations, ceremonies and events. Event planning, decoration labor, catering, photography, entertainment and venues remain CAT-009 Services; ordinary clothing remains CAT-005; general craft materials remain CAT-021; ordinary household furniture remains CAT-003; general consumer electronics remain CAT-002.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-020-01 | Wedding Decorations &amp; Backdrops | Primary catalogue scope for this subcategory. |
| CAT-020-02 | Party Decorations | Primary catalogue scope for this subcategory. |
| CAT-020-03 | Flowers, Artificial Flowers &amp; Floral Décor | Primary catalogue scope for this subcategory. |
| CAT-020-04 | Lighting &amp; Decorative Lighting | Primary catalogue scope for this subcategory. |
| CAT-020-05 | Tables, Chairs &amp; Event Furniture | Primary catalogue scope for this subcategory. |
| CAT-020-06 | Tents, Canopies &amp; Temporary Structures | Primary catalogue scope for this subcategory. |
| CAT-020-07 | Wedding Accessories &amp; Ceremony Items | Primary catalogue scope for this subcategory. |
| CAT-020-08 | Tableware &amp; Serving Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-09 | Party Supplies &amp; Disposable Items | Primary catalogue scope for this subcategory. |
| CAT-020-10 | Balloons &amp; Balloon Decoration Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-11 | Cake, Baking &amp; Dessert Decoration Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-12 | Invitation, Printing &amp; Stationery Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-13 | Gifts, Favors &amp; Return-Gift Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-14 | Kids &amp; Theme Party Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-15 | Event Audio, Stage &amp; Production Equipment | Primary catalogue scope for this subcategory. |
| CAT-020-16 | Other Wedding, Event &amp; Party Supplies | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| EVENT-ATTR-001 | Brand / Manufacturer / Maker | text. | No | Yes | Yes | No |
| EVENT-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| EVENT-ATTR-003 | Product Type | select | Yes | Yes | Yes | No |
| EVENT-ATTR-004 | Condition | select | Yes | Yes | No | No |
| EVENT-ATTR-005 | Material | select | No | Yes | No | Yes |
| EVENT-ATTR-006 | Color / Theme | select | No | Yes | No | Yes |
| EVENT-ATTR-007 | Size / Dimensions | text. | No | No | No | No |
| EVENT-ATTR-008 | Quantity | decimal. | No | No | No | No |
| EVENT-ATTR-009 | Quantity Unit | select. | No | No | No | No |
| EVENT-ATTR-010 | Capacity | decimal. | No | No | No | No |
| EVENT-ATTR-011 | Capacity Unit | select. | No | No | No | No |
| EVENT-ATTR-012 | Reusable | boolean. | No | No | No | No |
| EVENT-ATTR-013 | Purchase Year | integer. | No | No | No | No |
| EVENT-ATTR-014 | Warranty Status | select. | No | No | No | No |
| EVENT-ATTR-015 | Accessories Included | multi_select | No | Yes | No | Yes |
| EVENT-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Quantity Unit: Piece, Set, Pack, Box, Dozen, Pair, Meter, Roll, Other.

Capacity Unit: Person, Table, Seat, Piece, Liter, Other.

## Subcategory Attributes

### 01 — Wedding Decorations & Backdrops

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-01-ATTR-001 | Decoration Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-01-ATTR-002 | Wedding Theme | text | No | No | No | No | Free text |
| CAT-020-01-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-01-ATTR-004 | Backdrop Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-01-ATTR-005 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-01-ATTR-006 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-020-01-ATTR-007 | Mounting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-01-ATTR-008 | Included Components | boolean | No | Yes | No | Yes | true / false |

### 02 — Party Decorations

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-02-ATTR-001 | Decoration Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-02-ATTR-002 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-02-ATTR-003 | Theme | text | No | No | No | No | Free text |
| CAT-020-02-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-02-ATTR-005 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-02-ATTR-006 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-02-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-020-02-ATTR-008 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 03 — Flowers, Artificial Flowers & Floral Décor

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-03-ATTR-001 | Flower Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-03-ATTR-002 | Fresh / Artificial / Preserved | text | No | No | No | No | Free text |
| CAT-020-03-ATTR-003 | Flower Variety | text | No | No | No | No | Free text |
| CAT-020-03-ATTR-004 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-03-ATTR-005 | Arrangement Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-03-ATTR-006 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-03-ATTR-007 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-03-ATTR-008 | Reusable | boolean | No | Yes | No | No | true / false |

### 04 — Lighting & Decorative Lighting

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-04-ATTR-001 | Lighting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-04-ATTR-002 | Light Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-04-ATTR-003 | Voltage | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-04-ATTR-004 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-04-ATTR-005 | Light Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-04-ATTR-006 | Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-04-ATTR-007 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-020-04-ATTR-008 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-020-04-ATTR-009 | Control Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-04-ATTR-010 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 05 — Tables, Chairs & Event Furniture

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-05-ATTR-001 | Furniture Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-05-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-05-ATTR-003 | Seating Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-05-ATTR-004 | Dimensions | text | No | No | No | No | Free text |
| CAT-020-05-ATTR-005 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-020-05-ATTR-006 | Stackable | text | No | No | No | No | Free text |
| CAT-020-05-ATTR-007 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-020-05-ATTR-008 | Cushion Included | boolean | No | Yes | No | No | true / false |
| CAT-020-05-ATTR-009 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 06 — Tents, Canopies & Temporary Structures

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-06-ATTR-001 | Structure Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-06-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-06-ATTR-003 | Persons | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-06-ATTR-004 | Dimensions | text | No | No | No | No | Free text |
| CAT-020-06-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-06-ATTR-006 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-020-06-ATTR-007 | Wind Resistance | text | No | No | No | No | Free text |
| CAT-020-06-ATTR-008 | Setup Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-06-ATTR-009 | Frame Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-06-ATTR-010 | Carry Bag Included | boolean | No | Yes | No | No | true / false |

### 07 — Wedding Accessories & Ceremony Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-07-ATTR-001 | Item Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-07-ATTR-002 | Ceremony Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-07-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-07-ATTR-004 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-07-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-07-ATTR-006 | Theme | text | No | No | No | No | Free text |
| CAT-020-07-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-020-07-ATTR-008 | Included Components | boolean | No | Yes | No | Yes | true / false |

### 08 — Tableware & Serving Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-08-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-08-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-08-ATTR-003 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-08-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-08-ATTR-005 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-08-ATTR-006 | Food Safe | text | No | No | No | No | Free text |
| CAT-020-08-ATTR-007 | Disposable / Reusable | boolean | No | Yes | No | No | true / false |
| CAT-020-08-ATTR-008 | Dishwasher Safe | text | No | No | No | No | Free text |
| CAT-020-08-ATTR-009 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 09 — Party Supplies & Disposable Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-09-ATTR-002 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-09-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-09-ATTR-004 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-09-ATTR-005 | Theme | text | No | No | No | No | Free text |
| CAT-020-09-ATTR-006 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-09-ATTR-007 | Disposable / Reusable | boolean | No | Yes | No | No | true / false |
| CAT-020-09-ATTR-008 | Age Group | text | No | No | No | No | Free text |

### 10 — Balloons & Balloon Decoration Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-10-ATTR-001 | Balloon Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-10-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-10-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-10-ATTR-004 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-10-ATTR-005 | Theme | text | No | No | No | No | Free text |
| CAT-020-10-ATTR-006 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-10-ATTR-007 | Inflatable Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-10-ATTR-008 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-020-10-ATTR-009 | Accessories Included | boolean | No | Yes | No | Yes | true / false |

### 11 — Cake, Baking & Dessert Decoration Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-11-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-11-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-11-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-11-ATTR-004 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-11-ATTR-005 | Theme | text | No | No | No | No | Free text |
| CAT-020-11-ATTR-006 | Food Safe | text | No | No | No | No | Free text |
| CAT-020-11-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-020-11-ATTR-008 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-11-ATTR-009 | Decoration Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 12 — Invitation, Printing & Stationery Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-12-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-12-ATTR-002 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-12-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-12-ATTR-004 | Paper Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-12-ATTR-005 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-12-ATTR-006 | Printing Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-12-ATTR-007 | Customizable | text | No | No | No | No | Free text |
| CAT-020-12-ATTR-008 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-12-ATTR-009 | Design / Theme | text | No | No | No | No | Free text |

### 13 — Gifts, Favors & Return-Gift Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-13-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-13-ATTR-002 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-13-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-13-ATTR-004 | Theme | text | No | No | No | No | Free text |
| CAT-020-13-ATTR-005 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-13-ATTR-006 | Packaging Included | boolean | No | Yes | No | No | true / false |
| CAT-020-13-ATTR-007 | Customizable | text | No | No | No | No | Free text |
| CAT-020-13-ATTR-008 | Age Group | text | No | No | No | No | Free text |

### 14 — Kids & Theme Party Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-14-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-14-ATTR-002 | Theme | text | No | No | No | No | Free text |
| CAT-020-14-ATTR-003 | Age Group | text | No | No | No | No | Free text |
| CAT-020-14-ATTR-004 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-14-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-14-ATTR-006 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-14-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-020-14-ATTR-008 | Safety Feature | text | No | No | No | No | Free text |

### 15 — Event Audio, Stage & Production Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-15-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-15-ATTR-002 | Audio / Production Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-15-ATTR-003 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-15-ATTR-004 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-15-ATTR-005 | Connectivity | text | No | No | No | No | Free text |
| CAT-020-15-ATTR-006 | Channel Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-15-ATTR-007 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-020-15-ATTR-008 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-15-ATTR-009 | Mounting / Setup Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-15-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 16 — Other Wedding, Event & Party Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-020-16-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-16-ATTR-002 | Event Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-16-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-020-16-ATTR-004 | Theme | text | No | No | No | No | Free text |
| CAT-020-16-ATTR-005 | Intended Use | text | No | No | No | No | Free text |
| CAT-020-16-ATTR-006 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange, Wanted, Free, Rent, Lease (limited), Offer. Service and Job are not applicable.

## Boundary Rules

- Event planning, decoration labor, catering, photography, entertainment and venue services belong to CAT-009.
- Wedding clothing and ordinary fashion belong to CAT-005.
- General craft materials belong to CAT-021.
- Ordinary household furniture belongs to CAT-003.
- General consumer electronics belong to CAT-019.
- Event-specific physical products remain CAT-020 even when normally used temporarily.

## Implementation Rules

- Event type and theme remain separate.
- Quantity and quantity unit remain separate.
- Capacity and capacity unit remain separate.
- Disposable versus reusable is explicit where applicable.
- Food-contact and safety claims are seller-provided unless independently verified.
- Electrical specifications apply only to relevant products.
- Rental is supported for suitable reusable decorations, furniture, tents, equipment and similar products.
- Setup/installation service is not implied by a physical listing.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Wedding, Event & Party Supplies is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.