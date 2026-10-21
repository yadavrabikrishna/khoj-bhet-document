# CAT-019 — Industrial, Machinery & Heavy Equipment — Detailed Catalogue

**Catalogue ID:** CAT-019

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope Boundary

CAT-019 covers heavy machinery, industrial equipment, generators, compressors, material-handling equipment, specialized machinery and heavy-duty production equipment. Construction materials and ordinary construction tools remain CAT-020; commercial office/POS/medical/shop equipment remains CAT-010; road vehicles remain CAT-004; machinery operation, installation, repair and maintenance remain CAT-009.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-019-01 | Excavators &amp; Earthmoving Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-02 | Loaders, Backhoes &amp; Skid Steers | Primary catalogue scope for this subcategory. |
| CAT-019-03 | Cranes &amp; Lifting Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-04 | Forklifts &amp; Material Handling | Primary catalogue scope for this subcategory. |
| CAT-019-05 | Generators &amp; Power Generation | Primary catalogue scope for this subcategory. |
| CAT-019-06 | Compressors &amp; Air Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-07 | Welding &amp; Fabrication Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-08 | Manufacturing &amp; Production Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-09 | Food Processing Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-10 | Packaging &amp; Processing Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-11 | Mining &amp; Quarry Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-12 | Concrete &amp; Construction Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-13 | Agricultural &amp; Forestry Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-14 | Industrial Pumps &amp; Fluid Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-15 | Industrial Electrical &amp; Power Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-16 | Other Industrial &amp; Heavy Equipment | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| IND-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| IND-ATTR-002 | Equipment Name / Model | text | Yes | Yes | Yes | No |
| IND-ATTR-003 | Equipment Type | select | Yes | Yes | Yes | No |
| IND-ATTR-004 | Condition | select | Yes | Yes | No | No |
| IND-ATTR-005 | Manufacture Year | integer. | No | No | No | No |
| IND-ATTR-006 | Operating Hours | decimal. | No | No | No | No |
| IND-ATTR-007 | Capacity | decimal. | No | No | No | No |
| IND-ATTR-008 | Capacity Unit | select. | No | No | No | No |
| IND-ATTR-009 | Power Rating | decimal. | No | No | No | No |
| IND-ATTR-010 | Power Unit | select. | No | No | No | No |
| IND-ATTR-011 | Power Source | select. | No | No | No | No |
| IND-ATTR-012 | Weight | decimal. | No | No | No | No |
| IND-ATTR-013 | Weight Unit | select. | No | No | No | No |
| IND-ATTR-014 | Application | select | No | Yes | No | Yes |
| IND-ATTR-015 | Warranty Status | select. | No | No | No | No |
| IND-ATTR-016 | Accessories / Attachments Included | multi_select | No | Yes | No | Yes |
| IND-ATTR-017 | Service / Maintenance History | text. | No | Yes | Yes | No |
| IND-ATTR-018 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used, For Parts.

Power Unit: W, kW, HP, MW, VA, kVA, Other.

Power Source: Electricity, Diesel, Petrol, LPG, Gas, Battery, Hydraulic, Pneumatic, Manual, Hybrid, Other.

Weight Unit: kg, Ton, lb.

## Subcategory Attributes

### 01 — Excavators & Earthmoving Machinery

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-01-ATTR-001 | Machine Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-01-ATTR-002 | Operating Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-01-ATTR-003 | Engine Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-01-ATTR-004 | Bucket Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-01-ATTR-005 | Maximum Digging Depth | text | No | No | No | No | Free text |
| CAT-019-01-ATTR-006 | Maximum Reach | text | No | No | No | No | Free text |
| CAT-019-01-ATTR-007 | Hydraulic System | text | No | No | No | No | Free text |
| CAT-019-01-ATTR-008 | Track / Wheel Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-01-ATTR-009 | Attachments | text | No | No | No | No | Free text |
| CAT-019-01-ATTR-010 | Hours Used | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 02 — Loaders, Backhoes & Skid Steers

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-02-ATTR-001 | Machine Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-02-ATTR-002 | Operating Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-02-ATTR-003 | Engine Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-02-ATTR-004 | Bucket Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-02-ATTR-005 | Lift Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-02-ATTR-006 | Hydraulic Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-02-ATTR-007 | Drive Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-02-ATTR-008 | Attachment Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-02-ATTR-009 | Hours Used | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 03 — Cranes & Lifting Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-03-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-03-ATTR-002 | Maximum Load Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-03-ATTR-003 | Maximum Lift Height | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-03-ATTR-004 | Boom Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-03-ATTR-005 | Working Radius | text | No | No | No | No | Free text |
| CAT-019-03-ATTR-006 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-03-ATTR-007 | Mobility Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-03-ATTR-008 | Safety Features | text | No | No | No | Yes | Free text |
| CAT-019-03-ATTR-009 | Certification / Inspection Status | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 04 — Forklifts & Material Handling

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-04-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-04-ATTR-002 | Load Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-04-ATTR-003 | Lift Height | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-04-ATTR-004 | Mast Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-04-ATTR-005 | Fork Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-04-ATTR-006 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-04-ATTR-007 | Tire Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-04-ATTR-008 | Turning Radius | text | No | No | No | No | Free text |
| CAT-019-04-ATTR-009 | Operating Hours | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 05 — Generators & Power Generation

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-05-ATTR-001 | Generator Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-05-ATTR-002 | Rated Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-05-ATTR-003 | Maximum Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-05-ATTR-004 | Voltage | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-05-ATTR-005 | Phase | text | No | No | No | No | Free text |
| CAT-019-05-ATTR-006 | Frequency | text | No | No | No | No | Free text |
| CAT-019-05-ATTR-007 | Fuel Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-05-ATTR-008 | Fuel Capacity | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-05-ATTR-009 | Runtime | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-05-ATTR-010 | Automatic / Manual Start | boolean | No | Yes | No | No | true / false |
| CAT-019-05-ATTR-011 | Noise Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 06 — Compressors & Air Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-06-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-06-ATTR-002 | Compressor Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-06-ATTR-003 | Air Flow Rate | text | No | No | No | No | Free text |
| CAT-019-06-ATTR-004 | Pressure | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-06-ATTR-005 | Tank Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-06-ATTR-006 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-06-ATTR-007 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-06-ATTR-008 | Motor Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-06-ATTR-009 | Duty Cycle | text | No | No | No | No | Free text |
| CAT-019-06-ATTR-010 | Noise Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 07 — Welding & Fabrication Machinery

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-07-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-07-ATTR-002 | Welding Process | text | No | No | No | No | Free text |
| CAT-019-07-ATTR-003 | Output Current | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-07-ATTR-004 | Input Voltage | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-07-ATTR-005 | Duty Cycle | text | No | No | No | No | Free text |
| CAT-019-07-ATTR-006 | Material Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-07-ATTR-007 | Wire / Electrode Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-07-ATTR-008 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-07-ATTR-009 | Accessories | text | No | No | No | Yes | Free text |

### 08 — Manufacturing & Production Machinery

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-08-ATTR-001 | Machine Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-08-ATTR-002 | Manufacturing Process | text | No | No | No | No | Free text |
| CAT-019-08-ATTR-003 | Production Capacity | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-08-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-08-ATTR-005 | Automation Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-08-ATTR-006 | Material Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-08-ATTR-007 | Motor Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-08-ATTR-008 | Operating Mode | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-08-ATTR-009 | Control System | text | No | No | No | No | Free text |
| CAT-019-08-ATTR-010 | Dimensions | text | No | No | No | No | Free text |

### 09 — Food Processing Machinery

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-09-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-09-ATTR-002 | Food Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-09-ATTR-003 | Processing Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-09-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-09-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-09-ATTR-006 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-09-ATTR-007 | Motor Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-09-ATTR-008 | Automation Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-09-ATTR-009 | Food Contact Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-09-ATTR-010 | Cleaning Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 10 — Packaging & Processing Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-10-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-10-ATTR-002 | Packaging Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-10-ATTR-003 | Production Speed | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-10-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-10-ATTR-005 | Material Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-10-ATTR-006 | Automation Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-10-ATTR-007 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-10-ATTR-008 | Packaging Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-10-ATTR-009 | Control System | text | No | No | No | No | Free text |

### 11 — Mining & Quarry Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-11-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-11-ATTR-002 | Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-11-ATTR-003 | Processing Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-11-ATTR-004 | Engine / Motor Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-11-ATTR-005 | Operating Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-11-ATTR-006 | Material Handled | text | No | No | No | No | Free text |
| CAT-019-11-ATTR-007 | Mobility | text | No | No | No | No | Free text |
| CAT-019-11-ATTR-008 | Hours Used | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-11-ATTR-009 | Attachments | text | No | No | No | No | Free text |

### 12 — Concrete & Construction Machinery

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-12-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-12-ATTR-002 | Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-12-ATTR-003 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-12-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-12-ATTR-005 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-12-ATTR-006 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-12-ATTR-007 | Mixing / Processing Rate | text | No | No | No | No | Free text |
| CAT-019-12-ATTR-008 | Mobility | text | No | No | No | No | Free text |
| CAT-019-12-ATTR-009 | Batch Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-12-ATTR-010 | Operating Hours | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 13 — Agricultural & Forestry Machinery

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-13-ATTR-001 | Machine Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-13-ATTR-002 | Agricultural / Forestry Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-13-ATTR-003 | Engine Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-13-ATTR-004 | Engine Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-13-ATTR-005 | Working Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-13-ATTR-006 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-13-ATTR-007 | Fuel Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-13-ATTR-008 | Attachment Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-13-ATTR-009 | Operating Hours | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 14 — Industrial Pumps & Fluid Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-14-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-14-ATTR-002 | Pump Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-14-ATTR-003 | Flow Rate | text | No | No | No | No | Free text |
| CAT-019-14-ATTR-004 | Pressure / Head | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-14-ATTR-005 | Inlet / Outlet Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-14-ATTR-006 | Fluid Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-14-ATTR-007 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-14-ATTR-008 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-14-ATTR-009 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-14-ATTR-010 | Temperature Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 15 — Industrial Electrical & Power Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-15-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-15-ATTR-002 | Rated Power | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-15-ATTR-003 | Voltage | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-15-ATTR-004 | Current | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-15-ATTR-005 | Phase | text | No | No | No | No | Free text |
| CAT-019-15-ATTR-006 | Frequency | text | No | No | No | No | Free text |
| CAT-019-15-ATTR-007 | Input / Output | text | No | No | No | No | Free text |
| CAT-019-15-ATTR-008 | Protection Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-15-ATTR-009 | Installation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-15-ATTR-010 | Certification | text | No | No | No | No | Free text |

### 16 — Other Industrial & Heavy Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-019-16-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-16-ATTR-002 | Industrial Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-16-ATTR-003 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-019-16-ATTR-004 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-16-ATTR-005 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-16-ATTR-006 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-16-ATTR-007 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-019-16-ATTR-008 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange, Wanted, Free (limited), Rent, Lease, Offer. Service and Job are not applicable.

## Boundary Rules

- Construction materials belong to CAT-020.
- Ordinary hand/power tools belong to CAT-020.
- Commercial office/POS/medical/shop equipment belongs to CAT-010.
- Agricultural machinery may belong to CAT-019 when heavy/industrial; simpler agricultural equipment is classified according to primary commercial use.
- Road vehicles belong to CAT-004.
- Machinery operation, installation, repair and maintenance services belong to CAT-009.

## Implementation Rules

- Capacity and capacity unit remain separate.
- Power rating and power unit remain separate.
- Operating hours are distinct from manufacture year.
- Service/maintenance history is seller-provided unless independently verified.
- Safety certification, inspection and compliance claims are not automatically verified.
- Heavy machinery supports attachments as multi-value data.
- Rental/lease is supported for appropriate equipment.
- Used equipment should expose relevant operational/maintenance information where available.
- Exact serial numbers and other sensitive identifiers are not public listing attributes.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Industrial & Heavy Equipment is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.