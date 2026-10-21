# 13.1 Category & Attribute Catalogue

**Project:** KHOJ BHET  

**Document:** Category & Attribute Catalogue  

**Document ID:** KB-TECH-013

**Status:** Active — Canonical 25-Category Taxonomy Confirmed / CAT-002 Detail Reconciliation Pending

> **Taxonomy decision — 2026-10-16:** CAT-002 is confirmed as **Mobile & Electronics**; **Television remains subcategory CAT-002-05**. Preserve the existing 25-category / 372-subcategory baseline and all assigned CAT IDs.
> 

> 
> 

> **Catalogue completeness gate — 2026-10-16:** CAT-002's separate detailed page remains incomplete relative to the full attribute specification recorded here. Do not treat all category detail pages as seed-ready until CAT-002's missing attributes and option/flag metadata are reconciled.
> 

**Version:** 1.2

**Owner:** KHOJ BHET Product & Engineering  

**Last Reviewed:** 2026-10-21  

**Parent:** 13. Database Architecture & Data Model  

# 1. Canonical Active Catalogue Order — CAT-001 to CAT-025

| CAT ID | Active Catalogue |
| --- | --- |
| CAT-001 | Property |
| CAT-002 | Mobile & Electronics |
| CAT-003 | Furniture & Home |
| CAT-004 | Vehicles |
| CAT-005 | Fashion & Clothing |
| CAT-006 | Home Appliances & Kitchen |
| CAT-007 | Sports, Fitness & Outdoor |
| CAT-008 | Jobs & Employment |
| CAT-009 | Services |
| CAT-010 | Business, Office & Commercial Equipment |
| CAT-011 | Baby, Kids & Toys |
| CAT-012 | Books, Media & Collectibles |
| CAT-013 | Food, Agriculture Products & Livestock |
| CAT-014 | Health, Beauty & Personal Care Products |
| CAT-015 | Home & Garden |
| CAT-016 | Pet Supplies & Animals |
| CAT-017 | Travel, Luggage & Accessories |
| CAT-018 | Construction, Tools & Building Materials |
| CAT-019 | Industrial, Machinery & Heavy Equipment |
| CAT-020 | Weddings, Events & Party Supplies |
| CAT-021 | Office, School & Stationery Supplies |
| CAT-022 | Religious, Spiritual & Cultural Items |
| CAT-023 | Health, Medical & Wellness Equipment |
| CAT-024 | Security, Safety & Emergency Products |
| CAT-025 | Baby, Maternity & Parenting Products |

# 2. Catalogue Rules

- Structure: Category → Subcategory → Attribute → Data Type → Required → Filterable → Searchable → Multi-value → Options.
- Universal listing fields are not duplicated as category attributes.
- Controlled options are used where consistency/filtering benefits from them.
- Typed free-form values are used where controlled options are inappropriate.
- Multi-value attributes are supported.
- Requiredness may differ by subcategory.
- Attribute definitions and options map to category_attribute_definitions and category_attribute_options.
- Brands are reference/data values, not schema columns.

## 2.1 Catalogue Seed Contract

Each catalogue definition must be seed-ready before implementation. The authoritative catalogue record must define:

- **Public:** whether the catalogue/subcategory is exposed to marketplace users.
- **Unit Rule:** which numeric/unit pairs are allowed and whether units are mandatory.
- **Validation Rules:** field-level constraints, allowed ranges/formats, conditional requirements, and moderation-sensitive rules.
- **Subcategory Applicability:** which attributes apply to each subcategory.
- **Listing-Type Applicability:** which listing types are allowed for each subcategory.
- **Ordering:** stable display/order sequence for catalogues, subcategories, attributes, and options.
- **Option Set:** explicit controlled options for every select/multi-select attribute; no implementation-time invention of options.
- **Attribute Flags:** required, filterable, searchable, and multi-value behavior.
- **Data Type:** one of the Document 13 canonical types only: text, integer, decimal, boolean, date, datetime, select, multi_select, or json.

These fields are part of the catalogue authority even when they are represented as documented metadata rather than separate Notion database columns.

# 3. CAT-001 — Property

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-001-01 | Room | Primary catalogue scope for this subcategory. |
| CAT-001-02 | Flat | Primary catalogue scope for this subcategory. |
| CAT-001-03 | House | Primary catalogue scope for this subcategory. |
| CAT-001-04 | Apartment | Primary catalogue scope for this subcategory. |
| CAT-001-05 | Building | Primary catalogue scope for this subcategory. |
| CAT-001-06 | Land | Primary catalogue scope for this subcategory. |
| CAT-001-07 | Office | Primary catalogue scope for this subcategory. |
| CAT-001-08 | Shop | Primary catalogue scope for this subcategory. |
| CAT-001-09 | Warehouse | Primary catalogue scope for this subcategory. |

# 4. CAT-002 — Mobile & Electronics

**Status:** APPROVED — 2026-09-28

## Common Electronics Attribute Specification

#### Common Electronics Attributes

| ID | Attribute | Type | Required | Filterable | Searchable | Multi |
| --- | --- | --- | --- | --- | --- | --- |
| ELEC-ATTR-001 | Brand | text | No | Yes | Yes | No |
| ELEC-ATTR-002 | Model | text | No | No | Yes | No |
| ELEC-ATTR-003 | Condition | select | Yes | Yes | No | No |
| ELEC-ATTR-004 | Purchase Year | integer | No | Yes | No | No |
| ELEC-ATTR-005 | Warranty Status | select | No | Yes | No | No |
| ELEC-ATTR-006 | Warranty Expiry | date | No | Yes | No | No |
| ELEC-ATTR-007 | Color | select | No | Yes | Yes | No |
| ELEC-ATTR-008 | Box Available | boolean | No | Yes | No | No |
| ELEC-ATTR-009 | Bill Available | boolean | No | Yes | No | No |
| ELEC-ATTR-010 | Original Accessories | multi_select | No | Yes | No | Yes |
| ELEC-ATTR-011 | Seller Notes | text | No | No | Yes | No |

Condition = New, Like New, Good, Fair, Needs Repair, Refurbished, Used. Warranty Status = None, Active, Expired, Seller Warranty, Manufacturer Warranty. Original Accessories (multi) = Original Charger, Cable, Adapter, Earphones, Battery, Remote, Stand, Box, Manual, Other.

#### CAT-002-01 Mobile Phone

MOB-001 Operating System — select: Android, iOS, Other. MOB-002 RAM — integer. MOB-003 Storage Capacity — integer. MOB-004 Storage Unit — select: GB, TB. MOB-005 Screen Size — decimal. MOB-006 Battery Capacity — integer. MOB-007 Network Type — select/multi: 2G, 3G, 4G, 5G. MOB-008 SIM Type — select/multi: Physical SIM, eSIM, Nano SIM, Other. MOB-009 Front Camera — text. MOB-010 Rear Camera — text. MOB-011 Fingerprint Sensor — boolean. MOB-012 Face Unlock — boolean. MOB-013 5G — boolean. MOB-014 Dual SIM — boolean. MOB-015 Battery Health — integer.

#### CAT-002-02 Tablet

TAB-001 Operating System — select. TAB-002 RAM — integer. TAB-003 Storage Capacity — integer. TAB-004 Storage Unit — select. TAB-005 Screen Size — decimal. TAB-006 Cellular Support — boolean. TAB-007 Network Type — select/multi. TAB-008 Stylus Support — boolean.

#### CAT-002-03 Laptop

LAP-001 Processor — text. LAP-002 Processor Generation — text. LAP-003 RAM — integer. LAP-004 RAM Unit — select. LAP-005 Storage Type — select: HDD, SSD, NVMe SSD, eMMC, Hybrid, Other. LAP-006 Storage Capacity — integer. LAP-007 Storage Unit — select. LAP-008 GPU — text. LAP-009 Screen Size — decimal. LAP-010 Operating System — select. LAP-011 Battery Condition — select: Excellent, Good, Fair, Poor, Needs Replacement. LAP-012 Touchscreen — boolean. LAP-013 Keyboard Layout — select: US, UK, Other.

#### CAT-002-04 Desktop Computer

DESK-001 Processor — text. DESK-002 RAM — integer. DESK-003 Storage Type — select. DESK-004 Storage Capacity — integer. DESK-005 GPU — text. DESK-006 Operating System — select. DESK-007 Monitor Included — boolean. DESK-008 Monitor Size — decimal. DESK-009 Keyboard Included — boolean. DESK-010 Mouse Included — boolean.

#### CAT-002-05 Television

TV-001 Screen Size — decimal. TV-002 Display Technology — select: LED, OLED, QLED, Mini LED, Plasma, LCD, Other. TV-003 Resolution — select: HD, Full HD, 2K, 4K, 8K, Other. TV-004 Smart TV — boolean. TV-005 Operating System — select. TV-006 HDR Support — boolean. TV-007 Refresh Rate — integer. TV-008 HDMI Ports — integer. TV-009 Wall Mount Included — boolean.

#### CAT-002-06 Camera

CAM-001 Camera Type — select: DSLR, Mirrorless, Point-and-Shoot, Action Camera, Video Camera, Other. CAM-002 Sensor Resolution — decimal. CAM-003 Lens Mount — text. CAM-004 Lens Included — boolean. CAM-005 Video Resolution — multi-select: HD, Full HD, 4K, 6K, 8K, Other. CAM-006 Optical Zoom — decimal. CAM-007 Image Stabilization — boolean.

#### CAT-002-07 Audio Equipment

AUD-001 Audio Type — select: Speaker, Soundbar, Home Theater, Headphones, Earbuds, Microphone, Amplifier, Mixer, Other. AUD-002 Connectivity — multi-select: Bluetooth, Wi-Fi, AUX, USB, HDMI, Optical, RCA, XLR, Other. AUD-003 Wireless — boolean. AUD-004 Power Type — select: Battery, USB, AC, Rechargeable, Other. AUD-005 Wattage — decimal. AUD-006 Channels — select. AUD-007 Microphone Included — boolean.

#### CAT-002-08 Gaming

GAME-001 Gaming Type — select: Console, Handheld Console, Gaming PC, Gaming Accessory, Game Software, Other. GAME-002 Platform — multi-select: PlayStation, Xbox, Nintendo, PC, Mobile, Other. GAME-003 Storage Capacity — integer. GAME-004 Storage Unit — select. GAME-005 Controllers Included — integer. GAME-006 Games Included — text, multi-value. GAME-007 Online Account Included — boolean.

#### CAT-002-09 Computer Accessories

CACC-001 Accessory Type — select: Monitor, Keyboard, Mouse, Webcam, Printer, Scanner, Router, UPS, Storage Device, Dock, Adapter, Cable, Other. CACC-002 Compatible Device — text, multi-value. CACC-003 Connectivity — multi_select, multi-value. CACC-004 Quantity — integer.

#### CAT-002-10 Mobile Accessories

MACC-001 Accessory Type — select: Case, Cover, Screen Protector, Charger, Cable, Power Bank, Car Mount, Wireless Charger, Earphones, Adapter, Stand, Other. MACC-002 Compatible Brand — text, multi-value. MACC-003 Compatible Model — text, multi-value. MACC-004 Compatibility Type — select: Universal, Brand Specific, Model Specific. MACC-005 Quantity — integer.

#### CAT-002-11 Other Electronics

Common electronics attributes plus Product Type (select), Compatibility, and Key Features. Controlled fallback only; recurring products should become dedicated subcategories.

CAT-002 listing types: every CAT-002 subcategory supports Sale, Exchange, Wanted. Rent, Lease, Free, Offer, Service, and Job are not initially exposed.

# 5. CAT-003 — Furniture & Home

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-003-01 | Sofa & Couch | Primary catalogue scope for this subcategory. |
| CAT-003-02 | Bed | Primary catalogue scope for this subcategory. |
| CAT-003-03 | Mattress | Primary catalogue scope for this subcategory. |
| CAT-003-04 | Table | Primary catalogue scope for this subcategory. |
| CAT-003-05 | Chair | Primary catalogue scope for this subcategory. |
| CAT-003-06 | Dining Set | Primary catalogue scope for this subcategory. |
| CAT-003-07 | Wardrobe & Cabinet | Primary catalogue scope for this subcategory. |
| CAT-003-08 | Desk & Office Furniture | Primary catalogue scope for this subcategory. |
| CAT-003-09 | Shelf & Storage | Primary catalogue scope for this subcategory. |
| CAT-003-10 | Kitchen Furniture | Primary catalogue scope for this subcategory. |
| CAT-003-11 | Home Decor | Primary catalogue scope for this subcategory. |
| CAT-003-12 | Other Furniture & Home | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Furniture & Home Attributes

| ID | Attribute | Type | Required | Filterable | Searchable | Multi |
| --- | --- | --- | --- | --- | --- | --- |
| FURN-ATTR-001 | Brand / Manufacturer | text | No | Yes | Yes | No |
| FURN-ATTR-002 | Model / Product Name | text | No | No | Yes | No |
| FURN-ATTR-003 | Condition | select | Yes | Yes | No | No |
| FURN-ATTR-004 | Material | select | No | Yes | Yes | No |
| FURN-ATTR-005 | Color | select | No | Yes | Yes | No |
| FURN-ATTR-006 | Purchase Year | integer | No | Yes | No | No |
| FURN-ATTR-007 | Warranty Status | select | No | Yes | No | No |
| FURN-ATTR-008 | Dimensions | text | No | No | Yes | No |
| FURN-ATTR-009 | Assembly Required | boolean | No | Yes | No | No |
| FURN-ATTR-010 | Delivery Available | boolean | No | Yes | No | No |
| FURN-ATTR-011 | Original Packaging | boolean | No | Yes | No | No |
| FURN-ATTR-012 | Accessories Included | multi_select | No | Yes | No | Yes |
| FURN-ATTR-013 | Seller Notes | text | No | No | Yes | No |

### Controlled values

- Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used
- Warranty Status: None, Active, Expired, Seller Warranty, Manufacturer Warranty
- Material: Wood, Engineered Wood, Metal, Steel, Plastic, Glass, Fabric, Leather, Rattan, Bamboo, Mixed, Other
- Accessories Included (multi): Cushion, Cover, Legs, Hardware, Key, Mirror, Shelf, Drawer, Remote, Manual, Other

## CAT-003-01 Sofa & Couch

- Sofa Type: Sofa, Sectional, Recliner Sofa, Sofa Bed, Loveseat, Divan, Other
- Seating Capacity: integer
- Number of Pieces: integer
- Upholstery Material: select
- Recliner: boolean
- Convertible: boolean

## CAT-003-02 Bed

- Bed Type: Single, Double, Queen, King, Bunk Bed, Loft Bed, Storage Bed, Other
- Bed Size: select
- Number of Sleeping Places: integer
- Headboard Included: boolean
- Storage Included: boolean
- Bed Frame Included: boolean

## CAT-003-03 Mattress

- Mattress Type: Spring, Pocket Spring, Memory Foam, Foam, Latex, Hybrid, Other
- Mattress Size: select
- Thickness: decimal
- Firmness: select
- Orthopedic: boolean
- Waterproof: boolean

## CAT-003-04 Table

- Table Type: Dining Table, Coffee Table, Center Table, Side Table, Study Table, Computer Table, Office Table, Folding Table, Other
- Seating Capacity: integer
- Shape: select
- Number of Drawers: integer
- Foldable: boolean

## CAT-003-05 Chair

- Chair Type: Dining Chair, Office Chair, Gaming Chair, Recliner Chair, Armchair, Plastic Chair, Folding Chair, Rocking Chair, Stool, Other
- Seating Capacity: integer
- Adjustable Height: boolean
- Armrest: boolean
- Foldable: boolean
- Wheels: boolean

## CAT-003-06 Dining Set

- Set Type: Dining Table Set, Breakfast Set, Bar Set, Other
- Number of Chairs: integer
- Table Included: boolean
- Chair Included: boolean
- Bench Included: boolean

## CAT-003-07 Wardrobe & Cabinet

- Storage Type: Wardrobe, Cabinet, Cupboard, Chest of Drawers, Shoe Cabinet, Display Cabinet, Other
- Number of Doors: integer
- Number of Drawers: integer
- Number of Shelves: integer
- Mirror Included: boolean
- Lock Available: boolean

## CAT-003-08 Desk & Office Furniture

- Furniture Type: Office Desk, Reception Desk, Workstation, Conference Table, Filing Cabinet, Office Chair, Other
- Number of Seats: integer
- Number of Drawers: integer
- Cable Management: boolean
- Adjustable Height: boolean

## CAT-003-09 Shelf & Storage

- Storage Type: Bookshelf, Wall Shelf, Rack, Storage Rack, Shoe Rack, Plastic Storage, Other
- Number of Shelves: integer
- Wall Mounted: boolean
- Foldable: boolean
- Load Capacity: decimal
- Load Capacity Unit: select

## CAT-003-10 Kitchen Furniture

- Kitchen Item Type: Kitchen Cabinet, Kitchen Rack, Pantry Cabinet, Kitchen Island, Dining Cabinet, Other
- Number of Shelves: integer
- Number of Drawers: integer
- Countertop Included: boolean
- Sink Included: boolean
- Wall Mounted: boolean

## CAT-003-11 Home Decor

- Decor Type: Wall Art, Mirror, Clock, Vase, Curtain, Carpet, Rug, Lamp, Decorative Item, Other
- Style: Modern, Traditional, Minimalist, Vintage, Industrial, Other
- Indoor / Outdoor: Indoor, Outdoor, Both
- Handmade: boolean

## CAT-003-12 Other Furniture & Home

- Product Type: select
- Compatibility / Intended Use: text
- Key Features: text
- Common furniture attributes apply.

Rule: controlled fallback only; recurring product types should become dedicated subcategories.

## Listing-Type Applicability

All CAT-003 subcategories initially support: Sale, Exchange, Wanted.

Not initially exposed: Rent, Lease, Free, Offer, Service, Job.

## Catalogue Rules

- Common attributes are inherited by each subcategory unless explicitly overridden.
- Multi-value attributes are stored as multiple attribute values.
- Single-value attributes allow at most one value.
- Exactly one typed value representation is valid per attribute row.
- Option-backed values must use valid catalogue options.
- Requiredness, filterability, searchability, and multi-value behavior must be explicitly finalized before approval.

## Approval Record

- Approved: 2026-09-28
- Catalogue status: Approved
- The CAT-003 specification is now part of the approved v1 category catalogue.

# 6. CAT-004 — Vehicles

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-004-01 | Car | Primary catalogue scope for this subcategory. |
| CAT-004-02 | SUV / Jeep | Primary catalogue scope for this subcategory. |
| CAT-004-03 | Van / Minivan | Primary catalogue scope for this subcategory. |
| CAT-004-04 | Pickup | Primary catalogue scope for this subcategory. |
| CAT-004-05 | Truck | Primary catalogue scope for this subcategory. |
| CAT-004-06 | Bus / Microbus | Primary catalogue scope for this subcategory. |
| CAT-004-07 | Motorcycle | Primary catalogue scope for this subcategory. |
| CAT-004-08 | Scooter | Primary catalogue scope for this subcategory. |
| CAT-004-09 | Electric Two-Wheeler | Primary catalogue scope for this subcategory. |
| CAT-004-10 | Electric Car | Primary catalogue scope for this subcategory. |
| CAT-004-11 | Tractor & Agricultural Vehicle | Primary catalogue scope for this subcategory. |
| CAT-004-12 | Bicycle | Primary catalogue scope for this subcategory. |
| CAT-004-13 | Auto Rickshaw / Three-Wheeler | Primary catalogue scope for this subcategory. |
| CAT-004-14 | Vehicle Parts & Accessories | Primary catalogue scope for this subcategory. |
| CAT-004-15 | Other Vehicles | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Vehicle Attributes

| ID | Attribute | Type | Required | Filterable | Searchable | Multi |
| --- | --- | --- | --- | --- | --- | --- |
| VEH-ATTR-001 | Brand | text | No | Yes | Yes | No |
| VEH-ATTR-002 | Model | text | No | Yes | Yes | No |
| VEH-ATTR-003 | Variant / Trim | text | No | Yes | Yes | No |
| VEH-ATTR-004 | Manufacturing Year | integer | Yes | Yes | No | No |
| VEH-ATTR-005 | Registration Year | integer | No | Yes | No | No |
| VEH-ATTR-006 | Condition | select | Yes | Yes | No | No |
| VEH-ATTR-007 | Mileage / Usage | decimal | No | Yes | No | No |
| VEH-ATTR-008 | Mileage Unit | select | No | Yes | No | No |
| VEH-ATTR-009 | Fuel Type | select | No | Yes | Yes | No |
| VEH-ATTR-010 | Transmission | select | No | Yes | No | No |
| VEH-ATTR-011 | Color | select | No | Yes | Yes | No |
| VEH-ATTR-012 | Engine Capacity | integer | No | Yes | No | No |
| VEH-ATTR-013 | Engine Unit | select | No | Yes | No | No |
| VEH-ATTR-014 | Ownership Count | integer | No | Yes | No | No |
| VEH-ATTR-015 | Insurance Status | select | No | Yes | No | No |
| VEH-ATTR-016 | Insurance Expiry | date | No | Yes | No | No |
| VEH-ATTR-017 | Tax Status | select | No | Yes | No | No |
| VEH-ATTR-018 | Tax Expiry | date | No | Yes | No | No |
| VEH-ATTR-019 | Service History | boolean | No | Yes | No | No |
| VEH-ATTR-020 | Warranty Status | select | No | Yes | No | No |
| VEH-ATTR-021 | Warranty Expiry | date | No | Yes | No | No |
| VEH-ATTR-022 | Documents Available | multi_select | No | Yes | No | Yes |
| VEH-ATTR-023 | Features | multi_select | No | Yes | No | Yes |
| VEH-ATTR-024 | Seller Notes | text | No | No | Yes | No |

Condition = New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Fuel Type = Petrol, Diesel, Electric, Hybrid, CNG, LPG, Hydrogen, Other.

Transmission = Manual, Automatic, AMT, CVT, DCT, Other.

Mileage Unit = km, miles, hours. Engine Unit = cc, L.

Insurance Status = Active, Expired, None, Unknown.

Tax Status = Paid, Due, Overdue, Exempt, Unknown.

Warranty Status = Active, Expired, None, Manufacturer Warranty, Seller Warranty.

Documents Available = Blue Book, Insurance, Tax Receipt, Purchase Invoice, Service Records, Pollution Certificate, Registration Certificate, Other.

Features = Air Conditioning, Power Steering, Power Windows, Central Locking, ABS, Airbags, Sunroof, Cruise Control, Reverse Camera, Parking Sensors, Alloy Wheels, LED Headlights, Fog Lights, GPS, Bluetooth, Touchscreen, Android Auto, Apple CarPlay, Keyless Entry, Push Start, Heated Seats, Leather Seats, Roof Rack, 4WD, AWD.

## Subcategory Specifications

### CAT-004-01 Car

CAR-001 Body Type (select): Sedan, Hatchback, Coupe, Convertible, Wagon, Crossover, Other.

CAR-002 Seating Capacity (integer).

CAR-003 Door Count (integer).

CAR-004 Drive Type (select): FWD, RWD, AWD, 4WD, Other.

CAR-005 Number of Cylinders (integer).

CAR-006 Boot Capacity (decimal).

### CAT-004-02 SUV / Jeep

SUV-001 Body Type (select): Compact SUV, SUV, Crossover, Jeep, Off-road, Other.

SUV-002 Seating Capacity (integer).

SUV-003 Door Count (integer).

SUV-004 Drive Type (select).

SUV-005 Ground Clearance (decimal).

SUV-006 Number of Cylinders (integer).

### CAT-004-03 Van / Minivan

VAN-001 Seating Capacity (integer).

VAN-002 Door Count (integer).

VAN-003 Vehicle Purpose (select): Passenger, Cargo, Commercial, School, Tourism, Other.

VAN-004 Drive Type (select).

### CAT-004-04 Pickup

PICK-001 Cab Type (select): Single Cab, Double Cab, Extended Cab, Other.

PICK-002 Seating Capacity (integer).

PICK-003 Payload Capacity (decimal).

PICK-004 Payload Unit (select).

PICK-005 Drive Type (select).

PICK-006 Bed Type (select): Standard, Long Bed, Short Bed, Flatbed, Other.

### CAT-004-05 Truck

TRK-001 Truck Type (select): Light Truck, Medium Truck, Heavy Truck, Tipper, Tanker, Container Truck, Cargo Truck, Other.

TRK-002 Payload Capacity (decimal).

TRK-003 Payload Unit (select).

TRK-004 Axle Count (integer).

TRK-005 Drive Type (select).

TRK-006 Body Type (select).

### CAT-004-06 Bus / Microbus

BUS-001 Vehicle Type (select): Bus, Mini Bus, Microbus, Tourist Bus, School Bus, Other.

BUS-002 Seating Capacity (integer).

BUS-003 Door Count (integer).

BUS-004 Usage Type (select): Public Transport, Tourist, School, Staff, Private, Other.

BUS-005 Air Conditioning (boolean).

### CAT-004-07 Motorcycle

MOTO-001 Motorcycle Type (select): Standard, Sports, Cruiser, Adventure, Touring, Off-road, Dirt Bike, Other.

MOTO-002 Engine Capacity (integer).

MOTO-003 Seating Capacity (integer).

MOTO-004 Gear Count (integer).

MOTO-005 ABS (boolean).

MOTO-006 Electric Start (boolean).

### CAT-004-08 Scooter

SCOOT-001 Scooter Type (select): Standard, Maxi Scooter, Electric Scooter, Other.

SCOOT-002 Engine Capacity (integer).

SCOOT-003 Seating Capacity (integer).

SCOOT-004 Electric Start (boolean).

SCOOT-005 Underseat Storage (boolean).

### CAT-004-09 Electric Two-Wheeler

EV2-001 Vehicle Type (select): Electric Scooter, Electric Motorcycle, Electric Moped, Other.

EV2-002 Battery Capacity (decimal).

EV2-003 Battery Unit (select).

EV2-004 Range (decimal).

EV2-005 Range Unit (select).

EV2-006 Charging Time (decimal).

EV2-007 Battery Removable (boolean).

### CAT-004-10 Electric Car

EVC-001 Body Type (select).

EVC-002 Battery Capacity (decimal).

EVC-003 Battery Unit (select).

EVC-004 Range (decimal).

EVC-005 Range Unit (select).

EVC-006 Charging Time (decimal).

EVC-007 Charging Connector (select): Type 1, Type 2, CCS, CHAdeMO, GB/T, Other.

EVC-008 Seating Capacity (integer).

### CAT-004-11 Tractor & Agricultural Vehicle

AGR-001 Vehicle Type (select): Tractor, Power Tiller, Harvester, Agricultural Machine, Other.

AGR-002 Horsepower (decimal).

AGR-003 Drive Type (select).

AGR-004 PTO (boolean).

AGR-005 Hydraulic System (boolean).

AGR-006 Hours Used (decimal).

### CAT-004-12 Construction / Heavy Equipment

HEAVY-001 Equipment Type (select): Excavator, Backhoe Loader, Bulldozer, Loader, Crane, Roller, Grader, Forklift, Concrete Mixer, Other.

HEAVY-002 Operating Hours (decimal).

HEAVY-003 Engine Power (decimal).

HEAVY-004 Power Unit (select).

HEAVY-005 Operating Weight (decimal).

HEAVY-006 Weight Unit (select).

### CAT-004-13 Bicycle

BIKE-001 Bicycle Type (select): Mountain, Road, Hybrid, City, BMX, Kids, Folding, Electric, Other.

BIKE-002 Wheel Size (decimal).

BIKE-003 Frame Material (select): Steel, Aluminum, Carbon Fiber, Titanium, Other.

BIKE-004 Gear Count (integer).

BIKE-005 Suspension (select).

BIKE-006 Electric Assist (boolean).

### CAT-004-14 Auto Rickshaw / Three-Wheeler

THREE-001 Vehicle Type (select): Auto Rickshaw, Electric Three-Wheeler, Cargo Three-Wheeler, Passenger Three-Wheeler, Other.

THREE-002 Seating Capacity (integer).

THREE-003 Fuel Type (select).

THREE-004 Engine Capacity (integer).

THREE-005 Commercial Registration (boolean).

### CAT-004-15 Vehicle Parts & Accessories

| ID | Attribute | Type | Required | Filterable | Searchable | Multi |
| --- | --- | --- | --- | --- | --- | --- |
| VPA-001 | Part Type | select | Yes | Yes | Yes | No |
| VPA-002 | Brand | text | No | Yes | Yes | No |
| VPA-003 | Compatible Brand | text | No | Yes | Yes | Yes |
| VPA-004 | Compatible Model | text | No | Yes | Yes | Yes |
| VPA-005 | Part Number | text | No | Yes | Yes | No |
| VPA-006 | Condition | select | Yes | Yes | No | No |
| VPA-007 | Quantity | integer | No | Yes | No | No |

### CAT-004-16 Other Vehicles

Common vehicle attributes plus Product / Vehicle Type, Compatibility / Intended Use, and Key Features. Controlled fallback only.

## Listing-Type Applicability

All CAT-004 subcategories support **Sale, Exchange, Wanted**.

Rent, Lease, Free, Offer, Service, and Job are not initially exposed.

## Category Rules

- Common vehicle attributes inherit into applicable subcategories.
- EV-specific attributes apply only to electric vehicles.
- Engine attributes are not required for electric vehicles.
- Battery attributes are not required for conventional ICE vehicles.
- Multi-value compatibility, document, and feature attributes create multiple attribute rows.
- Single-value attributes allow at most one value.
- Exactly one typed value representation is valid for each attribute row.
- Option-backed values must match catalogue options.
- Required/filterable/searchable/multi-value flags are authoritative.
- Seller-provided document, insurance, tax, ownership, and authenticity claims are not independently verified merely because they are stored.

# 7. CAT-005 — Fashion & Clothing

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-005-01 | Men's Clothing | Primary catalogue scope for this subcategory. |
| CAT-005-02 | Women's Clothing | Primary catalogue scope for this subcategory. |
| CAT-005-03 | Kids' Clothing | Primary catalogue scope for this subcategory. |
| CAT-005-04 | Traditional & Ethnic Wear | Primary catalogue scope for this subcategory. |
| CAT-005-05 | Footwear | Primary catalogue scope for this subcategory. |
| CAT-005-06 | Fashion Bags & Wallets | Primary catalogue scope for this subcategory. |
| CAT-005-07 | Watches | Primary catalogue scope for this subcategory. |
| CAT-005-08 | Jewelry & Accessories | Primary catalogue scope for this subcategory. |
| CAT-005-09 | Wedding & Occasion Wear | Primary catalogue scope for this subcategory. |
| CAT-005-10 | Sportswear & Activewear | Primary catalogue scope for this subcategory. |
| CAT-005-11 | Baby & Infant Clothing | Primary catalogue scope for this subcategory. |
| CAT-005-12 | Uniforms & Workwear | Primary catalogue scope for this subcategory. |
| CAT-005-13 | Fashion Accessories | Primary catalogue scope for this subcategory. |
| CAT-005-14 | Other Fashion & Clothing | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Fashion & Clothing Attributes

| ID | Attribute | Type | Required | Filterable | Searchable | Multi |
| --- | --- | --- | --- | --- | --- | --- |
| FASH-ATTR-001 | Brand / Manufacturer | text | No | Yes | Yes | No |
| FASH-ATTR-002 | Product Name / Model | text | No | No | Yes | No |
| FASH-ATTR-003 | Condition | select | Yes | Yes | No | No |
| FASH-ATTR-004 | Size | select | No | Yes | Yes | No |
| FASH-ATTR-005 | Color | select | No | Yes | Yes | No |
| FASH-ATTR-006 | Material / Fabric | select | No | Yes | Yes | No |
| FASH-ATTR-007 | Pattern / Design | select | No | Yes | Yes | No |
| FASH-ATTR-008 | Gender / Target Group | select | No | Yes | Yes | No |
| FASH-ATTR-009 | Age Group | select | No | Yes | Yes | No |
| FASH-ATTR-010 | Purchase Year | integer | No | Yes | No | No |
| FASH-ATTR-011 | Original / Authentic | boolean | No | Yes | No | No |
| FASH-ATTR-012 | Warranty Status | select | No | Yes | No | No |
| FASH-ATTR-013 | Warranty Expiry | date | No | Yes | No | No |
| FASH-ATTR-014 | Quantity | integer | No | Yes | No | No |
| FASH-ATTR-015 | Packaging Available | boolean | No | Yes | No | No |
| FASH-ATTR-016 | Accessories Included | multi_select | No | Yes | No | Yes |
| FASH-ATTR-017 | Seller Notes | text | No | No | Yes | No |

Condition = New, Like New, Good, Fair, Needs Repair, Refurbished, Used, Handmade.

Gender / Target Group = Men, Women, Unisex, Boys, Girls, Other.

Age Group = Newborn, Infant, Toddler, Kids, Teen, Adult, Senior, All Ages.

Material / Fabric = Cotton, Polyester, Wool, Silk, Linen, Denim, Leather, Faux Leather, Nylon, Rayon, Velvet, Chiffon, Georgette, Synthetic, Mixed, Other.

Pattern / Design = Plain, Printed, Striped, Checked, Floral, Embroidered, Traditional, Graphic, Patterned, Other.

Warranty Status = None, Active, Expired, Seller Warranty, Manufacturer Warranty.

Accessories Included = Original Packaging, Tags, Belt, Scarf, Tie, Socks, Shoe Box, Dust Bag, Warranty Card, Other.

## Subcategory Specifications

### CAT-005-01 Men's Clothing

MEN-001 Clothing Type (select, required): Shirt, T-Shirt, Polo Shirt, Pants, Jeans, Trousers, Shorts, Jacket, Coat, Sweater, Hoodie, Blazer, Suit, Kurta, Daura Suruwal, Vest, Underwear, Other.

MEN-002 Sleeve Type (select). MEN-003 Fit Type (select): Slim, Regular, Relaxed, Oversized, Other. MEN-004 Collar Type (select). MEN-005 Occasion (select, multi): Casual, Formal, Office, Party, Wedding, Traditional, Sports, Other.

### CAT-005-02 Women's Clothing

WOMEN-001 Clothing Type (select, required): Saree, Kurta, Kurti, Salwar Suit, Lehenga, Dress, Gown, Blouse, Top, T-Shirt, Shirt, Jeans, Pants, Skirt, Jacket, Coat, Sweater, Hoodie, Shawl, Other.

WOMEN-002 Sleeve Type (select). WOMEN-003 Fit Type (select): Slim, Regular, Relaxed, Oversized, Other. WOMEN-004 Length Type (select): Crop, Waist, Hip, Knee, Midi, Ankle, Full Length, Other. WOMEN-005 Occasion (select, multi).

### CAT-005-03 Kids' Clothing

KIDS-001 Clothing Type (select, required): T-Shirt, Shirt, Pants, Jeans, Shorts, Dress, Skirt, Frock, Kurta, Jacket, Sweater, Hoodie, School Wear, Other.

KIDS-002 Age Range (select). KIDS-003 Size (select). KIDS-004 Occasion (select, multi). KIDS-005 Gender (select).

### CAT-005-04 Traditional & Ethnic Wear

ETHNIC-001 Wear Type (select, required): Saree, Daura Suruwal, Kurta Suruwal, Dhoti, Lehenga, Sherwani, Kurti, Salwar Suit, Tharu Wear, Maithili Wear, Newari Wear, Other.

ETHNIC-002 Cultural / Regional Style (select, multi). ETHNIC-003 Embroidery (boolean). ETHNIC-004 Handmade (boolean). ETHNIC-005 Occasion (select, multi).

### CAT-005-05 Footwear

FOOT-001 Footwear Type (select, required): Sports Shoes, Running Shoes, Sneakers, Formal Shoes, Sandals, Slippers, Boots, Heels, Flats, Loafers, School Shoes, Safety Shoes, Traditional Footwear, Other.

FOOT-002 Size (select, required). FOOT-003 Gender (select). FOOT-004 Sole Material (select). FOOT-005 Closure Type (select): Lace, Velcro, Buckle, Slip-on, Zip, Other. FOOT-006 Waterproof (boolean).

### CAT-005-06 Bags & Luggage

BAG-001 Bag Type (select, required): Backpack, Handbag, Shoulder Bag, Sling Bag, Laptop Bag, School Bag, Travel Bag, Suitcase, Trolley Bag, Wallet, Purse, Briefcase, Sports Bag, Other.

BAG-002 Material (select). BAG-003 Capacity (decimal). BAG-004 Capacity Unit (select). BAG-005 Number of Compartments (integer). BAG-006 Waterproof (boolean).

### CAT-005-07 Watches

WATCH-001 Watch Type (select, required): Analog, Digital, Smartwatch, Chronograph, Luxury, Sports, Other.

WATCH-002 Movement (select): Quartz, Mechanical, Automatic, Solar, Other. WATCH-003 Display Type (select): Analog, Digital, Analog-Digital. WATCH-004 Strap Material (select). WATCH-005 Water Resistance (boolean). WATCH-006 Smart Features (option, multi): Bluetooth, GPS, Heart Rate, Fitness Tracking, Calling, Notifications, Sleep Tracking, Other.

### CAT-005-08 Jewelry & Accessories

JEW-001 Jewelry Type (select, required): Ring, Necklace, Chain, Bracelet, Bangle, Earrings, Pendant, Anklet, Brooch, Nose Ring, Traditional Jewelry, Other.

JEW-002 Material (select). JEW-003 Gemstone (select, multi). JEW-004 Purity (select): 24K, 22K, 18K, 14K, 10K, Other. JEW-005 Handmade (boolean). JEW-006 Certificate Available (boolean).

### CAT-005-09 Wedding & Occasion Wear

OCC-001 Wear Type (select, required): Wedding Dress, Lehenga, Saree, Sherwani, Suit, Gown, Party Dress, Traditional Wear, Other.

OCC-002 Gender (select). OCC-003 Occasion (select, multi): Wedding, Engagement, Reception, Festival, Party, Formal Event, Traditional Ceremony, Other. OCC-004 Embroidery (boolean). OCC-005 Custom Made (boolean). OCC-006 Rental Available (boolean).

### CAT-005-10 Sportswear & Activewear

SPORT-001 Sportswear Type (select, required): Jersey, Tracksuit, Shorts, Sports T-Shirt, Sports Shoes, Compression Wear, Sports Jacket, Other.

SPORT-002 Sport (select, multi). SPORT-003 Size (select). SPORT-004 Gender (select). SPORT-005 Team / Club (text).

### CAT-005-11 Baby & Infant Clothing

BABY-001 Clothing Type (select, required): Bodysuit, Romper, Frock, T-Shirt, Pants, Jacket, Sweater, Sleepwear, Traditional Wear, Set, Other.

BABY-002 Age Range (select). BABY-003 Size (select). BABY-004 Gender (select). BABY-005 Material (select). BABY-006 Set Quantity (integer).

### CAT-005-12 Uniforms & Workwear

UNI-001 Uniform Type (select, required): School Uniform, College Uniform, Hospital Uniform, Security Uniform, Corporate Uniform, Industrial Workwear, Hospitality Uniform, Sports Uniform, Other.

UNI-002 Profession / Institution (select). UNI-003 Size (select). UNI-004 Gender (select). UNI-005 Customization Available (boolean). UNI-006 Bulk Quantity Available (integer).

### CAT-005-13 Fashion Accessories

ACC-001 Accessory Type (select, required): Belt, Tie, Scarf, Cap, Hat, Sunglasses, Gloves, Socks, Hair Accessories, Hair Clip, Headband, Wallet, Keychain, Other.

ACC-002 Material (select). ACC-003 Gender (select). ACC-004 Compatibility / Intended Use (text).

### CAT-005-14 Other Fashion & Clothing

Common fashion attributes plus Product Type, Intended Use, and Key Features. Controlled fallback only; recurring product types should be promoted to dedicated subcategories.

## Listing-Type Applicability

- Clothing, Footwear, Bags & Luggage, Watches, Jewelry & Accessories, Sportswear, Baby Clothing, Uniforms & Workwear, Fashion Accessories, and Other Fashion: **Sale, Exchange, Wanted**.
- Wedding & Occasion Wear: **Sale, Exchange, Wanted, Rent**.
- Lease, Service, Job, and Offer are not initially exposed.

## Category Rules

- Common fashion attributes inherit into applicable subcategories.
- Size is category-specific; footwear size is not treated as a generic clothing size.
- Jewelry purity and gemstone information apply only to relevant jewelry.
- Multi-value attributes create multiple attribute rows.
- Single-value attributes allow at most one value.
- Option-backed values must match valid catalogue options.
- Required/filterable/searchable/multi-value flags are authoritative.
- Seller-provided authenticity/originality claims are not independently verified merely because they are stored.

# 8. CAT-006 — Home Appliances & Kitchen

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-006-01 | Refrigerator & Freezer | Primary catalogue scope for this subcategory. |
| CAT-006-02 | Washing Machine | Primary catalogue scope for this subcategory. |
| CAT-006-03 | Air Conditioner | Primary catalogue scope for this subcategory. |
| CAT-006-04 | Microwave & Oven | Primary catalogue scope for this subcategory. |
| CAT-006-05 | Rice Cooker & Electric Cooker | Primary catalogue scope for this subcategory. |
| CAT-006-06 | Water Heater / Geyser | Primary catalogue scope for this subcategory. |
| CAT-006-07 | Water Purifier & Filter | Primary catalogue scope for this subcategory. |
| CAT-006-08 | Kitchen Appliances | Primary catalogue scope for this subcategory. |
| CAT-006-09 | Vacuum Cleaner | Primary catalogue scope for this subcategory. |
| CAT-006-10 | Fan & Air Circulation | Primary catalogue scope for this subcategory. |
| CAT-006-11 | Small Home Appliances | Primary catalogue scope for this subcategory. |
| CAT-006-12 | Solar / Inverter Appliances | Primary catalogue scope for this subcategory. |
| CAT-006-13 | Other Home Appliances | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| HOME-ATTR-001 | Brand | text. | No | No | No | No |
| HOME-ATTR-002 | Model | text. | No | No | No | No |
| HOME-ATTR-003 | Condition | select | Yes | No | No | No |
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
| HOME-ATTR-016 | Accessories Included | multi_select | No | No | No | Yes |
| HOME-ATTR-017 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Warranty Status: None, Active, Expired, Seller Warranty, Manufacturer Warranty.

Power Source: Electricity, Battery, Solar, Gas, LPG, Induction, Hybrid, Other.

Energy Rating: 1 Star, 2 Star, 3 Star, 4 Star, 5 Star, Other.

## Subcategory Specifications

Refrigerator & Freezer: Type, Door Count, Refrigerator Capacity, Freezer Capacity, Capacity Unit, Cooling Technology, Inverter, Ice Maker, Water Dispenser.

Washing Machine: Type, Capacity, Capacity Unit, Automatic Type, Spin Speed, Dryer, Inverter Motor, Loading Type.

Air Conditioner: Type, Cooling Capacity, Capacity Unit, Inverter, Energy Rating, Room Size, Refrigerant, Heating.

Microwave & Oven: Type, Capacity, Capacity Unit, Power, Power Unit, Convection, Grill, Rotisserie, Digital Control.

Rice Cooker & Electric Cooker: Type, Capacity, Capacity Unit, Power, Power Unit, Keep Warm, Timer, Inner Pot Material.

Water Heater / Geyser: Type, Capacity, Capacity Unit, Power, Heating Element, Temperature Control, Safety Features.

Water Purifier & Filter: Type, Filtration Type, Storage Capacity, Capacity Unit, Purification Capacity, UV/RO/UF, Filter Replacement.

Kitchen Appliances: Type, Capacity, Capacity Unit, Power, Material, Functions, Accessories. Types include blender, mixer grinder, juicer, food processor, kettle, toaster, sandwich maker, coffee maker, hand blender, chopper, air fryer, electric grill, other.

Vacuum Cleaner: Type, Power, Power Unit, Dust Capacity, Capacity Unit, Cordless, Wet/Dry, HEPA, Attachments.

Fan & Air Circulation: Type, Blade Count, Sweep Size, Sweep Size Unit, Speed Levels, Remote, Oscillation, Power.

Small Home Appliances: Type, Capacity, Power, Key Functions.

Solar / Inverter Appliances: Appliance Type, System Type, Power Capacity, Power Unit, Battery Capacity, Battery Unit, Backup Time, Solar Compatible, Inverter Type.

Other Home Appliances: Common attributes plus Product Type, Intended Use, Key Features.

## Listing Types

Sale, Exchange, Wanted. Rent, Lease, Job, and Service are not initially exposed.

## Category Rules

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

# 9. CAT-007 — Sports, Fitness & Outdoor

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-007-01 | Fitness Equipment | Primary catalogue scope for this subcategory. |
| CAT-007-02 | Gym Equipment | Primary catalogue scope for this subcategory. |
| CAT-007-03 | Yoga & Pilates | Primary catalogue scope for this subcategory. |
| CAT-007-04 | Cricket | Primary catalogue scope for this subcategory. |
| CAT-007-05 | Football | Primary catalogue scope for this subcategory. |
| CAT-007-06 | Basketball | Primary catalogue scope for this subcategory. |
| CAT-007-07 | Badminton & Tennis | Primary catalogue scope for this subcategory. |
| CAT-007-08 | Table Tennis | Primary catalogue scope for this subcategory. |
| CAT-007-09 | Cycling Equipment | Primary catalogue scope for this subcategory. |
| CAT-007-10 | Camping & Hiking | Primary catalogue scope for this subcategory. |
| CAT-007-11 | Fishing | Primary catalogue scope for this subcategory. |
| CAT-007-12 | Swimming & Water Sports | Primary catalogue scope for this subcategory. |
| CAT-007-13 | Martial Arts & Combat Sports | Primary catalogue scope for this subcategory. |
| CAT-007-14 | Sports Accessories | Primary catalogue scope for this subcategory. |
| CAT-007-15 | Outdoor Recreation | Primary catalogue scope for this subcategory. |
| CAT-007-16 | Other Sports & Outdoor | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| SPORT-ATTR-001 | Brand / Manufacturer | text | No | Yes | Yes | No |
| SPORT-ATTR-002 | Model / Product Name | text | No | Yes | Yes | No |
| SPORT-ATTR-003 | Condition | select | Yes | Yes | No | No |
| SPORT-ATTR-004 | Material | select | No | Yes | Yes | No |
| SPORT-ATTR-005 | Size | select | No | Yes | Yes | No |
| SPORT-ATTR-006 | Color | select | No | Yes | Yes | No |
| SPORT-ATTR-007 | Weight | decimal | No | Yes | No | No |
| SPORT-ATTR-008 | Weight Unit | select | No | Yes | No | No |
| SPORT-ATTR-009 | Purchase Year | integer | No | Yes | No | No |
| SPORT-ATTR-010 | Warranty Status | select | No | Yes | No | No |
| SPORT-ATTR-011 | Warranty Expiry | date | No | Yes | No | No |
| SPORT-ATTR-012 | Suitable Age Group | select | No | Yes | Yes | No |
| SPORT-ATTR-013 | Skill Level | select | No | Yes | Yes | No |
| SPORT-ATTR-014 | Quantity | integer | No | Yes | No | No |
| SPORT-ATTR-015 | Accessories Included | multi_select | No | Yes | No | Yes |
| SPORT-ATTR-016 | Seller Notes | text | No | No | Yes | No |

## Subcategory Attribute Baseline

Fitness Equipment: Equipment Type, Resistance Type, Maximum User Weight, Maximum User Weight Unit, Adjustable, Foldable, Digital Display, Power Required.

Gym Equipment: Equipment Type, Weight Capacity, Weight Unit, Resistance Type, Adjustable, Weight Plates Included, Assembly Required.

Yoga & Pilates: Product Type, Material, Thickness, Thickness Unit, Length, Width, Non-Slip.

Cricket: Equipment Type, Playing Level, Bat Size, Bat Material, Ball Type, Protective Equipment Type.

Football: Product Type, Ball Size, Material, Surface Type, Goal Type, Pump Included.

Basketball: Product Type, Ball Size, Material, Hoop Type, Adjustable Height.

Badminton & Tennis: Sport, Product Type, Racket Material, Weight, Weight Unit, String Tension, String Tension Unit, Grip Size, Set Quantity.

Table Tennis: Product Type, Table Type, Table Thickness, Paddle Material, Net Included, Set Quantity.

Cycling Equipment: Product Type, Compatibility/Bicycle Type, Wheel Size, Wheel Size Unit, Material, Helmet Size, Safety Certification, Electric Compatibility.

Camping & Hiking: Equipment Type, Capacity, Capacity Unit, Number of Persons, Waterproof, Season Rating, Packed Size.

Fishing: Equipment Type, Rod Length, Rod Length Unit, Reel Type, Line Capacity, Target Fish (multi), Saltwater Compatible.

Swimming & Water Sports: Equipment Type, Size, Material, Buoyancy Aid, Suitable Water Type (multi).

Martial Arts & Combat Sports: Equipment Type, Sport/Discipline (multi), Size, Protective Equipment, Material.

Sports Accessories: Accessory Type, Sport (multi), Compatibility, Material, Quantity.

Outdoor Recreation: Recreation Type, Equipment Type, Capacity, Capacity Unit, Number of Persons, Portable, Safety Equipment Included.

Other Sports & Outdoor: Product Type, Sport/Activity, Intended Use, Key Features.

## Listing Types

Default: Sale, Exchange, Wanted.

Rent additionally applies to Camping & Hiking, Swimming & Water Sports, and Outdoor Recreation where applicable.

Lease, Service, Job, and Offer are not initially exposed.

## Category Rules

- Common attributes inherit into applicable subcategories.
- Equipment-specific technical attributes remain scoped to the relevant activity.
- Measurements require explicit units.
- Multi-value attributes create multiple attribute rows.
- Single-value attributes allow at most one value.
- Option-backed values must match approved catalogue options.
- Required/filterable/searchable/multi-value flags are authoritative.
- Other Sports & Outdoor is a controlled fallback.
- Safety/certification information is seller-provided unless independently verified.
- Rental availability affects permitted listing type, not product category.

# 10. CAT-008 — Jobs & Employment

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-008-01 | Full-Time Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-02 | Part-Time Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-03 | Contract / Temporary Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-04 | Freelance Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-05 | Internship / Trainee | Primary catalogue scope for this subcategory. |
| CAT-008-06 | Work From Home / Remote | Primary catalogue scope for this subcategory. |
| CAT-008-07 | Government / Public Sector Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-08 | Teaching & Education Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-09 | Healthcare Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-10 | IT & Technology Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-11 | Sales & Marketing Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-12 | Hospitality & Tourism Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-13 | Construction & Skilled Trades | Primary catalogue scope for this subcategory. |
| CAT-008-14 | Driver & Delivery Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-15 | Domestic & Household Jobs | Primary catalogue scope for this subcategory. |
| CAT-008-16 | Other Jobs | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| JOB-ATTR-001 | Employer / Organization | text | Yes | Yes | Yes | No |
| JOB-ATTR-002 | Job Title | text | Yes | Yes | Yes | No |
| JOB-ATTR-003 | Employment Type | select | Yes | Yes | Yes | No |
| JOB-ATTR-004 | Work Mode | select | Yes | Yes | Yes | No |
| JOB-ATTR-005 | Experience Level | select | No | Yes | Yes | No |
| JOB-ATTR-006 | Experience Required | decimal | No | Yes | No | No |
| JOB-ATTR-007 | Experience Unit | select | No | Yes | No | No |
| JOB-ATTR-008 | Education Level | select | No | Yes | Yes | No |
| JOB-ATTR-009 | Skills | multi_select | No | Yes | Yes | Yes |
| JOB-ATTR-010 | Salary Minimum | decimal | No | Yes | No | No |
| JOB-ATTR-011 | Salary Maximum | decimal | No | Yes | No | No |
| JOB-ATTR-012 | Salary Period | select | No | Yes | No | No |
| JOB-ATTR-013 | Salary Currency | select | No | Yes | No | No |
| JOB-ATTR-014 | Vacancy Count | integer | No | Yes | No | No |
| JOB-ATTR-015 | Application Deadline | date | No | Yes | No | No |
| JOB-ATTR-016 | Gender Preference | select | No | Yes | No | No |
| JOB-ATTR-017 | Age Requirement | text | No | Yes | No | No |
| JOB-ATTR-018 | Benefits | multi_select | No | Yes | Yes | Yes |
| JOB-ATTR-019 | Required Languages | multi_select | No | Yes | Yes | Yes |
| JOB-ATTR-020 | Job Description | text | Yes | No | Yes | No |
| JOB-ATTR-021 | Application Instructions | text | Yes | No | Yes | No |
| JOB-ATTR-022 | Seller / Employer Notes | text | No | No | Yes | No |

## Controlled Values

Employment Type: Full-Time, Part-Time, Contract, Temporary, Freelance, Internship, Apprenticeship, Volunteer, Seasonal, Other.

Work Mode: On-site, Remote, Hybrid, Field Work, Other.

Experience Level: No Experience, Entry Level, Junior, Mid Level, Senior, Manager, Executive, Other.

Experience Unit: Months, Years.

Education Level: No Formal Education, SEE / Equivalent, +2 / Intermediate, Diploma, Bachelor, Master, MPhil, PhD, Professional Certification, Other.

Salary Period: Hourly, Daily, Weekly, Monthly, Annual, Project Based, Negotiable.

Salary Currency: NPR, USD, INR, Other.

Gender Preference: Any, Male, Female, Other.

Benefits: Provident Fund, Insurance, Health Insurance, Accident Insurance, Paid Leave, Festival Allowance, Dashain Bonus, Transportation, Food / Meal, Accommodation, Training, Communication Allowance, Internet Allowance, Performance Bonus, Other.

Required Languages: Nepali, Maithili, Bhojpuri, Newari, Tamang, Tharu, Hindi, English, Urdu, Other.

## Subcategory Specifications

Full-Time: Job Category, Work Schedule, Probation Period, Office Location, Relocation Required, Benefits.

Part-Time: Hours Per Week, Work Schedule, Shift, Duration, Duration Unit.

Contract / Temporary: Contract Duration, Duration Unit, Contract Type, Renewable, Project Name.

Freelance: Project Type, Project Duration, Duration Unit, Payment Type, Remote Allowed, Deliverables, Required Portfolio.

Internship / Trainee: Internship Type, Duration, Duration Unit, Paid / Unpaid, Stipend, Training Provided, Potential Employment.

Work From Home / Remote: Remote Type, Required Time Zone, Required Internet, Equipment Provided, Communication Platform, Location Restriction.

Government / Public Sector: Government Level, Organization, Position Level, Exam Required, Application Method, Official Notice Reference.

Teaching & Education: Teaching Level, Subject, Teaching Qualification, Classroom / Online, Certification Required, Institution Type.

Healthcare: Profession, Specialization, Qualification, License Required, Experience, Shift Type, Institution Type.

IT & Technology: Technology Role, Technical Skills, Programming Languages, Frameworks / Platforms, Certification, Portfolio Required, Remote Availability.

Sales & Marketing: Sales / Marketing Role, Industry, Target / Commission, Travel Required, Field Work, Communication Skills.

Hospitality & Tourism: Job Role, Establishment Type, Shift Type, Accommodation Provided, Food Provided, Tourism Experience Required.

Construction & Skilled Trades: Trade Type, Skill Level, Certification Required, Tools Provided, Accommodation, Field Location.

Driver & Delivery: Driver Type, License Category, Vehicle Type, Experience Required, Commercial License Required, Own Vehicle Required, Route / Area, Accommodation.

Domestic & Household: Job Type, Live-in / Live-out, Working Hours, Accommodation, Food Provided, Experience Required, Number of Persons / Household.

Other Jobs: Job Type, Industry, Required Skills, Intended Role, Key Requirements.

## Listing Types

Job and Wanted only. Sale, Exchange, Rent, Lease, Free, Offer, and Service are not applicable.

## Category Rules

- Employer/organization and job poster identity are separate concepts.
- A business may publish jobs through authorized business members.
- Salary minimum, maximum, period, and currency are modeled independently.
- Salary may be negotiable without requiring numeric values.
- Skills and languages are multi-value.
- Application deadline is distinct from listing expiration.
- Government/public-sector listings support an official source/reference.
- Qualification and licensing requirements are seller/employer-provided unless independently verified.
- Sensitive applicant information is not stored as ordinary listing attributes.
- Job listings follow review-before-publication lifecycle.
- Expired jobs are not searchable as active opportunities.
- Other Jobs is a controlled fallback.

# 11. CAT-009 — Services

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-009-01 | Home & Domestic Services | Primary catalogue scope for this subcategory. |
| CAT-009-02 | Repair & Maintenance | Primary catalogue scope for this subcategory. |
| CAT-009-03 | Construction & Renovation Services | Primary catalogue scope for this subcategory. |
| CAT-009-04 | Automotive Services | Primary catalogue scope for this subcategory. |
| CAT-009-05 | IT & Digital Services | Primary catalogue scope for this subcategory. |
| CAT-009-06 | Business & Professional Services | Primary catalogue scope for this subcategory. |
| CAT-009-07 | Education & Training | Primary catalogue scope for this subcategory. |
| CAT-009-08 | Health & Wellness Services | Primary catalogue scope for this subcategory. |
| CAT-009-09 | Beauty & Personal Care | Primary catalogue scope for this subcategory. |
| CAT-009-10 | Photography & Videography | Primary catalogue scope for this subcategory. |
| CAT-009-11 | Events & Entertainment | Primary catalogue scope for this subcategory. |
| CAT-009-12 | Travel & Tourism Services | Primary catalogue scope for this subcategory. |
| CAT-009-13 | Delivery & Moving Services | Primary catalogue scope for this subcategory. |
| CAT-009-14 | Financial & Legal Services | Primary catalogue scope for this subcategory. |
| CAT-009-15 | Agricultural Services | Primary catalogue scope for this subcategory. |
| CAT-009-16 | Other Services | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| SERV-ATTR-001 | Service Provider | text | Yes | Yes | Yes | No |
| SERV-ATTR-002 | Service Title | text | Yes | Yes | Yes | No |
| SERV-ATTR-003 | Service Type | select | Yes | Yes | Yes | No |
| SERV-ATTR-004 | Service Description | text | Yes | No | Yes | No |
| SERV-ATTR-005 | Service Area | json | Yes | Yes | Yes | Yes |
| SERV-ATTR-006 | Availability | select | No | Yes | Yes | No |
| SERV-ATTR-007 | Pricing Type | select | No | Yes | Yes | No |
| SERV-ATTR-008 | Starting Price | decimal | No | Yes | No | No |
| SERV-ATTR-009 | Price Unit | select | No | Yes | No | No |
| SERV-ATTR-010 | Experience | decimal | No | Yes | No | No |
| SERV-ATTR-011 | Experience Unit | select | No | Yes | No | No |
| SERV-ATTR-012 | Skills / Expertise | multi_select | No | Yes | Yes | Yes |
| SERV-ATTR-013 | Languages | multi_select | No | Yes | Yes | Yes |
| SERV-ATTR-014 | Service Delivery Mode | select | No | Yes | Yes | No |
| SERV-ATTR-015 | Emergency Service | boolean | No | Yes | No | No |
| SERV-ATTR-016 | Home Visit | boolean | No | Yes | No | No |
| SERV-ATTR-017 | Booking Required | boolean | No | Yes | No | No |
| SERV-ATTR-018 | Warranty / Service Guarantee | text | No | No | Yes | No |
| SERV-ATTR-019 | Certifications | multi_select | No | Yes | Yes | Yes |
| SERV-ATTR-020 | Provider Notes | text | No | No | Yes | No |

## Controlled Values

Availability: Available Now, By Appointment, Weekdays, Weekends, Evenings, Flexible, Seasonal, Other.

Pricing Type: Fixed Price, Starting From, Hourly, Daily, Monthly, Per Visit, Per Project, Negotiable, Free.

Price Unit: Hour, Day, Visit, Project, Item, Month, Other.

Experience Unit: Months, Years.

Service Delivery Mode: On-site, At Customer Location, Provider Location, Remote / Online, Mobile, Hybrid.

## Subcategory Specifications

Home & Domestic: Service Type, Household Task, Frequency, Number of Persons / Rooms, Live-in / Live-out, Supplies Provided, Equipment Provided.

Repair & Maintenance: Repair Type, Equipment / Product Type, Brand Compatibility, Parts Included, Parts Cost Included, Diagnosis Available, Warranty Period.

Construction & Renovation: Service Type, Construction Stage, Property Type, Work Area, Materials Provided, Labor Only, Site Visit Available, Estimated Duration.

Automotive Services: Vehicle Type, Service Type, Compatible Brands, Mobile Service, Parts Provided, Diagnostic Service, Emergency Roadside Service.

IT & Digital: Service Type, Technology / Platform, Programming Language, Framework / CMS, Project Type, Remote Available, Portfolio Available, Maintenance Included.

Business & Professional: Professional Service Type, Industry, Business Size, Consultation Available, On-site / Remote, Certification, Deliverable Type.

Education & Training: Subject / Skill, Education Level, Training Type, Class Mode, Class Size, Course Duration, Certification Provided, Trial Class.

Health & Wellness: Service Type, Specialty, Consultation Type, Location Type, Appointment Required, Certification, Emergency Availability.

Beauty & Personal Care: Service Type, Gender / Customer Group, Home Service, Appointment Required, Product Included, Package Type, Duration.

Photography & Videography: Service Type, Event Type, Photography / Video, Equipment Type, Editing Included, Number of Hours, Deliverables, Album Included, Drone Service.

Events & Entertainment: Service Type, Event Type, Guest Capacity, Performance Duration, Equipment Included, Setup Included, Travel Available.

Travel & Tourism: Service Type, Destination, Tour Type, Number of Persons, Duration, Transportation Included, Accommodation Included, Guide Included, Package Type.

Delivery & Moving: Service Type, Vehicle Type, Maximum Load, Service Area, Loading / Unloading, Packing Included, Insurance Available, Same-Day Service.

Financial & Legal: Service Type, Professional Specialty, Consultation Type, Certification / License, Remote Consultation, Appointment Required, Document Type.

Agricultural Services: Service Type, Crop Type, Farm Size, Equipment Type, Labor / Equipment, Seasonal Availability, Service Area.

Other Services: Service Type, Industry / Activity, Intended Use, Key Features.

## Listing Types

Service and Wanted are applicable. Offer may be used for explicitly modeled promotional/service offers. Sale, Exchange, Rent, Lease, Free, and Job are not applicable.

## Category Rules

- Service provider identity and listing poster identity remain separate.
- Businesses may publish services through authorized business members.
- Service area uses the existing structured location model and supports multiple areas.
- Pricing is optional because many services require quotation.
- Starting Price is not interpreted as a guaranteed final price.
- Skills, languages, certifications, and compatible brands can be multi-value.
- Service-specific technical attributes remain scoped to the relevant subcategory.
- Health, legal, financial, and other regulated professional claims remain provider-supplied unless independently verified.
- Emergency availability is explicit and never inferred from category.
- Service listings follow the standard Draft → Review → Published ↔ Paused → Expired → Archived lifecycle.
- Other Services is the controlled fallback.

# 12. CAT-010 — Business, Office & Commercial Equipment

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-010-01 | Computers & Office Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-02 | Printers, Scanners & Copiers | Primary catalogue scope for this subcategory. |
| CAT-010-03 | Networking & Communication Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-04 | POS & Billing Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-05 | Security & Surveillance Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-06 | Commercial Kitchen Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-07 | Restaurant & Hospitality Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-08 | Tools & Workshop Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-09 | Medical & Laboratory Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-10 | Shop & Display Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-11 | Packaging & Printing Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-12 | Office Furniture & Fixtures | Primary catalogue scope for this subcategory. |
| CAT-010-13 | Solar, Power & Electrical Equipment | Primary catalogue scope for this subcategory. |
| CAT-010-14 | Other Commercial Equipment | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| COMM-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| COMM-ATTR-002 | Model / Product Name | text | Yes | Yes | Yes | No |
| COMM-ATTR-003 | Equipment Type | select | Yes | Yes | Yes | No |
| COMM-ATTR-004 | Condition | select | Yes | Yes | Yes | No |
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
| COMM-ATTR-017 | Accessories Included | multi_select | No | No | No | Yes |
| COMM-ATTR-018 | Installation Included | boolean. | No | No | No | No |
| COMM-ATTR-019 | Service / Maintenance Available | boolean. | No | No | No | No |
| COMM-ATTR-020 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Power Source: Electricity, Battery, Solar, Diesel, Petrol, LPG, Gas, Manual, Hybrid, Other.

Warranty Status: None, Active, Expired, Seller Warranty, Manufacturer Warranty.

Power Unit: W, kW, HP, VA, kVA, Other.

## Subcategory Specifications

Computers & Office Equipment: Equipment Type, Processor, RAM, Storage Type, Storage Capacity, Operating System, Screen Size, Connectivity, Business Use Type.

Printers, Scanners & Copiers: Equipment Type, Print Technology, Color / Mono, Print Speed, Paper Size, Duplex, Network Printing, Scan Resolution, Monthly Duty Cycle.

Networking & Communication: Equipment Type, Network Standard, Number of Ports, Port Type, Wireless Standard, Speed, PoE Support, Managed / Unmanaged, SIM Support.

POS & Billing: Equipment Type, POS Software Compatibility, Receipt Printer, Barcode Scanner, Cash Drawer, Display Type, Touchscreen, Connectivity, Operating System.

Security & Surveillance: Equipment Type, Camera Type, Resolution, Night Vision, Storage Type, Storage Capacity, Number of Channels, Indoor / Outdoor, Motion Detection, Audio Support.

Commercial Kitchen: Equipment Type, Capacity, Capacity Unit, Fuel Type, Power Rating, Temperature Range, Material, Number of Burners / Sections, Commercial Grade.

Restaurant & Hospitality: Equipment Type, Capacity, Capacity Unit, Number of Persons / Units, Material, Commercial Grade, Installation Required, Service Availability.

Tools & Workshop: Tool Type, Application, Power Type, Power Rating, Voltage, Material, Compatible Accessories, Professional / Consumer Grade.

Medical & Laboratory: Equipment Type, Medical / Laboratory Use, Manufacturer, Model, Measurement Range, Accuracy, Certification, Calibration Available, Consumables Required.

Shop & Display: Equipment Type, Display Type, Material, Dimensions, Shelving, Number of Shelves, Lighting Included, Lockable, Portable.

Packaging & Printing: Equipment Type, Application, Production Speed, Capacity, Material Compatibility, Automation Level, Power Rating, Consumables.

Office Furniture & Fixtures: Furniture Type, Material, Seating Capacity, Number of Units, Dimensions, Storage Type, Assembly Required, Commercial Grade.

Solar, Power & Electrical: Equipment Type, Rated Power, Power Unit, Voltage, Battery Capacity, Battery Unit, Phase, Solar Compatible, Inverter Type, Backup Time.

Other Commercial Equipment: Common attributes plus Equipment Type, Commercial Application, Intended Use, Key Features.

## Listing Types

Sale, Exchange, Wanted, Rent, Lease, Free, and Offer where commercially appropriate. Service and Job are not applicable.

## Category Rules

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

# 13. CAT-011 — Baby, Kids & Toys

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-011-01 | Baby Clothing & Accessories | Primary catalogue scope for this subcategory. |
| CAT-011-02 | Baby Gear & Carriers | Primary catalogue scope for this subcategory. |
| CAT-011-03 | Strollers & Prams | Primary catalogue scope for this subcategory. |
| CAT-011-04 | Baby Furniture | Primary catalogue scope for this subcategory. |
| CAT-011-05 | Feeding & Nursing | Primary catalogue scope for this subcategory. |
| CAT-011-06 | Diapering & Baby Care | Primary catalogue scope for this subcategory. |
| CAT-011-07 | Toys | Primary catalogue scope for this subcategory. |
| CAT-011-08 | Educational Toys & Learning | Primary catalogue scope for this subcategory. |
| CAT-011-09 | Outdoor & Ride-On Toys | Primary catalogue scope for this subcategory. |
| CAT-011-10 | Video Games & Kids Electronics | Primary catalogue scope for this subcategory. |
| CAT-011-11 | Kids Books & Educational Materials | Primary catalogue scope for this subcategory. |
| CAT-011-12 | Party & Kids Event Supplies | Primary catalogue scope for this subcategory. |
| CAT-011-13 | Safety & Childproofing | Primary catalogue scope for this subcategory. |
| CAT-011-14 | Baby Health & Wellness Products | Primary catalogue scope for this subcategory. |
| CAT-011-15 | Kids Sports & Activity Equipment | Primary catalogue scope for this subcategory. |
| CAT-011-16 | Other Baby, Kids & Toys | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| KIDS-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| KIDS-ATTR-002 | Product Name / Model | text. | No | No | No | No |
| KIDS-ATTR-003 | Condition | select. | No | No | No | No |
| KIDS-ATTR-004 | Age Group | select. | No | No | No | No |
| KIDS-ATTR-005 | Recommended Age | select. | No | No | No | No |
| KIDS-ATTR-006 | Material | select. | No | No | No | No |
| KIDS-ATTR-007 | Color | select. | No | No | No | No |
| KIDS-ATTR-008 | Size | select. | No | No | No | No |
| KIDS-ATTR-009 | Gender / Target Group | select. | No | No | No | No |
| KIDS-ATTR-010 | Quantity | integer. | No | No | No | No |
| KIDS-ATTR-011 | Purchase Year | integer. | No | No | No | No |
| KIDS-ATTR-012 | Warranty Status | select. | No | No | No | No |
| KIDS-ATTR-013 | Accessories Included | multi_select | No | No | No | Yes |
| KIDS-ATTR-014 | Original Packaging | boolean. | No | No | No | No |
| KIDS-ATTR-015 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Age Group: Newborn, 0–3 Months, 3–6 Months, 6–12 Months, 1–2 Years, 2–3 Years, 3–5 Years, 5–8 Years, 8–12 Years, 12+ Years, All Ages.

Target Group: Boys, Girls, Unisex, All.

## Subcategory Specifications

Baby Clothing & Accessories: Clothing Type, Size, Fabric, Season, Set Quantity, Gender, Occasion.

Baby Gear & Carriers: Product Type, Weight Capacity, Weight Capacity Unit, Adjustable, Foldable, Safety Harness, Material.

Strollers & Prams: Type, Age Range, Weight Capacity, Reclining, Foldable, Wheel Type, Safety Harness, Storage Basket, Rain Cover.

Baby Furniture: Furniture Type, Material, Dimensions, Adjustable, Foldable, Safety Rail, Mattress Included, Assembly Required.

Feeding & Nursing: Product Type, Material, Capacity, Capacity Unit, BPA-Free, Sterilization Compatible, Age Suitability.

Diapering & Baby Care: Product Type, Size, Material, Quantity, Reusable, Fragrance-Free, Intended Age.

Toys: Toy Type, Material, Recommended Age, Battery Required, Battery Included, Educational, Indoor / Outdoor, Number of Pieces.

Educational Toys & Learning: Learning Type, Subject, Skill Level, Age Group, Language, Number of Pieces, Battery / Electronic.

Outdoor & Ride-On Toys: Product Type, Age Group, Weight Capacity, Electric / Manual, Battery Voltage, Maximum Speed, Safety Equipment, Assembly Required.

Video Games & Kids Electronics: Device Type, Platform, Compatibility, Storage, Screen Size, Parental Controls, Accessories, Age Rating.

Kids Books & Educational Materials: Material Type, Subject, Language, Age Group, Grade Level, Author / Publisher, Edition.

Party & Kids Event Supplies: Product Type, Event Type, Age Group, Theme, Quantity, Reusable, Decoration Type.

Safety & Childproofing: Product Type, Installation Type, Compatible Location, Material, Safety Function, Age Suitability, Certification.

Baby Health & Wellness Products: Product Type, Intended Use, Age Suitability, Material, Measurement Type, Battery Required, Certification.

Kids Sports & Activity Equipment: Equipment Type, Sport / Activity, Age Group, Size, Material, Safety Equipment Included, Skill Level.

Other Baby, Kids & Toys: Product Type, Intended Age, Intended Use, Key Features.

## Listing Types

Sale, Exchange, Wanted, Free. Rent may apply to appropriate reusable products. Lease, Service, and Job are not applicable. Offer may be used where explicitly modeled.

## Category Rules

- Age suitability is independently filterable from category.
- Safety-related attributes do not imply certification unless verified.
- Battery/electrical attributes apply only to relevant products.
- Multi-value attributes use separate attribute rows; single-value attributes allow at most one.
- Used baby products may require additional condition/safety information.
- Safety-sensitive products may receive additional moderation restrictions.
- Other Baby, Kids & Toys is the controlled fallback.
- Rental applies only to appropriate reusable products such as selected baby gear, toys, and event supplies.
- All listings follow the standard review-before-publication lifecycle.

# 14. CAT-012 — Books, Media & Collectibles

**Status:** APPROVED — 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-012-01 | Books & Novels | Primary catalogue scope for this subcategory. |
| CAT-012-02 | Academic & Educational Books | Primary catalogue scope for this subcategory. |
| CAT-012-03 | Religious & Spiritual Books | Primary catalogue scope for this subcategory. |
| CAT-012-04 | Magazines, Newspapers & Periodicals | Primary catalogue scope for this subcategory. |
| CAT-012-05 | Comics & Graphic Novels | Primary catalogue scope for this subcategory. |
| CAT-012-06 | Music & Audio Media | Primary catalogue scope for this subcategory. |
| CAT-012-07 | Movies & Video Media | Primary catalogue scope for this subcategory. |
| CAT-012-08 | Collectibles | Primary catalogue scope for this subcategory. |
| CAT-012-09 | Antiques & Vintage Items | Primary catalogue scope for this subcategory. |
| CAT-012-10 | Coins & Currency Collectibles | Primary catalogue scope for this subcategory. |
| CAT-012-11 | Stamps & Postal Collectibles | Primary catalogue scope for this subcategory. |
| CAT-012-12 | Art, Prints & Posters | Primary catalogue scope for this subcategory. |
| CAT-012-13 | Trading Cards & Memorabilia | Primary catalogue scope for this subcategory. |
| CAT-012-14 | Musical Instruments & Accessories | Primary catalogue scope for this subcategory. |
| CAT-012-15 | Hobby & Craft Collections | Primary catalogue scope for this subcategory. |
| CAT-012-16 | Other Books, Media & Collectibles | Primary catalogue scope for this subcategory. |

## Common Attributes

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| MEDIA-ATTR-001 | Item Type | select | Yes | Yes | Yes | No |
| MEDIA-ATTR-002 | Title / Name | text | Yes | Yes | Yes | No |
| MEDIA-ATTR-003 | Author / Creator / Artist | text | No | Yes | Yes | Yes |
| MEDIA-ATTR-004 | Publisher / Manufacturer | text | No | Yes | Yes | No |
| MEDIA-ATTR-005 | Condition | select | Yes | Yes | Yes | No |
| MEDIA-ATTR-006 | Year / Publication Year | integer | No | Yes | No | No |
| MEDIA-ATTR-007 | Edition | text | No | Yes | Yes | No |
| MEDIA-ATTR-008 | Language | select | No | Yes | Yes | Yes |
| MEDIA-ATTR-009 | ISBN / Catalog Number | text | No | Yes | Yes | No |
| MEDIA-ATTR-010 | Material / Format | select | No | Yes | Yes | No |
| MEDIA-ATTR-011 | Quantity | integer | No | Yes | No | No |
| MEDIA-ATTR-012 | Signed / Autographed | boolean | No | Yes | No | No |
| MEDIA-ATTR-013 | Original / Authenticity Status | select | No | Yes | Yes | No |
| MEDIA-ATTR-014 | Certificate / Documentation | boolean | No | Yes | No | No |
| MEDIA-ATTR-015 | Seller Notes | text | No | No | Yes | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Poor, Damaged, Restored, Used.

Language: Nepali, Maithili, Bhojpuri, Hindi, English, Urdu, Newari, Sanskrit, Other.

Authenticity Status: Original, Reproduction, Replica, Reprint, Unknown, Not Applicable.

## Subcategory Specifications

Books & Novels: Genre, Author, Publisher, Edition, ISBN, Publication Year, Pages, Binding Type, Language.

Academic & Educational Books: Subject, Grade / Level, Curriculum, Academic Year, Edition, Publisher, ISBN, Language.

Religious & Spiritual Books: Religion / Tradition, Text Type, Language, Author / Translator, Edition, Publisher, Script.

Magazines, Newspapers & Periodicals: Publication Name, Issue Number, Publication Date, Frequency, Language, Publisher, Topic.

Comics & Graphic Novels: Series, Volume, Issue Number, Character, Publisher, Language, Edition, Publication Year.

Music & Audio Media: Media Type, Artist, Album / Title, Genre, Format, Release Year, Number of Tracks, Original / Reissue.

Movies & Video Media: Media Type, Title, Director, Genre, Language, Release Year, Format, Region, Edition.

Collectibles: Collectible Type, Brand / Series, Collection, Production Year, Edition / Series Number, Rarity, Authenticity, Packaging.

Antiques & Vintage Items: Item Type, Estimated Period, Origin, Material, Maker / Artist, Restoration Status, Provenance / Documentation, Authenticity.

Coins & Currency Collectibles: Country, Currency, Denomination, Year, Mint, Metal / Material, Grade / Condition, Serial Number, Commemorative.

Stamps & Postal Collectibles: Country, Issue Year, Stamp Type, Denomination, Series, Perforation, Used / Unused, First Day Cover, Quantity.

Art, Prints & Posters: Artwork Type, Artist, Medium, Subject, Dimensions, Year, Original / Print, Signed, Framed.

Trading Cards & Memorabilia: Category, Player / Character, Team / Franchise, Year, Edition, Card / Item Number, Grading, Authenticity, Autographed.

Musical Instruments & Accessories: Instrument Type, Brand, Model, Material, Size, Skill Level, Acoustic / Electric, Accessories, Case Included.

Hobby & Craft Collections: Hobby Type, Collection Type, Material, Skill Level, Quantity, Complete / Partial Set, Accessories, Storage / Packaging.

Other Books, Media & Collectibles: Item Type, Creator / Maker, Year, Material / Format, Intended Use, Key Features.

## Listing Types

Sale, Exchange, Wanted, Free. Rent may apply to limited reusable items. Lease and Job are not applicable. Service is not applicable. Offer may be used where explicitly modeled.

## Category Rules

- ISBN, catalog numbers, issue numbers, serial numbers, and similar identifiers remain separate attributes.
- Author/creator/artist may be multi-value.
- Authenticity status does not constitute verified provenance.
- Seller-provided authenticity claims remain distinguishable from independently verified information.
- Collectible rarity is not automatically inferred.
- Currency/coin values are not derived automatically from face value.
- Media format is separate from condition.
- Signed/autographed status is independent from authenticity.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Books, Media & Collectibles is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

# 15. CAT-013 — Food, Agriculture Products & Livestock

**Status:** APPROVED — 2026-09-28

## Scope Boundary

CAT-001 covers land, farms, agricultural property and development land. CAT-009 covers agricultural services. CAT-013 covers physical food, agricultural products, planting materials and livestock.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-013-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-013-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-013-03 | Grains &amp;amp; Cereals | Primary catalogue scope for this subcategory. |
| CAT-013-04 | Pulses &amp;amp; Legumes | Primary catalogue scope for this subcategory. |
| CAT-013-05 | Fruits | Primary catalogue scope for this subcategory. |
| CAT-013-06 | Vegetables | Primary catalogue scope for this subcategory. |
| CAT-013-07 | Spices &amp;amp; Herbs | Primary catalogue scope for this subcategory. |
| CAT-013-08 | Dairy &amp;amp; Dairy Products | Primary catalogue scope for this subcategory. |
| CAT-013-09 | Meat &amp;amp; Poultry | Primary catalogue scope for this subcategory. |
| CAT-013-10 | Fish &amp;amp; Seafood | Primary catalogue scope for this subcategory. |
| CAT-013-11 | Eggs &amp;amp; Hatchery Products | Primary catalogue scope for this subcategory. |
| CAT-013-12 | Seeds &amp;amp; Planting Materials | Primary catalogue scope for this subcategory. |
| CAT-013-13 | Animal Feed &amp;amp; Fodder | Primary catalogue scope for this subcategory. |
| CAT-013-14 | Nursery Plants &amp;amp; Saplings | Primary catalogue scope for this subcategory. |
| CAT-013-15 | Livestock &amp;amp; Poultry | Primary catalogue scope for this subcategory. |
| CAT-013-16 | Processed &amp;amp; Packaged Food | Primary catalogue scope for this subcategory. |
| CAT-013-17 | Organic &amp;amp; Specialty Products | Primary catalogue scope for this subcategory. |
| CAT-013-18 | Other Food &amp;amp; Agricultural Products | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| FOOD-ATTR-001 | Product Name | text | Yes | Yes | Yes | No |
| FOOD-ATTR-002 | Product Type | select | Yes | Yes | Yes | No |
| FOOD-ATTR-003 | Brand / Producer | text | No | Yes | Yes | No |
| FOOD-ATTR-004 | Origin / Production Location | json | No | Yes | Yes | No |
| FOOD-ATTR-005 | Condition / Freshness | select | Yes | Yes | Yes | No |
| FOOD-ATTR-006 | Quantity | decimal | Yes | Yes | No | No |
| FOOD-ATTR-007 | Quantity Unit | select | Yes | Yes | No | No |
| FOOD-ATTR-008 | Price | decimal | No | Yes | No | No |
| FOOD-ATTR-009 | Price Unit | select | No | Yes | No | No |
| FOOD-ATTR-010 | Production Date | date | No | Yes | No | No |
| FOOD-ATTR-011 | Expiry Date | date | No | Yes | No | No |
| FOOD-ATTR-012 | Packaging Type | select | No | Yes | Yes | No |
| FOOD-ATTR-013 | Storage Requirement | select | No | Yes | Yes | No |
| FOOD-ATTR-014 | Organic / Specialty Claim | select | No | Yes | Yes | No |
| FOOD-ATTR-015 | Seller Notes | text | No | No | Yes | No |

## Controlled Values

Condition / Freshness: Fresh, Recently Harvested, Frozen, Dried, Processed, Packaged, Live, Other.

Quantity Units: g, kg, Quintal, Metric Ton, Piece, Dozen, Crate, Sack, Packet, Liter, ml, Other.

Packaging: Loose, Sack, Bag, Box, Bottle, Jar, Can, Packet, Crate, Other.

Storage: Ambient, Refrigerated, Frozen, Dry Storage, Humidity Controlled, Other.

## Subcategory Specifications

Grains & Cereals: Grain Type, Variety, Harvest Year, Moisture Level, Grade, Processing Type, Origin.

Pulses & Legumes: Pulse Type, Variety, Harvest Year, Grade, Processing Type, Origin.

Fruits: Fruit Type, Variety, Harvest Season, Grade, Ripeness, Organic Claim, Origin.

Vegetables: Vegetable Type, Variety, Harvest Date, Grade, Organic Claim, Growing Method, Origin.

Spices & Herbs: Spice / Herb Type, Form, Variety, Processing, Origin, Organic Claim, Purity / Blend Type.

Dairy & Dairy Products: Product Type, Source Animal, Fat Content, Processing Type, Pasteurized, Storage Requirement, Expiry Date.

Meat & Poultry: Meat Type, Animal Type, Fresh / Frozen, Cut Type, Processing Type, Weight, Packaging, Slaughter / Processing Date where applicable.

Fish & Seafood: Species, Fresh / Frozen, Farmed / Wild, Size / Weight, Processing Type, Origin, Storage Requirement.

Eggs & Hatchery Products: Product Type, Bird Type, Egg Type, Quantity, Grade, Production Date, Hatchery Type.

Seeds & Planting Materials: Crop Type, Variety, Seed Type, Season, Germination Information, Certification, Harvest / Production Year, Treatment.

Animal Feed & Fodder: Feed Type, Animal Type, Form, Nutritional Specification, Protein Content, Packaging, Storage Requirement.

Nursery Plants & Saplings: Plant Type, Species, Variety, Plant Age, Plant Height, Pot / Bare Root, Growing Condition, Suitable Climate.

Livestock & Poultry: Animal Type, Breed, Age, Sex, Quantity, Purpose, Vaccination Status, Health Documentation, Weight.

Processed & Packaged Food: Food Type, Brand, Ingredients, Net Weight, Packaging, Production Date, Expiry Date, Storage Requirement, Food Certification.

Organic & Specialty Products: Product Type, Certification, Certification Authority, Production Method, Origin, Specialty Claim, Packaging.

Other Food & Agricultural Products: Product Type, Intended Use, Origin, Key Features.

## Listing Types

Sale, Wanted, Exchange (limited), Free, Offer. Rent, Lease, Service and Job are not applicable.

## Category Rules

- Quantity and quantity unit remain separate attributes.
- Price and price unit remain separate.
- Production date and expiry date remain separate.
- Freshness is distinct from generic condition.
- Organic and certification claims are not automatically verified.
- Livestock health and vaccination information is seller-provided unless independently verified.
- Perishable products may require stricter expiration and moderation handling.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Food & Agricultural Products is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

# 16. CAT-014 — Health, Beauty & Personal Care Products

**Status:** APPROVED — 2026-09-28

## Scope Boundary

CAT-014 covers physical consumer health, beauty and personal-care products. Clinics, doctors, therapists, trainers, salons and other professional services remain under CAT-009 Services.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-014-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-014-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-014-03 | Personal Care &amp;amp; Hygiene | Primary catalogue scope for this subcategory. |
| CAT-014-04 | Skin Care | Primary catalogue scope for this subcategory. |
| CAT-014-05 | Hair Care | Primary catalogue scope for this subcategory. |
| CAT-014-06 | Makeup &amp;amp; Cosmetics | Primary catalogue scope for this subcategory. |
| CAT-014-07 | Fragrances &amp;amp; Perfumes | Primary catalogue scope for this subcategory. |
| CAT-014-08 | Shaving &amp;amp; Grooming | Primary catalogue scope for this subcategory. |
| CAT-014-09 | Dental &amp;amp; Oral Care | Primary catalogue scope for this subcategory. |
| CAT-014-10 | Baby Personal Care | Primary catalogue scope for this subcategory. |
| CAT-014-11 | Fitness &amp;amp; Wellness Products | Primary catalogue scope for this subcategory. |
| CAT-014-12 | Massage &amp;amp; Relaxation Products | Primary catalogue scope for this subcategory. |
| CAT-014-13 | Vision &amp;amp; Eye Care Products | Primary catalogue scope for this subcategory. |
| CAT-014-14 | Hearing &amp;amp; Assistive Products | Primary catalogue scope for this subcategory. |
| CAT-014-15 | Medical &amp;amp; Mobility Equipment | Primary catalogue scope for this subcategory. |
| CAT-014-16 | Beauty Equipment &amp;amp; Salon Supplies | Primary catalogue scope for this subcategory. |
| CAT-014-17 | Other Health, Beauty &amp;amp; Personal Care | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| CARE-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| CARE-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| CARE-ATTR-003 | Product Type | select | Yes | No | No | No |
| CARE-ATTR-004 | Condition | select | Yes | No | No | No |
| CARE-ATTR-005 | Intended User Group | select | No | No | No | Yes |
| CARE-ATTR-006 | Gender / Target Group | select. | No | No | No | No |
| CARE-ATTR-007 | Quantity / Pack Size | decimal. | No | No | No | No |
| CARE-ATTR-008 | Unit | select. | No | No | No | No |
| CARE-ATTR-009 | Expiry Date | date. | No | No | No | No |
| CARE-ATTR-010 | Manufacturing Date | date. | No | No | No | No |
| CARE-ATTR-011 | Ingredients / Materials | text | No | No | No | Yes |
| CARE-ATTR-012 | Warranty Status | select. | No | No | No | No |
| CARE-ATTR-013 | Certification / Compliance | text | No | No | No | Yes |
| CARE-ATTR-014 | Original Packaging | boolean. | No | No | No | No |
| CARE-ATTR-015 | Accessories Included | multi_select | No | No | No | Yes |
| CARE-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Open Box, Like New, Good, Fair, Used, Needs Repair, Refurbished.

Target Group: Newborn, Baby, Kids, Teen, Adult, Senior, All Ages.

Gender / Target Group: Male, Female, Unisex, All.

## Subcategory Specifications

Personal Care & Hygiene: Product Type, Skin / Body Area, Form, Pack Size, Fragrance, Intended Age, Ingredients.

Skin Care: Product Type, Skin Type, Skin Concern, SPF, Form, Ingredients, Intended Age, Fragrance-Free.

Hair Care: Product Type, Hair Type, Hair Concern, Form, Ingredients, Fragrance, Intended Age.

Makeup & Cosmetics: Product Type, Shade / Color, Skin Type, Finish, Coverage, Form, Ingredients, Expiry Date.

Fragrances & Perfumes: Product Type, Brand, Fragrance Family, Gender, Volume, Concentration, Original / Tester, Packaging.

Shaving & Grooming: Product Type, Manual / Electric, Power Source, Battery / Runtime, Blade Type, Attachments, Waterproof, Accessories.

Dental & Oral Care: Product Type, Brand, Electric / Manual, Power Source, Brush Head Type, Modes, Battery / Runtime, Accessories.

Baby Personal Care: Product Type, Intended Age, Skin / Body Area, Ingredients, Fragrance-Free, Hypoallergenic Claim, Pack Size, Expiry Date.

Fitness & Wellness Products: Product Type, Intended Use, Material, Size, Weight, Resistance / Capacity, Portable, Accessories.

Massage & Relaxation Products: Product Type, Massage Type, Body Area, Power Source, Heat Function, Intensity Levels, Portable, Accessories.

Vision & Eye Care Products: Product Type, Lens Type, Prescription / Non-Prescription, Lens Material, Frame Material, Frame Size, UV Protection, Accessories.

Hearing & Assistive Products: Product Type, Assistive Function, Power Source, Battery / Runtime, Compatibility, Adjustable, Connectivity, Accessories.

Beauty Equipment & Salon Supplies: Equipment Type, Professional / Consumer, Power Source, Power Rating, Temperature Range, Adjustable, Material, Accessories.

Other Health, Beauty & Personal Care: Product Type, Intended User, Intended Use, Key Features.

## Listing Types

Sale, Exchange, Wanted, Free (limited), Rent (limited), Offer. Lease, Service and Job are not applicable.

## Category Rules

- Expiry is first-class for applicable products.
- Expired products must not be treated as normally sellable active inventory.
- Health-related product claims are not automatically verified.
- Certification/compliance information is seller-provided unless independently verified.
- Prescription-specific information must not be treated as ordinary metadata where it creates privacy or regulated-use concerns.
- Medical and mobility equipment may receive stronger moderation rules.
- Ingredients and accessories may be multi-value.
- Electrical attributes apply only to applicable products.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Health, Beauty & Personal Care is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

## Phase 3 Audit Correction

Health monitoring and mobility equipment are assigned to CAT-023. CAT-014 remains consumer health, beauty, personal-care and general wellness products. Sport/exercise equipment remains CAT-007.

# 17. CAT-015 — Home & Garden

**Status:** APPROVED — 2026-09-28

## Scope Boundary

CAT-015 covers household goods, gardening products, décor, lighting, household tools, outdoor/home-improvement products. Furniture remains CAT-003; electrical home appliances remain CAT-006; sports/gym equipment remains CAT-007; commercial equipment remains CAT-010; agricultural products remain CAT-013.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-015-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-015-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-015-03 | Home Décor &amp;amp; Decorative Items | Primary catalogue scope for this subcategory. |
| CAT-015-04 | Lighting &amp;amp; Lamps | Primary catalogue scope for this subcategory. |
| CAT-015-05 | Kitchenware &amp;amp; Dining | Primary catalogue scope for this subcategory. |
| CAT-015-06 | Bedding &amp;amp; Linens | Primary catalogue scope for this subcategory. |
| CAT-015-07 | Bathroom Accessories | Primary catalogue scope for this subcategory. |
| CAT-015-08 | Storage &amp;amp; Organization | Primary catalogue scope for this subcategory. |
| CAT-015-09 | Cleaning &amp;amp; Household Supplies | Primary catalogue scope for this subcategory. |
| CAT-015-10 | Curtains, Blinds &amp;amp; Window Coverings | Primary catalogue scope for this subcategory. |
| CAT-015-11 | Carpets, Rugs &amp;amp; Mats | Primary catalogue scope for this subcategory. |
| CAT-015-12 | Garden &amp;amp; Gardening Supplies | Primary catalogue scope for this subcategory. |
| CAT-015-13 | Plants, Pots &amp;amp; Planters | Primary catalogue scope for this subcategory. |
| CAT-015-14 | Outdoor Furniture &amp;amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-015-15 | Home Improvement &amp;amp; Building Supplies | Primary catalogue scope for this subcategory. |
| CAT-015-16 | Hand Tools &amp;amp; Household Tools | Primary catalogue scope for this subcategory. |
| CAT-015-17 | Home Security &amp;amp; Safety Products | Primary catalogue scope for this subcategory. |
| CAT-015-18 | Other Home &amp;amp; Garden | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| HOMEG-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| HOMEG-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| HOMEG-ATTR-003 | Product Type | select | Yes | No | No | No |
| HOMEG-ATTR-004 | Condition | select | Yes | No | No | No |
| HOMEG-ATTR-005 | Material | select | No | No | No | Yes |
| HOMEG-ATTR-006 | Color | select. | No | No | No | No |
| HOMEG-ATTR-007 | Size / Dimensions | text. | No | No | No | No |
| HOMEG-ATTR-008 | Weight | decimal. | No | No | No | No |
| HOMEG-ATTR-009 | Weight Unit | select. | No | No | No | No |
| HOMEG-ATTR-010 | Quantity | integer. | No | No | No | No |
| HOMEG-ATTR-011 | Purchase Year | integer. | No | No | No | No |
| HOMEG-ATTR-012 | Warranty Status | select. | No | No | No | No |
| HOMEG-ATTR-013 | Power Source | select. | No | No | No | No |
| HOMEG-ATTR-014 | Assembly Required | boolean. | No | No | No | No |
| HOMEG-ATTR-015 | Accessories Included | multi_select | No | No | No | Yes |
| HOMEG-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Weight Unit: g, kg, lb.

Power Source: Electricity, Battery, Solar, Manual, Gas, LPG, Hybrid, Other.

Warranty: None, Active, Expired, Seller Warranty, Manufacturer Warranty.

## Subcategory Specifications

Home Décor & Decorative Items: Décor Type, Style, Material, Room / Placement, Handmade, Theme, Dimensions.

Lighting & Lamps: Lighting Type, Bulb Type, Wattage, Voltage, Light Color, Fixture Material, Indoor / Outdoor, Dimmable, Smart / Connected.

Kitchenware & Dining: Product Type, Material, Set Quantity, Capacity, Capacity Unit, Dishwasher Safe, Microwave Safe, Food Safe, Heat Resistance.

Bedding & Linens: Product Type, Bed Size, Material / Fabric, Thread Count, Color, Pattern, Set Components, Set Quantity.

Bathroom Accessories: Product Type, Material, Installation Type, Room / Placement, Water Resistant, Set Quantity, Dimensions.

Storage & Organization: Storage Type, Material, Capacity, Capacity Unit, Number of Compartments, Stackable, Foldable, Lockable, Dimensions.

Cleaning & Household Supplies: Product Type, Material, Intended Surface / Use, Reusable, Pack Quantity, Concentration / Form, Accessories.

Curtains, Blinds & Window Coverings: Product Type, Material / Fabric, Window Size, Length, Width, Mounting Type, Light Blocking, Pattern, Set Quantity.

Carpets, Rugs & Mats: Product Type, Material, Length, Width, Thickness, Pattern, Indoor / Outdoor, Washable, Non-Slip.

Garden & Gardening Supplies: Product Type, Gardening Use, Material, Tool Type, Size, Manual / Powered, Handle Material, Compatibility.

Plants, Pots & Planters: Product Type, Plant Type, Species, Variety, Plant Size, Pot Material, Pot Size, Indoor / Outdoor, Sunlight Requirement, Water Requirement.

Outdoor Furniture & Accessories: Product Type, Material, Seating Capacity, Weather Resistant, Foldable, Portable, Cushion Included, Dimensions.

Home Improvement & Building Supplies: Product Type, Material, Application, Grade, Dimensions, Quantity, Coverage, Brand, Compatibility.

Hand Tools & Household Tools: Tool Type, Application, Material, Manual / Powered, Power Source, Size, Professional / Consumer, Compatible Accessories.

Other Home & Garden: Product Type, Intended Use, Material, Key Features.

## Listing Types

Sale, Exchange, Wanted, Free, Rent (limited), Lease (limited), Offer. Service and Job are not applicable.

## Category Rules

- Dimensions should be structured where practical rather than stored only as free text.
- Weight and weight unit remain separate.
- Power attributes apply only to applicable products.
- Indoor/outdoor suitability is independent from product category.
- Safety/certification claims are seller-provided unless independently verified.
- Plants support species and variety separately.
- Rental/lease applies only to suitable reusable products.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Home & Garden is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

# 18. CAT-016 — Pet Supplies & Animals

**Status:** APPROVED — 2026-09-28

## Scope Boundary

CAT-016 covers pet-related products and animal listings. Agricultural livestock and poultry remain CAT-014. Veterinary, grooming and training services remain CAT-009 Services.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-016-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-016-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-016-03 | Dog Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-04 | Cat Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-05 | Bird Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-06 | Fish &amp;amp; Aquarium Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-07 | Small Animal Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-08 | Reptile &amp;amp; Exotic Pet Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-09 | Pet Food &amp;amp; Treats | Primary catalogue scope for this subcategory. |
| CAT-016-10 | Pet Grooming &amp;amp; Hygiene Products | Primary catalogue scope for this subcategory. |
| CAT-016-11 | Pet Health &amp;amp; Wellness Products | Primary catalogue scope for this subcategory. |
| CAT-016-12 | Pet Beds, Cages &amp;amp; Housing | Primary catalogue scope for this subcategory. |
| CAT-016-13 | Pet Toys &amp;amp; Enrichment | Primary catalogue scope for this subcategory. |
| CAT-016-14 | Pet Travel &amp;amp; Safety | Primary catalogue scope for this subcategory. |
| CAT-016-15 | Aquarium &amp;amp; Aquatic Equipment | Primary catalogue scope for this subcategory. |
| CAT-016-16 | Pets for Sale / Adoption | Primary catalogue scope for this subcategory. |
| CAT-016-17 | Pet Accessories &amp;amp; Apparel | Primary catalogue scope for this subcategory. |
| CAT-016-18 | Other Pet Supplies &amp;amp; Animals | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| PET-ATTR-001 | Product / Animal Name | text | Yes | Yes | Yes | No |
| PET-ATTR-002 | Item / Animal Type | select | Yes | Yes | Yes | No |
| PET-ATTR-003 | Brand / Producer | text | No | Yes | Yes | No |
| PET-ATTR-004 | Condition | select | No | Yes | Yes | No |
| PET-ATTR-005 | Species | select | No | Yes | Yes | No |
| PET-ATTR-006 | Breed / Variety | select | No | Yes | Yes | No |
| PET-ATTR-007 | Age | decimal | No | Yes | No | No |
| PET-ATTR-008 | Age Unit | select | No | Yes | No | No |
| PET-ATTR-009 | Gender / Sex | select | No | Yes | Yes | No |
| PET-ATTR-010 | Material | select | No | No | No | Yes |
| PET-ATTR-011 | Size | select | No | Yes | Yes | No |
| PET-ATTR-012 | Quantity | integer | No | Yes | No | No |
| PET-ATTR-013 | Weight | decimal | No | Yes | No | No |
| PET-ATTR-014 | Weight Unit | select | No | Yes | No | No |
| PET-ATTR-015 | Seller Notes | text | No | No | Yes | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Age Unit: Days, Weeks, Months, Years.

Sex: Male, Female, Unknown.

Weight Unit: g, kg, lb.

## Subcategory Specifications

Dog Supplies: Product Type, Dog Size, Breed Compatibility, Material, Size, Weight Capacity, Indoor / Outdoor, Washable.

Cat Supplies: Product Type, Cat Size, Material, Size, Capacity, Indoor / Outdoor, Washable, Compatibility.

Bird Supplies: Bird Type, Product Type, Cage Size, Material, Capacity, Compatible Species, Indoor / Outdoor.

Fish & Aquarium Supplies: Product Type, Aquarium Type, Tank Capacity, Capacity Unit, Compatible Species, Freshwater / Saltwater, Material, Power Requirement.

Small Animal Supplies: Animal Type, Product Type, Size, Material, Capacity, Compatible Species, Indoor / Outdoor.

Reptile & Exotic Pet Supplies: Animal Type, Product Type, Habitat Type, Size, Temperature Requirement, Humidity Requirement, Lighting Requirement, Compatible Species.

Pet Food & Treats: Animal Type, Food Type, Brand, Ingredients, Age Group, Weight / Pack Size, Expiry Date, Flavor, Special Diet.

Pet Grooming & Hygiene Products: Product Type, Animal Type, Material / Ingredients, Size, Reusable, Fragrance, Intended Use, Age Suitability.

Pet Health & Wellness Products: Product Type, Animal Type, Intended Use, Ingredients / Material, Size / Dosage Form, Expiry Date, Manufacturer, Certification / Documentation.

Pet Beds, Cages & Housing: Product Type, Animal Type, Material, Dimensions, Weight Capacity, Foldable, Portable, Indoor / Outdoor, Assembly Required.

Pet Toys & Enrichment: Toy Type, Animal Type, Material, Size, Interactive, Indoor / Outdoor, Battery Required, Recommended Size.

Pet Travel & Safety: Product Type, Animal Type, Size, Weight Capacity, Material, Vehicle Compatibility, Foldable, Safety Feature.

Aquarium & Aquatic Equipment: Equipment Type, Aquarium Capacity, Capacity Unit, Power Rating, Power Source, Freshwater / Saltwater, Flow Rate, Temperature Range, Compatibility.

Pets for Sale / Adoption: Animal Type, Species, Breed, Age, Sex, Vaccination Status, Health Documentation, Sterilization Status, Temperament, Location, Adoption / Sale Type.

Pet Accessories & Apparel: Product Type, Animal Type, Size, Material, Color, Adjustable, Washable, Seasonal / Occasion.

Other Pet Supplies & Animals: Item / Animal Type, Species, Breed / Variety, Intended Use, Key Features.

## Listing Types

Sale, Wanted, Exchange (limited), Free, Rent (limited), Offer. Lease is not applicable. Service and Job are not applicable.

## Category Rules

- Animal listings are modeled differently from ordinary products where necessary.
- Species, breed, age and sex remain independent attributes.
- Vaccination and health information is seller-provided unless independently verified.
- Health/certification claims are not automatically verified.
- Regulated or restricted animals may require additional moderation or may be prohibited according to applicable rules.
- Expiry dates are first-class for pet food and applicable consumables.
- Product condition does not apply to live-animal listings.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Pet Supplies & Animals is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

# 19. CAT-017 — Travel, Luggage & Accessories

**Status:** APPROVED — 2026-09-28

## Scope Boundary

CAT-017 covers physical travel-related products. Travel agencies, tour operators, guides, ticketing, transport, and other travel services remain CAT-009 Services. General vehicle accessories remain CAT-004; ordinary clothing remains CAT-005; general electronics remain CAT-002.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-017-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-017-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-017-03 | Luggage &amp;amp; Suitcases | Primary catalogue scope for this subcategory. |
| CAT-017-04 | Backpacks &amp;amp; Travel Bags | Primary catalogue scope for this subcategory. |
| CAT-017-05 | Travel Organizers &amp;amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-06 | Travel Clothing &amp;amp; Footwear | Primary catalogue scope for this subcategory. |
| CAT-017-07 | Camping &amp;amp; Travel Gear | Primary catalogue scope for this subcategory. |
| CAT-017-08 | Travel Electronics &amp;amp; Gadgets | Primary catalogue scope for this subcategory. |
| CAT-017-09 | Travel Safety &amp;amp; Security | Primary catalogue scope for this subcategory. |
| CAT-017-10 | Passport &amp;amp; Document Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-11 | Neck Pillows &amp;amp; Travel Comfort | Primary catalogue scope for this subcategory. |
| CAT-017-12 | Travel Toiletry &amp;amp; Personal Care Kits | Primary catalogue scope for this subcategory. |
| CAT-017-13 | Car Travel Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-14 | Motorcycle Travel Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-15 | Outdoor &amp;amp; Adventure Travel Gear | Primary catalogue scope for this subcategory. |
| CAT-017-16 | Travel Souvenirs &amp;amp; Memorabilia | Primary catalogue scope for this subcategory. |
| CAT-017-17 | Business Travel Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-18 | Other Travel Products | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| TRAVEL-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| TRAVEL-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| TRAVEL-ATTR-003 | Product Type | select | Yes | No | No | No |
| TRAVEL-ATTR-004 | Condition | select | Yes | No | No | No |
| TRAVEL-ATTR-005 | Material | select | No | No | No | Yes |
| TRAVEL-ATTR-006 | Color | select. | No | No | No | No |
| TRAVEL-ATTR-007 | Size | select. | No | No | No | No |
| TRAVEL-ATTR-008 | Dimensions | text. | No | No | No | No |
| TRAVEL-ATTR-009 | Weight | decimal. | No | No | No | No |
| TRAVEL-ATTR-010 | Weight Unit | select. | No | No | No | No |
| TRAVEL-ATTR-011 | Capacity | decimal. | No | No | No | No |
| TRAVEL-ATTR-012 | Capacity Unit | select. | No | No | No | No |
| TRAVEL-ATTR-013 | Purchase Year | integer. | No | No | No | No |
| TRAVEL-ATTR-014 | Warranty Status | select. | No | No | No | No |
| TRAVEL-ATTR-015 | Accessories Included | multi_select | No | No | No | Yes |
| TRAVEL-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Weight Unit: g, kg, lb.

Capacity Unit: L, ml, kg, Piece, Other.

Warranty: None, Active, Expired, Seller Warranty, Manufacturer Warranty.

## Subcategory Specifications

Luggage & Suitcases: Luggage Type, Capacity, Capacity Unit, Size / Cabin Size, Number of Wheels, Wheel Type, Lock Type, Expandable, Handle Type, TSA Lock.

Backpacks & Travel Bags: Bag Type, Capacity, Capacity Unit, Laptop Compartment, Laptop Size, Water Resistant, Number of Compartments, Carrying Type.

Travel Organizers & Accessories: Product Type, Material, Size, Number of Compartments, Waterproof, Set Quantity, Compatibility.

Travel Clothing & Footwear: Product Type, Size, Material, Gender, Season, Weather Suitability, Waterproof, Intended Activity.

Camping & Travel Gear: Equipment Type, Capacity, Persons, Weight, Packed Size, Waterproof, Season Rating, Portable, Setup Required.

Travel Electronics & Gadgets: Device Type, Brand, Model, Power Source, Battery Capacity, Voltage, Connectivity, Compatibility, Accessories.

Travel Safety & Security: Product Type, Security Function, Lock Type, Material, TSA Compatible, Alarm, Connectivity, Battery Required.

Passport & Document Accessories: Product Type, Material, Number of Compartments, Card Slots, RFID Protection, Passport Compatibility, Waterproof.

Neck Pillows & Travel Comfort: Product Type, Material, Filling, Adjustable, Washable, Inflatable, Size, Carry Bag Included.

Travel Toiletry & Personal Care Kits: Product Type, Container Type, Material, Capacity, Number of Pieces, Leak Resistant, TSA / Travel Compatibility.

Car Travel Accessories: Product Type, Vehicle Compatibility, Installation Type, Material, Power Source, Universal / Model Specific, Safety Feature.

Motorcycle Travel Accessories: Product Type, Motorcycle Compatibility, Mounting Type, Material, Waterproof, Capacity, Safety Feature.

Outdoor & Adventure Travel Gear: Equipment Type, Activity, Material, Size, Weight, Capacity, Waterproof, Safety Equipment, Skill Level.

Travel Souvenirs & Memorabilia: Item Type, Origin / Destination, Material, Year, Handmade, Theme, Dimensions.

Business Travel Accessories: Product Type, Laptop Size, Device Compatibility, Material, Compartments, RFID Protection, Carrying Type, Business / Professional Use.

Other Travel Products: Product Type, Intended Travel Use, Material, Compatibility, Key Features.

## Listing Types

Sale, Exchange, Wanted, Free, Rent (limited), Offer. Lease, Service and Job are not applicable.

## Category Rules

- Capacity, weight and dimensions remain separate attributes.
- Cabin-size compatibility is explicit for luggage.
- Vehicle compatibility is explicit for vehicle travel accessories.
- Electrical specifications apply only to applicable products.
- Safety claims/certifications are seller-provided unless independently verified.
- TSA compatibility is a product attribute and not a guarantee of acceptance by a particular carrier or authority.
- Rental applies only to suitable reusable equipment.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Travel Products is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

# 20. CAT-018 — Construction, Tools & Building Materials

**Status:** APPROVED — 2026-09-28

## Scope Boundary

CAT-018 covers physical construction materials, hardware, tools, plumbing, electrical supplies, renovation products and construction-site supplies. Household/garden tools remain CAT-016; commercial/industrial equipment remains CAT-010; construction, repair, plumbing and electrical labor/services remain CAT-009.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-018-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-018-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-018-03 | Cement, Concrete &amp;amp; Aggregates | Primary catalogue scope for this subcategory. |
| CAT-018-04 | Bricks, Blocks &amp;amp; Pavers | Primary catalogue scope for this subcategory. |
| CAT-018-05 | Steel, Metal &amp;amp; Structural Materials | Primary catalogue scope for this subcategory. |
| CAT-018-06 | Wood, Timber &amp;amp; Boards | Primary catalogue scope for this subcategory. |
| CAT-018-07 | Roofing &amp;amp; Waterproofing Materials | Primary catalogue scope for this subcategory. |
| CAT-018-08 | Doors, Windows &amp;amp; Frames | Primary catalogue scope for this subcategory. |
| CAT-018-09 | Flooring &amp;amp; Tiles | Primary catalogue scope for this subcategory. |
| CAT-018-10 | Paint, Wall Finishes &amp;amp; Coatings | Primary catalogue scope for this subcategory. |
| CAT-018-11 | Plumbing &amp;amp; Sanitary Materials | Primary catalogue scope for this subcategory. |
| CAT-018-12 | Electrical &amp;amp; Wiring Materials | Primary catalogue scope for this subcategory. |
| CAT-018-13 | Hardware, Fasteners &amp;amp; Fittings | Primary catalogue scope for this subcategory. |
| CAT-018-14 | Hand Tools | Primary catalogue scope for this subcategory. |
| CAT-018-15 | Power Tools | Primary catalogue scope for this subcategory. |
| CAT-018-16 | Safety Equipment &amp;amp; Workwear | Primary catalogue scope for this subcategory. |
| CAT-018-17 | Construction Equipment &amp;amp; Site Supplies | Primary catalogue scope for this subcategory. |
| CAT-018-18 | Other Construction &amp;amp; Building Materials | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| BUILD-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| BUILD-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| BUILD-ATTR-003 | Product Type | select | Yes | No | No | No |
| BUILD-ATTR-004 | Condition | select | Yes | No | No | No |
| BUILD-ATTR-005 | Material | select | No | No | No | Yes |
| BUILD-ATTR-006 | Grade / Specification | text. | No | No | No | No |
| BUILD-ATTR-007 | Size / Dimensions | text. | No | No | No | No |
| BUILD-ATTR-008 | Quantity | decimal. | No | No | No | No |
| BUILD-ATTR-009 | Quantity Unit | select. | No | No | No | No |
| BUILD-ATTR-010 | Weight | decimal. | No | No | No | No |
| BUILD-ATTR-011 | Weight Unit | select. | No | No | No | No |
| BUILD-ATTR-012 | Application / Compatibility | text | No | No | No | Yes |
| BUILD-ATTR-013 | Purchase / Manufacture Year | integer. | No | No | No | No |
| BUILD-ATTR-014 | Warranty Status | select. | No | No | No | No |
| BUILD-ATTR-015 | Accessories Included | multi_select | No | No | No | Yes |
| BUILD-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Quantity Units: Piece, Set, Box, Pack, Bag, Sack, kg, Ton, Meter, Square Meter, Cubic Meter, Liter, Other.

Weight Unit: g, kg, Ton, lb.

## Subcategory Specifications

Cement, Concrete & Aggregates: Material Type, Grade, Cement Type, Aggregate Type, Particle Size, Bag Weight, Quantity, Manufacturer, Production Date.

Bricks, Blocks & Pavers: Product Type, Material, Dimensions, Grade, Compressive Strength, Color, Finish, Quantity per Pack.

Steel, Metal & Structural Materials: Material Type, Steel / Metal Grade, Shape / Profile, Thickness, Length, Width, Diameter, Weight per Unit, Surface Finish.

Wood, Timber & Boards: Product Type, Wood Species, Grade, Thickness, Length, Width, Moisture / Treatment, Finish, Intended Application.

Roofing & Waterproofing Materials: Product Type, Material, Thickness, Length, Width, Coverage Area, Waterproofing Type, UV Resistance, Installation Method.

Doors, Windows & Frames: Product Type, Material, Width, Height, Frame Material, Glass Type, Opening Type, Lock Type, Security Features.

Flooring & Tiles: Product Type, Material, Tile / Board Size, Thickness, Surface Finish, Indoor / Outdoor, Slip Resistance, Coverage per Box, Pattern.

Paint, Wall Finishes & Coatings: Product Type, Surface Type, Finish, Color, Volume, Coverage, Application Method, Indoor / Outdoor, Drying Time.

Plumbing & Sanitary Materials: Product Type, Material, Diameter, Length, Pressure Rating, Connection Type, Thread Type, Compatible System, Indoor / Outdoor.

Electrical & Wiring Materials: Product Type, Cable / Wire Type, Conductor Material, Core Count, Cross Section, Voltage Rating, Current Rating, Length, Insulation Type, Certification.

Hardware, Fasteners & Fittings: Product Type, Material, Size, Thread Type, Finish, Strength / Grade, Quantity, Compatible Material, Application.

Hand Tools: Tool Type, Material, Size, Handle Material, Professional / Consumer, Application, Set Quantity, Compatible Accessories.

Power Tools: Tool Type, Power Source, Power Rating, Voltage, Battery Type, Battery Included, Speed, Chuck / Bit Compatibility, Professional / Consumer, Accessories.

Safety Equipment & Workwear: Product Type, Safety Function, Size, Material, Protection Standard, Certification, PPE Category, Gender / Fit, Intended Application.

Construction Equipment & Site Supplies: Equipment Type, Application, Capacity, Capacity Unit, Material, Power Source, Dimensions, Weight, Portable, Assembly Required.

Other Construction & Building Materials: Product Type, Material, Grade / Specification, Intended Application, Compatibility, Key Features.

## Listing Types

Sale, Exchange, Wanted, Free, Rent (limited), Lease (limited), Offer. Service and Job are not applicable.

## Boundary Rules

- Household hand/garden tools primarily for ordinary consumers belong to CAT-016.
- Industrial machinery and commercial equipment belong to CAT-010.
- Construction, renovation, plumbing and electrical labor belong to CAT-009.
- Construction materials and physical tools belong to CAT-018.
- Professional construction equipment can remain CAT-018 when primarily construction-site equipment rather than general commercial machinery.

## Category Rules

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

# 21. CAT-019 — Industrial, Machinery & Heavy Equipment

**Status:** APPROVED — 2026-09-28

## Scope Boundary

CAT-019 covers heavy machinery, industrial equipment, generators, compressors, material-handling equipment, specialized machinery and heavy-duty production equipment. Construction materials and ordinary construction tools remain CAT-020; commercial office/POS/medical/shop equipment remains CAT-010; road vehicles remain CAT-004; machinery operation, installation, repair and maintenance remain CAT-009.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-019-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-019-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-019-03 | Excavators &amp;amp; Earthmoving Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-04 | Loaders, Backhoes &amp;amp; Skid Steers | Primary catalogue scope for this subcategory. |
| CAT-019-05 | Cranes &amp;amp; Lifting Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-06 | Forklifts &amp;amp; Material Handling | Primary catalogue scope for this subcategory. |
| CAT-019-07 | Generators &amp;amp; Power Generation | Primary catalogue scope for this subcategory. |
| CAT-019-08 | Compressors &amp;amp; Air Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-09 | Welding &amp;amp; Fabrication Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-10 | Manufacturing &amp;amp; Production Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-11 | Food Processing Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-12 | Packaging &amp;amp; Processing Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-13 | Mining &amp;amp; Quarry Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-14 | Concrete &amp;amp; Construction Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-15 | Agricultural &amp;amp; Forestry Machinery | Primary catalogue scope for this subcategory. |
| CAT-019-16 | Industrial Pumps &amp;amp; Fluid Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-17 | Industrial Electrical &amp;amp; Power Equipment | Primary catalogue scope for this subcategory. |
| CAT-019-18 | Other Industrial &amp;amp; Heavy Equipment | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| IND-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| IND-ATTR-002 | Equipment Name / Model | text | Yes | No | No | No |
| IND-ATTR-003 | Equipment Type | select | Yes | No | No | No |
| IND-ATTR-004 | Condition | select | Yes | No | No | No |
| IND-ATTR-005 | Manufacture Year | integer. | No | No | No | No |
| IND-ATTR-006 | Operating Hours | decimal. | No | No | No | No |
| IND-ATTR-007 | Capacity | decimal. | No | No | No | No |
| IND-ATTR-008 | Capacity Unit | select. | No | No | No | No |
| IND-ATTR-009 | Power Rating | decimal. | No | No | No | No |
| IND-ATTR-010 | Power Unit | select. | No | No | No | No |
| IND-ATTR-011 | Power Source | select. | No | No | No | No |
| IND-ATTR-012 | Weight | decimal. | No | No | No | No |
| IND-ATTR-013 | Weight Unit | select. | No | No | No | No |
| IND-ATTR-014 | Application | select | No | No | No | Yes |
| IND-ATTR-015 | Warranty Status | select. | No | No | No | No |
| IND-ATTR-016 | Accessories / Attachments Included | multi_select | No | No | No | Yes |
| IND-ATTR-017 | Service / Maintenance History | text. | No | No | No | No |
| IND-ATTR-018 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used, For Parts.

Power Unit: W, kW, HP, MW, VA, kVA, Other.

Power Source: Electricity, Diesel, Petrol, LPG, Gas, Battery, Hydraulic, Pneumatic, Manual, Hybrid, Other.

Weight Unit: kg, Ton, lb.

## Subcategory Specifications

Excavators & Earthmoving Machinery: Machine Type, Operating Weight, Engine Power, Bucket Capacity, Maximum Digging Depth, Maximum Reach, Hydraulic System, Track / Wheel Type, Attachments, Hours Used.

Loaders, Backhoes & Skid Steers: Machine Type, Operating Weight, Engine Power, Bucket Capacity, Lift Capacity, Hydraulic Capacity, Drive Type, Attachment Compatibility, Hours Used.

Cranes & Lifting Equipment: Equipment Type, Maximum Load Capacity, Maximum Lift Height, Boom Length, Working Radius, Power Source, Mobility Type, Safety Features, Certification / Inspection Status.

Forklifts & Material Handling: Equipment Type, Load Capacity, Lift Height, Mast Type, Fork Length, Power Source, Tire Type, Turning Radius, Operating Hours.

Generators & Power Generation: Generator Type, Rated Power, Maximum Power, Voltage, Phase, Frequency, Fuel Type, Fuel Capacity, Runtime, Automatic / Manual Start, Noise Rating.

Compressors & Air Equipment: Equipment Type, Compressor Type, Air Flow Rate, Pressure, Tank Capacity, Power Rating, Power Source, Motor Type, Duty Cycle, Noise Level.

Welding & Fabrication Machinery: Equipment Type, Welding Process, Output Current, Input Voltage, Duty Cycle, Material Compatibility, Wire / Electrode Size, Power Source, Accessories.

Manufacturing & Production Machinery: Machine Type, Manufacturing Process, Production Capacity, Capacity Unit, Automation Level, Material Compatibility, Motor Power, Operating Mode, Control System, Dimensions.

Food Processing Machinery: Equipment Type, Food Application, Processing Capacity, Capacity Unit, Material, Power Source, Motor Power, Automation Level, Food Contact Material, Cleaning Method.

Packaging & Processing Equipment: Equipment Type, Packaging Type, Production Speed, Capacity, Material Compatibility, Automation Level, Power Rating, Packaging Size, Control System.

Mining & Quarry Equipment: Equipment Type, Application, Processing Capacity, Engine / Motor Power, Operating Weight, Material Handled, Mobility, Hours Used, Attachments.

Concrete & Construction Machinery: Equipment Type, Application, Capacity, Capacity Unit, Power Source, Power Rating, Mixing / Processing Rate, Mobility, Batch Size, Operating Hours.

Agricultural & Forestry Machinery: Machine Type, Agricultural / Forestry Application, Engine Type, Engine Power, Working Width, Capacity, Fuel Type, Attachment Compatibility, Operating Hours.

Industrial Pumps & Fluid Equipment: Equipment Type, Pump Type, Flow Rate, Pressure / Head, Inlet / Outlet Size, Fluid Compatibility, Power Source, Power Rating, Material, Temperature Range.

Industrial Electrical & Power Equipment: Equipment Type, Rated Power, Voltage, Current, Phase, Frequency, Input / Output, Protection Rating, Installation Type, Certification.

Other Industrial & Heavy Equipment: Equipment Type, Industrial Application, Capacity, Power Source, Power Rating, Material, Compatibility, Key Features.

## Listing Types

Sale, Exchange, Wanted, Free (limited), Rent, Lease, Offer. Service and Job are not applicable.

## Boundary Rules

- Construction materials belong to CAT-020.
- Ordinary hand/power tools belong to CAT-020.
- Commercial office/POS/medical/shop equipment belongs to CAT-010.
- Agricultural machinery may belong to CAT-019 when heavy/industrial; simpler agricultural equipment is classified according to primary commercial use.
- Road vehicles belong to CAT-004.
- Machinery operation, installation, repair and maintenance services belong to CAT-009.

## Category Rules

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

# 22. CAT-020 — Weddings, Events & Party Supplies

**Status:** APPROVED — 2026-09-28

## Scope Boundary

CAT-020 covers physical products used for weddings, parties, celebrations, ceremonies and events. Event planning, decoration labor, catering, photography, entertainment and venues remain CAT-009 Services; ordinary clothing remains CAT-005; general craft materials remain CAT-021; ordinary household furniture remains CAT-003; general consumer electronics remain CAT-002.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-020-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-020-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-020-03 | Wedding Decorations &amp;amp; Backdrops | Primary catalogue scope for this subcategory. |
| CAT-020-04 | Party Decorations | Primary catalogue scope for this subcategory. |
| CAT-020-05 | Flowers, Artificial Flowers &amp;amp; Floral Décor | Primary catalogue scope for this subcategory. |
| CAT-020-06 | Lighting &amp;amp; Decorative Lighting | Primary catalogue scope for this subcategory. |
| CAT-020-07 | Tables, Chairs &amp;amp; Event Furniture | Primary catalogue scope for this subcategory. |
| CAT-020-08 | Tents, Canopies &amp;amp; Temporary Structures | Primary catalogue scope for this subcategory. |
| CAT-020-09 | Wedding Accessories &amp;amp; Ceremony Items | Primary catalogue scope for this subcategory. |
| CAT-020-10 | Tableware &amp;amp; Serving Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-11 | Party Supplies &amp;amp; Disposable Items | Primary catalogue scope for this subcategory. |
| CAT-020-12 | Balloons &amp;amp; Balloon Decoration Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-13 | Cake, Baking &amp;amp; Dessert Decoration Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-14 | Invitation, Printing &amp;amp; Stationery Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-15 | Gifts, Favors &amp;amp; Return-Gift Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-16 | Kids &amp;amp; Theme Party Supplies | Primary catalogue scope for this subcategory. |
| CAT-020-17 | Event Audio, Stage &amp;amp; Production Equipment | Primary catalogue scope for this subcategory. |
| CAT-020-18 | Other Wedding, Event &amp;amp; Party Supplies | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| EVENT-ATTR-001 | Brand / Manufacturer / Maker | text. | No | No | No | No |
| EVENT-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| EVENT-ATTR-003 | Product Type | select | Yes | No | No | No |
| EVENT-ATTR-004 | Condition | select | Yes | No | No | No |
| EVENT-ATTR-005 | Material | select | No | No | No | Yes |
| EVENT-ATTR-006 | Color / Theme | select | No | No | No | Yes |
| EVENT-ATTR-007 | Size / Dimensions | text. | No | No | No | No |
| EVENT-ATTR-008 | Quantity | decimal. | No | No | No | No |
| EVENT-ATTR-009 | Quantity Unit | select. | No | No | No | No |
| EVENT-ATTR-010 | Capacity | decimal. | No | No | No | No |
| EVENT-ATTR-011 | Capacity Unit | select. | No | No | No | No |
| EVENT-ATTR-012 | Reusable | boolean. | No | No | No | No |
| EVENT-ATTR-013 | Purchase Year | integer. | No | No | No | No |
| EVENT-ATTR-014 | Warranty Status | select. | No | No | No | No |
| EVENT-ATTR-015 | Accessories Included | multi_select | No | No | No | Yes |
| EVENT-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Quantity Unit: Piece, Set, Pack, Box, Dozen, Pair, Meter, Roll, Other.

Capacity Unit: Person, Table, Seat, Piece, Liter, Other.

## Subcategory Specifications

Wedding Decorations & Backdrops: Decoration Type, Wedding Theme, Material, Backdrop Size, Color, Reusable, Mounting Type, Included Components.

Party Decorations: Decoration Type, Event Type, Theme, Material, Color, Size, Reusable, Set Quantity.

Flowers, Artificial Flowers & Floral Décor: Flower Type, Fresh / Artificial / Preserved, Flower Variety, Color, Arrangement Type, Material, Quantity, Reusable.

Lighting & Decorative Lighting: Lighting Type, Light Source, Voltage, Power Rating, Light Color, Length, Indoor / Outdoor, Waterproof, Control Type, Power Source.

Tables, Chairs & Event Furniture: Furniture Type, Material, Seating Capacity, Dimensions, Foldable, Stackable, Indoor / Outdoor, Cushion Included, Weight Capacity.

Tents, Canopies & Temporary Structures: Structure Type, Capacity, Persons, Dimensions, Material, Waterproof, Wind Resistance, Setup Method, Frame Material, Carry Bag Included.

Wedding Accessories & Ceremony Items: Item Type, Ceremony Type, Material, Color, Size, Theme, Reusable, Included Components.

Tableware & Serving Supplies: Product Type, Material, Set Quantity, Capacity, Capacity Unit, Food Safe, Disposable / Reusable, Dishwasher Safe, Event Type.

Party Supplies & Disposable Items: Product Type, Event Type, Material, Color, Theme, Quantity, Disposable / Reusable, Age Group.

Balloons & Balloon Decoration Supplies: Balloon Type, Material, Size, Color, Theme, Quantity, Inflatable Type, Reusable, Accessories Included.

Cake, Baking & Dessert Decoration Supplies: Product Type, Material, Size, Quantity, Theme, Food Safe, Reusable, Compatibility, Decoration Type.

Invitation, Printing & Stationery Supplies: Product Type, Event Type, Material, Paper Size, Quantity, Printing Type, Customizable, Language, Design / Theme.

Gifts, Favors & Return-Gift Supplies: Product Type, Event Type, Material, Theme, Quantity, Packaging Included, Customizable, Age Group.

Kids & Theme Party Supplies: Product Type, Theme, Age Group, Event Type, Material, Quantity, Reusable, Safety Feature.

Event Audio, Stage & Production Equipment: Equipment Type, Audio / Production Type, Power Rating, Power Source, Connectivity, Channel Count, Capacity, Compatibility, Mounting / Setup Type, Accessories.

Other Wedding, Event & Party Supplies: Product Type, Event Type, Material, Theme, Intended Use, Key Features.

## Listing Types

Sale, Exchange, Wanted, Free, Rent, Lease (limited), Offer. Service and Job are not applicable.

## Boundary Rules

- Event planning, decoration labor, catering, photography, entertainment and venue services belong to CAT-009.
- Wedding clothing and ordinary fashion belong to CAT-005.
- General craft materials belong to CAT-021.
- Ordinary household furniture belongs to CAT-003.
- General consumer electronics belong to CAT-019.
- Event-specific physical products remain CAT-020 even when normally used temporarily.

## Category Rules

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

# 23. CAT-021 — Office, School & Stationery Supplies

**Status:** APPROVED — 2026-09-28

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
| CAT-021-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-021-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-021-03 | Writing Instruments | Primary catalogue scope for this subcategory. |
| CAT-021-04 | Paper &amp;amp; Notebooks | Primary catalogue scope for this subcategory. |
| CAT-021-05 | Files, Folders &amp;amp; Document Storage | Primary catalogue scope for this subcategory. |
| CAT-021-06 | Office Desk Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-07 | School Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-08 | Art &amp;amp; Drawing School Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-09 | Calculators &amp;amp; Basic Learning Devices | Primary catalogue scope for this subcategory. |
| CAT-021-10 | Labels, Stickers &amp;amp; Identification Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-11 | Envelopes, Packaging &amp;amp; Mailing Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-12 | Printing &amp;amp; Binding Consumables | Primary catalogue scope for this subcategory. |
| CAT-021-13 | Office Organization &amp;amp; Storage Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-14 | Presentation &amp;amp; Teaching Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-15 | Calendar, Planner &amp;amp; Time-Management Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-16 | Business Forms &amp;amp; Administrative Supplies | Primary catalogue scope for this subcategory. |
| CAT-021-17 | School Bags &amp;amp; Student Accessories | Primary catalogue scope for this subcategory. |
| CAT-021-18 | Other Office, School &amp;amp; Stationery Supplies | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| STAT-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| STAT-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| STAT-ATTR-003 | Product Type | select | Yes | No | No | No |
| STAT-ATTR-004 | Condition | select | Yes | No | No | No |
| STAT-ATTR-005 | Material | select | No | No | No | Yes |
| STAT-ATTR-006 | Color | select | No | No | No | Yes |
| STAT-ATTR-007 | Size / Format | select. | No | No | No | No |
| STAT-ATTR-008 | Quantity | decimal. | No | No | No | No |
| STAT-ATTR-009 | Quantity Unit | select. | No | No | No | No |
| STAT-ATTR-010 | Dimensions | text. | No | No | No | No |
| STAT-ATTR-011 | Paper / Sheet Count | integer. | No | No | No | No |
| STAT-ATTR-012 | Compatibility | text | No | No | No | Yes |
| STAT-ATTR-013 | Reusable | boolean. | No | No | No | No |
| STAT-ATTR-014 | Original Packaging | boolean. | No | No | No | No |
| STAT-ATTR-015 | Accessories Included | multi_select | No | No | No | Yes |
| STAT-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Like New, Good, Fair, Used, Damaged.

Quantity Unit: Piece, Set, Pack, Box, Ream, Roll, Dozen, Pair, Other.

Common Formats: A4, A5, A6, Letter, Legal, Executive, B5, Other.

## Subcategory Specifications

Writing Instruments: Instrument Type, Ink Type, Tip Size, Ink Color, Refillable, Set Quantity, Material, Intended Use.

Paper & Notebooks: Paper Type, Format, GSM, Sheet Count, Page Count, Ruled / Plain / Grid, Binding Type, Cover Type, Color.

Files, Folders & Document Storage: Product Type, Material, Size / Format, Capacity, Closure Type, Number of Compartments, Label Holder, Color.

Office Desk Supplies: Product Type, Material, Size, Quantity, Color, Desktop / Portable, Reusable, Compatibility.

School Supplies: Product Type, Grade / Age Group, Subject, Material, Size, Set Quantity, School Level, Language.

Art & Drawing School Supplies: Product Type, Medium, Material, Color Count, Set Quantity, Grade / Age Group, Student / Artist Grade, Surface Compatibility.

Calculators & Basic Learning Devices: Device Type, Display Type, Number of Digits, Functions, Power Source, Battery Included, Solar Powered, School / Exam Suitability.

Labels, Stickers & Identification Supplies: Product Type, Material, Size, Shape, Adhesive Type, Printable, Waterproof, Quantity, Color.

Envelopes, Packaging & Mailing Supplies: Product Type, Material, Size, Closure Type, Window, Quantity, Reusable, Security Feature.

Printing & Binding Consumables: Product Type, Compatible Device, Paper / Material Type, Size, GSM, Quantity, Color, Binding Type.

Office Organization & Storage Supplies: Product Type, Material, Storage Capacity, Number of Compartments, Stackable, Desktop / Floor, Dimensions, Color.

Presentation & Teaching Supplies: Product Type, Material, Size, Surface Type, Magnetic, Writable, Reusable, Mounting Type.

Calendar, Planner & Time-Management Supplies: Product Type, Year / Period, Format, Size, Binding, Layout, Language, Reusable.

Business Forms & Administrative Supplies: Product Type, Form Type, Format, Paper Type, Sheet Count, Numbering, Carbon Copy, Language.

School Bags & Student Accessories: Product Type, Material, Capacity, Capacity Unit, Age Group, Compartments, Laptop / Tablet Compartment, Water Resistant, Adjustable.

Other Office, School & Stationery Supplies: Product Type, Intended Use, Material, Size, Compatibility, Key Features.

## Listing Types

Sale, Exchange (limited), Wanted, Free, Offer. Rent and Lease are not ordinary listing types. Service and Job are not applicable.

## Category Rules

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

# 24. CAT-022 — Religious, Spiritual & Cultural Items

**Status:** APPROVED — 2026-09-28

## Scope

CAT-022 covers physical religious, spiritual, ceremonial and culturally significant consumer items.

## Boundary

- CAT-013 covers religious/spiritual books and printed media.
- CAT-005 covers ordinary clothing and fashion; specifically religious/ceremonial clothing may belong here when religious/cultural use is primary.
- CAT-021 covers general arts, crafts and musical instruments.
- CAT-003 covers ordinary furniture.
- CAT-014 covers physical food/agricultural products.
- CAT-009 covers religious/cultural services, ceremonies, performers and event services.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-022-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-022-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-022-03 | Religious Statues &amp;amp; Idols | Primary catalogue scope for this subcategory. |
| CAT-022-04 | Puja &amp;amp; Worship Supplies | Primary catalogue scope for this subcategory. |
| CAT-022-05 | Prayer &amp;amp; Meditation Items | Primary catalogue scope for this subcategory. |
| CAT-022-06 | Religious Clothing &amp;amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-022-07 | Prayer Mats, Carpets &amp;amp; Floor Items | Primary catalogue scope for this subcategory. |
| CAT-022-08 | Rosaries, Mala &amp;amp; Prayer Beads | Primary catalogue scope for this subcategory. |
| CAT-022-09 | Incense, Lamps &amp;amp; Ritual Burning Items | Primary catalogue scope for this subcategory. |
| CAT-022-10 | Religious Vessels &amp;amp; Ritual Utensils | Primary catalogue scope for this subcategory. |
| CAT-022-11 | Temple, Shrine &amp;amp; Home Altar Items | Primary catalogue scope for this subcategory. |
| CAT-022-12 | Religious Flags, Banners &amp;amp; Symbols | Primary catalogue scope for this subcategory. |
| CAT-022-13 | Festival &amp;amp; Cultural Celebration Items | Primary catalogue scope for this subcategory. |
| CAT-022-14 | Traditional &amp;amp; Cultural Handicrafts | Primary catalogue scope for this subcategory. |
| CAT-022-15 | Spiritual &amp;amp; Meditation Equipment | Primary catalogue scope for this subcategory. |
| CAT-022-16 | Cultural Musical Instruments | Primary catalogue scope for this subcategory. |
| CAT-022-17 | Religious Gift &amp;amp; Devotional Items | Primary catalogue scope for this subcategory. |
| CAT-022-18 | Other Religious, Spiritual &amp;amp; Cultural Items | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| CULT-ATTR-001 | Brand / Manufacturer / Maker | text. | No | No | No | No |
| CULT-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| CULT-ATTR-003 | Product Type | select | Yes | No | No | No |
| CULT-ATTR-004 | Tradition / Cultural Context | select. | No | No | No | No |
| CULT-ATTR-005 | Religion / Spiritual Tradition | select | No | No | No | Yes |
| CULT-ATTR-006 | Material | select | No | No | No | Yes |
| CULT-ATTR-007 | Condition | select. | No | No | No | No |
| CULT-ATTR-008 | Color | select | No | No | No | Yes |
| CULT-ATTR-009 | Size / Dimensions | text. | No | No | No | No |
| CULT-ATTR-010 | Weight | decimal. | No | No | No | No |
| CULT-ATTR-011 | Weight Unit | select. | No | No | No | No |
| CULT-ATTR-012 | Quantity | decimal. | No | No | No | No |
| CULT-ATTR-013 | Quantity Unit | select. | No | No | No | No |
| CULT-ATTR-014 | Handmade | boolean. | No | No | No | No |
| CULT-ATTR-015 | Accessories Included | multi_select | No | No | No | Yes |
| CULT-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Used, Damaged, Restored.

Weight Unit: g, kg, lb, Other.

Quantity Unit: Piece, Set, Pack, Pair, Dozen, Meter, Other.

Religion / Spiritual Tradition: Hindu, Buddhist, Muslim, Christian, Jain, Sikh, Kirat, Indigenous / Local Tradition, Interfaith, Spiritual / Meditation, Other.

## Subcategory Specifications

Religious Statues & Idols: Deity / Figure, Tradition, Material, Height, Width, Finish, Handmade, Indoor / Outdoor, Base / Stand Included.

Puja & Worship Supplies: Product Type, Ritual Use, Material, Set Quantity, Tradition, Reusable, Included Components, Size.

Prayer & Meditation Items: Product Type, Intended Practice, Material, Size, Portability, Handmade, Accessories, Suitable User Group.

Religious Clothing & Accessories: Clothing / Accessory Type, Tradition, Gender / Target Group, Size, Material, Color, Occasion, Handmade.

Prayer Mats, Carpets & Floor Items: Product Type, Tradition, Material, Length, Width, Thickness, Pattern, Foldable, Washable.

Rosaries, Mala & Prayer Beads: Product Type, Tradition, Bead Material, Bead Count, Bead Size, String Material, Handmade, Pendant / Tassel Included.

Incense, Lamps & Ritual Burning Items: Product Type, Fuel / Material, Fragrance, Burn Type, Burn Time, Quantity, Reusable, Intended Use.

Religious Vessels & Ritual Utensils: Vessel Type, Material, Capacity, Capacity Unit, Ritual Use, Finish, Set Quantity, Handmade.

Temple, Shrine & Home Altar Items: Product Type, Tradition, Material, Dimensions, Mounting / Placement Type, Indoor / Outdoor, Assembly Required, Included Components.

Religious Flags, Banners & Symbols: Product Type, Symbol / Design, Tradition, Material, Size, Indoor / Outdoor, Mounting Type, Weather Resistant.

Festival & Cultural Celebration Items: Festival / Occasion, Product Type, Tradition / Community, Material, Theme, Quantity, Reusable / Disposable, Intended Use.

Traditional & Cultural Handicrafts: Craft Type, Cultural / Regional Origin, Maker, Material, Handmade, Technique, Dimensions, Intended Use.

Spiritual & Meditation Equipment: Product Type, Meditation / Practice Type, Material, Size, Power Source, Portable, Sound / Vibration Feature, Accessories.

Cultural Musical Instruments: Instrument Type, Cultural / Regional Tradition, Material, Size, Acoustic / Electronic, Skill Level, Handmade, Accessories / Case.

Religious Gift & Devotional Items: Gift Type, Tradition, Occasion, Material, Theme, Customizable, Packaging Included, Recipient Group.

Other Religious, Spiritual & Cultural Items: Product Type, Tradition / Cultural Context, Material, Intended Use, Origin, Key Features.

## Listing Types

Sale, Exchange, Wanted, Free (limited), Rent (limited), Offer. Lease is not ordinary. Service and Job are not applicable.

## Category Rules

- Religion/tradition is metadata and must not be inferred solely from product name.
- Cultural or religious origin is seller-provided unless independently verified.
- Handmade status is explicit and is not an authenticity guarantee.
- Material and dimensions remain structured independently.
- Quantity and quantity unit remain separate.
- Capacity and capacity unit remain separate where applicable.
- Combustible/burning products may require additional moderation and applicable safety restrictions.
- Historical, spiritual, cultural or religious authenticity claims are not automatically verified.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Religious, Spiritual & Cultural Items is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

# 25. CAT-023 — Health, Medical & Wellness Equipment

**Status:** APPROVED — 2026-09-28

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
| CAT-023-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-023-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-023-03 | Blood Pressure &amp;amp; Vital Signs Monitors | Primary catalogue scope for this subcategory. |
| CAT-023-04 | Thermometers &amp;amp; Temperature Monitoring | Primary catalogue scope for this subcategory. |
| CAT-023-05 | Blood Glucose &amp;amp; Diabetes Monitoring | Primary catalogue scope for this subcategory. |
| CAT-023-06 | Pulse Oximeters &amp;amp; Respiratory Monitoring | Primary catalogue scope for this subcategory. |
| CAT-023-07 | Diagnostic &amp;amp; Examination Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-08 | Mobility Aids &amp;amp; Walking Support | Primary catalogue scope for this subcategory. |
| CAT-023-09 | Wheelchairs &amp;amp; Mobility Vehicles | Primary catalogue scope for this subcategory. |
| CAT-023-10 | Patient Beds &amp;amp; Home Care Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-11 | Physiotherapy &amp;amp; Rehabilitation Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-12 | Respiratory &amp;amp; Oxygen Support Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-13 | Orthopedic &amp;amp; Support Products | Primary catalogue scope for this subcategory. |
| CAT-023-14 | Home Health &amp;amp; Recovery Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-15 | First Aid &amp;amp; Emergency Equipment | Primary catalogue scope for this subcategory. |
| CAT-023-16 | Medical Storage &amp;amp; Care Supplies | Primary catalogue scope for this subcategory. |
| CAT-023-17 | Wellness &amp;amp; Recovery Devices | Primary catalogue scope for this subcategory. |
| CAT-023-18 | Other Health, Medical &amp;amp; Wellness Equipment | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| MED-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| MED-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| MED-ATTR-003 | Equipment Type | select | Yes | No | No | No |
| MED-ATTR-004 | Condition | select. | No | No | No | No |
| MED-ATTR-005 | Intended Use | select. | No | No | No | No |
| MED-ATTR-006 | Intended User Group | select | No | No | No | Yes |
| MED-ATTR-007 | Material | select | No | No | No | Yes |
| MED-ATTR-008 | Size / Dimensions | text. | No | No | No | No |
| MED-ATTR-009 | Weight | decimal. | No | No | No | No |
| MED-ATTR-010 | Weight Unit | select. | No | No | No | No |
| MED-ATTR-011 | Capacity | decimal. | No | No | No | No |
| MED-ATTR-012 | Capacity Unit | select. | No | No | No | No |
| MED-ATTR-013 | Power Source | select. | No | No | No | No |
| MED-ATTR-014 | Warranty Status | select. | No | No | No | No |
| MED-ATTR-015 | Certification / Compliance | text | No | No | No | Yes |
| MED-ATTR-016 | Accessories Included | multi_select | No | No | No | Yes |
| MED-ATTR-017 | Purchase Year | integer. | No | No | No | No |
| MED-ATTR-018 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Open Box, Like New, Good, Fair, Used, Needs Repair, Refurbished.

Intended User Group: Infant, Child, Adult, Senior, Patient, Caregiver, Professional, General Household, Other.

Power Source: AC, Battery, Rechargeable Battery, USB, Manual, Solar, Compressed Air, Oxygen, Hydraulic, Other.

Weight Unit: g, kg, lb, Other.

Capacity Unit: ml, L, kg, Person, Patient, Other.

## Subcategory Specifications

Blood Pressure & Vital Signs Monitors: Device Type, Measurement Type, Measurement Range, Accuracy, Cuff Size, Cuff Type, Display Type, Memory / Data Storage, Connectivity, Power Source.

Thermometers & Temperature Monitoring: Device Type, Measurement Method, Measurement Range, Accuracy, Measurement Location, Display, Memory, Battery Type, Measurement Unit.

Blood Glucose & Diabetes Monitoring: Device Type, Measurement Type, Measurement Range, Test Method, Sample Type, Memory, Connectivity, Battery Type, Compatible Consumables, Accessories.

Pulse Oximeters & Respiratory Monitoring: Device Type, Measurement Type, Measurement Range, Accuracy, Display, Sensor Type, Battery Type, Alarm, Memory, Portability.

Diagnostic & Examination Equipment: Equipment Type, Measurement Type, Measurement Range, Accuracy, Intended Clinical / Household Use, Power Source, Display, Portable, Accessories, Calibration Status.

Mobility Aids & Walking Support: Product Type, Support Type, Height Range, Weight Capacity, Weight Capacity Unit, Adjustable, Foldable, Wheel Type, Material, Non-Slip Feature.

Wheelchairs & Mobility Vehicles: Product Type, Manual / Electric, Weight Capacity, Seat Width, Seat Height, Foldable, Wheel Size, Battery Type, Battery Range, Maximum Speed.

Patient Beds & Home Care Equipment: Equipment Type, Bed / Equipment Type, Weight Capacity, Dimensions, Adjustable Sections, Manual / Electric, Side Rails, Mattress Included, Wheels / Locking, Accessories.

Physiotherapy & Rehabilitation Equipment: Equipment Type, Therapy Type, Intended Body Area, Resistance / Load, Adjustable, Power Source, Portability, Material, Weight Capacity, Accessories.

Respiratory & Oxygen Support Equipment: Equipment Type, Oxygen / Respiratory Function, Flow Rate, Flow Rate Unit, Oxygen Concentration, Power Source, Battery Backup, Portability, Noise Level, Accessories.

Orthopedic & Support Products: Product Type, Body Area, Support Type, Size, Material, Adjustable, Compression Level, Laterality, Intended Use, Reusable.

Home Health & Recovery Equipment: Equipment Type, Intended Use, Body Area, Capacity, Capacity Unit, Adjustable, Portable, Power Source, Material, Accessories.

First Aid & Emergency Equipment: Product Type, Intended Use, Contents, Quantity, Sterile / Non-Sterile, Reusable / Disposable, Expiry Date, Packaging, Certification / Compliance.

Medical Storage & Care Supplies: Product Type, Intended Use, Material, Capacity, Capacity Unit, Number of Compartments, Portable, Lockable, Cleaning Method, Dimensions.

Wellness & Recovery Devices: Device Type, Intended Wellness Use, Body Area, Function, Intensity Levels, Heat / Cold Function, Power Source, Portable, Timer, Accessories.

Other Health, Medical & Wellness Equipment: Equipment Type, Intended Use, Intended User, Material, Power Source, Compatibility, Key Features.

## Listing Types

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

## Category Rules

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

# 26. CAT-024 — Security, Safety & Emergency Products

**Status:** APPROVED — 2026-09-28

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
| CAT-024-01 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-024-02 | Subcategory | Primary catalogue scope for this subcategory. |
| CAT-024-03 | Locks, Padlocks &amp;amp; Access Control | Primary catalogue scope for this subcategory. |
| CAT-024-04 | Safes, Lockboxes &amp;amp; Secure Storage | Primary catalogue scope for this subcategory. |
| CAT-024-05 | Home Security Products | Primary catalogue scope for this subcategory. |
| CAT-024-06 | Personal Safety &amp;amp; Protection | Primary catalogue scope for this subcategory. |
| CAT-024-07 | Fire Extinguishers &amp;amp; Fire Safety | Primary catalogue scope for this subcategory. |
| CAT-024-08 | Smoke, Gas &amp;amp; Safety Alarms | Primary catalogue scope for this subcategory. |
| CAT-024-09 | Emergency &amp;amp; Disaster Preparedness | Primary catalogue scope for this subcategory. |
| CAT-024-10 | First Response &amp;amp; Rescue Equipment | Primary catalogue scope for this subcategory. |
| CAT-024-11 | Reflective, Visibility &amp;amp; Warning Products | Primary catalogue scope for this subcategory. |
| CAT-024-12 | Workplace Safety Products | Primary catalogue scope for this subcategory. |
| CAT-024-13 | Electrical Safety Products | Primary catalogue scope for this subcategory. |
| CAT-024-14 | Child Safety &amp;amp; Home Safety | Primary catalogue scope for this subcategory. |
| CAT-024-15 | Travel &amp;amp; Personal Security | Primary catalogue scope for this subcategory. |
| CAT-024-16 | Security Signs, Barriers &amp;amp; Access Products | Primary catalogue scope for this subcategory. |
| CAT-024-17 | Safety Lighting &amp;amp; Emergency Lighting | Primary catalogue scope for this subcategory. |
| CAT-024-18 | Other Security, Safety &amp;amp; Emergency Products | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| SAFE-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| SAFE-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| SAFE-ATTR-003 | Product Type | select | Yes | No | No | No |
| SAFE-ATTR-004 | Condition | select. | No | No | No | No |
| SAFE-ATTR-005 | Safety / Security Function | select | No | No | No | Yes |
| SAFE-ATTR-006 | Intended Use | select. | No | No | No | No |
| SAFE-ATTR-007 | Material | select | No | No | No | Yes |
| SAFE-ATTR-008 | Size / Dimensions | text. | No | No | No | No |
| SAFE-ATTR-009 | Weight | decimal. | No | No | No | No |
| SAFE-ATTR-010 | Weight Unit | select. | No | No | No | No |
| SAFE-ATTR-011 | Power Source | select. | No | No | No | No |
| SAFE-ATTR-012 | Installation Type | select. | No | No | No | No |
| SAFE-ATTR-013 | Indoor / Outdoor | select. | No | No | No | No |
| SAFE-ATTR-014 | Certification / Standard | text | No | No | No | Yes |
| SAFE-ATTR-015 | Warranty Status | select. | No | No | No | No |
| SAFE-ATTR-016 | Accessories Included | multi_select | No | No | No | Yes |
| SAFE-ATTR-017 | Purchase Year | integer. | No | No | No | No |
| SAFE-ATTR-018 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Open Box, Like New, Good, Fair, Used, Needs Repair, Refurbished.

Power Source: AC, Battery, Rechargeable Battery, USB, Solar, Manual, None, Other.

Installation Type: None / Portable, Wall Mounted, Ceiling Mounted, Floor Mounted, Door / Gate Mounted, Vehicle Mounted, Surface Mounted, Built-in, Other.

Indoor / Outdoor: Indoor, Outdoor, Indoor / Outdoor.

## Subcategory Specifications

Locks, Padlocks & Access Control: Lock Type, Lock Mechanism, Key Type, Number of Keys, Digital / Mechanical, Smart / Connected, Material, Weather Resistant, Installation Type, Compatibility.

Safes, Lockboxes & Secure Storage: Safe Type, Lock Type, Fire Resistance, Water Resistance, Capacity, Capacity Unit, Wall / Floor Mount, Interior Compartments, Security Rating, Emergency Override.

Home Security Products: Product Type, Security Function, Installation Type, Indoor / Outdoor, Power Source, Connectivity, Alarm, Motion Detection, Remote Access, Compatibility.

Personal Safety & Protection: Product Type, Protection Function, Intended User Group, Size, Material, Wearable, Visibility, Reusable, Certification / Standard, Intended Environment.

Fire Extinguishers & Fire Safety: Equipment Type, Extinguishing Agent, Fire Class, Capacity, Capacity Unit, Pressure, Rechargeable, Manufacture Date, Expiry / Service Date, Certification / Standard.

Smoke, Gas & Safety Alarms: Alarm Type, Detection Type, Sensor Type, Detection Range, Alarm Type, Power Source, Battery Backup, Connectivity, Indoor / Outdoor, Test Function.

Emergency & Disaster Preparedness: Product Type, Emergency Type, Contents, Capacity, Quantity, Portable, Waterproof, Power Source, Storage Type, Intended Environment.

First Response & Rescue Equipment: Equipment Type, Emergency Use, Capacity, Weight Capacity, Material, Foldable, Portable, Reusable, Accessories, Certification / Standard.

Reflective, Visibility & Warning Products: Product Type, Visibility Function, Reflective Material, Color, Size, Visibility Distance, Indoor / Outdoor, Weather Resistant, Mounting Type, Reusable.

Workplace Safety Products: Product Type, Safety Function, Workplace Type, Protection Area, Size, Material, PPE / Non-PPE, Certification / Standard, Reusable, Intended Application.

Electrical Safety Products: Product Type, Electrical Safety Function, Voltage Rating, Current Rating, Power Rating, Protection Rating, Plug / Connector Type, Surge Protection, Grounding, Certification / Standard.

Child Safety & Home Safety: Product Type, Safety Function, Compatible Location, Child Age Range, Installation Type, Material, Adjustable, Lockable, Reusable, Compatibility.

Travel & Personal Security: Product Type, Security Function, Lock Type, Material, TSA Compatible, Portable, Alarm, RFID Protection, Weather Resistant, Intended Travel Use.

Security Signs, Barriers & Access Products: Product Type, Security Function, Material, Size, Mounting Type, Indoor / Outdoor, Reflective, Portable, Lockable, Intended Environment.

Safety Lighting & Emergency Lighting: Lighting Type, Light Source, Brightness, Battery Capacity, Runtime, Charging Method, Emergency Mode, Indoor / Outdoor, Mounting Type, Waterproof.

Other Security, Safety & Emergency Products: Product Type, Safety / Security Function, Intended Use, Material, Installation Type, Key Features.

## Listing Types

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

## Category Rules

- Safety/security function is separate from product type.
- Certification is separate from manufacturer information.
- Installation type is separate from indoor/outdoor placement.
- Electrical ratings use structured values and units where applicable.
- Capacity and capacity unit remain separate.
- Weight and weight unit remain separate.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Security, Safety & Emergency Products is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

# 27. CAT-025 — Baby, Maternity & Parenting Products

**Status:** APPROVED — 2026-09-28

## Scope

CAT-025 covers physical products for pregnancy, maternity, newborn care, parenting, breastfeeding, postpartum care and early-childhood needs.

## Boundary

- CAT-012 covers general baby, kids and toys.
- CAT-015 covers general personal-care, health and wellness products.
- CAT-023 covers medical/diagnostic equipment.
- CAT-005 covers ordinary clothing/fashion.
- CAT-003 covers furniture; dedicated maternity/nursing furniture may remain CAT-025.
- CAT-006 covers home appliances.
- CAT-024 covers school supplies.
- CAT-009 covers maternity, childcare, doula, nursing and other human-delivered services.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-025-01 | Maternity Clothing &amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-025-02 | Pregnancy Support &amp; Comfort Products | Primary catalogue scope for this subcategory. |
| CAT-025-03 | Maternity &amp; Hospital Bags | Primary catalogue scope for this subcategory. |
| CAT-025-04 | Breastfeeding &amp; Nursing Products | Primary catalogue scope for this subcategory. |
| CAT-025-05 | Breast Pumps &amp; Milk Storage | Primary catalogue scope for this subcategory. |
| CAT-025-06 | Maternity &amp; Nursing Furniture | Primary catalogue scope for this subcategory. |
| CAT-025-07 | Pregnancy &amp; Parenting Books / Materials | Primary catalogue scope for this subcategory. |
| CAT-025-08 | Postpartum Care Products | Primary catalogue scope for this subcategory. |
| CAT-025-09 | Parenting &amp; Childcare Accessories | Primary catalogue scope for this subcategory. |
| CAT-025-10 | Prenatal &amp; Postpartum Support Equipment | Primary catalogue scope for this subcategory. |
| CAT-025-11 | Pregnancy Testing &amp; Monitoring Products | Primary catalogue scope for this subcategory. |
| CAT-025-12 | Maternity Recovery &amp; Comfort Products | Primary catalogue scope for this subcategory. |
| CAT-025-13 | Nursing Covers &amp; Breastfeeding Accessories | Primary catalogue scope for this subcategory. |
| CAT-025-14 | Parenting Organization &amp; Care Kits | Primary catalogue scope for this subcategory. |
| CAT-025-15 | Other Maternity &amp; Parenting Products | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| PARENT-ATTR-001 | Brand / Manufacturer | text. | No | No | No | No |
| PARENT-ATTR-002 | Product Name / Model | text | Yes | No | No | No |
| PARENT-ATTR-003 | Product Type | select | Yes | No | No | No |
| PARENT-ATTR-004 | Condition | select. | No | No | No | No |
| PARENT-ATTR-005 | Intended User Group | select | No | No | No | Yes |
| PARENT-ATTR-006 | Material | select | No | No | No | Yes |
| PARENT-ATTR-007 | Size | select. | No | No | No | No |
| PARENT-ATTR-008 | Color | select | No | No | No | Yes |
| PARENT-ATTR-009 | Quantity | decimal. | No | No | No | No |
| PARENT-ATTR-010 | Quantity Unit | select. | No | No | No | No |
| PARENT-ATTR-011 | Dimensions | text. | No | No | No | No |
| PARENT-ATTR-012 | Age / Stage Suitability | select. | No | No | No | No |
| PARENT-ATTR-013 | Warranty Status | select. | No | No | No | No |
| PARENT-ATTR-014 | Accessories Included | multi_select | No | No | No | Yes |
| PARENT-ATTR-015 | Original Packaging | boolean. | No | No | No | No |
| PARENT-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Sealed, Open Box, Like New, Good, Fair, Used, Needs Repair, Refurbished.

Intended User Group: Pregnant Person, Postpartum Parent, Nursing Parent, Newborn, Infant, Baby, Parent / Caregiver, Family, Other.

Quantity Unit: Piece, Set, Pack, Pair, Bottle, Box, Dozen, Other.

## Subcategory Specifications

Maternity Clothing & Accessories: Clothing Type, Pregnancy / Postpartum Stage, Size, Gender / Target Group, Material / Fabric, Season, Adjustable, Nursing Friendly, Occasion, Set Quantity.

Pregnancy Support & Comfort Products: Product Type, Body Area, Support Type, Size, Material, Adjustable, Wearable, Reusable, Intended Stage, Care Instructions.

Maternity & Hospital Bags: Bag Type, Capacity, Capacity Unit, Material, Number of Compartments, Waterproof, Shoulder / Carry Type, Included Organizer, Suitable Stage, Dimensions.

Breastfeeding & Nursing Products: Product Type, Intended Use, Material, Size / Capacity, BPA-Free, Sterilization Compatible, Reusable, Portability, Accessories, Suitable Stage.

Breast Pumps & Milk Storage: Pump Type, Manual / Electric, Power Source, Pumping Modes, Suction Levels, Bottle Capacity, Capacity Unit, Battery Runtime, Sterilization Compatible, Accessories.

Baby Feeding & Bottle Supplies: Product Type, Material, Capacity, Capacity Unit, Bottle Type, Nipple / Flow Type, Age Suitability, BPA-Free, Sterilization Compatible, Set Quantity.

Baby Carriers & Wraps: Product Type, Carrying Position, Age Range, Weight Capacity, Weight Capacity Unit, Material, Adjustable, Safety Harness, Front / Back Carry, Washable.

Maternity & Nursing Furniture: Furniture Type, Material, Dimensions, Adjustable, Reclining, Foldable, Nursing Function, Storage, Cushion / Mattress Included, Assembly Required.

Pregnancy & Parenting Books / Materials: Material Type, Topic, Language, Author / Creator, Publisher, Edition, Publication Year, Format, Intended Stage, ISBN / Catalog Number.

Postpartum Care Products: Product Type, Intended Use, Body Area, Material, Size, Reusable, Disposable, Intended Postpartum Stage, Care Instructions, Quantity.

Newborn Care & Essentials: Product Type, Intended Use, Age Suitability, Material, Size, Reusable, Disposable, Skin Contact, Quantity, Accessories.

Baby Bathing & Hygiene: Product Type, Intended Use, Material / Ingredients, Age Suitability, Size / Capacity, Reusable, Fragrance-Free, Hypoallergenic Claim, Quantity, Accessories.

Baby Sleep & Bedding: Product Type, Age Suitability, Material, Dimensions, Mattress / Padding Type, Firmness, Washable, Foldable, Portable, Safety Feature.

Baby Safety & Monitoring: Product Type, Safety / Monitoring Function, Age Suitability, Installation Type, Power Source, Connectivity, Alarm, Sensor Type, Indoor / Outdoor, Accessories.

Parenting & Childcare Accessories: Product Type, Intended Use, Age / Stage, Material, Size, Portable, Foldable, Reusable, Quantity, Accessories.

Other Baby, Maternity & Parenting Products: Product Type, Intended User, Intended Stage, Material, Intended Use, Key Features.

## Listing Types

Sale, Exchange (limited), Wanted, Free, Rent (limited), Offer. Lease, Service and Job are not ordinary listing types.

## Safety & Boundary Rules

- General baby clothing, toys, kids products and children's equipment belong to CAT-012 unless maternity/parenting lifecycle is the primary purpose.
- General personal-care products belong to CAT-015.
- Medical diagnostic or therapeutic equipment belongs to CAT-023.
- Pregnancy/maternity books belong to CAT-025 when specifically parenting/maternity-oriented; general books remain CAT-012.
- Ordinary furniture belongs to CAT-003; dedicated maternity/nursing furniture may remain CAT-025.
- Maternity and childcare services belong to CAT-009.
- Baby appliances such as sterilizers and dedicated electrical appliances belong to CAT-006 where appliance classification is primary.
- School/learning supplies belong to CAT-024.
- Safety claims are not automatically verified.
- “Medical grade,” “hospital grade” and similar claims are seller-provided unless independently verified.
- Feeding and milk-storage products require appropriate material and capacity information.
- Products intended for newborn sleep or infant safety may require stronger moderation.
- Age/stage suitability is explicit and should not be inferred from product title alone.
- Hygiene-sensitive used products may require additional moderation.
- Expired consumables should not remain active marketplace inventory.
- Health or medical treatment claims should not be treated as verified product capabilities.

## Category Rules

- Pregnancy stage, postpartum stage and infant age/stage remain distinct concepts where applicable.
- Capacity and capacity unit remain separate.
- Quantity and quantity unit remain separate.
- Age/stage suitability is structured where practical.
- Disposable versus reusable is explicit.
- Material remains separate from ingredients/material composition where relevant.
- Multi-value attributes use multiple attribute rows; single-value attributes allow at most one.
- Other Baby, Maternity & Parenting Products is the controlled fallback.
- All listings follow the standard review-before-publication lifecycle.

## Phase 3 Audit Correction

CAT-025 is restricted to pregnancy, maternity, breastfeeding/nursing, postpartum and parenting-lifecycle products. General baby/kids products remain CAT-011.

# 28. Catalogue Status & Detailed Documents

| Catalogue | Status | Detailed Notion Document |
| --- | --- | --- |
| CAT-001 — Property | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-001%20%E2%80%94%20Property%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8184b48cf6330a7d223f.md) |
| CAT-002 — Mobile & Electronics | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-002%20%E2%80%94%20Mobile%20&%20Electronics%20%E2%80%94%20Detailed%20Catalogu%203e99628c857d81768d83ff9dbec52ea9.md) |
| CAT-003 — Furniture & Home | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-003%20%E2%80%94%20Furniture%20&%20Home%203e99628c857d8142a212ffa951d05c93.md) |
| CAT-004 — Vehicles | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-004%20%E2%80%94%20Vehicles%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8175926fc30f494937a2.md) |
| CAT-005 — Fashion & Clothing | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-005%20%E2%80%94%20Fashion%20&%20Clothing%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8188afebcd5aa774440c.md) |
| CAT-006 — Home Appliances & Kitchen | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-006%20%E2%80%94%20Home%20Appliances%20&%20Kitchen%20%E2%80%94%20Detailed%20Cat%203e99628c857d8118874ddf151d2bd700.md) |
| CAT-007 — Sports, Fitness & Outdoor | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-007%20%E2%80%94%20Sports,%20Fitness%20&%20Outdoor%20%E2%80%94%20Detailed%20Cat%203e99628c857d81b995c7c6657bbf068d.md) |
| CAT-008 — Jobs & Employment | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-008%20%E2%80%94%20Jobs%20&%20Employment%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d812d899be7d943aa026e.md) |
| CAT-009 — Services | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-009%20%E2%80%94%20Services%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d81428aaad662e3a5ddfa.md) |
| CAT-010 — Business, Office & Commercial Equipment | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-010%20%E2%80%94%20Business,%20Office%20&%20Commercial%20Equipment%20%203e99628c857d8104a0f0ea9439b9cb94.md) |
| CAT-011 — Baby, Kids & Toys | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-011%20%E2%80%94%20Baby,%20Kids%20&%20Toys%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8107a548f23d2ab5d398.md) |
| CAT-012 — Books, Media & Collectibles | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-012%20%E2%80%94%20Books,%20Media%20&%20Collectibles%20%E2%80%94%20Detailed%20C%203e99628c857d81618d63c21b82a1f65d.md) |
| CAT-013 — Food, Agriculture Products & Livestock | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-013%20%E2%80%94%20Food,%20Agriculture%20Products%20&%20Livestock%20%E2%80%94%203e99628c857d81d4a68dc17dba6b6f1c.md) |
| CAT-014 — Health, Beauty & Personal Care Products | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-014%20%E2%80%94%20Health,%20Beauty%20&%20Personal%20Care%20Products%20%203e99628c857d813baaaac51356df8891.md) |
| CAT-015 — Home & Garden | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-015%20%E2%80%94%20Home%20&%20Garden%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8159a5f3f14ecf0854e3.md) |
| CAT-016 — Pet Supplies & Animals | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-016%20%E2%80%94%20Pet%20Supplies%20&%20Animals%20%E2%80%94%20Detailed%20Catalo%203e99628c857d8185a330cbe7709f7fae.md) |
| CAT-017 — Travel, Luggage & Accessories | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-017%20%E2%80%94%20Travel,%20Luggage%20&%20Accessories%20%E2%80%94%20Detailed%203e99628c857d81d69e28fd171beac2b2.md) |
| CAT-018 — Construction, Tools & Building Materials | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-018%20%E2%80%94%20Construction,%20Tools%20&%20Building%20Materials%203e99628c857d818286b6f36116dd6c8b.md) |
| CAT-019 — Industrial, Machinery & Heavy Equipment | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-019%20%E2%80%94%20Industrial,%20Machinery%20&%20Heavy%20Equipment%20%203e99628c857d8193a836fd56a41cc31d.md) |
| CAT-020 — Weddings, Events & Party Supplies | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-020%20%E2%80%94%20Weddings,%20Events%20&%20Party%20Supplies%20%E2%80%94%20Deta%203e99628c857d81099194c78be60fee26.md) |
| CAT-021 — Office, School & Stationery Supplies | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-021%20%E2%80%94%20Office,%20School%20&%20Stationery%20Supplies%20%E2%80%94%20D%203e99628c857d81afa141e2f3ac5e0188.md) |
| CAT-022 — Religious, Spiritual & Cultural Items | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-022%20%E2%80%94%20Religious,%20Spiritual%20&%20Cultural%20Items%20%E2%80%94%20%203e99628c857d814d98cae93c5330a18b.md) |
| CAT-023 — Health, Medical & Wellness Equipment | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-023%20%E2%80%94%20Health,%20Medical%20&%20Wellness%20Equipment%20%E2%80%94%20D%203e99628c857d81239864c3f22ad5b4fb.md) |
| CAT-024 — Security, Safety & Emergency Products | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-024%20%E2%80%94%20Security,%20Safety%20&%20Emergency%20Products%20%E2%80%94%20%203e99628c857d819d8b8be71bb00c0599.md) |
| CAT-025 — Baby, Maternity & Parenting Products | APPROVED — 2026-09-28 | [Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-025%20%E2%80%94%20Baby,%20Maternity%20&%20Parenting%20Products%20%E2%80%94%20D%203e99628c857d8101b1fec3e877b0a34b.md) |

# 29. Cross-Catalogue Rules

- Common attributes use canonical definitions where the same concept has the same meaning across catalogues.
- Category-specific attributes remain owned by their catalogue.
- Multi-value attributes create multiple `listing_attributes` rows; single-value attributes allow at most one value.
- Exactly one typed value representation is valid for each attribute value row.
- Option-backed values must match valid catalogue options.
- Capacity, quantity, weight, area, length, distance, and duration use separate numeric/unit concepts.
- Sensitive identifiers such as IMEI, serial numbers, private registration identifiers, identity-document numbers, payment/provider references, and private verification evidence are not ordinary public filter attributes.
- TV/display products belong to CAT-002; household appliances belong to CAT-006.
- Heavy construction, industrial, and agricultural machinery belongs to CAT-019; ordinary construction tools and materials belong to CAT-018.
- Consumer health/beauty/personal-care products belong to CAT-014; health/medical/wellness equipment belongs to CAT-023.
- General baby/kids products belong to CAT-011; pregnancy, maternity, breastfeeding, postpartum, and parenting-lifecycle products belong to CAT-025.
- General arts, crafts, music, and collectibles belong to CAT-012; religious/spiritual/cultural-purpose items belong to CAT-022.
- Travel-specific luggage belongs to CAT-017; fashion bags/accessories belong to CAT-005.
- Moving/packing/storage products belong to CAT-015; moving services belong to CAT-009.
- Pets and pet products belong to CAT-016; livestock and agricultural animals belong to CAT-013.
- Commercial/business equipment belongs to CAT-010; industrial/heavy equipment belongs to CAT-019.

## Option Registry — CAT-001 to CAT-005

**Purpose:** Central implementation registry for controlled `select` and `multi_select` values. It mirrors the approved option-backed attributes; it does not introduce new taxonomy.

| Option Set ID | Catalogue | Attribute ID | Attribute | Type | Approved Values |
| --- | --- | --- | --- | --- | --- |
| OPT-CAT-001-PROP-001 | CAT-001 | PROP-ATTR-001 | Property Condition | select | New, Like New, Good, Fair, Needs Repair, Under Construction, Renovation Required |
| OPT-CAT-001-PROP-002 | CAT-001 | PROP-ATTR-002 | Furnished Status | select | Fully Furnished, Semi Furnished, Unfurnished |
| OPT-CAT-001-PROP-009 | CAT-001 | PROP-ATTR-009 | Area Unit | select | sq ft, sq m, aana, paisa, daam, ropani, bigha, kattha, dhur |
| OPT-CAT-001-PROP-013 | CAT-001 | PROP-ATTR-013 | Road Access | select | None, Footpath, Gravel, Paved, Blacktopped, Highway, Other |
| OPT-CAT-001-PROP-014 | CAT-001 | PROP-ATTR-014 | Facing Direction | select | North, South, East, West, North-East, North-West, South-East, South-West |
| OPT-CAT-001-PROP-016 | CAT-001 | PROP-ATTR-016 | Property Amenities | multi_select | Balcony, Terrace, Garden, Swimming Pool, Gym, Elevator, Security Guard, CCTV, Internet, Solar, Generator, Backup Power, Air Conditioning, Heating, Modular Kitchen, Attached Bathroom, Common Bathroom, Store Room, Laundry, Servant Quarter, Basement, Rooftop Access, Community Hall, Playground |
| OPT-CAT-001-PROP-017 | CAT-001 | PROP-ATTR-017 | Nearby Facilities | multi_select | School, College, Hospital, Clinic, Pharmacy, Bank, ATM, Police Station, Bus Stop, Airport, Market, Shopping Center, Restaurant, Temple, Mosque, Church, Park, Government Office, Railway Station, Highway, Petrol Pump |
| OPT-CAT-002-MOB-001 | CAT-002 | MOB-001 | Operating System | select | Android, iOS, Other |
| OPT-CAT-002-CAM-001 | CAT-002 | CAM-001 | Camera Type | select | DSLR, Mirrorless, Point-and-Shoot, Action Camera, Video Camera, Other |
| OPT-CAT-002-AUD-001 | CAT-002 | AUD-001 | Audio Type | select | Speaker, Soundbar, Home Theater, Headphones, Earbuds, Microphone, Amplifier, Mixer, Other |
| OPT-CAT-002-GAME-001 | CAT-002 | GAME-001 | Gaming Type | select | Console, Handheld Console, Gaming PC, Gaming Accessory, Game Software, Other |
| OPT-CAT-002-CACC-001 | CAT-002 | CACC-001 | Accessory Type | select | Monitor, Keyboard, Mouse, Webcam, Printer, Scanner, Router, UPS, Storage Device, Dock, Adapter, Cable, Other |
| OPT-CAT-003-SOFA-001 | CAT-003 | SOFA-001 | Sofa Type | select | Sofa, Sectional, Recliner Sofa, Sofa Bed, Loveseat, Divan, Other |
| OPT-CAT-003-SOFA-004 | CAT-003 | SOFA-004 | Upholstery Material | select | Wood, Fabric, Leather, Faux Leather, Mixed, Other |
| OPT-CAT-003-BED-001 | CAT-003 | BED-001 | Bed Type | select | Single, Double, Queen, King, Bunk Bed, Loft Bed, Storage Bed, Other |
| OPT-CAT-003-BED-002 | CAT-003 | BED-002 | Bed Size | select | Single, Twin, Double, Queen, King, California King, Bunk, Other |
| OPT-CAT-003-MAT-001 | CAT-003 | MAT-001 | Mattress Type | select | Spring, Pocket Spring, Memory Foam, Foam, Latex, Hybrid, Other |
| OPT-CAT-003-MAT-002 | CAT-003 | MAT-002 | Mattress Size | select | Single, Twin, Double, Queen, King, California King, Other |
| OPT-CAT-003-MAT-004 | CAT-003 | MAT-004 | Firmness | select | Soft, Medium Soft, Medium, Medium Firm, Firm, Extra Firm, Other |
| OPT-CAT-003-TAB-001 | CAT-003 | TAB-001 | Table Type | select | Dining Table, Coffee Table, Center Table, Side Table, Study Table, Computer Table, Office Table, Folding Table, Other |
| OPT-CAT-003-TAB-003 | CAT-003 | TAB-003 | Shape | select | Rectangular, Square, Round, Oval, L-Shaped, Other |
| OPT-CAT-003-CHAIR-001 | CAT-003 | CHAIR-001 | Chair Type | select | Dining Chair, Office Chair, Gaming Chair, Recliner Chair, Armchair, Plastic Chair, Folding Chair, Rocking Chair, Stool, Other |
| OPT-CAT-003-DSET-001 | CAT-003 | DSET-001 | Set Type | select | Dining Table Set, Breakfast Set, Bar Set, Other |
| OPT-CAT-003-WARD-001 | CAT-003 | WARD-001 | Storage Type | select | Wardrobe, Cabinet, Cupboard, Chest of Drawers, Shoe Cabinet, Display Cabinet, Other |
| OPT-CAT-003-DESK-001 | CAT-003 | DESK-001 | Furniture Type | select | Office Desk, Reception Desk, Workstation, Conference Table, Filing Cabinet, Office Chair, Other |
| OPT-CAT-003-SHELF-001 | CAT-003 | SHELF-001 | Storage Type | select | Bookshelf, Wall Shelf, Rack, Storage Rack, Shoe Rack, Plastic Storage, Other |
| OPT-CAT-003-SHELF-006 | CAT-003 | SHELF-006 | Load Capacity Unit | select | kg, ton, lb |
| OPT-CAT-003-KF-001 | CAT-003 | KF-001 | Kitchen Item Type | select | Kitchen Cabinet, Kitchen Rack, Pantry Cabinet, Kitchen Island, Dining Cabinet, Other |
| OPT-CAT-003-DECOR-001 | CAT-003 | DECOR-001 | Decor Type | select | Wall Art, Mirror, Clock, Vase, Curtain, Carpet, Rug, Lamp, Decorative Item, Other |
| OPT-CAT-003-DECOR-002 | CAT-003 | DECOR-002 | Style | select | Modern, Traditional, Minimalist, Vintage, Industrial, Other |
| OPT-CAT-003-DECOR-003 | CAT-003 | DECOR-003 | Indoor / Outdoor | select | Indoor, Outdoor, Both |
| OPT-CAT-003-OTHER-001 | CAT-003 | OTHER-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| OPT-CAT-004-CAR-001 | CAT-004 | CAR-001 | Body Type | select | Sedan, Hatchback, Coupe, Convertible, Wagon, Crossover, Other |
| OPT-CAT-004-CAR-004 | CAT-004 | CAR-004 | Drive Type | select | FWD, RWD, AWD, 4WD, Other |
| OPT-CAT-004-SUV-001 | CAT-004 | SUV-001 | Body Type | select | Compact SUV, SUV, Crossover, Jeep, Off-road, Other |
| OPT-CAT-004-VAN-003 | CAT-004 | VAN-003 | Vehicle Purpose | select | Passenger, Cargo, Commercial, School, Tourism, Other |
| OPT-CAT-004-PICK-001 | CAT-004 | PICK-001 | Cab Type | select | Single Cab, Double Cab, Extended Cab, Other |
| OPT-CAT-004-PICK-006 | CAT-004 | PICK-006 | Bed Type | select | Standard, Long Bed, Short Bed, Flatbed, Other |
| OPT-CAT-004-TRK-001 | CAT-004 | TRK-001 | Truck Type | select | Light Truck, Medium Truck, Heavy Truck, Tipper, Tanker, Container Truck, Cargo Truck, Other |
| OPT-CAT-004-BUS-001 | CAT-004 | BUS-001 | Vehicle Type | select | Bus, Mini Bus, Microbus, Tourist Bus, School Bus, Other |
| OPT-CAT-004-BUS-004 | CAT-004 | BUS-004 | Usage Type | select | Public Transport, Tourist, School, Staff, Private, Other |
| OPT-CAT-004-MOTO-001 | CAT-004 | MOTO-001 | Motorcycle Type | select | Standard, Sports, Cruiser, Adventure, Touring, Off-road, Dirt Bike, Other |
| OPT-CAT-004-SCOOT-001 | CAT-004 | SCOOT-001 | Scooter Type | select | Standard, Maxi Scooter, Electric Scooter, Other |
| OPT-CAT-004-EVC-007 | CAT-004 | EVC-007 | Charging Connector | select | Type 1, Type 2, CCS, CHAdeMO, GB/T, Other |
| OPT-CAT-004-AGR-001 | CAT-004 | AGR-001 | Vehicle Type | select | Tractor, Power Tiller, Harvester, Agricultural Machine, Other |
| OPT-CAT-004-BIKE-001 | CAT-004 | BIKE-001 | Bicycle Type | select | Mountain, Road, Hybrid, City, BMX, Kids, Folding, Electric, Other |
| OPT-CAT-004-BIKE-003 | CAT-004 | BIKE-003 | Frame Material | select | Steel, Aluminum, Carbon Fiber, Titanium, Other |
| OPT-CAT-004-THREE-001 | CAT-004 | THREE-001 | Vehicle Type | select | Auto Rickshaw, Electric Three-Wheeler, Cargo Three-Wheeler, Passenger Three-Wheeler, Other |
| OPT-CAT-005-MEN-001 | CAT-005 | MEN-001 | Clothing Type | select | Shirt, T-Shirt, Polo Shirt, Pants, Jeans, Trousers, Shorts, Jacket, Coat, Sweater, Hoodie, Blazer, Suit, Kurta, Daura Suruwal, Vest, Underwear, Other |
| OPT-CAT-005-MEN-003 | CAT-005 | MEN-003 | Fit Type | select | Slim, Regular, Relaxed, Oversized, Other |
| OPT-CAT-005-MEN-005 | CAT-005 | MEN-005 | Occasion | select | Casual, Formal, Office, Party, Wedding, Traditional, Sports, Other |
| OPT-CAT-005-WOMEN-001 | CAT-005 | WOMEN-001 | Clothing Type | select | Saree, Kurta, Kurti, Salwar Suit, Lehenga, Dress, Gown, Blouse, Top, T-Shirt, Shirt, Jeans, Pants, Skirt, Jacket, Coat, Sweater, Hoodie, Shawl, Other |
| OPT-CAT-005-WOMEN-003 | CAT-005 | WOMEN-003 | Fit Type | select | Slim, Regular, Relaxed, Oversized, Other |
| OPT-CAT-005-WOMEN-004 | CAT-005 | WOMEN-004 | Length Type | select | Crop, Waist, Hip, Knee, Midi, Ankle, Full Length, Other |
| OPT-CAT-005-KIDS-001 | CAT-005 | KIDS-001 | Clothing Type | select | T-Shirt, Shirt, Pants, Jeans, Shorts, Dress, Skirt, Frock, Kurta, Jacket, Sweater, Hoodie, School Wear, Other |
| OPT-CAT-005-ETHNIC-001 | CAT-005 | ETHNIC-001 | Wear Type | select | Saree, Daura Suruwal, Kurta Suruwal, Dhoti, Lehenga, Sherwani, Kurti, Salwar Suit, Tharu Wear, Maithili Wear, Newari Wear, Other |
| OPT-CAT-005-FOOT-001 | CAT-005 | FOOT-001 | Footwear Type | select | Sports Shoes, Running Shoes, Sneakers, Formal Shoes, Sandals, Slippers, Boots, Heels, Flats, Loafers, School Shoes, Safety Shoes, Traditional Footwear, Other |
| OPT-CAT-005-FOOT-005 | CAT-005 | FOOT-005 | Closure Type | select | Lace, Velcro, Buckle, Slip-on, Zip, Other |
| OPT-CAT-005-BAG-001 | CAT-005 | BAG-001 | Bag Type | select | Backpack, Handbag, Shoulder Bag, Sling Bag, Laptop Bag, School Bag, Wallet, Purse, Briefcase, Sports Bag, Other |
| OPT-CAT-005-WATCH-001 | CAT-005 | WATCH-001 | Watch Type | select | Analog, Digital, Smartwatch, Chronograph, Luxury, Sports, Other |
| OPT-CAT-005-WATCH-002 | CAT-005 | WATCH-002 | Movement | select | Quartz, Mechanical, Automatic, Solar, Other |
| OPT-CAT-005-WATCH-003 | CAT-005 | WATCH-003 | Display Type | select | Analog, Digital, Analog-Digital |
| OPT-CAT-005-WATCH-006 | CAT-005 | WATCH-006 | Smart Features | multi_select | Bluetooth, GPS, Heart Rate, Fitness Tracking, Calling, Notifications, Sleep Tracking, Other |
| OPT-CAT-005-JEW-001 | CAT-005 | JEW-001 | Jewelry Type | select | Ring, Necklace, Chain, Bracelet, Bangle, Earrings, Pendant, Anklet, Brooch, Nose Ring, Traditional Jewelry, Other |
| OPT-CAT-005-JEW-004 | CAT-005 | JEW-004 | Purity | select | 24K, 22K, 18K, 14K, 10K, Other |
| OPT-CAT-005-OCC-001 | CAT-005 | OCC-001 | Wear Type | select | Wedding Dress, Lehenga, Saree, Sherwani, Suit, Gown, Party Dress, Traditional Wear, Other |
| OPT-CAT-005-OCC-003 | CAT-005 | OCC-003 | Occasion | select | Wedding, Engagement, Reception, Festival, Party, Formal Event, Traditional Ceremony, Other |
| OPT-CAT-005-SPORT-001 | CAT-005 | SPORT-001 | Sportswear Type | select | Jersey, Tracksuit, Shorts, Sports T-Shirt, Sports Shoes, Compression Wear, Sports Jacket, Other |
| OPT-CAT-005-BABY-001 | CAT-005 | BABY-001 | Clothing Type | select | Bodysuit, Romper, Frock, T-Shirt, Pants, Jacket, Sweater, Sleepwear, Traditional Wear, Set, Other |
| OPT-CAT-005-UNI-001 | CAT-005 | UNI-001 | Uniform Type | select | School Uniform, College Uniform, Hospital Uniform, Security Uniform, Corporate Uniform, Industrial Workwear, Hospitality Uniform, Sports Uniform, Other |
| OPT-CAT-005-ACC-001 | CAT-005 | ACC-001 | Accessory Type | select | Belt, Tie, Scarf, Cap, Hat, Sunglasses, Gloves, Socks, Hair Accessories, Hair Clip, Headband, Wallet, Keychain, Other |

**Registry rule:** seed these values explicitly. No implementation-time invention of option values. Controlled values defined in catalogue prose must also be resolved into this registry before database seeding.

# 30. Detailed Catalogue Page References

[CAT-001 — Property — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-001%20%E2%80%94%20Property%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8184b48cf6330a7d223f.md)

[CAT-002 — Mobile & Electronics — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-002%20%E2%80%94%20Mobile%20&%20Electronics%20%E2%80%94%20Detailed%20Catalogu%203e99628c857d81768d83ff9dbec52ea9.md)

[CAT-003 — Furniture & Home](13%201%20Category%20&%20Attribute%20Catalogue/CAT-003%20%E2%80%94%20Furniture%20&%20Home%203e99628c857d8142a212ffa951d05c93.md)

[CAT-004 — Vehicles — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-004%20%E2%80%94%20Vehicles%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8175926fc30f494937a2.md)

[CAT-005 — Fashion & Clothing — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-005%20%E2%80%94%20Fashion%20&%20Clothing%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8188afebcd5aa774440c.md)

[CAT-006 — Home Appliances & Kitchen — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-006%20%E2%80%94%20Home%20Appliances%20&%20Kitchen%20%E2%80%94%20Detailed%20Cat%203e99628c857d8118874ddf151d2bd700.md)

[CAT-007 — Sports, Fitness & Outdoor — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-007%20%E2%80%94%20Sports,%20Fitness%20&%20Outdoor%20%E2%80%94%20Detailed%20Cat%203e99628c857d81b995c7c6657bbf068d.md)

[CAT-008 — Jobs & Employment — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-008%20%E2%80%94%20Jobs%20&%20Employment%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d812d899be7d943aa026e.md)

[CAT-009 — Services — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-009%20%E2%80%94%20Services%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d81428aaad662e3a5ddfa.md)

[CAT-010 — Business, Office & Commercial Equipment — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-010%20%E2%80%94%20Business,%20Office%20&%20Commercial%20Equipment%20%203e99628c857d8104a0f0ea9439b9cb94.md)

[CAT-011 — Baby, Kids & Toys — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-011%20%E2%80%94%20Baby,%20Kids%20&%20Toys%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8107a548f23d2ab5d398.md)

[CAT-012 — Books, Media & Collectibles — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-012%20%E2%80%94%20Books,%20Media%20&%20Collectibles%20%E2%80%94%20Detailed%20C%203e99628c857d81618d63c21b82a1f65d.md)

[CAT-013 — Food, Agriculture Products & Livestock — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-013%20%E2%80%94%20Food,%20Agriculture%20Products%20&%20Livestock%20%E2%80%94%203e99628c857d81d4a68dc17dba6b6f1c.md)

[CAT-014 — Health, Beauty & Personal Care Products — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-014%20%E2%80%94%20Health,%20Beauty%20&%20Personal%20Care%20Products%20%203e99628c857d813baaaac51356df8891.md)

[CAT-015 — Home & Garden — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-015%20%E2%80%94%20Home%20&%20Garden%20%E2%80%94%20Detailed%20Catalogue%203e99628c857d8159a5f3f14ecf0854e3.md)

[CAT-016 — Pet Supplies & Animals — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-016%20%E2%80%94%20Pet%20Supplies%20&%20Animals%20%E2%80%94%20Detailed%20Catalo%203e99628c857d8185a330cbe7709f7fae.md)

[CAT-017 — Travel, Luggage & Accessories — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-017%20%E2%80%94%20Travel,%20Luggage%20&%20Accessories%20%E2%80%94%20Detailed%203e99628c857d81d69e28fd171beac2b2.md)

[CAT-018 — Construction, Tools & Building Materials — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-018%20%E2%80%94%20Construction,%20Tools%20&%20Building%20Materials%203e99628c857d818286b6f36116dd6c8b.md)

[CAT-019 — Industrial, Machinery & Heavy Equipment — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-019%20%E2%80%94%20Industrial,%20Machinery%20&%20Heavy%20Equipment%20%203e99628c857d8193a836fd56a41cc31d.md)

[CAT-020 — Weddings, Events & Party Supplies — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-020%20%E2%80%94%20Weddings,%20Events%20&%20Party%20Supplies%20%E2%80%94%20Deta%203e99628c857d81099194c78be60fee26.md)

[CAT-021 — Office, School & Stationery Supplies — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-021%20%E2%80%94%20Office,%20School%20&%20Stationery%20Supplies%20%E2%80%94%20D%203e99628c857d81afa141e2f3ac5e0188.md)

[CAT-022 — Religious, Spiritual & Cultural Items — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-022%20%E2%80%94%20Religious,%20Spiritual%20&%20Cultural%20Items%20%E2%80%94%20%203e99628c857d814d98cae93c5330a18b.md)

[CAT-023 — Health, Medical & Wellness Equipment — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-023%20%E2%80%94%20Health,%20Medical%20&%20Wellness%20Equipment%20%E2%80%94%20D%203e99628c857d81239864c3f22ad5b4fb.md)

[CAT-024 — Security, Safety & Emergency Products — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-024%20%E2%80%94%20Security,%20Safety%20&%20Emergency%20Products%20%E2%80%94%20%203e99628c857d819d8b8be71bb00c0599.md)

[CAT-025 — Baby, Maternity & Parenting Products — Detailed Catalogue](13%201%20Category%20&%20Attribute%20Catalogue/CAT-025%20%E2%80%94%20Baby,%20Maternity%20&%20Parenting%20Products%20%E2%80%94%20D%203e99628c857d8101b1fec3e877b0a34b.md)

---

# Seed Data Package — 2026-09-29

The current CAT-001 through CAT-025 detailed pages contain **25 top-level categories and 372 documented subcategories**. These seed artifacts are derived from those current pages and are not intended to invent missing taxonomy.

## Category Seed CSVs

[khoj-bhet-category-seed-CAT-001-005-v2.csv](13%201%20Category%20&%20Attribute%20Catalogue/khoj-bhet-category-seed-CAT-001-005-v2.csv)

[khoj-bhet-category-seed-CAT-006-010-v2.csv](13%201%20Category%20&%20Attribute%20Catalogue/khoj-bhet-category-seed-CAT-006-010-v2.csv)

[khoj-bhet-category-seed-CAT-011-015-v2.csv](13%201%20Category%20&%20Attribute%20Catalogue/khoj-bhet-category-seed-CAT-011-015-v2.csv)

[khoj-bhet-category-seed-CAT-016-020-v2.csv](13%201%20Category%20&%20Attribute%20Catalogue/khoj-bhet-category-seed-CAT-016-020-v2.csv)

[khoj-bhet-category-seed-CAT-021-025-v2.csv](13%201%20Category%20&%20Attribute%20Catalogue/khoj-bhet-category-seed-CAT-021-025-v2.csv)

## Laravel Category Seeder

[CategoryCatalogueSeeder.txt](13%201%20Category%20&%20Attribute%20Catalogue/CategoryCatalogueSeeder.txt)

## Nepal Administrative Location Seed

Source JSON contains the Nepal province → district → local-level → ward hierarchy used by the location seeder.

[nepal-administrative-locations.json](13%201%20Category%20&%20Attribute%20Catalogue/nepal-administrative-locations.json)

## Laravel Location Seeder

[NepalLocationSeeder.txt](13%201%20Category%20&%20Attribute%20Catalogue/NepalLocationSeeder.txt)

**Location-source note:** The JSON is a developer-friendly public dataset. Validate the final administrative master data against the current Government of Nepal / MoFAGA source before production deployment. The current MoFAGA local-contact portal reports 753 local levels; Nepal Census 2021 reports 6,743 wards.

**Option-seed rule:** Attributes described only as “UNRESOLVED — explicit catalogue options required before seed” are not assigned invented values. Their explicit options must be resolved from the catalogue before category_attribute_options is populated.

# 31. Phase 3 — Category & Attribute Catalogue Reconciliation Gate

**Resolution Date:** 2026-09-30  

**Result:** **SUPERSEDED — deterministic catalogue option and unit resolution was completed by Phase 3B on 2026-09-30. The remaining work is production seed materialization and runtime validation.**

## 31.1 Canonical Baseline — CONFIRMED

- **25** top-level categories: CAT-001 through CAT-025.
- **372** documented subcategories across the 25 detailed catalogue pages.
- The 25 detailed CAT pages remain the authority for category/subcategory/attribute definitions.
- The parent catalogue page is the implementation registry and cross-reference; it must not invent taxonomy absent from the detailed pages.
- No 385 or 399 subcategory baseline is accepted.

## 31.2 Catalogue-vs-Seed Distinction — RESOLVED

A catalogue may be **APPROVED** as a product definition while still being **NOT SEED-READY**. Seed readiness requires every option-backed attribute to have explicit values, stable applicability, and deterministic validation metadata.

## 31.3 Work Completed in This Phase

- Re-audited all 25 CAT page references and confirmed all 25 canonical detailed pages are linked from the parent catalogue.
- Preserved the 25 / 372 taxonomy baseline.
- CAT-001 blank option cells were converted to explicit **UNRESOLVED** markers instead of silently implying that an empty cell is a valid option definition.
- CAT-001 common controlled values already defined in its catalogue prose were added explicitly to the central Option Registry for PROP-ATTR-001, 002, 009, 013, 014, 016, and 017.
- Literal Controlled option set placeholders were converted to explicit **UNRESOLVED — explicit catalogue options required before seed** markers across the affected detailed CAT pages and central registry. No option values were invented during this reconciliation pass.

## 31.4 Historical Seed Blocker Snapshot — Superseded

This list is retained as historical context and is not a current defect inventory. Later decisions supersede several items: CAT-001 option sets and area-unit policy are recorded in its detailed page; Phase 3B §43–§44 defines shared controlled-option and unit rules; CAT-002 product defaults are recorded in §45. Do not treat the old wording below as evidence that those decisions are still open.

The current work is implementation validation: materialize the final catalogue, confirm every source attribute and option is represented exactly once with correct applicability/inheritance and listing-type constraints, resolve documented cross-category boundary/duplicate-semantic cases, and pass automated structural validation plus a clean-MySQL migration/seed test. The current authoritative status is in §46.

## 31.5 Seed-Readiness Gate

A catalogue attribute is **SEED-READY** only when all are true:

- valid canonical data type;
- required/filterable/searchable/multi-value flags explicitly defined;
- applicable subcategories explicitly known;
- option-backed type has a non-empty explicit option set;
- option values are unique within the attribute definition;
- numeric units and canonical conversion policy are defined where applicable;
- listing-type applicability is explicit;
- no unresolved placeholder remains;
- no boundary/ownership conflict remains.

## 31.6 No-Invention Rule

During Phase 3, missing option values are **not** filled from model assumptions. If the detailed catalogue does not define the values, the attribute remains UNRESOLVED until an explicit catalogue decision is made. This protects the 25-category authority and prevents seed data from silently changing product taxonomy.

## 31.7 Next Execution Order

1. Resolve CAT-001 completely, including subcategory option sets and land-area unit/conversion rules.
2. Reconcile CAT-002 through CAT-005 option registry against their detailed pages.
3. Reconcile CAT-006 through CAT-015.
4. Reconcile CAT-016 through CAT-025.
5. Resolve cross-category boundaries and duplicate semantics.
6. Produce the final attribute applicability matrix.
7. Regenerate attribute/options seed data only after the gate passes.

**Phase 3 is superseded by Phase 3B for controlled-option and unit policy only. This does not certify every category's attribute flags, applicability, ordering, or validation metadata as complete. CAT-002's completeness gate remains open; production seed materialization must follow §43–§44 and pass structural validation before release.**

## 32. Phase 3 Audit Finding — Option Registry Coverage

This section records the **historical Phase 3 registry-coverage defect**; the 135-entry count and per-category counts below are not current outstanding-defect counts. Phase 3B §43–§44 supersedes the historical option-value resolution work by defining deterministic controlled-option families, semantic fallbacks, and unit rules.

The current implementation gate is not satisfied merely by having a vocabulary policy. Before production option seeding, the implementation must materialize the applicable §43 rules and verify 100% option-backed attribute coverage, zero literal UNRESOLVED values, no orphan option rows, and compatibility with the final CAT-page attribute definitions. The detailed CAT pages remain authoritative for attribute IDs, types, flags, and applicability; §43 is authoritative for shared option/unit semantics unless an exact CAT-page definition takes precedence.

**Current related blocker:** CAT-002 remains **NOT seed-ready** because its 96-attribute reconciliation still has unresolved required/filterable/searchable flags and other attribute-level metadata. This is a catalogue-completeness defect, distinct from the historical registry-coverage count. Do not treat the old 135-entry count as a current count of missing registry rows without rerunning a materialized registry cross-check.

# 33. Phase 3 — CAT-002 to CAT-005 Option Registry Reconciliation

**Status:** HISTORICAL RECONCILIATION — superseded by Phase 3B policy; implementation verification pending

The 77-entry count and the two malformed CAT-004 Vehicle Parts rows describe the 2026-09-30 reconciliation snapshot. They must not be presented as a verified current registry count. Phase 3B §43 supplies approved semantic option families and unit rules for previously unresolved values, subject to exact CAT-page options taking precedence. The remaining work is to materialize those rules against the current 25 CAT pages, resolve any conflicts, and run the structural validation gate. The malformed CAT-004 Vehicle Parts rows remain excluded until the authoritative CAT-004 definition is repaired and verified.

Do not invent values where neither an exact CAT-page definition nor an applicable approved §43 semantic family resolves the field.

> **Historical snapshot warning for Sections 33–37:** These tables preserve the 2026-09-30 registry-reconciliation snapshots. Their row counts and literal `UNRESOLVED` entries are not the current materialized registry state. Apply §43 semantic families where the mapping is explicitly valid, honor exact CAT-page option lists, and do not use the historical counts as current seed-coverage evidence. The current registry/materialization status remains unverified until the deterministic seed audit is run.
> 

## CAT-002

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| ELEC-ATTR-003 | Condition | select | New, Like New, Good, Fair, Needs Repair, Refurbished, Used |
| ELEC-ATTR-005 | Warranty Status | select | None, Active, Expired, Seller Warranty, Manufacturer Warranty |
| ELEC-ATTR-007 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| ELEC-ATTR-010 | Original Accessories | multi_select | Original Charger, Cable, Adapter, Earphones, Battery, Remote, Stand, Box, Manual, Other |
| AUD-002 | Connectivity | multi_select | Bluetooth, Wi-Fi, AUX, USB, HDMI, Optical, RCA, XLR, Other |
| GAME-002 | Platform | multi_select | PlayStation, Xbox, Nintendo, PC, Mobile, Other |

## CAT-003

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| FURN-ATTR-003 | Condition | select | New, Like New, Good, Fair, Needs Repair, Refurbished, Used |
| FURN-ATTR-004 | Material | select | Wood, Engineered Wood, Metal, Steel, Plastic, Glass, Fabric, Leather, Rattan, Bamboo, Mixed, Other |
| FURN-ATTR-005 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| FURN-ATTR-007 | Warranty Status | select | None, Active, Expired, Seller Warranty, Manufacturer Warranty |
| FURN-ATTR-012 | Accessories Included | multi_select | Cushion, Cover, Legs, Hardware, Key, Mirror, Shelf, Drawer, Remote, Manual, Other |

## CAT-004

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| VEH-ATTR-006 | Condition | select | New, Like New, Good, Fair, Needs Repair, Refurbished, Used |
| VEH-ATTR-008 | Mileage Unit | select | km, miles |
| VEH-ATTR-009 | Fuel Type | select | Petrol, Diesel, Electric, Hybrid, CNG, LPG, Hydrogen, Other |
| VEH-ATTR-010 | Transmission | select | Manual, Automatic, AMT, CVT, DCT, Other |
| VEH-ATTR-011 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| VEH-ATTR-013 | Engine Unit | select | cc, L |
| VEH-ATTR-015 | Insurance Status | select | Active, Expired, None, Unknown |
| VEH-ATTR-017 | Tax Status | select | Paid, Due, Overdue, Exempt, Unknown |
| VEH-ATTR-020 | Warranty Status | select | Active, Expired, None, Manufacturer Warranty, Seller Warranty |
| VEH-ATTR-022 | Documents Available | multi_select | Blue Book, Insurance, Tax Receipt, Purchase Invoice, Service Records, Pollution Certificate, Registration Certificate, Other |
| VEH-ATTR-023 | Features | multi_select | Air Conditioning, Power Steering, Power Windows, Central Locking, ABS, Airbags, Sunroof, Cruise Control, Reverse Camera, Parking Sensors, Alloy Wheels, LED Headlights, Fog Lights, GPS, Bluetooth, Touchscreen, Android Auto, Apple CarPlay, Keyless Entry, Push Start, Heated Seats, Leather Seats, Roof Rack, 4WD, AWD |
| SUV-004 | Drive Type | select | UNRESOLVED — explicit catalogue options required before seed |
| VAN-004 | Drive Type | select | UNRESOLVED — explicit catalogue options required before seed |
| PICK-004 | Payload Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| PICK-005 | Drive Type | select | UNRESOLVED — explicit catalogue options required before seed |
| TRK-003 | Payload Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| TRK-005 | Drive Type | select | UNRESOLVED — explicit catalogue options required before seed |
| TRK-006 | Body Type | select | UNRESOLVED — explicit catalogue options required before seed |
| EVC-001 | Body Type | select | UNRESOLVED — explicit catalogue options required before seed |
| EVC-003 | Battery Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| EVC-005 | Range Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| AGR-003 | Drive Type | select | UNRESOLVED — explicit catalogue options required before seed |
| BIKE-005 | Suspension | select | UNRESOLVED — explicit catalogue options required before seed |
| THREE-003 | Fuel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| VPA-001 | &lt;/td&gt; &lt;td&gt;Part Type&lt;/td&gt; &lt;td&gt;select&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;/tr&gt; &lt;tr&gt; &lt;td&gt; | select | UNRESOLVED — explicit catalogue options required before seed |
| VPA-006 | &lt;/td&gt; &lt;td&gt;Condition&lt;/td&gt; &lt;td&gt;select&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;/tr&gt; &lt;tr&gt; &lt;td&gt; | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-005

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| FASH-ATTR-003 | Condition | select | New, Like New, Good, Fair, Needs Repair, Refurbished, Used, Handmade |
| FASH-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| FASH-ATTR-005 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| FASH-ATTR-006 | Material / Fabric | select | Cotton, Polyester, Wool, Silk, Linen, Denim, Leather, Faux Leather, Nylon, Rayon, Velvet, Chiffon, Georgette, Synthetic, Mixed, Other |
| FASH-ATTR-007 | Pattern / Design | select | Plain, Printed, Striped, Checked, Floral, Embroidered, Traditional, Graphic, Patterned, Other |
| FASH-ATTR-008 | Gender / Target Group | select | Men, Women, Unisex, Boys, Girls, Other |
| FASH-ATTR-009 | Age Group | select | Newborn, Infant, Toddler, Kids, Teen, Adult, Senior, All Ages |
| FASH-ATTR-012 | Warranty Status | select | None, Active, Expired, Seller Warranty, Manufacturer Warranty |
| FASH-ATTR-016 | Accessories Included | multi_select | Original Packaging, Tags, Belt, Scarf, Tie, Socks, Shoe Box, Dust Bag, Warranty Card, Other |
| MEN-002 | Sleeve Type | select | UNRESOLVED — explicit catalogue options required before seed |
| MEN-004 | Collar Type | select | UNRESOLVED — explicit catalogue options required before seed |
| WOMEN-002 | Sleeve Type | select | UNRESOLVED — explicit catalogue options required before seed |
| WOMEN-005 | Occasion | select | UNRESOLVED — explicit catalogue options required before seed |
| KIDS-002 | Age Range | select | UNRESOLVED — explicit catalogue options required before seed |
| KIDS-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| KIDS-004 | Occasion | select | UNRESOLVED — explicit catalogue options required before seed |
| KIDS-005 | Gender | select | UNRESOLVED — explicit catalogue options required before seed |
| ETHNIC-002 | Cultural / Regional Style | select | UNRESOLVED — explicit catalogue options required before seed |
| ETHNIC-005 | Occasion | select | UNRESOLVED — explicit catalogue options required before seed |
| FOOT-002 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| FOOT-003 | Gender | select | UNRESOLVED — explicit catalogue options required before seed |
| FOOT-004 | Sole Material | select | UNRESOLVED — explicit catalogue options required before seed |
| BAG-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| BAG-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| WATCH-004 | Strap Material | select | UNRESOLVED — explicit catalogue options required before seed |
| JEW-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| JEW-003 | Gemstone | select | UNRESOLVED — explicit catalogue options required before seed |
| OCC-002 | Gender | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-002 | Sport | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-004 | Gender | select | UNRESOLVED — explicit catalogue options required before seed |
| BABY-002 | Age Range | select | UNRESOLVED — explicit catalogue options required before seed |
| BABY-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| BABY-004 | Gender | select | UNRESOLVED — explicit catalogue options required before seed |
| BABY-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| UNI-002 | Profession / Institution | select | UNRESOLVED — explicit catalogue options required before seed |
| UNI-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| UNI-004 | Gender | select | UNRESOLVED — explicit catalogue options required before seed |
| ACC-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| ACC-003 | Gender | select | UNRESOLVED — explicit catalogue options required before seed |

## Reconciliation Rules

- Existing registry entries are not duplicated.
- Explicit controlled values already defined in the detailed CAT pages are mirrored exactly.
- No option set is invented for an attribute whose catalogue definition is blank.
- The two malformed CAT-004 Vehicle Parts attribute rows are excluded from the seed contract until the source table is repaired.
- This reconciliation does not alter the 25-category / 372-subcategory taxonomy.

# 34. Phase 3 — CAT-006 to CAT-010 Option Registry Reconciliation

**Status:** RECONCILED FROM TABLE DEFINITIONS — 2026-09-30

The registry had no existing mirrored option IDs for these five detailed catalogues. **233 option-backed attribute IDs** are now represented below. Values are copied only when the detailed catalogue table explicitly provides them; otherwise the entry remains unresolved.

## CAT-006

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| HOME-ATTR-003 | Condition | select | No |
| HOME-ATTR-016 | Accessories Included | multi_select | Yes |
| CAT-006-01-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-01-ATTR-005 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-01-ATTR-006 | Cooling Technology | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-02-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-02-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-02-ATTR-008 | Loading Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-03-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-03-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-03-ATTR-005 | Energy Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-03-ATTR-006 | Room Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-04-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-04-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-04-ATTR-005 | Power Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-05-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-05-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-05-ATTR-005 | Power Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-05-ATTR-008 | Inner Pot Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-06-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-06-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-07-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-07-ATTR-002 | Filtration Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-07-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-08-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-08-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-08-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-09-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-09-ATTR-003 | Power Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-09-ATTR-005 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-10-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-10-ATTR-003 | Sweep Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-10-ATTR-004 | Sweep Size Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-11-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-12-ATTR-001 | Appliance Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-12-ATTR-002 | System Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-12-ATTR-004 | Power Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-006-13-ATTR-001 | Common attributes plus Product Type | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-007

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| SPORT-ATTR-003 | Condition | select | No |
| SPORT-ATTR-004 | Material | select | No |
| SPORT-ATTR-005 | Size | select | No |
| SPORT-ATTR-006 | Color | select | No |
| SPORT-ATTR-008 | Weight Unit | select | No |
| SPORT-ATTR-010 | Warranty Status | select | No |
| SPORT-ATTR-012 | Suitable Age Group | select | No |
| SPORT-ATTR-013 | Skill Level | select | No |
| SPORT-01-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-01-ATTR-002 | Resistance Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-02-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-02-ATTR-004 | Resistance Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-03-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-03-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-04-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-04-ATTR-002 | Playing Level | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-04-ATTR-004 | Bat Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-04-ATTR-005 | Ball Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-04-ATTR-006 | Protective Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-05-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-05-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-05-ATTR-004 | Surface Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-05-ATTR-005 | Goal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-06-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-06-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-06-ATTR-004 | Hoop Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-07-ATTR-001 | Sport | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-07-ATTR-002 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-07-ATTR-003 | Racket Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-08-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-08-ATTR-002 | Table Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-08-ATTR-004 | Paddle Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-09-ATTR-002 | Compatibility/Bicycle Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-09-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-09-ATTR-008 | Electric Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-10-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-10-ATTR-006 | Season Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-11-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-11-ATTR-004 | Reel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-12-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-12-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-12-ATTR-005 | Suitable Water Type (multi) | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-13-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-13-ATTR-002 | Sport/Discipline (multi) | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-13-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-14-ATTR-001 | Accessory Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-14-ATTR-002 | Sport (multi) | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-14-ATTR-003 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-14-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-15-ATTR-001 | Recreation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-15-ATTR-002 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-16-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-16-ATTR-002 | Sport/Activity | select | UNRESOLVED — explicit catalogue options required before seed |
| SPORT-16-ATTR-003 | Intended Use | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-008

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| JOB-ATTR-003 | Employment Type | select | No |
| JOB-ATTR-004 | Work Mode | select | No |
| JOB-ATTR-005 | Experience Level | select | No |
| JOB-ATTR-007 | Experience Unit | select | No |
| JOB-ATTR-008 | Education Level | select | No |
| JOB-ATTR-012 | Salary Period | select | No |
| JOB-ATTR-013 | Salary Currency | select | No |
| JOB-ATTR-016 | Gender Preference | select | No |
| CAT-008-01-ATTR-001 | Job Category | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-02-ATTR-005 | Duration Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-03-ATTR-002 | Duration Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-03-ATTR-003 | Contract Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-04-ATTR-001 | Project Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-04-ATTR-003 | Duration Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-04-ATTR-004 | Payment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-05-ATTR-001 | Internship Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-05-ATTR-003 | Duration Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-06-ATTR-005 | Communication Platform | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-07-ATTR-001 | Government Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-07-ATTR-003 | Position Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-07-ATTR-005 | Application Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-08-ATTR-001 | Teaching Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-08-ATTR-002 | Subject | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-08-ATTR-006 | Institution Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-09-ATTR-006 | Shift Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-09-ATTR-007 | Institution Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-10-ATTR-001 | Technology Role | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-11-ATTR-001 | Sales / Marketing Role | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-11-ATTR-002 | Industry | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-12-ATTR-001 | Job Role | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-12-ATTR-002 | Establishment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-12-ATTR-003 | Shift Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-13-ATTR-001 | Trade Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-13-ATTR-002 | Skill Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-14-ATTR-001 | Driver Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-14-ATTR-002 | License Category | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-14-ATTR-003 | Vehicle Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-15-ATTR-001 | Job Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-16-ATTR-001 | Job Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-16-ATTR-002 | Industry | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-008-16-ATTR-004 | Intended Role | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-009

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| SERV-ATTR-003 | Service Type | select | No |
| SERV-ATTR-006 | Availability | select | No |
| SERV-ATTR-007 | Pricing Type | select | No |
| SERV-ATTR-009 | Price Unit | select | No |
| SERV-ATTR-011 | Experience Unit | select | No |
| SERV-ATTR-014 | Service Delivery Mode | select | No |
| CAT-009-01-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-02-ATTR-001 | Repair Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-02-ATTR-002 | Equipment / Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-02-ATTR-003 | Brand Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-03-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-03-ATTR-002 | Construction Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-03-ATTR-003 | Property Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-04-ATTR-001 | Vehicle Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-04-ATTR-002 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-05-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-05-ATTR-002 | Technology / Platform | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-05-ATTR-003 | Programming Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-05-ATTR-005 | Project Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-06-ATTR-001 | Professional Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-06-ATTR-002 | Industry | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-06-ATTR-003 | Business Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-06-ATTR-007 | Deliverable Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-07-ATTR-001 | Subject / Skill | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-07-ATTR-002 | Education Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-07-ATTR-003 | Training Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-07-ATTR-004 | Class Mode | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-07-ATTR-005 | Class Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-08-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-08-ATTR-003 | Consultation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-08-ATTR-004 | Location Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-09-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-09-ATTR-006 | Package Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-10-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-10-ATTR-002 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-10-ATTR-004 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-11-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-11-ATTR-002 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-12-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-12-ATTR-003 | Tour Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-12-ATTR-009 | Package Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-13-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-13-ATTR-002 | Vehicle Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-14-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-14-ATTR-003 | Consultation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-14-ATTR-007 | Document Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-15-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-15-ATTR-002 | Crop Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-15-ATTR-003 | Farm Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-15-ATTR-004 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-15-ATTR-005 | Labor / Equipment | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-009-16-ATTR-001 | Service Type | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-010

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| COMM-ATTR-003 | Equipment Type | select | No |
| COMM-ATTR-004 | Condition | select | No |
| COMM-ATTR-017 | Accessories Included | multi_select | Yes |
| CAT-010-01-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-01-ATTR-004 | Storage Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-01-ATTR-007 | Screen Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-01-ATTR-009 | Business Use Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-02-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-02-ATTR-002 | Print Technology | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-02-ATTR-005 | Paper Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-03-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-03-ATTR-004 | Port Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-04-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-04-ATTR-002 | POS Software Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-04-ATTR-006 | Display Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-05-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-05-ATTR-002 | Camera Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-05-ATTR-005 | Storage Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-06-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-06-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-06-ATTR-004 | Fuel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-06-ATTR-005 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-06-ATTR-007 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-07-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-07-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-07-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-08-ATTR-001 | Tool Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-08-ATTR-002 | Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-08-ATTR-003 | Power Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-08-ATTR-004 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-08-ATTR-006 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-09-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-10-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-10-ATTR-002 | Display Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-10-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-11-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-11-ATTR-002 | Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-11-ATTR-005 | Material Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-11-ATTR-006 | Automation Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-11-ATTR-007 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-12-ATTR-001 | Furniture Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-12-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-12-ATTR-006 | Storage Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-13-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-13-ATTR-003 | Power Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-14-ATTR-001 | Common attributes plus Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-010-14-ATTR-002 | Commercial Application | select | UNRESOLVED — explicit catalogue options required before seed |

## Gate Note

- This section does not infer option values from attribute names.
- Separate prose-defined controlled-value statements must still be promoted into the registry before the final seed gate.
- Blank option cells remain blockers.

# 35. Phase 3 — CAT-011 to CAT-015 Option Registry Reconciliation

**Status:** RECONCILED FROM TABLE DEFINITIONS — 2026-09-30

The registry had no existing mirrored option IDs for these five detailed catalogues. **246 option-backed attribute IDs** are now represented below. Values are copied only when the detailed catalogue table explicitly provides them; otherwise the entry remains unresolved.

## CAT-011

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| KIDS-ATTR-013 | Accessories Included | multi_select | Yes |
| CAT-011-01-ATTR-001 | Clothing Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-01-ATTR-002 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-01-ATTR-004 | Season | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-02-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-02-ATTR-003 | Weight Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-02-ATTR-007 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-03-ATTR-001 | Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-03-ATTR-006 | Wheel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-04-ATTR-001 | Furniture Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-04-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-05-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-05-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-05-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-06-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-06-ATTR-002 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-06-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-07-ATTR-001 | Toy Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-07-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-08-ATTR-001 | Learning Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-08-ATTR-002 | Subject | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-08-ATTR-003 | Skill Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-08-ATTR-005 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-09-ATTR-007 | Safety Equipment | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-10-ATTR-001 | Device Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-10-ATTR-002 | Platform | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-10-ATTR-003 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-10-ATTR-004 | Storage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-10-ATTR-005 | Screen Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-10-ATTR-008 | Age Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-11-ATTR-001 | Material Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-11-ATTR-002 | Subject | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-11-ATTR-003 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-11-ATTR-005 | Grade Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-12-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-12-ATTR-002 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-12-ATTR-007 | Decoration Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-13-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-13-ATTR-002 | Installation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-13-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-13-ATTR-005 | Safety Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-14-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-14-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-14-ATTR-005 | Measurement Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-15-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-15-ATTR-002 | Sport / Activity | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-15-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-15-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-15-ATTR-007 | Skill Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-011-16-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-012

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| MEDIA-ATTR-001 | Item Type | select | No |
| MEDIA-ATTR-005 | Condition | select | No |
| MEDIA-ATTR-008 | Language | select | Yes |
| MEDIA-ATTR-010 | Material / Format | select | No |
| MEDIA-ATTR-013 | Original / Authenticity Status | select | No |
| CAT-012-01-ATTR-008 | Binding Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-01-ATTR-009 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-02-ATTR-001 | Subject | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-02-ATTR-002 | Grade / Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-02-ATTR-008 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-03-ATTR-002 | Text Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-03-ATTR-003 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-04-ATTR-005 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-04-ATTR-007 | Topic | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-05-ATTR-006 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-06-ATTR-001 | Media Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-06-ATTR-005 | Format | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-07-ATTR-001 | Media Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-07-ATTR-005 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-07-ATTR-007 | Format | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-08-ATTR-001 | Collectible Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-09-ATTR-001 | Item Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-09-ATTR-003 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-09-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-09-ATTR-006 | Restoration Status | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-10-ATTR-006 | Metal / Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-11-ATTR-003 | Stamp Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-12-ATTR-001 | Artwork Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-12-ATTR-004 | Subject | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-13-ATTR-001 | Category | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-14-ATTR-001 | Instrument Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-14-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-14-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-14-ATTR-006 | Skill Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-15-ATTR-001 | Hobby Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-15-ATTR-002 | Collection Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-15-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-15-ATTR-004 | Skill Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-16-ATTR-001 | Item Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-012-16-ATTR-004 | Material / Format | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-013

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| FOOD-ATTR-002 | Product Type | select | No |
| FOOD-ATTR-005 | Condition / Freshness | select | No |
| FOOD-ATTR-007 | Quantity Unit | select | No |
| FOOD-ATTR-009 | Price Unit | select | No |
| FOOD-ATTR-012 | Packaging Type | select | No |
| FOOD-ATTR-013 | Storage Requirement | select | No |
| FOOD-ATTR-014 | Organic / Specialty Claim | select | No |
| CAT-013-01-ATTR-001 | Grain Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-01-ATTR-004 | Moisture Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-01-ATTR-005 | Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-01-ATTR-006 | Processing Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-01-ATTR-007 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-02-ATTR-001 | Pulse Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-02-ATTR-004 | Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-02-ATTR-005 | Processing Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-02-ATTR-006 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-03-ATTR-001 | Fruit Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-03-ATTR-003 | Harvest Season | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-03-ATTR-004 | Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-03-ATTR-007 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-04-ATTR-001 | Vegetable Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-04-ATTR-004 | Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-04-ATTR-006 | Growing Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-04-ATTR-007 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-05-ATTR-001 | Spice / Herb Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-05-ATTR-005 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-05-ATTR-007 | Purity / Blend Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-06-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-06-ATTR-002 | Source Animal | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-06-ATTR-004 | Processing Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-07-ATTR-001 | Meat Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-07-ATTR-002 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-07-ATTR-004 | Cut Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-07-ATTR-005 | Processing Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-08-ATTR-005 | Processing Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-08-ATTR-006 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-09-ATTR-002 | Bird Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-09-ATTR-003 | Egg Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-09-ATTR-005 | Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-09-ATTR-007 | Hatchery Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-10-ATTR-001 | Crop Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-10-ATTR-003 | Seed Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-10-ATTR-004 | Season | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-11-ATTR-001 | Feed Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-11-ATTR-002 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-12-ATTR-001 | Plant Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-13-ATTR-001 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-13-ATTR-006 | Purpose | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-13-ATTR-007 | Vaccination Status | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-14-ATTR-001 | Food Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-15-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-15-ATTR-004 | Production Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-15-ATTR-005 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-16-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-013-16-ATTR-003 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-014

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| CARE-ATTR-003 | Product Type | select | No |
| CARE-ATTR-004 | Condition | select | No |
| CARE-ATTR-005 | Intended User Group | select | Yes |
| CARE-ATTR-015 | Accessories Included | multi_select | Yes |
| CAT-014-01-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-01-ATTR-004 | Pack Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-02-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-02-ATTR-002 | Skin Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-03-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-03-ATTR-002 | Hair Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-04-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-04-ATTR-002 | Shade / Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-04-ATTR-003 | Skin Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-04-ATTR-004 | Finish | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-05-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-06-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-06-ATTR-003 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-06-ATTR-005 | Blade Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-07-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-07-ATTR-004 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-07-ATTR-005 | Brush Head Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-08-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-08-ATTR-007 | Pack Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-09-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-09-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-10-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-10-ATTR-002 | Massage Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-10-ATTR-004 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-10-ATTR-005 | Heat Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-11-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-11-ATTR-002 | Lens Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-11-ATTR-004 | Lens Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-11-ATTR-005 | Frame Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-11-ATTR-006 | Frame Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-12-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-12-ATTR-002 | Assistive Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-12-ATTR-003 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-12-ATTR-005 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-13-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-13-ATTR-003 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-13-ATTR-004 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-13-ATTR-007 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-014-14-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-015

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| HOMEG-ATTR-003 | Product Type | select | No |
| HOMEG-ATTR-004 | Condition | select | No |
| HOMEG-ATTR-005 | Material | select | Yes |
| HOMEG-ATTR-015 | Accessories Included | multi_select | Yes |
| CAT-015-01-ATTR-001 | Décor Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-01-ATTR-002 | Style | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-01-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-02-ATTR-001 | Lighting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-02-ATTR-002 | Bulb Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-02-ATTR-005 | Light Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-02-ATTR-006 | Fixture Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-03-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-03-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-03-ATTR-005 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-04-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-04-ATTR-002 | Bed Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-04-ATTR-005 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-05-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-05-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-05-ATTR-003 | Installation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-06-ATTR-001 | Storage Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-06-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-06-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-07-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-07-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-08-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-08-ATTR-003 | Window Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-08-ATTR-006 | Mounting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-09-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-10-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-10-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-10-ATTR-004 | Tool Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-10-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-10-ATTR-007 | Handle Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-10-ATTR-008 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-11-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-11-ATTR-002 | Plant Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-11-ATTR-005 | Plant Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-11-ATTR-006 | Pot Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-11-ATTR-007 | Pot Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-12-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-12-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-13-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-13-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-13-ATTR-003 | Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-13-ATTR-004 | Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-13-ATTR-009 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-14-ATTR-001 | Tool Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-14-ATTR-002 | Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-14-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-14-ATTR-005 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-14-ATTR-006 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-15-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-015-15-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |

## Gate Note

- No option values were inferred from attribute names.
- Prose-defined controlled-value statements still require promotion into the registry.
- Blank option cells remain blockers.

# 36. Phase 3 — CAT-016 to CAT-020 Option Registry Reconciliation

**Status:** RECONCILED FROM TABLE DEFINITIONS — 2026-09-30

**378 option-backed attribute IDs** are represented below. Explicit table values are mirrored; blank definitions remain unresolved.

## CAT-016

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| PET-ATTR-002 | Item / Animal Type | select | No |
| PET-ATTR-004 | Condition | select | No |
| PET-ATTR-005 | Species | select | No |
| PET-ATTR-006 | Breed / Variety | select | No |
| PET-ATTR-008 | Age Unit | select | No |
| PET-ATTR-009 | Gender / Sex | select | No |
| PET-ATTR-010 | Material | select | Yes |
| PET-ATTR-011 | Size | select | No |
| PET-ATTR-014 | Weight Unit | select | No |
| CAT-016-01-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-01-ATTR-002 | Dog Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-01-ATTR-003 | Breed Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-01-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-01-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-02-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-02-ATTR-002 | Cat Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-02-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-02-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-02-ATTR-008 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-03-ATTR-001 | Bird Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-03-ATTR-002 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-03-ATTR-003 | Cage Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-03-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-04-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-04-ATTR-002 | Aquarium Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-04-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-04-ATTR-007 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-05-ATTR-001 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-05-ATTR-002 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-05-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-05-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-06-ATTR-001 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-06-ATTR-002 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-06-ATTR-003 | Habitat Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-06-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-07-ATTR-001 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-07-ATTR-002 | Food Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-07-ATTR-006 | Weight / Pack Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-08-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-08-ATTR-002 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-08-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-09-ATTR-002 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-09-ATTR-004 | Ingredients / Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-10-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-10-ATTR-002 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-10-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-11-ATTR-001 | Toy Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-11-ATTR-002 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-11-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-11-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-11-ATTR-008 | Recommended Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-12-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-12-ATTR-002 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-12-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-12-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-12-ATTR-006 | Vehicle Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-13-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-13-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-13-ATTR-004 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-13-ATTR-005 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-13-ATTR-009 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-14-ATTR-001 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-14-ATTR-006 | Vaccination Status | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-14-ATTR-011 | Adoption / Sale Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-15-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-15-ATTR-002 | Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-15-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-15-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-15-ATTR-005 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-016-16-ATTR-001 | Item / Animal Type | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-017

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| TRAVEL-ATTR-003 | Product Type | select | No |
| TRAVEL-ATTR-004 | Condition | select | No |
| TRAVEL-ATTR-005 | Material | select | Yes |
| TRAVEL-ATTR-015 | Accessories Included | multi_select | Yes |
| CAT-017-01-ATTR-001 | Luggage Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-01-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-01-ATTR-004 | Size / Cabin Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-01-ATTR-006 | Wheel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-01-ATTR-007 | Lock Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-01-ATTR-009 | Handle Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-01-ATTR-010 | TSA Lock | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-02-ATTR-001 | Bag Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-02-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-02-ATTR-005 | Laptop Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-02-ATTR-008 | Carrying Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-03-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-03-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-03-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-03-ATTR-007 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-04-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-04-ATTR-002 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-04-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-04-ATTR-005 | Season | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-05-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-05-ATTR-005 | Packed Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-05-ATTR-007 | Season Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-06-ATTR-001 | Device Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-06-ATTR-004 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-06-ATTR-008 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-07-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-07-ATTR-002 | Security Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-07-ATTR-003 | Lock Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-07-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-08-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-08-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-08-ATTR-006 | Passport Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-09-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-09-ATTR-007 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-10-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-10-ATTR-002 | Container Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-10-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-10-ATTR-007 | TSA / Travel Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-11-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-11-ATTR-002 | Vehicle Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-11-ATTR-003 | Installation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-11-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-11-ATTR-005 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-12-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-12-ATTR-002 | Motorcycle Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-12-ATTR-003 | Mounting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-12-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-13-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-13-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-13-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-13-ATTR-008 | Safety Equipment | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-13-ATTR-009 | Skill Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-14-ATTR-001 | Item Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-14-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-15-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-15-ATTR-002 | Laptop Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-15-ATTR-003 | Device Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-15-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-15-ATTR-007 | Carrying Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-16-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-16-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-017-16-ATTR-004 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-018

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| BUILD-ATTR-003 | Product Type | select | No |
| BUILD-ATTR-004 | Condition | select | No |
| BUILD-ATTR-005 | Material | select | Yes |
| BUILD-ATTR-015 | Accessories Included | multi_select | Yes |
| CAT-018-01-ATTR-001 | Material Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-01-ATTR-002 | Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-01-ATTR-003 | Cement Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-01-ATTR-004 | Aggregate Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-01-ATTR-005 | Particle Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-01-ATTR-006 | Bag Weight | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-01-ATTR-009 | Production Date | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-02-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-02-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-02-ATTR-004 | Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-02-ATTR-006 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-02-ATTR-007 | Finish | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-03-ATTR-001 | Material Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-03-ATTR-002 | Steel / Metal Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-03-ATTR-008 | Weight per Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-03-ATTR-009 | Surface Finish | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-04-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-04-ATTR-003 | Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-04-ATTR-008 | Finish | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-04-ATTR-009 | Intended Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-05-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-05-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-05-ATTR-009 | Installation Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-06-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-06-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-06-ATTR-005 | Frame Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-06-ATTR-006 | Glass Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-06-ATTR-007 | Opening Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-06-ATTR-008 | Lock Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-07-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-07-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-07-ATTR-003 | Tile / Board Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-07-ATTR-005 | Surface Finish | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-08-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-08-ATTR-002 | Surface Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-08-ATTR-003 | Finish | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-08-ATTR-004 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-08-ATTR-007 | Application Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-09-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-09-ATTR-005 | Pressure Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-09-ATTR-006 | Connection Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-09-ATTR-007 | Thread Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-10-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-10-ATTR-002 | Cable / Wire Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-10-ATTR-003 | Conductor Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-10-ATTR-006 | Voltage Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-10-ATTR-007 | Current Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-10-ATTR-009 | Insulation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-11-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-11-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-11-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-11-ATTR-004 | Thread Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-11-ATTR-005 | Finish | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-11-ATTR-006 | Strength / Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-11-ATTR-009 | Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-12-ATTR-001 | Tool Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-12-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-12-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-12-ATTR-004 | Handle Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-12-ATTR-006 | Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-13-ATTR-001 | Tool Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-13-ATTR-002 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-13-ATTR-003 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-13-ATTR-008 | Chuck / Bit Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-14-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-14-ATTR-002 | Safety Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-14-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-14-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-14-ATTR-007 | PPE Category | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-14-ATTR-009 | Intended Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-15-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-15-ATTR-002 | Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-15-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-15-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-15-ATTR-006 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-16-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-16-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-16-ATTR-004 | Intended Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-018-16-ATTR-005 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-019

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| IND-ATTR-003 | Equipment Type | select | No |
| IND-ATTR-004 | Condition | select | No |
| IND-ATTR-014 | Application | select | Yes |
| IND-ATTR-016 | Accessories / Attachments Included | multi_select | Yes |
| CAT-019-01-ATTR-001 | Machine Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-01-ATTR-008 | Track / Wheel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-02-ATTR-001 | Machine Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-02-ATTR-007 | Drive Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-02-ATTR-008 | Attachment Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-03-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-03-ATTR-006 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-03-ATTR-007 | Mobility Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-03-ATTR-009 | Certification / Inspection Status | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-04-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-04-ATTR-004 | Mast Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-04-ATTR-006 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-04-ATTR-007 | Tire Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-05-ATTR-001 | Generator Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-05-ATTR-007 | Fuel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-05-ATTR-008 | Fuel Capacity | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-05-ATTR-011 | Noise Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-06-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-06-ATTR-002 | Compressor Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-06-ATTR-006 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-06-ATTR-007 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-06-ATTR-008 | Motor Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-06-ATTR-010 | Noise Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-07-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-07-ATTR-006 | Material Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-07-ATTR-007 | Wire / Electrode Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-07-ATTR-008 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-08-ATTR-001 | Machine Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-08-ATTR-003 | Production Capacity | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-08-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-08-ATTR-005 | Automation Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-08-ATTR-006 | Material Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-08-ATTR-008 | Operating Mode | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-09-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-09-ATTR-002 | Food Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-09-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-09-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-09-ATTR-006 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-09-ATTR-008 | Automation Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-09-ATTR-009 | Food Contact Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-09-ATTR-010 | Cleaning Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-10-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-10-ATTR-002 | Packaging Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-10-ATTR-003 | Production Speed | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-10-ATTR-005 | Material Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-10-ATTR-006 | Automation Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-10-ATTR-007 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-10-ATTR-008 | Packaging Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-11-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-11-ATTR-002 | Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-12-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-12-ATTR-002 | Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-12-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-12-ATTR-005 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-12-ATTR-006 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-12-ATTR-009 | Batch Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-13-ATTR-001 | Machine Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-13-ATTR-002 | Agricultural / Forestry Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-13-ATTR-003 | Engine Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-13-ATTR-007 | Fuel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-13-ATTR-008 | Attachment Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-14-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-14-ATTR-002 | Pump Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-14-ATTR-005 | Inlet / Outlet Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-14-ATTR-006 | Fluid Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-14-ATTR-007 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-14-ATTR-008 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-14-ATTR-009 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-15-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-15-ATTR-008 | Protection Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-15-ATTR-009 | Installation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-16-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-16-ATTR-002 | Industrial Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-16-ATTR-004 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-16-ATTR-005 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-16-ATTR-006 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-019-16-ATTR-007 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-020

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| EVENT-ATTR-003 | Product Type | select | No |
| EVENT-ATTR-004 | Condition | select | No |
| EVENT-ATTR-005 | Material | select | Yes |
| EVENT-ATTR-006 | Color / Theme | select | Yes |
| EVENT-ATTR-015 | Accessories Included | multi_select | Yes |
| CAT-020-01-ATTR-001 | Decoration Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-01-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-01-ATTR-004 | Backdrop Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-01-ATTR-005 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-01-ATTR-007 | Mounting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-02-ATTR-001 | Decoration Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-02-ATTR-002 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-02-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-02-ATTR-005 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-02-ATTR-006 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-03-ATTR-001 | Flower Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-03-ATTR-004 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-03-ATTR-005 | Arrangement Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-03-ATTR-006 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-04-ATTR-001 | Lighting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-04-ATTR-002 | Light Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-04-ATTR-004 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-04-ATTR-005 | Light Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-04-ATTR-009 | Control Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-04-ATTR-010 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-05-ATTR-001 | Furniture Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-05-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-06-ATTR-001 | Structure Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-06-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-06-ATTR-008 | Setup Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-06-ATTR-009 | Frame Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-07-ATTR-001 | Item Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-07-ATTR-002 | Ceremony Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-07-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-07-ATTR-004 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-07-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-08-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-08-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-08-ATTR-005 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-08-ATTR-009 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-09-ATTR-002 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-09-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-09-ATTR-004 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-10-ATTR-001 | Balloon Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-10-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-10-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-10-ATTR-004 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-10-ATTR-007 | Inflatable Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-11-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-11-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-11-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-11-ATTR-008 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-11-ATTR-009 | Decoration Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-12-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-12-ATTR-002 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-12-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-12-ATTR-004 | Paper Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-12-ATTR-006 | Printing Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-12-ATTR-008 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-13-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-13-ATTR-002 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-13-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-14-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-14-ATTR-004 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-14-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-15-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-15-ATTR-002 | Audio / Production Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-15-ATTR-003 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-15-ATTR-004 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-15-ATTR-008 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-15-ATTR-009 | Mounting / Setup Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-16-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-16-ATTR-002 | Event Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-020-16-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |

# 37. Phase 3 — CAT-021 to CAT-025 Option Registry Reconciliation

**Status:** RECONCILED FROM TABLE DEFINITIONS — 2026-09-30

**345 option-backed attribute IDs** are represented below. Explicit table values are mirrored; blank definitions remain unresolved.

## CAT-021

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| STAT-ATTR-003 | Product Type | select | No |
| STAT-ATTR-004 | Condition | select | No |
| STAT-ATTR-005 | Material | select | Yes |
| STAT-ATTR-006 | Color | select | Yes |
| STAT-ATTR-015 | Accessories Included | multi_select | Yes |
| CAT-021-01-ATTR-001 | Instrument Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-01-ATTR-002 | Ink Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-01-ATTR-003 | Tip Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-01-ATTR-004 | Ink Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-01-ATTR-007 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-02-ATTR-001 | Paper Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-02-ATTR-002 | Format | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-02-ATTR-007 | Binding Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-02-ATTR-008 | Cover Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-02-ATTR-009 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-03-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-03-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-03-ATTR-003 | Size / Format | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-03-ATTR-005 | Closure Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-03-ATTR-008 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-04-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-04-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-04-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-04-ATTR-005 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-04-ATTR-008 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-05-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-05-ATTR-003 | Subject | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-05-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-05-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-05-ATTR-007 | School Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-05-ATTR-008 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-06-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-06-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-06-ATTR-007 | Student / Artist Grade | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-06-ATTR-008 | Surface Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-07-ATTR-001 | Device Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-07-ATTR-002 | Display Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-07-ATTR-005 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-08-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-08-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-08-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-08-ATTR-004 | Shape | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-08-ATTR-005 | Adhesive Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-08-ATTR-009 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-09-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-09-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-09-ATTR-004 | Closure Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-10-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-10-ATTR-003 | Paper / Material Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-10-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-10-ATTR-007 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-10-ATTR-008 | Binding Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-11-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-11-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-11-ATTR-003 | Storage Capacity | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-11-ATTR-008 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-12-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-12-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-12-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-12-ATTR-004 | Surface Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-12-ATTR-008 | Mounting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-13-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-13-ATTR-003 | Format | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-13-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-13-ATTR-007 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-14-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-14-ATTR-002 | Form Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-14-ATTR-003 | Format | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-14-ATTR-004 | Paper Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-14-ATTR-008 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-15-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-15-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-15-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-16-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-16-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-16-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-021-16-ATTR-005 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-022

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| CULT-ATTR-003 | Product Type | select | No |
| CULT-ATTR-005 | Religion / Spiritual Tradition | select | Yes |
| CULT-ATTR-006 | Material | select | Yes |
| CULT-ATTR-008 | Color | select | Yes |
| CULT-ATTR-015 | Accessories Included | multi_select | Yes |
| CAT-022-01-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-01-ATTR-006 | Finish | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-02-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-02-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-02-ATTR-008 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-03-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-03-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-03-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-04-ATTR-001 | Clothing / Accessory Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-04-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-04-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-04-ATTR-006 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-05-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-05-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-06-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-06-ATTR-003 | Bead Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-06-ATTR-005 | Bead Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-06-ATTR-006 | String Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-07-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-07-ATTR-002 | Fuel / Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-07-ATTR-004 | Burn Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-08-ATTR-001 | Vessel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-08-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-08-ATTR-004 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-08-ATTR-006 | Finish | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-09-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-09-ATTR-005 | Mounting / Placement Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-10-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-10-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-10-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-10-ATTR-007 | Mounting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-11-ATTR-002 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-11-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-12-ATTR-001 | Craft Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-12-ATTR-002 | Cultural / Regional Origin | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-12-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-13-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-13-ATTR-002 | Meditation / Practice Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-13-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-13-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-13-ATTR-005 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-14-ATTR-001 | Instrument Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-14-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-14-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-14-ATTR-006 | Skill Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-15-ATTR-001 | Gift Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-15-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-16-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-16-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-022-16-ATTR-005 | Origin | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-023

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| MED-ATTR-003 | Equipment Type | select | No |
| MED-ATTR-006 | Intended User Group | select | Yes |
| MED-ATTR-007 | Material | select | Yes |
| MED-ATTR-016 | Accessories Included | multi_select | Yes |
| CAT-023-01-ATTR-001 | Device Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-01-ATTR-002 | Measurement Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-01-ATTR-005 | Cuff Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-01-ATTR-006 | Cuff Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-01-ATTR-007 | Display Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-01-ATTR-008 | Memory / Data Storage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-01-ATTR-010 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-02-ATTR-001 | Device Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-02-ATTR-002 | Measurement Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-02-ATTR-009 | Measurement Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-03-ATTR-001 | Device Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-03-ATTR-002 | Measurement Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-03-ATTR-004 | Test Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-03-ATTR-005 | Sample Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-04-ATTR-001 | Device Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-04-ATTR-002 | Measurement Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-04-ATTR-006 | Sensor Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-05-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-05-ATTR-002 | Measurement Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-05-ATTR-006 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-05-ATTR-010 | Calibration Status | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-06-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-06-ATTR-002 | Support Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-06-ATTR-005 | Weight Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-06-ATTR-008 | Wheel Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-06-ATTR-009 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-07-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-07-ATTR-007 | Wheel Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-08-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-08-ATTR-002 | Bed / Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-08-ATTR-009 | Wheels / Locking | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-09-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-09-ATTR-002 | Therapy Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-09-ATTR-006 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-09-ATTR-008 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-10-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-10-ATTR-002 | Oxygen / Respiratory Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-10-ATTR-004 | Flow Rate Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-10-ATTR-006 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-10-ATTR-009 | Noise Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-11-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-11-ATTR-003 | Support Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-11-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-11-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-11-ATTR-007 | Compression Level | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-12-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-12-ATTR-005 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-12-ATTR-008 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-12-ATTR-009 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-13-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-14-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-14-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-14-ATTR-005 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-14-ATTR-009 | Cleaning Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-15-ATTR-001 | Device Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-15-ATTR-004 | Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-15-ATTR-006 | Heat / Cold Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-15-ATTR-007 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-16-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-16-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-16-ATTR-005 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-023-16-ATTR-006 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-024

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| SAFE-ATTR-003 | Product Type | select | No |
| SAFE-ATTR-005 | Safety / Security Function | select | Yes |
| SAFE-ATTR-007 | Material | select | Yes |
| SAFE-ATTR-016 | Accessories Included | multi_select | Yes |
| CAT-024-01-ATTR-001 | Lock Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-01-ATTR-002 | Lock Mechanism | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-01-ATTR-003 | Key Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-01-ATTR-007 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-01-ATTR-009 | Installation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-01-ATTR-010 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-02-ATTR-001 | Safe Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-02-ATTR-002 | Lock Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-02-ATTR-006 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-02-ATTR-007 | Wall / Floor Mount | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-02-ATTR-009 | Security Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-03-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-03-ATTR-002 | Security Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-03-ATTR-003 | Installation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-03-ATTR-005 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-03-ATTR-010 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-04-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-04-ATTR-002 | Protection Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-04-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-04-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-05-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-05-ATTR-005 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-06-ATTR-001 | Alarm Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-06-ATTR-002 | Detection Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-06-ATTR-003 | Sensor Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-06-ATTR-005 | Alarm Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-06-ATTR-006 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-06-ATTR-010 | Test Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-07-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-07-ATTR-002 | Emergency Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-07-ATTR-008 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-07-ATTR-009 | Storage Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-08-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-08-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-09-ATTR-002 | Visibility Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-09-ATTR-003 | Reflective Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-09-ATTR-004 | Color | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-09-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-09-ATTR-009 | Mounting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-10-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-10-ATTR-002 | Safety Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-10-ATTR-003 | Workplace Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-10-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-10-ATTR-006 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-10-ATTR-010 | Intended Application | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-11-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-11-ATTR-003 | Voltage Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-11-ATTR-004 | Current Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-11-ATTR-005 | Power Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-11-ATTR-006 | Protection Rating | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-11-ATTR-007 | Plug / Connector Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-12-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-12-ATTR-002 | Safety Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-12-ATTR-005 | Installation Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-12-ATTR-006 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-12-ATTR-010 | Compatibility | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-13-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-13-ATTR-002 | Security Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-13-ATTR-003 | Lock Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-13-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-14-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-14-ATTR-002 | Security Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-14-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-14-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-14-ATTR-005 | Mounting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-15-ATTR-001 | Lighting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-15-ATTR-002 | Light Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-15-ATTR-006 | Charging Method | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-15-ATTR-007 | Emergency Mode | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-15-ATTR-009 | Mounting Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-16-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-16-ATTR-002 | Safety / Security Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-16-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-024-16-ATTR-005 | Installation Type | select | UNRESOLVED — explicit catalogue options required before seed |

## CAT-025

| Attribute ID | Attribute | Type | Registry Values |
| --- | --- | --- | --- |
| PARENT-ATTR-003 | Product Type | select | No |
| PARENT-ATTR-005 | Intended User Group | select | Yes |
| PARENT-ATTR-006 | Material | select | Yes |
| PARENT-ATTR-008 | Color | select | Yes |
| PARENT-ATTR-014 | Accessories Included | multi_select | Yes |
| CAT-025-01-ATTR-001 | Clothing Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-01-ATTR-002 | Pregnancy / Postpartum Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-01-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-01-ATTR-006 | Season | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-02-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-02-ATTR-003 | Support Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-02-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-02-ATTR-005 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-02-ATTR-009 | Intended Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-03-ATTR-001 | Bag Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-03-ATTR-003 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-03-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-03-ATTR-007 | Shoulder / Carry Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-03-ATTR-009 | Suitable Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-04-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-04-ATTR-003 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-04-ATTR-010 | Suitable Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-05-ATTR-001 | Pump Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-05-ATTR-003 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-05-ATTR-007 | Capacity Unit | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-06-ATTR-001 | Furniture Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-06-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-06-ATTR-007 | Nursing Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-06-ATTR-008 | Storage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-07-ATTR-001 | Material Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-07-ATTR-002 | Topic | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-07-ATTR-003 | Language | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-07-ATTR-008 | Format | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-07-ATTR-009 | Intended Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-08-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-08-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-08-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-08-ATTR-008 | Intended Postpartum Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-09-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-09-ATTR-003 | Age / Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-09-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-09-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-10-ATTR-001 | Equipment Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-10-ATTR-004 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-10-ATTR-009 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-11-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-11-ATTR-002 | Measurement / Test Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-11-ATTR-005 | Result Format | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-11-ATTR-007 | Power Source | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-12-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-12-ATTR-003 | Intended Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-12-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-12-ATTR-005 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-12-ATTR-006 | Support Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-12-ATTR-010 | Heat / Cooling Function | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-13-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-13-ATTR-002 | Material | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-13-ATTR-003 | Size | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-13-ATTR-004 | Coverage Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-13-ATTR-010 | Suitable Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-14-ATTR-001 | Kit Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-14-ATTR-003 | Stage / Age Group | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-14-ATTR-008 | Storage Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-15-ATTR-001 | Product Type | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-15-ATTR-003 | Intended Stage | select | UNRESOLVED — explicit catalogue options required before seed |
| CAT-025-15-ATTR-004 | Material | select | UNRESOLVED — explicit catalogue options required before seed |

# 38. Phase 3 — Boundary Resolution

**Status:** RESOLVED — 2026-09-30

## CAT-010 ↔ CAT-021 — Business/Commercial Equipment vs Office/School/Stationery Supplies

- **CAT-010** is the equipment domain: business/office/commercial machines, POS, professional equipment, and office furniture/fixtures used as business equipment.
- **CAT-021** is the consumable/general-supplies domain: stationery, writing materials, paper, school supplies, filing/storage supplies, and ordinary physical office/school supplies.
- A listing is assigned by the **primary product function**, not by the word “office” in its name.
- Ordinary household furniture remains CAT-003; office furniture/fixtures as commercial equipment remains CAT-010.

## CAT-011 ↔ CAT-025 — General Baby/Kids vs Maternity/Parenting Lifecycle

- **CAT-011** covers general baby/kids products, toys, children’s clothing, feeding/nursing products, and general child-use goods.
- **CAT-025** is restricted to pregnancy, maternity, breastfeeding/nursing, postpartum, and parenting-lifecycle products.
- Dedicated maternity/nursing furniture may remain CAT-025; ordinary furniture remains CAT-003.
- A product is assigned by its **primary intended lifecycle/use**, not merely because it can be used by a parent or child.

## CAT-014 ↔ CAT-023 — Consumer Personal Care vs Medical/Wellness Equipment

- **CAT-014** covers physical consumer health, beauty, hygiene, and personal-care products.
- **CAT-023** covers non-drug health, medical, diagnostic, rehabilitation, mobility, and wellness equipment.
- Commercial/institutional medical and laboratory equipment remains CAT-010.
- Professional health/beauty services remain CAT-009.
- The classification follows the **primary intended function and market context** of the physical product.

These rules resolve category ownership without changing the approved 25-category / 372-subcategory taxonomy.

# 39. Phase 3 — Applicability & Unit Validation Gate

**Status:** PASS — applicability framework defined on 2026-09-30; current materialized row coverage not verified

## Attribute Applicability Matrix — Normalized Rules

| Scope | Applicability rule | Authority |
| --- | --- | --- |
| Category common attributes | Inherit only into the subcategories explicitly covered by the detailed CAT page | Detailed CAT page common-attribute section |
| Subcategory-specific attributes | Apply only to the named subcategory; no cross-category inference | Detailed CAT subcategory table |
| Required | Use the CAT page flag; do not promote a No to Yes during seeding | Detailed CAT page |
| Filterable / Searchable | Use the CAT page flags exactly | Detailed CAT page |
| Multi-value | Use the CAT page multi-value flag; multi-select creates multiple listing_attributes rows | CAT page + Doc 13 typed-attribute model |
| Listing type | Use each CAT page's Listing-Type Applicability section; it is independent from attribute applicability | Detailed CAT page |
| Boundary ownership | Use the Phase 3 boundary rules in §38 before applying subcategory attributes | §38 |

### Category-level applicability index

The 25 detailed CAT pages remain the attribute-level authority. The normalized seed process must materialize one applicability row for every category_attribute_definition × applicable subcategory pair; it must not assume that every category attribute applies to every subcategory.

## Unit / Conversion Validation Findings

- CAT-001 land/property area units have an explicit accepted unit set and documented normalization policy: preserve entered value + source unit and derive normalized square metres for comparison.
- CAT-004 explicitly defines Mileage Unit = km/miles and Engine Unit = cc/L; other vehicle unit selectors remain unresolved where the source table is blank.
- Multiple CAT-006, CAT-007, CAT-008, CAT-010, CAT-011, CAT-015, CAT-016, CAT-017, CAT-018, CAT-019, CAT-020 and later unit attributes still contain unresolved option cells or unit values documented only as “unit separate”.
- A unit attribute is not seed-ready until its allowed unit set, canonical storage unit, conversion rule (where conversion is valid), and display-preservation rule are explicit.
- Dimensionally incompatible systems must not be converted merely because a numerical conversion is possible.

## Current Seed Gate

**Policy and catalogue-owner decisions: COMPLETE.** This is not a seed-validation PASS. Production seed readiness remains pending until a generated seed artifact passes structural checks for attribute/subcategory coverage, datatype and flag resolution, non-empty option sets, unique normalized option slugs, duplicate/orphan consistency, unit semantics, listing-type applicability, category-boundary rules, and CAT-004 Vehicle Parts source-table integrity. A clean MySQL migration/seed run and invariant tests are also required.

## 46. Catalogue-Wide Flag Defaults and Final Validation Gate — 2026-10-21

The catalogue owner approved these defaults across all 25 categories and all catalogue attributes, not only CAT-002:

- **Required:** No by default. Set Yes only where omission makes a listing materially incomplete or unusable, and only when supported by the applicable category definition.
- **Filterable:** Yes by default for every catalogue attribute.
- **Searchable:** Yes by default for every catalogue attribute, using datatype-aware search: text matching for text; exact normalized matching for select/multi-select and boolean; typed equality/range comparisons for numeric/date fields. Do not convert typed values into arbitrary full-text strings.
- These defaults override legacy Filterable = No / Searchable = No cells in earlier catalogue tables unless an explicit, documented technical exception is approved based on measured performance or correctness. Seed generation must materialize the final effective flags; it must not preserve legacy No values by accident.
- Attribute-specific options remain governed by their approved detailed catalogue rows or the exact §43 family rule. Do not replace exact option lists with broad generic options.
- Approved CAT-001 area-unit and option definitions and CAT-002 product/measurement decisions remain authoritative. Preserve the 25-category / 372-subcategory taxonomy and all existing identifiers.

### Validation tasks remaining

1. Generate or reconcile the seed manifest from the canonical Notion catalogue.
2. Validate all identifiers, 372 subcategories, applicability/inheritance, ordering, listing-type applicability, flag resolution, option slugs, datatype compatibility, unit policies, and duplicate/orphan definitions/options.
3. Review the explicit cross-category boundary pairs CAT-010/CAT-021, CAT-011/CAT-025, CAT-014/CAT-023 and confirm CAT-004 Vehicle Parts rows.
4. Run migrations and seeders against a disposable clean MySQL database, then execute the saved schema-validation SQL, foreign-key/domain invariants, representative seed assertions, and query EXPLAIN checks.
5. Mark production seed readiness PASS only after the generated report and database execution results are recorded.

# 39. Phase 3 — Attribute Applicability Matrix

**Status:** DEFINED — Phase 3B option and unit rules resolved

The applicability matrix uses deterministic inheritance rather than duplicating the same attribute list 372 times.

| Scope | Applicability rule | Seed representation |
| --- | --- | --- |
| Catalogue common attribute | Applies to every subcategory in that CAT unless an explicit subcategory override exists | One attribute definition plus applicability rows |
| Subcategory-specific attribute | Applies only to the named subcategory | Attribute definition plus explicit applicability row |
| Explicit override | Replaces inherited behavior for that subcategory only | Override row with final flags/type/requiredness |
| Select / multi_select | Applicable only where the source catalogue defines the option set | Definition plus option rows plus applicability |
| Universal listing field | Not copied into catalogue attributes | Stored on listings or related universal tables |

### Attribute flag precedence

subcategory override > catalogue common definition > no applicability.

Required, filterable, searchable, multi-value, and data type are evaluated from the final applicable definition, never inferred from the UI.

### Deterministic seed rule

Every final applicability row must resolve to exactly one attribute definition, one data type, one flag set, and, when controlled, one explicit option set. No orphan attribute definition is allowed into the final seed.

### Listing-type rule

Use the listing types explicitly declared by each catalogue page. Do not infer additional listing types for catalogues whose source page has not finalized them.

# 42. Phase 3 — Final Gate

**Status: HISTORICAL — Phase 3B policy completed 2026-09-30; current seed-readiness pending.** Phase 3B resolved shared option and unit semantics, but it did not certify later CAT-002 attribute metadata or production seed execution. The canonical taxonomy remains 25 categories and 372 subcategories.

**Policy work completed:** Property option policy; historical registry reconciliation; category-boundary rules; applicability framework; deterministic option families; unit rules. The zero-UNRESOLVED result was a 2026-09-30 snapshot, not a current post-edit audit.

**Current pending items:** close CAT-002 field-level flags/options/ranges/applicability, materialize §43 rules, and verify current catalogue-wide seed coverage and structural integrity.

**Next:** materialize the resolved catalogue into production seed data, then run duplicate/orphan/type/applicability validation.

**Decision:** No taxonomy change is required.

# 43. Phase 3B — Deterministic Option & Unit Resolution

**Status:** RESOLVED — 2026-09-30

Phase 3B closes the catalogue-seeding blocker without changing the approved 25-category / 372-subcategory taxonomy.

## 43.1 Authority and precedence

1. Individual CAT-001–CAT-025 pages remain authoritative for attribute ID, attribute name, datatype, flags, and applicability.
2. This section is authoritative for controlled option vocabulary and unit rules wherever a CAT page previously contained an unresolved option marker.
3. An exact attribute-ID option list on a CAT page takes precedence over a shared semantic family.
4. No UI, API, or seeder may invent additional options at runtime.
5. Other is a valid terminal fallback where the catalogue permits an open-ended classification.
6. Boolean attributes are typed true/false values, not option-backed selects.

## 43.2 Standard controlled option families

| Family | Explicit options / rule |
| --- | --- |
| Condition | New, Like New, Good, Fair, Used, Needs Repair, Refurbished, Other |
| Material | Wood, Engineered Wood, Metal, Steel, Stainless Steel, Aluminium, Plastic, Glass, Fabric, Leather, Faux Leather, Rubber, Silicone, Ceramic, Paper, Cardboard, Bamboo, Rattan, Stone, Concrete, Mixed, Other |
| Color | Black, White, Grey, Silver, Brown, Beige, Red, Blue, Green, Yellow, Orange, Pink, Purple, Gold, Multicolor, Transparent, Other |
| Size | XS, S, M, L, XL, XXL, XXXL, Small, Medium, Large, Standard, Custom, Other |
| Season | All Season, Spring, Summer, Autumn, Winter, Monsoon, Other |
| Power Source | AC Mains, Battery, Rechargeable Battery, Solar, Fuel, Manual, USB, Hybrid, Other |
| Power Unit | W, kW, HP, VA, kVA |
| Capacity Unit | ml, L, g, kg, oz, lb |
| Count Unit | pcs, unit, pair, set, pack, dozen |
| Weight Unit | g, kg, lb |
| Length Unit | mm, cm, m, in, ft |
| Area Unit | sq ft, sq m |
| Volume Unit | ml, L, cu ft, cu m |
| Time Unit | hour, day, week, month, year |
| Duration Unit | hour, day, week, month, year |
| Voltage Unit | V, kV |
| Current Unit | mA, A, kA |
| Frequency Unit | Hz, kHz |
| Pressure Unit | Pa, kPa, bar, psi |
| Flow Rate Unit | L/min, L/h, mL/min, mL/h |
| Temperature Unit | °C, °F |
| Storage Unit | GB, TB |
| Connectivity | Wi-Fi, Bluetooth, Ethernet, USB, NFC, Cellular, HDMI, Other |
| Installation Type | Freestanding, Wall Mount, Floor Mount, Ceiling Mount, Built-in, Portable, Clamp Mount, Other |
| Mounting Type | Wall Mount, Ceiling Mount, Floor Mount, Tabletop, Freestanding, Clamp Mount, Portable, Other |
| Compatibility | Universal, Brand-specific, Model-specific, Platform-specific, Other |
| Platform | Android, iOS, Windows, macOS, Linux, PlayStation, Xbox, Nintendo Switch, Web, Other |
| Language | Nepali, English, Hindi, Maithili, Bhojpuri, Newari, Sanskrit, Urdu, Other |
| Skill Level | Beginner, Intermediate, Advanced, Professional, Other |
| Age Group | Newborn, Infant, Toddler, Preschool, Child, Teen, Adult, Senior, All Ages |
| Gender / Customer Group | Women, Men, Girls, Boys, Unisex, All, Other |
| Shift Type | Day, Night, Morning, Evening, Rotating, Flexible, Other |
| Business Size | Micro, Small, Medium, Large, Enterprise, Other |
| Government Level | Federal, Provincial, Local, Public Institution, Other |
| Institution Type | School, College, University, Training Institute, Hospital, Clinic, Government Office, Private Company, NGO/INGO, Other |
| Application Method | Online, In Person, Email, Phone, Employer Portal, Government Portal, Other |
| Payment Type | Hourly, Daily, Weekly, Monthly, Project-based, Commission, Fixed Price, Negotiable, Other |
| Contract Type | Full-time, Part-time, Contract, Temporary, Freelance, Internship, Trainee, Volunteer, Other |
| Review / Warranty Status | None, Active, Expired, Seller Warranty, Manufacturer Warranty, Service Contract, Other |
| Safety / Security Function | Theft Prevention, Fire Protection, Gas Detection, Smoke Detection, Emergency Lighting, Access Control, Personal Safety, Workplace Safety, Other |
| Protection Rating | IP20, IP44, IP54, IP55, IP65, IP66, IP67, IP68, Other |
| Lock Type | Key, Combination, Digital, Biometric, Smart, Cable, Padlock, Disc, Other |
| Lock Mechanism | Mechanical, Electronic, Combination, Biometric, Smart, Other |
| Size / Format | A4, A5, A6, Letter, Legal, B5, Standard, Compact, Large, Custom, Other |
| Paper Size | A3, A4, A5, A6, Letter, Legal, B4, B5, Other |
| Grade | Economy, Standard, Premium, Professional, Industrial, Food Grade, Medical Grade, Other |
| Finish | Matte, Gloss, Satin, Brushed, Polished, Textured, Laminated, Natural, Other |
| Light Color | Warm White, Neutral White, Cool White, Daylight, RGB, Multicolor, Other |
| Light Source | LED, CFL, Halogen, Incandescent, Solar, Other |
| Media Format | Physical, Digital, CD, DVD, Blu-ray, Download, Streaming, Other |

## 43.3 Domain-specific unit rules

- Property land area: sq ft, sq m, aana, paisa, daam, ropani, bigha, kattha, dhur. Preserve entered value + unit; derive normalized sq m separately. Ropani/Aana/Paisa/Daam and Bigha/Kattha/Dhur are separate source systems. citeturn0search0turn0search12
- Electrical voltage: numeric value + V/kV unit. Nepal specifies 230 V single-phase, 400 V three-phase and 50 Hz frequency. citeturn1search1turn1search0
- Power/current/frequency/pressure/flow/temperature: numeric value plus explicit unit.
- Capacity/weight/length/area/volume: numeric value plus explicit unit; preserve original value/unit and derive normalized values where comparison is required.
- Duration: numeric value + duration unit.
- Dimensions: structured length/width/height plus unit; do not silently parse arbitrary prose.
- Date/datetime attributes: typed date/datetime, not select options.
- Currency/price: listing monetary schema, not category-specific option sets.
- Medical/health equipment: catalogue metadata must not imply regulatory approval, calibration, or certification. Nepal's DDA publishes Health Technology Product and medical-device regulatory material, and government specifications can require certification and calibration evidence. citeturn2search0turn2search12

## 43.4 Semantic fallback rules

- Type, Product Type, Item Type, Equipment Type, Device Type, Tool Type, Furniture Type, Appliance Type, Machine Type, Service Type, Job Type, Project Type and Vehicle Type use the approved subcategory domain choices plus Other; identical labels do not force identical cross-category vocabularies.
- Material-family labels use the Material family.
- Size-family labels use the Size family unless the CAT page already defines a product-specific size vocabulary.
- Color-family labels use the Color family.
- Power Source / Power Type / Charging Method use Power Source.
- Compatibility-family labels use Compatibility.
- Installation / Mounting / Setup labels use the applicable Installation or Mounting family.
- Unit labels use the corresponding unit family; numeric measurements remain typed.
- Language, Skill Level, Season, Age Group, Shift Type, Business Size, Institution Type, Government Level, Application Method, Payment Type and Contract Type use the corresponding explicit family.
- Status fields use the narrowest existing status vocabulary on the same CAT page; lifecycle, warranty, verification and moderation statuses are not merged.
- Other is terminal fallback only where the field is genuinely open-ended.

## 43.5 Seed rule

Previously unresolved option-backed rows are resolved by this section or an exact CAT-page option list only where an approved semantic family maps unambiguously. If neither source supplies a valid vocabulary, the field remains a product decision and must not be seeded. The 2026-10-21 CAT-002 audit records the remaining exceptions (TAB-001/TAB-007, LAP-004/LAP-010, DESK-003/DESK-006, TV-005, and AUD-006). Production seeders must materialize only approved values into category_attribute_options and must never seed the literal text UNRESOLVED.

## 43.6 Phase 3B completion

**Result: COMPLETE — deterministic catalogue option and unit policy established.**

Final automated reconciliation must verify zero unresolved markers, zero orphan attribute definitions, zero orphan option rows, datatype/option compatibility, applicability coverage, duplicate option slugs, and unit-rule consistency before production seed generation.

## 43.7 Final Unit Semantics

1. A numeric measurement attribute must use only a unit from its declared physical-dimension family.
2. Capacity is restricted to volume or mass units defined by the specific CAT attribute; count units such as pcs, unit, pair, set, pack and dozen are handled by **Count Unit**, not Capacity Unit.
3. Storage capacity is a numeric value with **Storage Unit = GB or TB** unless an exact CAT page explicitly defines another storage-unit vocabulary.
4. Length, width, height and dimension measurements use **Length Unit**; area uses **Area Unit**; volume uses **Volume Unit**; weight uses **Weight Unit**; duration uses **Duration Unit**; electrical measurements use their corresponding Voltage, Current, Power or Frequency unit family.
5. Exact CAT-page unit definitions override a generic family only for that exact attribute ID; they do not broaden other attributes automatically.
6. Conversion is allowed only within the same physical dimension and only where the source unit is explicitly declared convertible. Source value and source unit remain preserved for display/audit, with normalized values used only where search/range comparison requires them.
7. Dimensionally incompatible units must never be converted or silently reinterpreted.
8. Product quantity/count is not a physical measurement and must use Count Unit where a unit is required.
9. A unit selector must not be used for date, datetime, boolean, select, text, currency/price, or other non-measurement fields.
10. If an exact CAT attribute already defines a complete unit rule, seed generation must use that rule rather than the generic family.

# 44. Phase 3B — Final Verification Gate

**Status:** PASS — historical Phase 3B policy verification, 2026-09-30; not a current catalogue seed-readiness PASS

Verification was performed by fetching all 25 canonical CAT pages after the Phase 3B policy updates on 2026-09-30. This result predates the CAT-002 detail reconciliation updated on 2026-10-16 and the follow-up audit on 2026-10-21; it must not be interpreted as approval of that later attribute metadata.

| Check | Result |
| --- | --- |
| Top-level categories | 25 / 25 |
| Documented subcategories | 372 |
| CAT pages with literal UNRESOLVED option markers | 0 / 25 in the 2026-09-30 verification snapshot; recheck after subsequent edits |
| CAT-001 property option/unit policy | Resolved |
| CAT-002–CAT-005 shared option/unit policy | §43 policy defined; CAT-002 has remaining field-specific option/flag decisions; materialized seed coverage not yet verified |
| CAT-006–CAT-025 previously unresolved option markers | Resolved through §43 semantic option families/rules |
| Unit policy | Resolved |
| Runtime option invention | Prohibited |
| Taxonomy changes | None |
| CAT-002 current detail readiness | NOT seed-ready — 2026-10-21 audit; 96 identifiers enumerated but field-level metadata decisions remain open |

### Seed authority

The CAT pages remain authoritative for what an attribute is and where it applies. The Option Registry §43 is authoritative for controlled vocabulary and unit semantics for previously unresolved definitions. This avoids copying the same large option list into dozens of CAT tables and prevents duplicate vocabularies from drifting.

### Production-seed condition

**Phase 3B policy is complete** for controlled-option and unit semantics. This PASS does not mean every category detail page is fully seed-ready, and it is not a production-seed validation result. CAT-002's current detailed page explicitly remains **NOT seed-ready** while attribute flags, applicability, ordering, and other field-level validation metadata remain incomplete. The next implementation pass must materialize §43 options, create the applicable category_attribute_definitions / applicability rows, and validate zero unresolved values, duplicate slugs, orphan definitions/options, datatype mismatches, applicability gaps, and unit-rule violations before any production seed package is approved.

**Phase 3B policy status: COMPLETE. Catalogue-wide materialization and seed-readiness verification: PENDING.**

# 45. CAT-002 Product Defaults Approved — 2026-10-21

The catalogue owner approved implementation defaults for CAT-002. This supersedes the CAT-002 field-level decision gaps listed in the 2026-10-21 audit snapshots; those older rows are historical evidence, not current product blockers.

- **Required:** No by default; only mark Yes when a field is essential to a usable listing.
- **Filterable:** Yes by default for all 96 CAT-002 attributes.
- **Searchable:** Yes by default for all 96 CAT-002 attributes, implemented according to datatype (text matching for text, exact normalized matching for options/booleans, typed comparisons for numeric/date fields).
- **TAB-001 Operating System:** Android, iPadOS, Windows, ChromeOS, Other.
- **TAB-007 Network Type:** 2G, 3G, 4G, 5G, Wi-Fi Only, Other.
- **LAP-004 RAM Unit:** GB canonical.
- **LAP-010 Operating System:** Windows, macOS, Linux, ChromeOS, Other.
- **DESK-003 Storage Type:** HDD, SSD, NVMe SSD, eMMC, Hybrid, Other.
- **DESK-006 Operating System:** Windows, macOS, Linux, Other.
- **TV-005 Operating System:** Android TV, Google TV, Tizen, webOS, Roku TV, Fire TV, VIDAA, Proprietary, Other.
- **AUD-006 Channels:** Mono, Stereo, 2.1, 5.1, 7.1, 9.1, Other.
- **RAM:** MOB-002, TAB-002, LAP-003, DESK-002 use GB and must be greater than 0.
- **MOB-006 Battery Capacity:** integer mAh, greater than 0.
- **MOB-015 Battery Health:** integer percent, 0–100 inclusive.
- **CAM-002 Sensor Resolution:** decimal megapixels, greater than 0; no arbitrary upper bound.
- **CAM-006 Optical Zoom:** magnification ratio, at least 1.0×.
- **AUD-005 Wattage:** decimal watts, greater than 0.
- **TV-007 Refresh Rate:** integer Hz, greater than 0.
- **MOB-005, TAB-005, LAP-009, TV-001, DESK-008 screen/monitor size:** §43 Length Unit family; value greater than 0, no arbitrary upper bound.

This closes CAT-002's recorded product-choice gaps. It does **not** certify production seed readiness. The remaining gate is objective validation: all attribute identifiers and applicability rows accounted for, valid option sets/slugs, datatype compatibility, no duplicate/orphan definitions or options, and ordering/inheritance integrity. Materialize the approved rules, then run the structural validation and a clean-MySQL migration/seed test before declaring the catalogue implementation-ready.

## 47. Catalogue-Wide Static Documentation Audit — 2026-10-21

A fresh read-only text audit was performed against the parent catalogue and all 25 linked CAT pages.

- Canonical taxonomy remains 25 categories / 372 subcategories.
- CAT-001 option sets and property-area conversion policy are already documented as approved on its detailed page.
- CAT-002 product decisions are recorded in §45 and its detailed page; stale RAM/sensor-resolution notes were corrected to the approved units and positive-value rules.
- CAT-003 through CAT-025 detailed pages did not return literal “UNRESOLVED”, “Decision required”, “not specified in master”, or “Options not specified” markers in this text-marker pass. CAT-001 also returned no unresolved/decision-required markers.
- This is a documentation text-marker audit only. It does not prove that the 372 subcategories and all attribute/applicability/option rows reconcile one-to-one in a generated seed. The historical 1,166 occurrences of “UNRESOLVED” within the parent catalogue include preserved old audit material and must not be counted as current defect count.
- Global flag defaults now apply to all 25 categories: Required No by default; Filterable Yes and Searchable Yes by default, with datatype-aware query behavior. Legacy No cells are overridden by the current effective-policy rule unless a documented technical exception is approved.
- Production seed readiness remains PENDING. The current repository's develop branch is still the Laravel skeleton baseline and does not expose the approved 55-table schema migration at database/migrations/2026_09_28_000000_create_khoj_bhet_schema.php; the checked path returned 404. A saved static reconciliation report exists for a 55-table / 89-FK reconstructed migration, but no current clean-MySQL run has been evidenced. Do not mark migration, seed, or database runtime validation complete on the strength of static documentation alone.

### Exact remaining execution gate

1. Reconcile the approved Document 13 DBML and generated Laravel migration against the current develop branch (55 application tables / 89 foreign keys in the latest saved reconstruction evidence).
2. Build the catalogue seed manifest from the canonical Notion pages and enforce the §46 global flag defaults.
3. Run PHP lint and static table/FK/column reconciliation against the exact migration committed to the API branch.
4. In the disposable Docker MySQL database, run php artisan migrate:fresh --seed only after confirming the target is disposable, then execute the saved schema-validation SQL and application invariants.
5. Capture actual command output and mark the gate PASS only if the clean database meets the expected inventory and all catalogue assertions pass.

## 47. Catalogue-Wide Static Documentation Audit — 2026-10-21

A fresh read-only text audit was performed against the parent catalogue and all 25 linked CAT pages. CAT-001 and CAT-003 through CAT-025 returned no literal unresolved, decision-required, or not-specified markers in the detail-page text pass. CAT-002 decisions are recorded in §45; stale RAM and sensor-resolution notes were corrected. The taxonomy remains 25 categories and 372 subcategories.

This is a documentation text-marker audit only. It does not prove one-to-one seed coverage or runtime validity. The historical 1,166 occurrences of UNRESOLVED within the parent catalogue include preserved old audit material and must not be counted as the current defect count.

The global flag policy in §46 applies across all categories: Required No by default, Filterable Yes and Searchable Yes by default, with datatype-aware query behavior. Legacy No cells are overridden by this effective policy unless a documented technical exception is approved.

**Current execution status: PENDING.** The checked GitHub develop branch is still a Laravel skeleton baseline; the expected approved-schema migration path was not found. A saved static reconciliation report exists for a reconstructed 55-table / 89-foreign-key migration, but that is not evidence that the migration is committed or that clean MySQL succeeds.

Remaining gate: reconcile the approved DBML to the migration actually committed on develop; generate and validate the catalogue seed manifest; run PHP lint and static table/FK/column reconciliation; run migrations and seeders in a confirmed disposable Docker MySQL database; execute the saved schema inventory/FK checks, domain invariants, catalogue option/applicability assertions, and representative query-plan checks; record captured output before declaring PASS.