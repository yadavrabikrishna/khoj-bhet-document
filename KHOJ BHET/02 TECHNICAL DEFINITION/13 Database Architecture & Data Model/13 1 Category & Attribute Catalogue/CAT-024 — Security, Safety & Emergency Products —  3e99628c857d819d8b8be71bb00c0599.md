# CAT-024 — Security, Safety & Emergency Products — Detailed Catalogue

**Catalogue ID:** CAT-024

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope

CAT-024 covers physical personal, household, commercial and emergency safety products used for protection, prevention, access control, fire safety, personal safety and emergency preparedness.

## Boundary

- CAT-016 covers household home-security products when primarily household/home-garden oriented.
- CAT-010 covers commercial security/surveillance equipment.
- CAT-019 covers general consumer electronics.
- CAT-020 covers construction PPE and worksite safety equipment.
- CAT-023 covers medical/health emergency equipment.
- CAT-009 covers security guards, safety services, installation and monitoring services.
- CAT-004 covers vehicle-specific safety/accessory products when vehicle-specific.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-024-01 | Locks, Padlocks &amp; Access Control | Primary catalogue scope for this subcategory. |
| CAT-024-02 | Safes, Lockboxes &amp; Secure Storage | Primary catalogue scope for this subcategory. |
| CAT-024-03 | Home Security Products | Primary catalogue scope for this subcategory. |
| CAT-024-04 | Personal Safety &amp; Protection | Primary catalogue scope for this subcategory. |
| CAT-024-05 | Fire Extinguishers &amp; Fire Safety | Primary catalogue scope for this subcategory. |
| CAT-024-06 | Smoke, Gas &amp; Safety Alarms | Primary catalogue scope for this subcategory. |
| CAT-024-07 | Emergency &amp; Disaster Preparedness | Primary catalogue scope for this subcategory. |
| CAT-024-08 | First Response &amp; Rescue Equipment | Primary catalogue scope for this subcategory. |
| CAT-024-09 | Reflective, Visibility &amp; Warning Products | Primary catalogue scope for this subcategory. |
| CAT-024-10 | Workplace Safety Products | Primary catalogue scope for this subcategory. |
| CAT-024-11 | Electrical Safety Products | Primary catalogue scope for this subcategory. |
| CAT-024-12 | Child Safety &amp; Home Safety | Primary catalogue scope for this subcategory. |
| CAT-024-13 | Travel &amp; Personal Security | Primary catalogue scope for this subcategory. |
| CAT-024-14 | Security Signs, Barriers &amp; Access Products | Primary catalogue scope for this subcategory. |
| CAT-024-15 | Safety Lighting &amp; Emergency Lighting | Primary catalogue scope for this subcategory. |
| CAT-024-16 | Other Security, Safety &amp; Emergency Products | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| SAFE-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| SAFE-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| SAFE-ATTR-003 | Product Type | select | Yes | Yes | Yes | No |
| SAFE-ATTR-004 | Condition | select. | No | No | No | No |
| SAFE-ATTR-005 | Safety / Security Function | select | No | Yes | No | Yes |
| SAFE-ATTR-006 | Intended Use | select. | No | No | No | No |
| SAFE-ATTR-007 | Material | select | No | Yes | No | Yes |
| SAFE-ATTR-008 | Size / Dimensions | text. | No | No | No | No |
| SAFE-ATTR-009 | Weight | decimal. | No | No | No | No |
| SAFE-ATTR-010 | Weight Unit | select. | No | No | No | No |
| SAFE-ATTR-011 | Power Source | select. | No | No | No | No |
| SAFE-ATTR-012 | Installation Type | select. | No | Yes | Yes | No |
| SAFE-ATTR-013 | Indoor / Outdoor | select. | No | No | No | No |
| SAFE-ATTR-014 | Certification / Standard | text | No | No | No | Yes |
| SAFE-ATTR-015 | Warranty Status | select. | No | No | No | No |
| SAFE-ATTR-016 | Accessories Included | multi_select | No | Yes | No | Yes |
| SAFE-ATTR-017 | Purchase Year | integer. | No | No | No | No |
| SAFE-ATTR-018 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Open Box, Like New, Good, Fair, Used, Needs Repair, Refurbished.

Power Source: AC, Battery, Rechargeable Battery, USB, Solar, Manual, None, Other.

Installation Type: None / Portable, Wall Mounted, Ceiling Mounted, Floor Mounted, Door / Gate Mounted, Vehicle Mounted, Surface Mounted, Built-in, Other.

Indoor / Outdoor: Indoor, Outdoor, Indoor / Outdoor.

## Subcategory Attributes

### 01 — Locks, Padlocks & Access Control

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-01-ATTR-001 | Lock Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-01-ATTR-002 | Lock Mechanism | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-01-ATTR-003 | Key Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-01-ATTR-004 | Number of Keys | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-01-ATTR-005 | Digital / Mechanical | boolean | No | Yes | No | No | true / false |
| CAT-024-01-ATTR-006 | Smart / Connected | boolean | No | Yes | No | No | true / false |
| CAT-024-01-ATTR-007 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-01-ATTR-008 | Weather Resistant | boolean | No | Yes | No | No | true / false |
| CAT-024-01-ATTR-009 | Installation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-01-ATTR-010 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 02 — Safes, Lockboxes & Secure Storage

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-02-ATTR-001 | Safe Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-02-ATTR-002 | Lock Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-02-ATTR-003 | Fire Resistance | text | No | No | No | No | Free text |
| CAT-024-02-ATTR-004 | Water Resistance | text | No | No | No | No | Free text |
| CAT-024-02-ATTR-005 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-02-ATTR-006 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-02-ATTR-007 | Wall / Floor Mount | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-02-ATTR-008 | Interior Compartments | text | No | No | No | No | Free text |
| CAT-024-02-ATTR-009 | Security Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-02-ATTR-010 | Emergency Override | text | No | No | No | No | Free text |

### 03 — Home Security Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-03-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-03-ATTR-002 | Security Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-03-ATTR-003 | Installation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-03-ATTR-004 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-024-03-ATTR-005 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-03-ATTR-006 | Connectivity | text | No | No | No | No | Free text |
| CAT-024-03-ATTR-007 | Alarm | text | No | No | No | No | Free text |
| CAT-024-03-ATTR-008 | Motion Detection | text | No | No | No | No | Free text |
| CAT-024-03-ATTR-009 | Remote Access | boolean | No | Yes | No | No | true / false |
| CAT-024-03-ATTR-010 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 04 — Personal Safety & Protection

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-04-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-04-ATTR-002 | Protection Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-04-ATTR-003 | Intended User Group | text | No | No | No | No | Free text |
| CAT-024-04-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-04-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-04-ATTR-006 | Wearable | text | No | No | No | No | Free text |
| CAT-024-04-ATTR-007 | Visibility | text | No | No | No | No | Free text |
| CAT-024-04-ATTR-008 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-024-04-ATTR-009 | Certification / Standard | text | No | No | No | No | Free text |
| CAT-024-04-ATTR-010 | Intended Environment | text | No | No | No | No | Free text |

### 05 — Fire Extinguishers & Fire Safety

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-05-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-05-ATTR-002 | Extinguishing Agent | text | No | No | No | No | Free text |
| CAT-024-05-ATTR-003 | Fire Class | text | No | No | No | No | Free text |
| CAT-024-05-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-05-ATTR-005 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-05-ATTR-006 | Pressure | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-05-ATTR-007 | Rechargeable | text | No | No | No | No | Free text |
| CAT-024-05-ATTR-008 | Manufacture Date | text | No | No | No | No | Free text |
| CAT-024-05-ATTR-009 | Expiry / Service Date | text | No | No | No | No | Free text |
| CAT-024-05-ATTR-010 | Certification / Standard | text | No | No | No | No | Free text |

### 06 — Smoke, Gas & Safety Alarms

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-06-ATTR-001 | Alarm Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-06-ATTR-002 | Detection Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-06-ATTR-003 | Sensor Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-06-ATTR-004 | Detection Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-06-ATTR-005 | Alarm Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-06-ATTR-006 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-06-ATTR-007 | Battery Backup | boolean | No | Yes | No | No | true / false |
| CAT-024-06-ATTR-008 | Connectivity | text | No | No | No | No | Free text |
| CAT-024-06-ATTR-009 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-024-06-ATTR-010 | Test Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 07 — Emergency & Disaster Preparedness

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-07-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-07-ATTR-002 | Emergency Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-07-ATTR-003 | Contents | text | No | No | No | Yes | Free text |
| CAT-024-07-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-07-ATTR-005 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-07-ATTR-006 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-024-07-ATTR-007 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-024-07-ATTR-008 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-07-ATTR-009 | Storage Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-07-ATTR-010 | Intended Environment | text | No | No | No | No | Free text |

### 08 — First Response & Rescue Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-08-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-08-ATTR-002 | Emergency Use | text | No | No | No | No | Free text |
| CAT-024-08-ATTR-003 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-08-ATTR-004 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-08-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-08-ATTR-006 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-024-08-ATTR-007 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-024-08-ATTR-008 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-024-08-ATTR-009 | Accessories | text | No | No | No | Yes | Free text |
| CAT-024-08-ATTR-010 | Certification / Standard | text | No | No | No | No | Free text |

### 09 — Reflective, Visibility & Warning Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-09-ATTR-002 | Visibility Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-09-ATTR-003 | Reflective Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-09-ATTR-004 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-09-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-09-ATTR-006 | Visibility Distance | text | No | No | No | No | Free text |
| CAT-024-09-ATTR-007 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-024-09-ATTR-008 | Weather Resistant | boolean | No | Yes | No | No | true / false |
| CAT-024-09-ATTR-009 | Mounting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-09-ATTR-010 | Reusable | boolean | No | Yes | No | No | true / false |

### 10 — Workplace Safety Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-10-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-10-ATTR-002 | Safety Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-10-ATTR-003 | Workplace Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-10-ATTR-004 | Protection Area | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-10-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-10-ATTR-006 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-10-ATTR-007 | PPE / Non-PPE | text | No | No | No | No | Free text |
| CAT-024-10-ATTR-008 | Certification / Standard | text | No | No | No | No | Free text |
| CAT-024-10-ATTR-009 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-024-10-ATTR-010 | Intended Application | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 11 — Electrical Safety Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-11-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-11-ATTR-002 | Electrical Safety Function | boolean | No | Yes | No | No | true / false |
| CAT-024-11-ATTR-003 | Voltage Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-11-ATTR-004 | Current Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-11-ATTR-005 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-11-ATTR-006 | Protection Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-11-ATTR-007 | Plug / Connector Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-11-ATTR-008 | Surge Protection | text | No | No | No | No | Free text |
| CAT-024-11-ATTR-009 | Grounding | text | No | No | No | No | Free text |
| CAT-024-11-ATTR-010 | Certification / Standard | text | No | No | No | No | Free text |

### 12 — Child Safety & Home Safety

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-12-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-12-ATTR-002 | Safety Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-12-ATTR-003 | Compatible Location | boolean | No | Yes | No | Yes | true / false |
| CAT-024-12-ATTR-004 | Child Age Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-12-ATTR-005 | Installation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-12-ATTR-006 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-12-ATTR-007 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-024-12-ATTR-008 | Lockable | boolean | No | Yes | No | No | true / false |
| CAT-024-12-ATTR-009 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-024-12-ATTR-010 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 13 — Travel & Personal Security

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-13-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-13-ATTR-002 | Security Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-13-ATTR-003 | Lock Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-13-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-13-ATTR-005 | TSA Compatible | boolean | No | Yes | No | Yes | true / false |
| CAT-024-13-ATTR-006 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-024-13-ATTR-007 | Alarm | text | No | No | No | No | Free text |
| CAT-024-13-ATTR-008 | RFID Protection | text | No | No | No | No | Free text |
| CAT-024-13-ATTR-009 | Weather Resistant | boolean | No | Yes | No | No | true / false |
| CAT-024-13-ATTR-010 | Intended Travel Use | text | No | No | No | No | Free text |

### 14 — Security Signs, Barriers & Access Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-14-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-14-ATTR-002 | Security Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-14-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-14-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-14-ATTR-005 | Mounting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-14-ATTR-006 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-024-14-ATTR-007 | Reflective | text | No | No | No | No | Free text |
| CAT-024-14-ATTR-008 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-024-14-ATTR-009 | Lockable | boolean | No | Yes | No | No | true / false |
| CAT-024-14-ATTR-010 | Intended Environment | text | No | No | No | No | Free text |

### 15 — Safety Lighting & Emergency Lighting

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-15-ATTR-001 | Lighting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-15-ATTR-002 | Light Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-15-ATTR-003 | Brightness | text | No | No | No | No | Free text |
| CAT-024-15-ATTR-004 | Battery Capacity | boolean | No | Yes | No | No | true / false |
| CAT-024-15-ATTR-005 | Runtime | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-024-15-ATTR-006 | Charging Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-15-ATTR-007 | Emergency Mode | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-15-ATTR-008 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-024-15-ATTR-009 | Mounting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-15-ATTR-010 | Waterproof | boolean | No | Yes | No | No | true / false |

### 16 — Other Security, Safety & Emergency Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-024-16-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-16-ATTR-002 | Safety / Security Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-16-ATTR-003 | Intended Use | text | No | No | No | No | Free text |
| CAT-024-16-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-16-ATTR-005 | Installation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-024-16-ATTR-006 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange (limited), Wanted, Free (limited), Rent (limited), Lease (limited), Offer. Service and Job are not applicable.

## Safety & Boundary Rules

- Commercial CCTV, surveillance systems and professional security equipment belong to CAT-010.
- Household security products may remain CAT-024 when their primary purpose is personal/home safety rather than general electronics.
- Construction PPE and construction-specific safety equipment belong to CAT-020.
- Medical emergency and patient-care equipment belongs to CAT-023.
- Security guards, installation, monitoring and emergency services belong to CAT-009.
- Vehicle-specific safety equipment/accessories belong to CAT-004 when vehicle-specific.
- General consumer electronic devices remain CAT-019.
- Safety and security claims are not automatically verified.
- Certification, compliance and standards information is seller-provided unless independently verified.
- Fire-safety equipment should expose manufacture/service/expiry information where applicable.
- Products requiring professional installation should not imply installation service.
- Electrical specifications apply only to relevant products.
- Child-safety products require age/compatibility information where applicable.
- Security ratings must not be treated as verified unless supported by an appropriate verification process.
- Emergency products should distinguish reusable equipment from consumable emergency supplies.
- Restricted or regulated safety/security products may require additional marketplace moderation.

## Implementation Rules

- Safety/security function is separate from product type.
- Certification is separate from manufacturer information.
- Installation type is separate from indoor/outdoor placement.
- Electrical ratings use structured values and units where applicable.
- Capacity and capacity unit remain separate.
- Weight and weight unit remain separate.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Security, Safety & Emergency Products is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.