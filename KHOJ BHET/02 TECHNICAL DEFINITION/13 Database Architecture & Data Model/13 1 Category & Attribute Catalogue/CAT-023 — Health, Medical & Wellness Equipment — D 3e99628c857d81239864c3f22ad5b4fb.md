# CAT-023 — Health, Medical & Wellness Equipment — Detailed Catalogue

**Catalogue ID:** CAT-023

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope

CAT-023 covers physical non-drug health, medical, diagnostic, rehabilitation, mobility and wellness equipment at consumer, household, small-provider or personal-use level.

## Boundary

- CAT-015 covers consumer health, beauty and personal-care products.
- CAT-009 covers doctors, clinics, therapists, nursing, fitness/wellness and other services.
- CAT-010 covers commercial medical/laboratory equipment.
- CAT-007 covers ordinary sports/fitness equipment.
- CAT-019 covers general consumer electronics.
- CAT-022 covers industrial/heavy machinery.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-023-01 | Blood Pressure &amp; Vital Signs Monitors | Primary catalogue scope for this subcategory. |
| CAT-023-02 | Thermometers &amp; Temperature Monitoring | Primary catalogue scope for this subcategory. |
| CAT-023-03 | Blood Glucose &amp; Diabetes Monitoring | Primary catalogue scope for this subcategory. |
| CAT-023-04 | Pulse Oximeters &amp; Respiratory Monitoring | Primary catalogue scope for this subcategory. |
| CAT-023-05 | Diagnostic &amp; Examination Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-06 | Mobility Aids &amp; Walking Support | Primary catalogue scope for this subcategory. |
| CAT-023-07 | Wheelchairs &amp; Mobility Vehicles | Primary catalogue scope for this subcategory. |
| CAT-023-08 | Patient Beds &amp; Home Care Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-09 | Physiotherapy &amp; Rehabilitation Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-10 | Respiratory &amp; Oxygen Support Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-11 | Orthopedic &amp; Support Products | Primary catalogue scope for this subcategory. |
| CAT-023-12 | Home Health &amp; Recovery Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-13 | First Aid &amp; Emergency Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-14 | Medical Storage &amp; Care Supplies | Primary catalogue scope for this subcategory. |
| CAT-023-15 | Wellness &amp; Recovery Devices | Primary catalogue scope for this subcategory. |
| CAT-023-16 | Other Health, Medical &amp; Wellness Equipment | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| MED-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| MED-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| MED-ATTR-003 | Equipment Type | select | Yes | Yes | Yes | No |
| MED-ATTR-004 | Condition | select. | No | No | No | No |
| MED-ATTR-005 | Intended Use | select. | No | No | No | No |
| MED-ATTR-006 | Intended User Group | select | No | Yes | No | Yes |
| MED-ATTR-007 | Material | select | No | Yes | No | Yes |
| MED-ATTR-008 | Size / Dimensions | text. | No | No | No | No |
| MED-ATTR-009 | Weight | decimal. | No | No | No | No |
| MED-ATTR-010 | Weight Unit | select. | No | No | No | No |
| MED-ATTR-011 | Capacity | decimal. | No | No | No | No |
| MED-ATTR-012 | Capacity Unit | select. | No | No | No | No |
| MED-ATTR-013 | Power Source | select. | No | No | No | No |
| MED-ATTR-014 | Warranty Status | select. | No | No | No | No |
| MED-ATTR-015 | Certification / Compliance | text | No | No | No | Yes |
| MED-ATTR-016 | Accessories Included | multi_select | No | Yes | No | Yes |
| MED-ATTR-017 | Purchase Year | integer. | No | No | No | No |
| MED-ATTR-018 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Open Box, Like New, Good, Fair, Used, Needs Repair, Refurbished.

Intended User Group: Infant, Child, Adult, Senior, Patient, Caregiver, Professional, General Household, Other.

Power Source: AC, Battery, Rechargeable Battery, USB, Manual, Solar, Compressed Air, Oxygen, Hydraulic, Other.

Weight Unit: g, kg, lb, Other.

Capacity Unit: ml, L, kg, Person, Patient, Other.

## Subcategory Attributes

### 01 — Blood Pressure & Vital Signs Monitors

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-01-ATTR-001 | Device Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-01-ATTR-002 | Measurement Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-01-ATTR-003 | Measurement Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-01-ATTR-004 | Accuracy | text | No | No | No | No | Free text |
| CAT-023-01-ATTR-005 | Cuff Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-01-ATTR-006 | Cuff Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-01-ATTR-007 | Display Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-01-ATTR-008 | Memory / Data Storage | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-01-ATTR-009 | Connectivity | text | No | No | No | No | Free text |
| CAT-023-01-ATTR-010 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 02 — Thermometers & Temperature Monitoring

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-02-ATTR-001 | Device Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-02-ATTR-002 | Measurement Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-02-ATTR-003 | Measurement Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-02-ATTR-004 | Accuracy | text | No | No | No | No | Free text |
| CAT-023-02-ATTR-005 | Measurement Location | text | No | No | No | No | Free text |
| CAT-023-02-ATTR-006 | Display | text | No | No | No | No | Free text |
| CAT-023-02-ATTR-007 | Memory | text | No | No | No | No | Free text |
| CAT-023-02-ATTR-008 | Battery Type | boolean | No | Yes | Yes | No | true / false |
| CAT-023-02-ATTR-009 | Measurement Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Blood Glucose & Diabetes Monitoring

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-03-ATTR-001 | Device Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-03-ATTR-002 | Measurement Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-03-ATTR-003 | Measurement Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-03-ATTR-004 | Test Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-03-ATTR-005 | Sample Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-03-ATTR-006 | Memory | text | No | No | No | No | Free text |
| CAT-023-03-ATTR-007 | Connectivity | text | No | No | No | No | Free text |
| CAT-023-03-ATTR-008 | Battery Type | boolean | No | Yes | Yes | No | true / false |
| CAT-023-03-ATTR-009 | Compatible Consumables | boolean | No | Yes | No | Yes | true / false |
| CAT-023-03-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 04 — Pulse Oximeters & Respiratory Monitoring

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-04-ATTR-001 | Device Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-04-ATTR-002 | Measurement Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-04-ATTR-003 | Measurement Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-04-ATTR-004 | Accuracy | text | No | No | No | No | Free text |
| CAT-023-04-ATTR-005 | Display | text | No | No | No | No | Free text |
| CAT-023-04-ATTR-006 | Sensor Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-04-ATTR-007 | Battery Type | boolean | No | Yes | Yes | No | true / false |
| CAT-023-04-ATTR-008 | Alarm | text | No | No | No | No | Free text |
| CAT-023-04-ATTR-009 | Memory | text | No | No | No | No | Free text |
| CAT-023-04-ATTR-010 | Portability | text | No | No | No | No | Free text |

### 05 — Diagnostic & Examination Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-05-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-05-ATTR-002 | Measurement Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-05-ATTR-003 | Measurement Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-05-ATTR-004 | Accuracy | text | No | No | No | No | Free text |
| CAT-023-05-ATTR-005 | Intended Clinical / Household Use | text | No | No | No | No | Free text |
| CAT-023-05-ATTR-006 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-05-ATTR-007 | Display | text | No | No | No | No | Free text |
| CAT-023-05-ATTR-008 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-023-05-ATTR-009 | Accessories | text | No | No | No | Yes | Free text |
| CAT-023-05-ATTR-010 | Calibration Status | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 06 — Mobility Aids & Walking Support

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-06-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-06-ATTR-002 | Support Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-06-ATTR-003 | Height Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-06-ATTR-004 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-06-ATTR-005 | Weight Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-06-ATTR-006 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-023-06-ATTR-007 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-023-06-ATTR-008 | Wheel Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-06-ATTR-009 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-06-ATTR-010 | Non-Slip Feature | boolean | No | Yes | No | No | true / false |

### 07 — Wheelchairs & Mobility Vehicles

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-07-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-07-ATTR-002 | Manual / Electric | boolean | No | Yes | No | No | true / false |
| CAT-023-07-ATTR-003 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-07-ATTR-004 | Seat Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-07-ATTR-005 | Seat Height | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-07-ATTR-006 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-023-07-ATTR-007 | Wheel Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-07-ATTR-008 | Battery Type | boolean | No | Yes | Yes | No | true / false |
| CAT-023-07-ATTR-009 | Battery Range | boolean | No | Yes | No | No | true / false |
| CAT-023-07-ATTR-010 | Maximum Speed | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 08 — Patient Beds & Home Care Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-08-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-08-ATTR-002 | Bed / Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-08-ATTR-003 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-08-ATTR-004 | Dimensions | text | No | No | No | No | Free text |
| CAT-023-08-ATTR-005 | Adjustable Sections | boolean | No | Yes | No | No | true / false |
| CAT-023-08-ATTR-006 | Manual / Electric | boolean | No | Yes | No | No | true / false |
| CAT-023-08-ATTR-007 | Side Rails | text | No | No | No | No | Free text |
| CAT-023-08-ATTR-008 | Mattress Included | boolean | No | Yes | No | No | true / false |
| CAT-023-08-ATTR-009 | Wheels / Locking | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-08-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 09 — Physiotherapy & Rehabilitation Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-09-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-09-ATTR-002 | Therapy Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-09-ATTR-003 | Intended Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-09-ATTR-004 | Resistance / Load | text | No | No | No | No | Free text |
| CAT-023-09-ATTR-005 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-023-09-ATTR-006 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-09-ATTR-007 | Portability | text | No | No | No | No | Free text |
| CAT-023-09-ATTR-008 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-09-ATTR-009 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-09-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 10 — Respiratory & Oxygen Support Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-10-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-10-ATTR-002 | Oxygen / Respiratory Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-10-ATTR-003 | Flow Rate | text | No | No | No | No | Free text |
| CAT-023-10-ATTR-004 | Flow Rate Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-10-ATTR-005 | Oxygen Concentration | text | No | No | No | No | Free text |
| CAT-023-10-ATTR-006 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-10-ATTR-007 | Battery Backup | boolean | No | Yes | No | No | true / false |
| CAT-023-10-ATTR-008 | Portability | text | No | No | No | No | Free text |
| CAT-023-10-ATTR-009 | Noise Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-10-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 11 — Orthopedic & Support Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-11-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-11-ATTR-002 | Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-11-ATTR-003 | Support Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-11-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-11-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-11-ATTR-006 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-023-11-ATTR-007 | Compression Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-11-ATTR-008 | Laterality | text | No | No | No | No | Free text |
| CAT-023-11-ATTR-009 | Intended Use | text | No | No | No | No | Free text |
| CAT-023-11-ATTR-010 | Reusable | boolean | No | Yes | No | No | true / false |

### 12 — Home Health & Recovery Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-12-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-12-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-023-12-ATTR-003 | Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-12-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-12-ATTR-005 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-12-ATTR-006 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-023-12-ATTR-007 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-023-12-ATTR-008 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-12-ATTR-009 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-12-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 13 — First Aid & Emergency Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-13-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-13-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-023-13-ATTR-003 | Contents | text | No | No | No | Yes | Free text |
| CAT-023-13-ATTR-004 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-13-ATTR-005 | Sterile / Non-Sterile | text | No | No | No | No | Free text |
| CAT-023-13-ATTR-006 | Reusable / Disposable | boolean | No | Yes | No | No | true / false |
| CAT-023-13-ATTR-007 | Expiry Date | text | No | No | No | No | Free text |
| CAT-023-13-ATTR-008 | Packaging | text | No | No | No | No | Free text |
| CAT-023-13-ATTR-009 | Certification / Compliance | text | No | No | No | No | Free text |

### 14 — Medical Storage & Care Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-14-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-14-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-023-14-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-14-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-14-ATTR-005 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-14-ATTR-006 | Number of Compartments | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-14-ATTR-007 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-023-14-ATTR-008 | Lockable | boolean | No | Yes | No | No | true / false |
| CAT-023-14-ATTR-009 | Cleaning Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-14-ATTR-010 | Dimensions | text | No | No | No | No | Free text |

### 15 — Wellness & Recovery Devices

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-15-ATTR-001 | Device Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-15-ATTR-002 | Intended Wellness Use | text | No | No | No | No | Free text |
| CAT-023-15-ATTR-003 | Body Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-023-15-ATTR-004 | Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-15-ATTR-005 | Intensity Levels | text | No | No | No | No | Free text |
| CAT-023-15-ATTR-006 | Heat / Cold Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-15-ATTR-007 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-15-ATTR-008 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-023-15-ATTR-009 | Timer | text | No | No | No | No | Free text |
| CAT-023-15-ATTR-010 | Accessories | text | No | No | No | Yes | Free text |

### 16 — Other Health, Medical & Wellness Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-023-16-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-16-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-023-16-ATTR-003 | Intended User | text | No | No | No | No | Free text |
| CAT-023-16-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-16-ATTR-005 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-16-ATTR-006 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-023-16-ATTR-007 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange (limited), Wanted, Free (limited), Rent (limited), Lease (limited), Offer. Service and Job are not applicable.

## Safety & Boundary Rules

- Prescription medicines, controlled medicines and other regulated drugs are not ordinary marketplace products in CAT-023.
- Medical services remain CAT-009.
- Large institutional/commercial medical and laboratory equipment remains CAT-010.
- Ordinary fitness equipment remains CAT-007.
- Consumer personal-care health products remain CAT-015.
- “Medical grade” is not treated as verified certification.
- Certification, calibration and compliance information is seller-provided unless independently verified.
- Prescription-specific patient information must not be stored as ordinary public listing attributes.
- Medical claims and treatment claims require appropriate moderation.
- Expired consumables or safety-critical products may require additional listing restrictions.

## Implementation Rules

- Measurement value and measurement unit remain separate.
- Capacity and capacity unit remain separate.
- Weight and weight unit remain separate.
- Battery/power specifications apply only to relevant equipment.
- Certification/compliance is distinct from manufacturer information.
- Calibration status is separate from general condition.
- Expiry date is first-class for applicable consumables and emergency supplies.
- Disposable versus reusable is explicit where applicable.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Health, Medical & Wellness Equipment is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.