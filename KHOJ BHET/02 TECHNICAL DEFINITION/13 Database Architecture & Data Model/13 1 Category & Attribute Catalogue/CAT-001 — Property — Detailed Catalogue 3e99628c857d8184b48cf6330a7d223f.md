# CAT-001 — Property — Detailed Catalogue

**Project:** KHOJ BHET

**Catalogue ID:** CAT-001

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Parent:** 13.1 Category & Attribute Catalogue

## Approved Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-001-01 | Room | Primary catalogue scope. |
| CAT-001-02 | Flat | Primary catalogue scope. |
| CAT-001-03 | House | Primary catalogue scope. |
| CAT-001-04 | Apartment | Primary catalogue scope. |
| CAT-001-05 | Building | Primary catalogue scope. |
| CAT-001-06 | Land | Primary catalogue scope. |
| CAT-001-07 | Office | Primary catalogue scope. |
| CAT-001-08 | Shop | Primary catalogue scope. |
| CAT-001-09 | Warehouse | Primary catalogue scope. |

## Property-wide Attributes

| ID | Attribute | Type | Required | Filterable | Searchable | Multi |
| --- | --- | --- | --- | --- | --- | --- |
| PROP-ATTR-001 | Property Condition | select | No | Yes | No | No |
| PROP-ATTR-002 | Furnished Status | select | No | Yes | No | No |
| PROP-ATTR-003 | Bedrooms | integer | No | Yes | No | No |
| PROP-ATTR-004 | Bathrooms | integer | No | Yes | No | No |
| PROP-ATTR-005 | Floor Number | integer | No | Yes | No | No |
| PROP-ATTR-006 | Total Floors | integer | No | Yes | No | No |
| PROP-ATTR-007 | Built-up Area | decimal | No | Yes | No | No |
| PROP-ATTR-008 | Land Area | decimal | No | Yes | No | No |
| PROP-ATTR-009 | Area Unit | select | No | Yes | No | No |
| PROP-ATTR-010 | Parking | boolean | No | Yes | No | No |
| PROP-ATTR-011 | Water Supply | boolean | No | Yes | No | No |
| PROP-ATTR-012 | Electricity Available | boolean | No | Yes | No | No |
| PROP-ATTR-013 | Road Access | select | No | Yes | No | No |
| PROP-ATTR-014 | Facing Direction | select | No | Yes | No | No |
| PROP-ATTR-015 | Construction Year | integer | No | Yes | No | No |
| PROP-ATTR-016 | Property Amenities | multi_select | No | Yes | No | Yes |
| PROP-ATTR-017 | Nearby Facilities | multi_select | No | Yes | No | Yes |

### Controlled Values

Property Condition: New, Like New, Good, Fair, Needs Repair, Under Construction, Renovation Required.

Furnished Status: Fully Furnished, Semi Furnished, Unfurnished.

Area Unit: sq ft, sq m, aana, paisa, daam, ropani, bigha, kattha, dhur.

Road Access: None, Footpath, Gravel, Paved, Blacktopped, Highway, Other.

Facing Direction: North, South, East, West, North-East, North-West, South-East, South-West.

Property Amenities (multi): Balcony, Terrace, Garden, Swimming Pool, Gym, Elevator, Security Guard, CCTV, Internet, Solar, Generator, Backup Power, Air Conditioning, Heating, Modular Kitchen, Attached Bathroom, Common Bathroom, Store Room, Laundry, Servant Quarter, Basement, Rooftop Access, Community Hall, Playground.

Nearby Facilities (multi): School, College, Hospital, Clinic, Pharmacy, Bank, ATM, Police Station, Bus Stop, Airport, Market, Shopping Center, Restaurant, Temple, Mosque, Church, Park, Government Office, Railway Station, Highway, Petrol Pump.

## Subcategory Specifications

### Room

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ROOM-001 | Room Type | select | No | Yes | No | No | Single Room, Shared Room, Studio Room, PG/Hostel Room, Other |
| ROOM-002 | Attached Bathroom | boolean | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| ROOM-003 | Kitchen Access | select | No | Yes | No | No | Private, Shared, None |
| ROOM-004 | Balcony | boolean | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| ROOM-005 | Internet Available | boolean | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| ROOM-006 | Security | boolean | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### Flat

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| FLAT-001 | BHK Type | select | No | Yes | No | No | 1 BHK, 2 BHK, 3 BHK, 4 BHK, 5 BHK, 6+ BHK, Other |

### House

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| HOUSE-001 | House Type | select | No | Yes | No | No | Single Family, Duplex, Bungalow, Villa, Mansion, Row House, Other |

### Apartment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| APT-001 | BHK Type | select | No | Yes | No | No | 1 BHK, 2 BHK, 3 BHK, 4 BHK, 5 BHK, 6+ BHK, Other |

### Building

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| BLD-001 | Building Type | select | No | Yes | No | No | Residential, Commercial, Mixed-use, Apartment Building, Office Building, Warehouse Building, Other |

### Land

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAND-001 | Land Type | select | No | Yes | No | No | Residential, Commercial, Agricultural, Industrial, Mixed-use, Development Land, Other |

### Office

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| OFF-001 | Office Type | select | No | Yes | No | No | Private Office, Shared Office, Coworking, Corporate Office, Commercial Office, Other |

### Shop

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SHOP-001 | Shop Type | select | No | Yes | No | No | Retail Shop, Showroom, Grocery, Restaurant/Cafe, Pharmacy, Electronics, Clothing, Other |

### Warehouse

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| WH-001 | Warehouse Type | select | No | Yes | No | No | General Storage, Cold Storage, Industrial, Logistics/Distribution, Commercial, Other |

## Listing-Type Applicability

Room: Rent, Lease, Wanted.

Flat, House, Apartment, Building, Office, Shop, Warehouse: Sale, Rent, Lease, Wanted.

Land: Sale, Lease, Wanted.

Exchange, Service, and Job are not exposed for Property initially.

## Inheritance & Modeling Rules

Property → Common Property Attributes → subcategory-specific attributes.

Requiredness may differ by subcategory. Multi-value attributes create multiple attribute-value rows. Single-value attributes allow at most one value. Exactly one typed value representation is valid per attribute row. Option-backed values must match valid catalogue options.

## Phase 3 Option Resolution — CAT-001

**Status:** APPROVED — 2026-09-30. The proposed option sets below are now accepted for CAT-001 production-seed reconciliation.

The accepted option sets below resolve the previously missing select-value definitions. They do not change the approved taxonomy.

| Attribute ID | Attribute | Proposed Values |
| --- | --- | --- |
| ROOM-001 | Room Type | Single Room, Shared Room, Studio Room, PG/Hostel Room, Other |
| ROOM-003 | Kitchen Access | Private, Shared, None |
| FLAT-001 | BHK Type | 1 BHK, 2 BHK, 3 BHK, 4 BHK, 5 BHK, 6+ BHK, Other |
| APT-001 | BHK Type | 1 BHK, 2 BHK, 3 BHK, 4 BHK, 5 BHK, 6+ BHK, Other |
| HOUSE-001 | House Type | Single Family, Duplex, Bungalow, Villa, Mansion, Row House, Other |
| BLD-001 | Building Type | Residential, Commercial, Mixed-use, Apartment Building, Office Building, Warehouse Building, Other |
| LAND-001 | Land Type | Residential, Commercial, Agricultural, Industrial, Mixed-use, Development Land, Other |
| OFF-001 | Office Type | Private Office, Shared Office, Coworking, Corporate Office, Commercial Office, Other |
| SHOP-001 | Shop Type | Retail Shop, Showroom, Grocery, Restaurant/Cafe, Pharmacy, Electronics, Clothing, Other |
| WH-001 | Warehouse Type | General Storage, Cold Storage, Industrial, Logistics/Distribution, Commercial, Other |

### CAT-001 Area Unit Policy

The catalogue retains the existing explicit unit set: **sq ft, sq m, aana, paisa, daam, ropani, bigha, kattha, dhur**.

For V1, the entered value and selected unit remain the user-facing representation. A normalized square-metre value should be derivable for search/range comparison, while the original unit/value is preserved for display. The Ropani and Bigha systems must not be treated as interchangeable source systems merely because they can be converted numerically.

Reference relationships for the normalized conversion layer:

- 1 Ropani = 16 Aana = 64 Paisa = 256 Daam = 5,476 sq ft.
- 1 Bigha = 20 Kattha = 400 Dhur = 72,900 sq ft.
- 1 Aana = 342.25 sq ft; 1 Paisa = 85.5625 sq ft; 1 Daam = 21.390625 sq ft.
- 1 Kattha = 3,645 sq ft; 1 Dhur = 182.25 sq ft.

These are reference conversion constants for the catalogue/application layer; final production validation should use the applicable Nepal land-measurement authority/source for the deployment policy. citeturn0search1turn0search6