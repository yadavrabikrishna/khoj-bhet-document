# CAT-002 — Mobile & Electronics — Detailed Catalogue

> **Canonical taxonomy decision — 2026-10-16:** CAT-002 is Mobile & Electronics; Television remains CAT-002-05. Preserve all existing CAT IDs. This taxonomy decision does not make the detailed attribute page seed-ready; the completeness gate below remains open.
> 

**Project:** KHOJ BHET

**Catalogue ID:** CAT-002

**Status:** APPROVED taxonomy and field-decision baseline — structural/runtime validation pending; NOT seed-ready

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Parent:** 13.1 Category & Attribute Catalogue

> **Completeness gate — audit updated 2026-10-21:** The CAT-002 master specifies 96 attribute identifiers. The 69 identifiers missing from the original detail tables have been enumerated, so identifier coverage is structurally reconciled; this is not approval of all field metadata. Phase 3B §43–§44 resolves shared controlled-option and unit semantics where its rules clearly apply, but it does not supply missing product-specific flags, options, numeric ranges, or applicability decisions. The previous 48 flag-cell gaps across 16 subcategory-specific attributes are closed by the defaults recorded below: Required = No, Filterable = Yes, Searchable = Yes. The same filter/search defaults apply to all 96 CAT-002 attributes, including common electronics attributes; requiredness remains No by default unless a field is essential. The remaining CAT-002 option and measurement decisions have been resolved by the 2026-10-21 catalogue-owner defaults in the decision record below. Numeric constraints use basic domain validation (positive values where applicable, and 0–100 for battery health) rather than unsupported device-specific upper bounds. The final applicability/ordering review and catalogue-wide structural seed validation remain required before production seeding. Preserve the approved taxonomy and all existing IDs.
> 

## Approved Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-002-01 | Mobile Phone | Primary catalogue scope. |
| CAT-002-02 | Tablet | Primary catalogue scope. |
| CAT-002-03 | Laptop | Primary catalogue scope. |
| CAT-002-04 | Desktop Computer | Primary catalogue scope. |
| CAT-002-05 | Television | Primary catalogue scope. |
| CAT-002-06 | Camera | Primary catalogue scope. |
| CAT-002-07 | Audio Equipment | Primary catalogue scope. |
| CAT-002-08 | Gaming | Primary catalogue scope. |
| CAT-002-09 | Computer Accessories | Primary catalogue scope. |
| CAT-002-10 | Mobile Accessories | Primary catalogue scope. |
| CAT-002-11 | Other Electronics | Primary catalogue scope. |

## Common Electronics Attributes

| ID | Attribute | Type | Required | Filterable | Searchable | Multi |
| --- | --- | --- | --- | --- | --- | --- |
| ELEC-ATTR-001 | Brand | text | No | Yes | Yes | No |
| ELEC-ATTR-002 | Model | text | No | Yes | Yes | No |
| ELEC-ATTR-003 | Condition | select | Yes | Yes | Yes | No |
| ELEC-ATTR-004 | Purchase Year | integer | No | Yes | Yes | No |
| ELEC-ATTR-005 | Warranty Status | select | No | Yes | Yes | No |
| ELEC-ATTR-006 | Warranty Expiry | date | No | Yes | Yes | No |
| ELEC-ATTR-007 | Color | select | No | Yes | Yes | No |
| ELEC-ATTR-008 | Box Available | boolean | No | Yes | Yes | No |
| ELEC-ATTR-009 | Bill Available | boolean | No | Yes | Yes | No |
| ELEC-ATTR-010 | Original Accessories | multi_select | No | Yes | Yes | Yes |
| ELEC-ATTR-011 | Seller Notes | text | No | Yes | Yes | No |

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Warranty Status: None, Active, Expired, Seller Warranty, Manufacturer Warranty.

Original Accessories (multi): Original Charger, Cable, Adapter, Earphones, Battery, Remote, Stand, Box, Manual, Other.

## Subcategory Attributes

### Mobile Phone

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| MOB-001 | Operating System | select | No | Yes | Yes | No | Android, iOS, Other Master does not specify required/filterable/searchable flags for this attribute; confirm before seed generation. |
| MOB-002 | RAM | integer | No | Yes | Yes | No |  Numeric RAM value in GB; greater than 0. Required = No; Filterable = Yes; Searchable = Yes. |

</table>

### Tablet

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TAB-001 | Operating System | select | No | Yes | Yes | No | Android, iPadOS, Windows, ChromeOS, Other. |

</table>

### Laptop

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAP-001 | Processor | text | No | Yes | Yes | No |  Master does not specify required/filterable/searchable flags for this attribute; confirm before seed generation. |

</table>

### Desktop Computer

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| DESK-001 | Processor | text | No | Yes | Yes | No |  Master does not specify required/filterable/searchable flags for this attribute; confirm before seed generation. |

</table>

### Television

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TV-001 | Screen Size | decimal | No | Yes | Yes | No |  Numeric diagonal length; use §43 Length Unit family (mm, cm, m, in, ft); valid range remains unspecified. Master does not specify required/filterable/searchable flags for this attribute; confirm before seed generation. |

</table>

### Camera

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAM-001 | Camera Type | select | No | Yes | Yes | No | DSLR, Mirrorless, Point-and-Shoot, Action Camera, Video Camera, Other Master does not specify required/filterable/searchable flags for this attribute; confirm before seed generation. |
| CAM-002 | Sensor Resolution | decimal | No | Yes | Yes | No |  Sensor resolution in megapixels (MP), greater than 0. Required = No; Filterable = Yes; Searchable = Yes. |

</table>

### Audio Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| AUD-001 | Audio Type | select | No | Yes | Yes | No | Speaker, Soundbar, Home Theater, Headphones, Earbuds, Microphone, Amplifier, Mixer, Other Master does not specify required/filterable/searchable flags for this attribute; confirm before seed generation. |
| AUD-002 | Connectivity | multi_select | No | Yes | Yes | Yes | Bluetooth, Wi-Fi, AUX, USB, HDMI, Optical, RCA, XLR, Other. Master specifies multiple values; required/filterable/searchable flags are not specified in master. |

</table>

### Gaming

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| GAME-001 | Gaming Type | select | No | Yes | Yes | No | Console, Handheld Console, Gaming PC, Gaming Accessory, Game Software, Other Master does not specify required/filterable/searchable flags for this attribute; confirm before seed generation. |
| GAME-002 | Platform | multi_select | No | Yes | Yes | Yes | PlayStation, Xbox, Nintendo, PC, Mobile, Other. Master specifies multiple values; required/filterable/searchable flags are not specified in master. |

</table>

### Computer Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CACC-001 | Accessory Type | select | No | Yes | Yes | No | Monitor, Keyboard, Mouse, Webcam, Printer, Scanner, Router, UPS, Storage Device, Dock, Adapter, Cable, Other Master does not specify required/filterable/searchable flags for this attribute; confirm before seed generation. |
| CACC-002 | Compatible Device | text | No | Yes | Yes | Yes | Master specifies text with multi-value support; required/filterable/searchable flags are not specified in master. |

</table>

### Mobile Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| MACC-001 | Accessory Type | select | No | Yes | Yes | No | Case, Cover, Screen Protector, Charger, Cable, Power Bank, Car Mount, Wireless Charger, Earphones, Adapter, Stand, Other. Master specifies type/options; required/filterable/searchable flags are not specified in master. |
| MACC-002 | Compatible Brand | text | No | Yes | Yes | Yes |  Master specifies text with multi-value support. |

</table>

### Other Electronics

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| OTHER-001 | Product Type | select | No | Yes | Yes | No | Controlled fallback product-type set; recurring products should become dedicated subcategories. |
| OTHER-002 | Compatibility | text | No | Yes | Yes | Yes | Free text; multiple compatible products may be stored. |
| OTHER-003 | Key Features | text | No | No | Yes | Yes | Free text; multiple feature values may be stored. |

## Catalogue-owner decisions adopted — 2026-10-21

These are approved working defaults for CAT-002 to unblock implementation. They do not alter the approved taxonomy or existing attribute IDs.

### Attribute flags

- **Required:** No by default. A subcategory-specific field becomes required only when omission would make the listing materially incomplete or unusable. Do not make every attribute mandatory.
- **Filterable:** Yes by default for all 96 CAT-002 attributes.
- **Searchable:** Yes by default for all 96 CAT-002 attributes. Search behavior is datatype-aware: text fields use text matching; select/multi-select and boolean fields use exact normalized values; numeric/date fields use typed comparisons and ranges. Do not full-text-index every typed value as raw prose.
- Existing explicit Required values on common attributes remain authoritative. Common attributes previously marked Filterable = No or Searchable = No are normalized to Yes under this policy, unless a later measured performance/security review documents a specific override.

### Controlled options adopted

- **TAB-001 Operating System:** Android, iPadOS, Windows, ChromeOS, Other.
- **TAB-007 Network Type:** 2G, 3G, 4G, 5G, Wi-Fi Only, Other.
- **LAP-004 RAM Unit:** GB only as the canonical consumer RAM unit; store numeric RAM in GB and convert input units before persistence if the UI accepts them.
- **LAP-010 Operating System:** Windows, macOS, Linux, ChromeOS, Other.
- **DESK-003 Storage Type:** HDD, SSD, NVMe SSD, eMMC, Hybrid, Other.
- **DESK-006 Operating System:** Windows, macOS, Linux, Other.
- **TV-005 Operating System:** Android TV, Google TV, Tizen, webOS, Roku TV, Fire TV, VIDAA, Proprietary, Other.
- **AUD-006 Channels:** Mono, Stereo, 2.1, 5.1, 7.1, 9.1, Other.

Exact attribute-specific options override generic §43 families. Seed slugs are normalized; display labels preserve the listed form.

### Measurement semantics adopted

- **RAM (MOB-002, TAB-002, LAP-003, DESK-002):** numeric value in GB, greater than 0.
- **Battery Capacity (MOB-006):** integer mAh, greater than 0.
- **Battery Health (MOB-015):** integer percentage, 0–100 inclusive.
- **Sensor Resolution (CAM-002):** decimal megapixels (MP), greater than 0; no unsupported upper bound.
- **Optical Zoom (CAM-006):** decimal optical magnification ratio, at least 1.0×.
- **Wattage (AUD-005):** decimal watts (W), greater than 0.
- **Refresh Rate (TV-007):** integer Hz, greater than 0.
- **Screen / monitor size (MOB-005, TAB-005, LAP-009, TV-001, DESK-008):** use §43 Length Unit family; numeric value must be greater than 0. Do not impose a model-specific maximum.
- Other numeric capacity/count fields use positive/non-negative validation appropriate to the semantic field, with no arbitrary maximum unless supported by a documented product requirement.

### Implementation rules

- Requiredness defaults to No; Filterable and Searchable default to Yes. Seeder output must materialize final resolved values rather than null/“Decision required”.
- These choices resolve CAT-002's documented product-specific option and measurement gaps. Before production seed approval, still run complete checks for attribute/subcategory coverage, option slug uniqueness, type compatibility, duplicate/orphan rows, and applicability/order integrity.

## Inheritance & Modeling Rules

Common electronics attributes inherit into subcategories unless explicitly overridden. Multi-value attributes create multiple attribute-value rows. Single-value attributes allow at most one value. Exactly one typed value representation is valid per attribute row. Option-backed values must match valid catalogue options.

## Master-specification reconciliation — 2026-10-16

**Authority:** Attribute names, data types, and explicit option/value rules below are transcribed from Section 4, CAT-002 of the parent **13.1 Category & Attribute Catalogue**. Where the master does not define an option set, it is marked **Not specified in master**. Product/engineering default policy adopted 2026-10-21: Required = No unless a field is explicitly essential to creating a usable listing; Filterable = Yes and Searchable = Yes for every CAT-002 attribute by default. Search/filter implementations must respect datatype and avoid treating structured values as arbitrary full-text strings. These defaults apply to the complete 96-attribute CAT-002 catalogue unless an explicit row override is recorded.

### Missing attributes added from the master specification

| Subcategory | Attribute ID | Attribute | Canonical type / multi-value rule | Explicit options / value rule from master |
| --- | --- | --- | --- | --- |
| Mobile Phone | MOB-003 | Storage Capacity | integer; single value unless later approved otherwise | Numeric capacity; unit is represented separately by MOB-004 |
| Mobile Phone | MOB-004 | Storage Unit | select | GB, TB |
| Mobile Phone | MOB-005 | Screen Size | decimal | Numeric diagonal length; use §43 Length Unit family (mm, cm, m, in, ft); numeric range remains unspecified |
| Mobile Phone | MOB-006 | Battery Capacity | integer | Numeric capacity in mAh; value must be greater than 0. |
| Mobile Phone | MOB-007 | Network Type | select; supports multiple values | 2G, 3G, 4G, 5G |
| Mobile Phone | MOB-008 | SIM Type | select; supports multiple values | Physical SIM, eSIM, Nano SIM, Other |
| Mobile Phone | MOB-009 | Front Camera | text | Free text |
| Mobile Phone | MOB-010 | Rear Camera | text | Free text |
| Mobile Phone | MOB-011 | Fingerprint Sensor | boolean | Boolean |
| Mobile Phone | MOB-012 | Face Unlock | boolean | Boolean |
| Mobile Phone | MOB-013 | 5G | boolean | Boolean |
| Mobile Phone | MOB-014 | Dual SIM | boolean | Boolean |
| Mobile Phone | MOB-015 | Battery Health | integer | Percentage from 0 to 100 inclusive. |
| Tablet | TAB-002 | RAM | integer | Numeric value in GB; greater than 0 |
| Tablet | TAB-003 | Storage Capacity | integer | Numeric capacity; unit is represented separately by TAB-004 |
| Tablet | TAB-004 | Storage Unit | select | GB, TB — resolved by parent catalogue §43.7 Storage Unit rule |
| Tablet | TAB-005 | Screen Size | decimal | Numeric diagonal length; use §43 Length Unit family (mm, cm, m, in, ft); numeric range remains unspecified |
| Tablet | TAB-006 | Cellular Support | boolean | Boolean |
| Tablet | TAB-007 | Network Type | select; supports multiple values | 2G, 3G, 4G, 5G, Wi-Fi Only, Other |
| Tablet | TAB-008 | Stylus Support | boolean | Boolean |
| Laptop | LAP-002 | Processor Generation | text | Free text |
| Laptop | LAP-003 | RAM | integer | Numeric value in GB; greater than 0 |
| Laptop | LAP-004 | RAM Unit | select | GB (canonical display/storage unit for consumer RAM) |
| Laptop | LAP-005 | Storage Type | select | HDD, SSD, NVMe SSD, eMMC, Hybrid, Other |
| Laptop | LAP-006 | Storage Capacity | integer | Numeric capacity; unit is represented separately by LAP-007 |
| Laptop | LAP-007 | Storage Unit | select | GB, TB — resolved by parent catalogue §43.7 Storage Unit rule |
| Laptop | LAP-008 | GPU | text | Free text |
| Laptop | LAP-009 | Screen Size | decimal | Numeric diagonal length; use §43 Length Unit family (mm, cm, m, in, ft); numeric range remains unspecified |
| Laptop | LAP-010 | Operating System | select | Windows, macOS, Linux, ChromeOS, Other |
| Laptop | LAP-011 | Battery Condition | select | Excellent, Good, Fair, Poor, Needs Replacement |
| Laptop | LAP-012 | Touchscreen | boolean | Boolean |
| Laptop | LAP-013 | Keyboard Layout | select | US, UK, Other |
| Desktop Computer | DESK-002 | RAM | integer | Numeric value in GB; greater than 0 |
| Desktop Computer | DESK-003 | Storage Type | select | HDD, SSD, NVMe SSD, eMMC, Hybrid, Other |
| Desktop Computer | DESK-004 | Storage Capacity | integer | Numeric storage capacity; use Storage Unit GB or TB per §43.7; numeric range remains unspecified |
| Desktop Computer | DESK-005 | GPU | text | Free text |
| Desktop Computer | DESK-006 | Operating System | select | Windows, macOS, Linux, Other |
| Desktop Computer | DESK-007 | Monitor Included | boolean | Boolean |
| Desktop Computer | DESK-008 | Monitor Size | decimal | Numeric diagonal length; use §43 Length Unit family (mm, cm, m, in, ft); numeric range remains unspecified |
| Desktop Computer | DESK-009 | Keyboard Included | boolean | Boolean |
| Desktop Computer | DESK-010 | Mouse Included | boolean | Boolean |
| Television | TV-002 | Display Technology | select | LED, OLED, QLED, Mini LED, Plasma, LCD, Other |
| Television | TV-003 | Resolution | select | HD, Full HD, 2K, 4K, 8K, Other |
| Television | TV-004 | Smart TV | boolean | Boolean |
| Television | TV-005 | Operating System | select | Android TV, Google TV, Tizen, webOS, Roku TV, Fire TV, VIDAA, Proprietary, Other |
| Television | TV-006 | HDR Support | boolean | Boolean |
| Television | TV-007 | Refresh Rate | integer | Integer refresh rate in Hz; value must be greater than 0. |
| Television | TV-008 | HDMI Ports | integer | Numeric count |
| Television | TV-009 | Wall Mount Included | boolean | Boolean |
| Camera | CAM-003 | Lens Mount | text | Free text |
| Camera | CAM-004 | Lens Included | boolean | Boolean |
| Camera | CAM-005 | Video Resolution | multi_select; multiple values | HD, Full HD, 4K, 6K, 8K, Other |
| Camera | CAM-006 | Optical Zoom | decimal | Optical magnification ratio (x); value must be at least 1.0. |
| Camera | CAM-007 | Image Stabilization | boolean | Boolean |
| Audio Equipment | AUD-003 | Wireless | boolean | Boolean |
| Audio Equipment | AUD-004 | Power Type | select | Battery, USB, AC, Rechargeable, Other |
| Audio Equipment | AUD-005 | Wattage | decimal | Power in watts (W); value must be greater than 0. |
| Audio Equipment | AUD-006 | Channels | select | Mono, Stereo, 2.1, 5.1, 7.1, 9.1, Other |
| Audio Equipment | AUD-007 | Microphone Included | boolean | Boolean |
| Gaming | GAME-003 | Storage Capacity | integer | Numeric capacity; unit is represented separately by GAME-004 |
| Gaming | GAME-004 | Storage Unit | select | GB, TB — resolved by parent catalogue §43.7 Storage Unit rule |
| Gaming | GAME-005 | Controllers Included | integer | Numeric count |
| Gaming | GAME-006 | Games Included | text; multi-value | Multiple text values |
| Gaming | GAME-007 | Online Account Included | boolean | Boolean |
| Computer Accessories | CACC-003 | Connectivity | multi_select; multiple values | Wi-Fi, Bluetooth, Ethernet, USB, NFC, Cellular, HDMI, Other — resolved by parent catalogue §43.2 Connectivity family, unless an exact attribute-ID option list takes precedence |
| Computer Accessories | CACC-004 | Quantity | integer | Numeric count |
| Mobile Accessories | MACC-003 | Compatible Model | text; multi-value | Multiple text values |
| Mobile Accessories | MACC-004 | Compatibility Type | select | Universal, Brand Specific, Model Specific |
| Mobile Accessories | MACC-005 | Quantity | integer | Numeric count |

### Existing-row corrections and consistency flags

- **MACC-001 Accessory Type:** canonical type is **select**, not integer. Master options: Case, Cover, Screen Protector, Charger, Cable, Power Bank, Car Mount, Wireless Charger, Earphones, Adapter, Stand, Other.
- **CACC-002 Compatible Device:** master defines text with multi-value support; the earlier detail row's Multi-value = No conflicts and must be corrected.
- **AUD-002 Connectivity:** master defines multi-select with multiple values; the earlier detail row's Multi-value = No conflicts and must be corrected. Options: Bluetooth, Wi-Fi, AUX, USB, HDMI, Optical, RCA, XLR, Other.
- **GAME-002 Platform:** master defines multi-select with multiple values; the earlier detail row's Multi-value = No conflicts and must be corrected. Options: PlayStation, Xbox, Nintendo, PC, Mobile, Other.
- **MOB-007 Network Type, MOB-008 SIM Type, and CAM-005 Video Resolution:** preserve the master-defined multi-value behavior.
- **CACC-003 Connectivity:** preserve the master-defined multi-value behavior.
- For every CAT-002 subcategory attribute, required/filterable/searchable flags must be approved from an authoritative decision before seed generation. The parent master does not currently specify these flags at subcategory-attribute level; values in earlier partial tables are not sufficient evidence to close this gap.
- **Audit disposition — superseded on 2026-10-21:** The initial list of open decisions is historical. The catalogue-owner defaults and product choices in “Catalogue-owner decisions adopted — 2026-10-21” supersede those gaps. Remaining work is validation rather than further product approval: confirm every attribute and option is materialized exactly once, applicability/order is correct, option slugs are unique, typed values match datatypes, and no orphan definitions/options remain. Production seed generation remains blocked until these automated checks pass.

### Listing-type rule — canonical master

Every CAT-002 subcategory supports **Sale, Exchange, Wanted**. **Rent, Lease, Free, Offer, Service, and Job** are not initially exposed. Preserve this rule when generating applicability seeds.

### Reconciliation status

The 69 attribute identifiers missing from the earlier detail tables are now enumerated here from the master specification. This is a **structural reconciliation**, not a seed-readiness approval. Before marking CAT-002 seed-ready, the catalogue owner must resolve all outstanding attribute flags, unspecified select options, unit/range validation rules, subcategory applicability, and ordering metadata. The approved CAT IDs and hierarchy remain unchanged.