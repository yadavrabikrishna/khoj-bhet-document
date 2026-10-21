# CAT-010 — Business, Office & Commercial Equipment — Detailed Catalogue

**Catalogue ID:** CAT-010

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-010-01 | Computers &amp; Office Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-02 | Printers, Scanners &amp; Copiers | Primary catalogue scope for this subcategory. |
| CAT-010-03 | Networking &amp; Communication Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-04 | POS &amp; Billing Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-05 | Security &amp; Surveillance Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-06 | Commercial Kitchen Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-07 | Restaurant &amp; Hospitality Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-08 | Tools &amp; Workshop Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-09 | Medical &amp; Laboratory Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-10 | Shop &amp; Display Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-11 | Packaging &amp; Printing Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-12 | Office Furniture &amp; Fixtures | Primary catalogue scope for this subcategory. |
| CAT-010-13 | Solar, Power &amp; Electrical Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-14 | Other Commercial Equipment | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| COMM-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| COMM-ATTR-002 | Model / Product Name | text | Yes | Yes | Yes | No |
| COMM-ATTR-003 | Equipment Type | select | Yes | Yes | Yes | No |
| COMM-ATTR-004 | Condition | select | Yes | Yes | No | No |
| COMM-ATTR-005 | Purchase Year | integer. | No | No | No | No |
| COMM-ATTR-006 | Material | select. | No | No | No | No |
| COMM-ATTR-007 | Capacity | decimal. | No | No | No | No |
| COMM-ATTR-008 | Capacity Unit | select. | No | No | No | No |
| COMM-ATTR-009 | Power Rating | decimal. | No | No | No | No |
| COMM-ATTR-010 | Power Unit | select. | No | No | No | No |
| COMM-ATTR-011 | Power Source | select. | No | No | No | No |
| COMM-ATTR-012 | Dimensions | text. | No | No | No | No |
| COMM-ATTR-013 | Weight | decimal. | No | No | No | No |
| COMM-ATTR-014 | Weight Unit | select. | No | No | No | No |
| COMM-ATTR-015 | Warranty Status | select. | No | No | No | No |
| COMM-ATTR-016 | Warranty Expiry | date. | No | No | No | No |
| COMM-ATTR-017 | Accessories Included | multi_select | No | Yes | No | Yes |
| COMM-ATTR-018 | Installation Included | boolean. | No | No | No | No |
| COMM-ATTR-019 | Service / Maintenance Available | boolean. | No | Yes | Yes | No |
| COMM-ATTR-020 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Power Source: Electricity, Battery, Solar, Diesel, Petrol, LPG, Gas, Manual, Hybrid, Other.

Warranty Status: None, Active, Expired, Seller Warranty, Manufacturer Warranty.

Power Unit: W, kW, HP, VA, kVA, Other.

## Subcategory Attributes

### 01 — omputers & Office Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-01-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-01-ATTR-002 | Processor | text | No | No | No | No | Free text |
| CAT-010-01-ATTR-003 | RAM | text | No | No | No | No | Free text |
| CAT-010-01-ATTR-004 | Storage Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-01-ATTR-005 | Storage Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-01-ATTR-006 | Operating System | text | No | No | No | No | Free text |
| CAT-010-01-ATTR-007 | Screen Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-01-ATTR-008 | Connectivity | text | No | No | No | No | Free text |
| CAT-010-01-ATTR-009 | Business Use Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 02 — Printers, Scanners & Copiers

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-02-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-02-ATTR-002 | Print Technology | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-02-ATTR-003 | Color / Mono | text | No | No | No | No | Free text |
| CAT-010-02-ATTR-004 | Print Speed | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-02-ATTR-005 | Paper Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-02-ATTR-006 | Duplex | text | No | No | No | No | Free text |
| CAT-010-02-ATTR-007 | Network Printing | text | No | No | No | No | Free text |
| CAT-010-02-ATTR-008 | Scan Resolution | text | No | No | No | No | Free text |
| CAT-010-02-ATTR-009 | Monthly Duty Cycle | text | No | No | No | No | Free text |

### 03 — Networking & Communication

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-03-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-03-ATTR-002 | Network Standard | text | No | No | No | No | Free text |
| CAT-010-03-ATTR-003 | Number of Ports | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-03-ATTR-004 | Port Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-03-ATTR-005 | Wireless Standard | boolean | No | Yes | No | No | true / false |
| CAT-010-03-ATTR-006 | Speed | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-03-ATTR-007 | PoE Support | text | No | No | No | No | Free text |
| CAT-010-03-ATTR-008 | Managed / Unmanaged | text | No | No | No | No | Free text |
| CAT-010-03-ATTR-009 | SIM Support | text | No | No | No | No | Free text |

### 04 — POS & Billing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-04-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-04-ATTR-002 | POS Software Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-04-ATTR-003 | Receipt Printer | text | No | No | No | No | Free text |
| CAT-010-04-ATTR-004 | Barcode Scanner | text | No | No | No | No | Free text |
| CAT-010-04-ATTR-005 | Cash Drawer | text | No | No | No | No | Free text |
| CAT-010-04-ATTR-006 | Display Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-04-ATTR-007 | Touchscreen | boolean | No | Yes | No | No | true / false |
| CAT-010-04-ATTR-008 | Connectivity | text | No | No | No | No | Free text |
| CAT-010-04-ATTR-009 | Operating System | text | No | No | No | No | Free text |

### 05 — Security & Surveillance

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-05-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-05-ATTR-002 | Camera Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-05-ATTR-003 | Resolution | text | No | No | No | No | Free text |
| CAT-010-05-ATTR-004 | Night Vision | text | No | No | No | No | Free text |
| CAT-010-05-ATTR-005 | Storage Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-05-ATTR-006 | Storage Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-05-ATTR-007 | Number of Channels | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-05-ATTR-008 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-010-05-ATTR-009 | Motion Detection | text | No | No | No | No | Free text |
| CAT-010-05-ATTR-010 | Audio Support | text | No | No | No | No | Free text |

### 06 — Commercial Kitchen

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-06-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-06-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-06-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-06-ATTR-004 | Fuel Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-06-ATTR-005 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-06-ATTR-006 | Temperature Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-06-ATTR-007 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-06-ATTR-008 | Number of Burners / Sections | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-06-ATTR-009 | Commercial Grade | boolean | No | Yes | No | No | true / false |

### 07 — Restaurant & Hospitality

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-07-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-07-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-07-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-07-ATTR-004 | Number of Persons / Units | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-07-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-07-ATTR-006 | Commercial Grade | boolean | No | Yes | No | No | true / false |
| CAT-010-07-ATTR-007 | Installation Required | boolean | No | Yes | No | No | true / false |
| CAT-010-07-ATTR-008 | Service Availability | text | No | No | No | No | Free text |

### 08 — Tools & Workshop

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-08-ATTR-001 | Tool Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-08-ATTR-002 | Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-08-ATTR-003 | Power Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-08-ATTR-004 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-08-ATTR-005 | Voltage | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-08-ATTR-006 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-08-ATTR-007 | Compatible Accessories | boolean | No | Yes | No | Yes | true / false |
| CAT-010-08-ATTR-008 | Professional / Consumer Grade | boolean | No | Yes | No | No | true / false |

### 09 — Medical & Laboratory

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-09-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-09-ATTR-002 | Medical / Laboratory Use | text | No | No | No | No | Free text |
| CAT-010-09-ATTR-003 | Manufacturer | text | No | No | No | No | Free text |
| CAT-010-09-ATTR-004 | Model | text | No | No | Yes | No | Free text |
| CAT-010-09-ATTR-005 | Measurement Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-09-ATTR-006 | Accuracy | text | No | No | No | No | Free text |
| CAT-010-09-ATTR-007 | Certification | text | No | No | No | No | Free text |
| CAT-010-09-ATTR-008 | Calibration Available | boolean | No | Yes | No | No | true / false |
| CAT-010-09-ATTR-009 | Consumables Required | boolean | No | Yes | No | No | true / false |

### 10 — Shop & Display

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-10-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-10-ATTR-002 | Display Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-10-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-10-ATTR-004 | Dimensions | text | No | No | No | No | Free text |
| CAT-010-10-ATTR-005 | Shelving | text | No | No | No | No | Free text |
| CAT-010-10-ATTR-006 | Number of Shelves | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-10-ATTR-007 | Lighting Included | boolean | No | Yes | No | No | true / false |
| CAT-010-10-ATTR-008 | Lockable | boolean | No | Yes | No | No | true / false |
| CAT-010-10-ATTR-009 | Portable | boolean | No | Yes | No | No | true / false |

### 11 — Packaging & Printing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-11-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-11-ATTR-002 | Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-11-ATTR-003 | Production Speed | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-11-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-11-ATTR-005 | Material Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-11-ATTR-006 | Automation Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-11-ATTR-007 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-11-ATTR-008 | Consumables | text | No | No | No | No | Free text |

### 12 — Office Furniture & Fixtures

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-12-ATTR-001 | Furniture Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-12-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-12-ATTR-003 | Seating Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-12-ATTR-004 | Number of Units | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-12-ATTR-005 | Dimensions | text | No | No | No | No | Free text |
| CAT-010-12-ATTR-006 | Storage Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-12-ATTR-007 | Assembly Required | boolean | No | Yes | No | No | true / false |
| CAT-010-12-ATTR-008 | Commercial Grade | boolean | No | Yes | No | No | true / false |

### 13 — Solar, Power & Electrical

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-13-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-13-ATTR-002 | Rated Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-13-ATTR-003 | Power Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-13-ATTR-004 | Voltage | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-010-13-ATTR-005 | Battery Capacity | boolean | No | Yes | No | No | true / false |
| CAT-010-13-ATTR-006 | Battery Unit | boolean | No | Yes | No | No | true / false |
| CAT-010-13-ATTR-007 | Phase | text | No | No | No | No | Free text |
| CAT-010-13-ATTR-008 | Solar Compatible | boolean | No | Yes | No | Yes | true / false |
| CAT-010-13-ATTR-009 | Inverter Type | boolean | No | Yes | Yes | No | true / false |
| CAT-010-13-ATTR-010 | Backup Time | text | No | No | No | No | Free text |

### 14 — Other Commercial Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-010-14-ATTR-001 | Common attributes plus Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-14-ATTR-002 | Commercial Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-010-14-ATTR-003 | Intended Use | text | No | No | No | No | Free text |
| CAT-010-14-ATTR-004 | Key Features | text | No | No | No | Yes | Free text |

## Listing Types

Sale, Exchange, Wanted, Rent, Lease, Free, and Offer where commercially appropriate. Service and Job are not applicable.

## Implementation Rules

- Common attributes inherit into applicable commercial-equipment subcategories.
- Technical attributes remain scoped to their equipment type.
- Capacity, power, voltage, weight, and other measurements require explicit units.
- Multi-value attributes create separate attribute rows; single-value attributes allow at most one value.
- Equipment condition is mandatory.
- Safety, certification, calibration, and compliance claims remain seller-provided unless independently verified.
- Rental and lease are listing types, not separate categories.
- Used industrial equipment may include maintenance/service information.
- Other Commercial Equipment is the controlled fallback.
- Business listings may be published through authorized business members.
- All listings follow the standard review-before-publication lifecycle.