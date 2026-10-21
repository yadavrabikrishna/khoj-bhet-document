# CAT-021 — Office, School & Stationery Supplies — Detailed Catalogue

**Catalogue ID:** CAT-021

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope

CAT-021 covers physical office supplies, school supplies, stationery, writing materials, filing/storage products and educational/office consumables.

## Boundary

- CAT-013 covers academic books, educational books and media.
- CAT-010 covers computers, printers, POS and commercial office equipment.
- CAT-021 covers specialized art/craft supplies.
- CAT-003 covers furniture.
- CAT-019 covers general consumer electronics.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-021-01 | Writing Instruments | Primary catalogue scope for this subcategory. |
| CAT-021-02 | Paper &amp; Notebooks | Primary catalogue scope for this subcategory. |
| CAT-021-03 | Files, Folders &amp; Document Storage | Primary catalogue scope for this subcategory. |
| CAT-021-04 | Office Desk Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-05 | School Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-06 | Art &amp; Drawing School Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-07 | Calculators &amp; Basic Learning Devices | Primary catalogue scope for this subcategory. |
| CAT-021-08 | Labels, Stickers &amp; Identification Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-09 | Envelopes, Packaging &amp; Mailing Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-10 | Printing &amp; Binding Consumables | Primary catalogue scope for this subcategory. |
| CAT-021-11 | Office Organization &amp; Storage Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-12 | Presentation &amp; Teaching Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-13 | Calendar, Planner &amp; Time-Management Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-14 | Business Forms &amp; Administrative Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-15 | School Bags &amp; Student Accessories | Primary catalogue scope for this subcategory. |
| CAT-021-16 | Other Office, School &amp; Stationery Supplies | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| STAT-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| STAT-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| STAT-ATTR-003 | Product Type | select | Yes | Yes | Yes | No |
| STAT-ATTR-004 | Condition | select | Yes | Yes | No | No |
| STAT-ATTR-005 | Material | select | No | Yes | No | Yes |
| STAT-ATTR-006 | Color | select | No | Yes | No | Yes |
| STAT-ATTR-007 | Size / Format | select. | No | No | No | No |
| STAT-ATTR-008 | Quantity | decimal. | No | No | No | No |
| STAT-ATTR-009 | Quantity Unit | select. | No | No | No | No |
| STAT-ATTR-010 | Dimensions | text. | No | No | No | No |
| STAT-ATTR-011 | Paper / Sheet Count | integer. | No | No | No | No |
| STAT-ATTR-012 | Compatibility | text | No | No | No | Yes |
| STAT-ATTR-013 | Reusable | boolean. | No | No | No | No |
| STAT-ATTR-014 | Original Packaging | boolean. | No | No | No | No |
| STAT-ATTR-015 | Accessories Included | multi_select | No | Yes | No | Yes |
| STAT-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Like New, Good, Fair, Used, Damaged.

Quantity Unit: Piece, Set, Pack, Box, Ream, Roll, Dozen, Pair, Other.

Common Formats: A4, A5, A6, Letter, Legal, Executive, B5, Other.

## Subcategory Attributes

### 01 — Writing Instruments

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-01-ATTR-001 | Instrument Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-01-ATTR-002 | Ink Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-01-ATTR-003 | Tip Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-01-ATTR-004 | Ink Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-01-ATTR-005 | Refillable | text | No | No | No | No | Free text |
| CAT-021-01-ATTR-006 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-01-ATTR-007 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-01-ATTR-008 | Intended Use | text | No | No | No | No | Free text |

### 02 — Paper & Notebooks

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-02-ATTR-001 | Paper Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-02-ATTR-002 | Format | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-02-ATTR-003 | GSM | text | No | No | No | No | Free text |
| CAT-021-02-ATTR-004 | Sheet Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-02-ATTR-005 | Page Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-02-ATTR-006 | Ruled / Plain / Grid | text | No | No | No | No | Free text |
| CAT-021-02-ATTR-007 | Binding Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-02-ATTR-008 | Cover Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-02-ATTR-009 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Files, Folders & Document Storage

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-03-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-03-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-03-ATTR-003 | Size / Format | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-03-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-03-ATTR-005 | Closure Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-03-ATTR-006 | Number of Compartments | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-03-ATTR-007 | Label Holder | text | No | No | No | No | Free text |
| CAT-021-03-ATTR-008 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 04 — Office Desk Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-04-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-04-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-04-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-04-ATTR-004 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-04-ATTR-005 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-04-ATTR-006 | Desktop / Portable | boolean | No | Yes | No | No | true / false |
| CAT-021-04-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-021-04-ATTR-008 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 05 — School Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-05-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-05-ATTR-002 | Grade / Age Group | text | No | No | No | No | Free text |
| CAT-021-05-ATTR-003 | Subject | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-05-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-05-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-05-ATTR-006 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-05-ATTR-007 | School Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-05-ATTR-008 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 06 — Art & Drawing School Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-06-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-06-ATTR-002 | Medium | text | No | No | No | No | Free text |
| CAT-021-06-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-06-ATTR-004 | Color Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-06-ATTR-005 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-06-ATTR-006 | Grade / Age Group | text | No | No | No | No | Free text |
| CAT-021-06-ATTR-007 | Student / Artist Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-06-ATTR-008 | Surface Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 07 — Calculators & Basic Learning Devices

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-07-ATTR-001 | Device Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-07-ATTR-002 | Display Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-07-ATTR-003 | Number of Digits | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-07-ATTR-004 | Functions | text | No | No | No | No | Free text |
| CAT-021-07-ATTR-005 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-07-ATTR-006 | Battery Included | boolean | No | Yes | No | No | true / false |
| CAT-021-07-ATTR-007 | Solar Powered | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-07-ATTR-008 | School / Exam Suitability | text | No | No | No | No | Free text |

### 08 — Labels, Stickers & Identification Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-08-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-08-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-08-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-08-ATTR-004 | Shape | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-08-ATTR-005 | Adhesive Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-08-ATTR-006 | Printable | text | No | No | No | No | Free text |
| CAT-021-08-ATTR-007 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-021-08-ATTR-008 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-08-ATTR-009 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 09 — Envelopes, Packaging & Mailing Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-09-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-09-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-09-ATTR-004 | Closure Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-09-ATTR-005 | Window | text | No | No | No | No | Free text |
| CAT-021-09-ATTR-006 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-09-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-021-09-ATTR-008 | Security Feature | text | No | No | No | No | Free text |

### 10 — Printing & Binding Consumables

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-10-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-10-ATTR-002 | Compatible Device | boolean | No | Yes | No | Yes | true / false |
| CAT-021-10-ATTR-003 | Paper / Material Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-10-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-10-ATTR-005 | GSM | text | No | No | No | No | Free text |
| CAT-021-10-ATTR-006 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-10-ATTR-007 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-10-ATTR-008 | Binding Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 11 — Office Organization & Storage Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-11-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-11-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-11-ATTR-003 | Storage Capacity | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-11-ATTR-004 | Number of Compartments | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-11-ATTR-005 | Stackable | text | No | No | No | No | Free text |
| CAT-021-11-ATTR-006 | Desktop / Floor | text | No | No | No | No | Free text |
| CAT-021-11-ATTR-007 | Dimensions | text | No | No | No | No | Free text |
| CAT-021-11-ATTR-008 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 12 — Presentation & Teaching Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-12-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-12-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-12-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-12-ATTR-004 | Surface Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-12-ATTR-005 | Magnetic | text | No | No | No | No | Free text |
| CAT-021-12-ATTR-006 | Writable | text | No | No | No | No | Free text |
| CAT-021-12-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-021-12-ATTR-008 | Mounting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 13 — Calendar, Planner & Time-Management Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-13-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-13-ATTR-002 | Year / Period | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-13-ATTR-003 | Format | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-13-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-13-ATTR-005 | Binding | text | No | No | No | No | Free text |
| CAT-021-13-ATTR-006 | Layout | text | No | No | No | No | Free text |
| CAT-021-13-ATTR-007 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-13-ATTR-008 | Reusable | boolean | No | Yes | No | No | true / false |

### 14 — Business Forms & Administrative Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-14-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-14-ATTR-002 | Form Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-14-ATTR-003 | Format | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-14-ATTR-004 | Paper Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-14-ATTR-005 | Sheet Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-14-ATTR-006 | Numbering | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-14-ATTR-007 | Carbon Copy | text | No | No | No | No | Free text |
| CAT-021-14-ATTR-008 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 15 — School Bags & Student Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-15-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-15-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-15-ATTR-003 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-021-15-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-15-ATTR-005 | Age Group | text | No | No | No | No | Free text |
| CAT-021-15-ATTR-006 | Compartments | text | No | No | No | No | Free text |
| CAT-021-15-ATTR-007 | Laptop / Tablet Compartment | text | No | No | No | No | Free text |
| CAT-021-15-ATTR-008 | Water Resistant | boolean | No | Yes | No | No | true / false |
| CAT-021-15-ATTR-009 | Adjustable | boolean | No | Yes | No | No | true / false |

### 16 — Other Office, School & Stationery Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-021-16-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-16-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-021-16-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-16-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-16-ATTR-005 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-021-16-ATTR-006 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange (limited), Wanted, Free, Offer. Rent and Lease are not ordinary listing types. Service and Job are not applicable.

## Implementation Rules

- Paper format and physical dimensions remain distinct where useful.
- Quantity and quantity unit remain separate.
- Paper GSM remains separate from sheet count.
- Compatibility is explicit for printer, binding and label products.
- Exam suitability is descriptive and is not an official examination-board approval unless independently verified.
- Age/grade suitability is seller-provided unless independently verified.
- Consumables may require expiry or production information where applicable.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Office, School & Stationery Supplies is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.