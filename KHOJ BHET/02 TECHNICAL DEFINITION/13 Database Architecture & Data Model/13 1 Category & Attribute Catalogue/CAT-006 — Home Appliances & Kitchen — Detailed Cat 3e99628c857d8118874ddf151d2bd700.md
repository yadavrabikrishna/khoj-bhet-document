# CAT-006 — Home Appliances & Kitchen — Detailed Catalogue

**Catalogue ID:** CAT-006

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-006-01 | Refrigerator &amp; Freezer | Primary catalogue scope for this subcategory. |
| CAT-006-02 | Washing Machine | Primary catalogue scope for this subcategory. |
| CAT-006-03 | Air Conditioner | Primary catalogue scope for this subcategory. |
| CAT-006-04 | Microwave &amp; Oven | Primary catalogue scope for this subcategory. |
| CAT-006-05 | Rice Cooker &amp; Electric Cooker | Primary catalogue scope for this subcategory. |
| CAT-006-06 | Water Heater / Geyser | Primary catalogue scope for this subcategory. |
| CAT-006-07 | Water Purifier &amp; Filter | Primary catalogue scope for this subcategory. |
| CAT-006-08 | Kitchen Appliances | Primary catalogue scope for this subcategory. |
| CAT-006-09 | Vacuum Cleaner | Primary catalogue scope for this subcategory. |
| CAT-006-10 | Fan &amp; Air Circulation | Primary catalogue scope for this subcategory. |
| CAT-006-11 | Small Home Appliances | Primary catalogue scope for this subcategory. |
| CAT-006-12 | Solar / Inverter Appliances | Primary catalogue scope for this subcategory. |
| CAT-006-13 | Other Home Appliances | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| HOME-ATTR-001 | Brand | text. | No | Yes | Yes | No |
| HOME-ATTR-002 | Model | text. | No | Yes | Yes | No |
| HOME-ATTR-003 | Condition | select | Yes | Yes | No | No |
| HOME-ATTR-004 | Purchase Year | integer. | No | No | No | No |
| HOME-ATTR-005 | Warranty Status | select. | No | No | No | No |
| HOME-ATTR-006 | Warranty Expiry | date. | No | No | No | No |
| HOME-ATTR-007 | Power Source | select. | No | No | No | No |
| HOME-ATTR-008 | Power Consumption | decimal. | No | No | No | No |
| HOME-ATTR-009 | Power Unit | select. | No | No | No | No |
| HOME-ATTR-010 | Capacity | decimal. | No | No | No | No |
| HOME-ATTR-011 | Capacity Unit | select. | No | No | No | No |
| HOME-ATTR-012 | Color | select. | No | No | No | No |
| HOME-ATTR-013 | Energy Rating | select. | No | No | No | No |
| HOME-ATTR-014 | Remote Included | boolean. | No | No | No | No |
| HOME-ATTR-015 | Original Packaging | boolean. | No | No | No | No |
| HOME-ATTR-016 | Accessories Included | multi_select | No | Yes | No | Yes |
| HOME-ATTR-017 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Warranty Status: None, Active, Expired, Seller Warranty, Manufacturer Warranty.

Power Source: Electricity, Battery, Solar, Gas, LPG, Induction, Hybrid, Other.

Energy Rating: 1 Star, 2 Star, 3 Star, 4 Star, 5 Star, Other.

## Subcategory Attributes

### 01 — efrigerator & Freezer

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-01-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-01-ATTR-002 | Door Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-01-ATTR-003 | Refrigerator Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-01-ATTR-004 | Freezer Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-01-ATTR-005 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-01-ATTR-006 | Cooling Technology | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-01-ATTR-007 | Inverter | boolean | No | Yes | No | No | true / false |
| CAT-006-01-ATTR-008 | Ice Maker | text | No | No | No | No | Free text |
| CAT-006-01-ATTR-009 | Water Dispenser | text | No | No | No | No | Free text |

### 02 — Washing Machine

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-02-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-02-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-02-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-02-ATTR-004 | Automatic Type | boolean | No | Yes | Yes | No | true / false |
| CAT-006-02-ATTR-005 | Spin Speed | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-02-ATTR-006 | Dryer | text | No | No | No | No | Free text |
| CAT-006-02-ATTR-007 | Inverter Motor | boolean | No | Yes | No | No | true / false |
| CAT-006-02-ATTR-008 | Loading Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Air Conditioner

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-03-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-03-ATTR-002 | Cooling Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-03-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-03-ATTR-004 | Inverter | boolean | No | Yes | No | No | true / false |
| CAT-006-03-ATTR-005 | Energy Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-03-ATTR-006 | Room Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-03-ATTR-007 | Refrigerant | text | No | No | No | No | Free text |
| CAT-006-03-ATTR-008 | Heating | text | No | No | No | No | Free text |

### 04 — Microwave & Oven

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-04-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-04-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-04-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-04-ATTR-004 | Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-04-ATTR-005 | Power Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-04-ATTR-006 | Convection | text | No | No | No | No | Free text |
| CAT-006-04-ATTR-007 | Grill | text | No | No | No | No | Free text |
| CAT-006-04-ATTR-008 | Rotisserie | text | No | No | No | No | Free text |
| CAT-006-04-ATTR-009 | Digital Control | boolean | No | Yes | No | No | true / false |

### 05 — Rice Cooker & Electric Cooker

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-05-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-05-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-05-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-05-ATTR-004 | Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-05-ATTR-005 | Power Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-05-ATTR-006 | Keep Warm | text | No | No | No | No | Free text |
| CAT-006-05-ATTR-007 | Timer | text | No | No | No | No | Free text |
| CAT-006-05-ATTR-008 | Inner Pot Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 06 — Water Heater / Geyser

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-06-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-06-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-06-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-06-ATTR-004 | Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-06-ATTR-005 | Heating Element | text | No | No | No | No | Free text |
| CAT-006-06-ATTR-006 | Temperature Control | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-06-ATTR-007 | Safety Features | text | No | No | No | Yes | Free text |

### 07 — Water Purifier & Filter

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-07-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-07-ATTR-002 | Filtration Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-07-ATTR-003 | Storage Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-07-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-07-ATTR-005 | Purification Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-07-ATTR-006 | UV/RO/UF | text | No | No | No | No | Free text |
| CAT-006-07-ATTR-007 | Filter Replacement | text | No | No | No | No | Free text |

### 08 — Kitchen Appliances

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-08-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-08-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-08-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-08-ATTR-004 | Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-08-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-08-ATTR-006 | Functions | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-007 | Accessories. Types include blender | text | No | No | Yes | Yes | Free text |
| CAT-006-08-ATTR-008 | mixer grinder | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-009 | juicer | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-010 | food processor | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-011 | kettle | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-012 | toaster | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-013 | sandwich maker | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-014 | coffee maker | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-015 | hand blender | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-016 | chopper | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-017 | air fryer | text | No | No | No | No | Free text |
| CAT-006-08-ATTR-018 | electric grill | boolean | No | Yes | No | No | true / false |
| CAT-006-08-ATTR-019 | other | text | No | No | No | No | Free text |

### 09 — Vacuum Cleaner

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-09-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-09-ATTR-002 | Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-09-ATTR-003 | Power Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-09-ATTR-004 | Dust Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-09-ATTR-005 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-09-ATTR-006 | Cordless | boolean | No | Yes | No | No | true / false |
| CAT-006-09-ATTR-007 | Wet/Dry | boolean | No | Yes | No | No | true / false |
| CAT-006-09-ATTR-008 | HEPA | boolean | No | Yes | No | No | true / false |
| CAT-006-09-ATTR-009 | Attachments | text | No | No | No | No | Free text |

### 10 — Fan & Air Circulation

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-10-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-10-ATTR-002 | Blade Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-10-ATTR-003 | Sweep Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-10-ATTR-004 | Sweep Size Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-10-ATTR-005 | Speed Levels | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-10-ATTR-006 | Remote | boolean | No | Yes | No | No | true / false |
| CAT-006-10-ATTR-007 | Oscillation | text | No | No | No | No | Free text |
| CAT-006-10-ATTR-008 | Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 11 — Small Home Appliances

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-11-ATTR-001 | Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-11-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-11-ATTR-003 | Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-11-ATTR-004 | Key Functions | text | No | No | No | No | Free text |

### 12 — Solar / Inverter Appliances

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-12-ATTR-001 | Appliance Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-12-ATTR-002 | System Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-12-ATTR-003 | Power Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-006-12-ATTR-004 | Power Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-12-ATTR-005 | Battery Capacity | boolean | No | Yes | No | No | true / false |
| CAT-006-12-ATTR-006 | Battery Unit | boolean | No | Yes | No | No | true / false |
| CAT-006-12-ATTR-007 | Backup Time | text | No | No | No | No | Free text |
| CAT-006-12-ATTR-008 | Solar Compatible | boolean | No | Yes | No | Yes | true / false |
| CAT-006-12-ATTR-009 | Inverter Type | boolean | No | Yes | Yes | No | true / false |

### 13 — Other Home Appliances

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-006-13-ATTR-001 | Common attributes plus Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-006-13-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-006-13-ATTR-003 | Key Features | text | No | No | No | Yes | Free text |

## Listing Types

Sale, Exchange, Wanted. Rent, Lease, Job, and Service are not initially exposed.

## Implementation Rules

- Common attributes inherit into applicable subcategories.
- Measurements require explicit units.
- Power consumption and energy rating are separate attributes and must not be conflated.
- Multi-value attributes create multiple attribute rows.
- Single-value attributes allow at most one value.
- Option-backed values must match approved catalogue options.
- Required/filterable/searchable/multi-value flags are authoritative.
- Boolean flags are authoritative.
- Other is a controlled fallback.
- Subcategory-specific technical attributes remain scoped to the relevant appliance type.

## Phase 3 Audit Correction

Television and general displays belong to CAT-002. CAT-006 remains the household-appliance domain; ironing and garment-care appliances are included here.

## Catalogue-Wide Effective Flag Policy — 2026-10-21

Apply the parent catalogue §46 as the effective flag policy across all 25 categories: Required = No by default; Filterable = Yes and Searchable = Yes by default. Search must respect the attribute data type (text matching for text, normalized exact matching for options/booleans, typed comparisons for numeric/date values). This policy supersedes legacy Filterable = No / Searchable = No cells in this page unless an explicit, documented technical exception is approved. Preserve each attribute's explicit type, multi-value behavior, and approved option set.