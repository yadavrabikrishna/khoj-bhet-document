# CAT-004 — Vehicles — Detailed Catalogue

**Project:** KHOJ BHET

**Catalogue ID:** CAT-004

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

**Parent:** 13.1 Category & Attribute Catalogue

## 1. Subcategories

- CAT-004-01 Car
- CAT-004-02 SUV / Jeep
- CAT-004-03 Van / Minivan
- CAT-004-04 Pickup
- CAT-004-05 Truck
- CAT-004-06 Bus / Microbus
- CAT-004-07 Motorcycle
- CAT-004-08 Scooter
- CAT-004-09 Electric Two-Wheeler
- CAT-004-10 Electric Car
- CAT-004-11 Tractor & Agricultural Vehicle
- CAT-004-12 Bicycle
- CAT-004-13 Auto Rickshaw / Three-Wheeler
- CAT-004-14 Vehicle Parts & Accessories
- CAT-004-15 Other Vehicles

## 2. Common Vehicle Attributes

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

Mileage Unit = km, miles. Operating Hours is a separate decimal attribute with unit = hours. Engine Unit = cc, L.

Insurance Status = Active, Expired, None, Unknown.

Tax Status = Paid, Due, Overdue, Exempt, Unknown.

Warranty Status = Active, Expired, None, Manufacturer Warranty, Seller Warranty.

Documents Available = Blue Book, Insurance, Tax Receipt, Purchase Invoice, Service Records, Pollution Certificate, Registration Certificate, Other.

Features = Air Conditioning, Power Steering, Power Windows, Central Locking, ABS, Airbags, Sunroof, Cruise Control, Reverse Camera, Parking Sensors, Alloy Wheels, LED Headlights, Fog Lights, GPS, Bluetooth, Touchscreen, Android Auto, Apple CarPlay, Keyless Entry, Push Start, Heated Seats, Leather Seats, Roof Rack, 4WD, AWD.

## 3. Subcategory Attributes

### CAT-004-01 Car

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAR-001 | Body Type | select | No | Yes | Yes | No | Sedan, Hatchback, Coupe, Convertible, Wagon, Crossover, Other |
| CAR-002 | Seating Capacity | integer | No | Yes | No | No |  |
| CAR-003 | Door Count | integer | No | Yes | No | No |  |
| CAR-004 | Drive Type | select | No | Yes | Yes | No | FWD, RWD, AWD, 4WD, Other |
| CAR-005 | Number of Cylinders | integer | No | Yes | No | No |  |
| CAR-006 | Boot Capacity | decimal | No | Yes | No | No |  |

</table>

### CAT-004-02 SUV / Jeep

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SUV-001 | Body Type | select | No | Yes | Yes | No | Compact SUV, SUV, Crossover, Jeep, Off-road, Other |
| SUV-002 | Seating Capacity | integer | No | Yes | No | No |  |
| SUV-003 | Door Count | integer | No | Yes | No | No |  |
| SUV-004 | Drive Type | select | No | Yes | Yes | No |  |
| SUV-005 | Ground Clearance | decimal | No | Yes | No | No |  |
| SUV-006 | Number of Cylinders | integer | No | Yes | No | No |  |

</table>

### CAT-004-03 Van / Minivan

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| VAN-001 | Seating Capacity | integer | No | Yes | No | No |  |
| VAN-002 | Door Count | integer | No | Yes | No | No |  |
| VAN-003 | Vehicle Purpose | select | No | Yes | Yes | No | Passenger, Cargo, Commercial, School, Tourism, Other |
| VAN-004 | Drive Type | select | No | Yes | Yes | No |  |

</table>

### CAT-004-04 Pickup

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| PICK-001 | Cab Type | select | No | Yes | Yes | No | Single Cab, Double Cab, Extended Cab, Other |
| PICK-002 | Seating Capacity | integer | No | Yes | No | No |  |
| PICK-003 | Payload Capacity | decimal | No | Yes | No | No |  |
| PICK-004 | Payload Unit | select | No | Yes | No | No |  |
| PICK-005 | Drive Type | select | No | Yes | Yes | No |  |
| PICK-006 | Bed Type | select | No | Yes | Yes | No | Standard, Long Bed, Short Bed, Flatbed, Other |

</table>

### CAT-004-05 Truck

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TRK-001 | Truck Type | select | No | Yes | Yes | No | Light Truck, Medium Truck, Heavy Truck, Tipper, Tanker, Container Truck, Cargo Truck, Other |
| TRK-002 | Payload Capacity | decimal | No | Yes | No | No |  |
| TRK-003 | Payload Unit | select | No | Yes | No | No |  |
| TRK-004 | Axle Count | integer | No | Yes | No | No |  |
| TRK-005 | Drive Type | select | No | Yes | Yes | No |  |
| TRK-006 | Body Type | select | No | Yes | Yes | No |  |

</table>

### CAT-004-06 Bus / Microbus

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| BUS-001 | Vehicle Type | select | No | Yes | Yes | No | Bus, Mini Bus, Microbus, Tourist Bus, School Bus, Other |
| BUS-002 | Seating Capacity | integer | No | Yes | No | No |  |
| BUS-003 | Door Count | integer | No | Yes | No | No |  |
| BUS-004 | Usage Type | select | No | Yes | Yes | No | Public Transport, Tourist, School, Staff, Private, Other |
| BUS-005 | Air Conditioning | boolean | No | Yes | No | No | true / false |

</table>

### CAT-004-07 Motorcycle

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| MOTO-001 | Motorcycle Type | select | No | Yes | Yes | No | Standard, Sports, Cruiser, Adventure, Touring, Off-road, Dirt Bike, Other |
| MOTO-002 | Engine Capacity | integer | No | Yes | No | No |  |
| MOTO-003 | Seating Capacity | integer | No | Yes | No | No |  |
| MOTO-004 | Gear Count | integer | No | Yes | No | No |  |
| MOTO-005 | ABS | boolean | No | Yes | No | No | true / false |
| MOTO-006 | Electric Start | boolean | No | Yes | No | No | true / false |

</table>

### CAT-004-08 Scooter

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SCOOT-001 | Scooter Type | select | No | Yes | Yes | No | Standard, Maxi Scooter, Electric Scooter, Other |
| SCOOT-002 | Engine Capacity | integer | No | Yes | No | No |  |
| SCOOT-003 | Seating Capacity | integer | No | Yes | No | No |  |
| SCOOT-004 | Electric Start | boolean | No | Yes | No | No | true / false |
| SCOOT-005 | Underseat Storage | boolean | No | Yes | No | No | true / false |

</table>

### CAT-004-09 Electric Two-Wheeler

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |

</table>

### CAT-004-10 Electric Car

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| EVC-001 | Body Type | select | No | Yes | Yes | No |  |
| EVC-002 | Battery Capacity | decimal | No | Yes | No | No |  |
| EVC-003 | Battery Unit | select | No | Yes | No | No |  |
| EVC-004 | Range | decimal | No | Yes | No | No |  |
| EVC-005 | Range Unit | select | No | Yes | No | No |  |
| EVC-006 | Charging Time | decimal | No | Yes | No | No |  |
| EVC-007 | Charging Connector | select | No | Yes | No | No | Type 1, Type 2, CCS, CHAdeMO, GB/T, Other |
| EVC-008 | Seating Capacity | integer | No | Yes | No | No |  |

</table>

### CAT-004-11 Tractor & Agricultural Vehicle

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| AGR-001 | Vehicle Type | select | No | Yes | Yes | No | Tractor, Power Tiller, Harvester, Agricultural Machine, Other |
| AGR-002 | Horsepower | decimal | No | Yes | No | No |  |
| AGR-003 | Drive Type | select | No | Yes | Yes | No |  |
| AGR-004 | PTO | boolean | No | Yes | No | No | true / false |
| AGR-005 | Hydraulic System | boolean | No | Yes | No | No | true / false |
| AGR-006 | Hours Used | decimal | No | Yes | No | No |  |

</table>

### CAT-004-12 Bicycle

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| BIKE-001 | Bicycle Type | select | No | Yes | Yes | No | Mountain, Road, Hybrid, City, BMX, Kids, Folding, Electric, Other |
| BIKE-002 | Wheel Size | decimal | No | Yes | No | No |  |
| BIKE-003 | Frame Material | select | No | Yes | No | No | Steel, Aluminum, Carbon Fiber, Titanium, Other |
| BIKE-004 | Gear Count | integer | No | Yes | No | No |  |
| BIKE-005 | Suspension | select | No | Yes | No | No |  |
| BIKE-006 | Electric Assist | boolean | No | Yes | No | No | true / false |

</table>

### CAT-004-13 Auto Rickshaw / Three-Wheeler

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| THREE-001 | Vehicle Type | select | No | Yes | Yes | No | Auto Rickshaw, Electric Three-Wheeler, Cargo Three-Wheeler, Passenger Three-Wheeler, Other |
| THREE-002 | Seating Capacity | integer | No | Yes | No | No |  |
| THREE-003 | Fuel Type | select | No | Yes | Yes | No |  |
| THREE-004 | Engine Capacity | integer | No | Yes | No | No |  |
| THREE-005 | Commercial Registration | boolean | No | Yes | No | No | true / false |

</table>

### CAT-004-14 Vehicle Parts & Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| VPA-001 | &lt;/td&gt; &lt;td&gt;Part Type&lt;/td&gt; &lt;td&gt;select&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;/tr&gt; &lt;tr&gt; &lt;td&gt; | select | No | Yes | Yes | No |  |
| VPA-002 | &lt;/td&gt; &lt;td&gt;Brand&lt;/td&gt; &lt;td&gt;text&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;/tr&gt; &lt;tr&gt; &lt;td&gt; | text | No | Yes | Yes | No |  |
| VPA-003 | &lt;/td&gt; &lt;td&gt;Compatible Brand&lt;/td&gt; &lt;td&gt;text&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;/tr&gt; &lt;tr&gt; &lt;td&gt; | text | No | Yes | Yes | No |  |
| VPA-004 | &lt;/td&gt; &lt;td&gt;Compatible Model&lt;/td&gt; &lt;td&gt;text&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;/tr&gt; &lt;tr&gt; &lt;td&gt; | text | No | Yes | Yes | No |  |
| VPA-005 | &lt;/td&gt; &lt;td&gt;Part Number&lt;/td&gt; &lt;td&gt;text&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;/tr&gt; &lt;tr&gt; &lt;td&gt; | text | No | Yes | No | No |  |
| VPA-006 | &lt;/td&gt; &lt;td&gt;Condition&lt;/td&gt; &lt;td&gt;select&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;/tr&gt; &lt;tr&gt; &lt;td&gt; | select | No | Yes | No | No |  |
| VPA-007 | &lt;/td&gt; &lt;td&gt;Quantity&lt;/td&gt; &lt;td&gt;integer&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;td&gt;Yes&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;td&gt;No&lt;/td&gt; &lt;/tr&gt; &lt;/table&gt; | integer | No | Yes | No | No |  |

</table>

### CAT-004-15 Other Vehicles

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |

</table>

## 4. Listing-Type Applicability

All CAT-004 subcategories support **Sale, Exchange, Wanted**.

Rent, Lease, Free, Offer, Service, and Job are not initially exposed.

## 5. Implementation Rules

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

## Phase 3 Audit Note

CAT-019 is authoritative for industrial, heavy construction, and heavy agricultural machinery.