# CAT-017 — Travel, Luggage & Accessories — Detailed Catalogue

**Catalogue ID:** CAT-017

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope Boundary

CAT-017 covers physical travel-related products. Travel agencies, tour operators, guides, ticketing, transport, and other travel services remain CAT-009 Services. General vehicle accessories remain CAT-004; ordinary clothing remains CAT-005; general electronics remain CAT-002.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-017-01 | Luggage &amp; Suitcases | Primary catalogue scope for this subcategory. |
| CAT-017-02 | Backpacks &amp; Travel Bags | Primary catalogue scope for this subcategory. |
| CAT-017-03 | Travel Organizers &amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-04 | Travel Clothing &amp; Footwear | Primary catalogue scope for this subcategory. |
| CAT-017-05 | Camping &amp; Travel Gear | Primary catalogue scope for this subcategory. |
| CAT-017-06 | Travel Electronics &amp; Gadgets | Primary catalogue scope for this subcategory. |
| CAT-017-07 | Travel Safety &amp; Security | Primary catalogue scope for this subcategory. |
| CAT-017-08 | Passport &amp; Document Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-09 | Neck Pillows &amp; Travel Comfort | Primary catalogue scope for this subcategory. |
| CAT-017-10 | Travel Toiletry &amp; Personal Care Kits | Primary catalogue scope for this subcategory. |
| CAT-017-11 | Car Travel Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-12 | Motorcycle Travel Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-13 | Outdoor &amp; Adventure Travel Gear | Primary catalogue scope for this subcategory. |
| CAT-017-14 | Travel Souvenirs &amp; Memorabilia | Primary catalogue scope for this subcategory. |
| CAT-017-15 | Business Travel Accessories | Primary catalogue scope for this subcategory. |
| CAT-017-16 | Other Travel Products | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| TRAVEL-ATTR-001 | Brand / Manufacturer | text. | No | Yes | Yes | No |
| TRAVEL-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| TRAVEL-ATTR-003 | Product Type | select | Yes | Yes | Yes | No |
| TRAVEL-ATTR-004 | Condition | select | Yes | Yes | No | No |
| TRAVEL-ATTR-005 | Material | select | No | Yes | No | Yes |
| TRAVEL-ATTR-006 | Color | select. | No | No | No | No |
| TRAVEL-ATTR-007 | Size | select. | No | No | No | No |
| TRAVEL-ATTR-008 | Dimensions | text. | No | No | No | No |
| TRAVEL-ATTR-009 | Weight | decimal. | No | No | No | No |
| TRAVEL-ATTR-010 | Weight Unit | select. | No | No | No | No |
| TRAVEL-ATTR-011 | Capacity | decimal. | No | No | No | No |
| TRAVEL-ATTR-012 | Capacity Unit | select. | No | No | No | No |
| TRAVEL-ATTR-013 | Purchase Year | integer. | No | No | No | No |
| TRAVEL-ATTR-014 | Warranty Status | select. | No | No | No | No |
| TRAVEL-ATTR-015 | Accessories Included | multi_select | No | Yes | No | Yes |
| TRAVEL-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Weight Unit: g, kg, lb.

Capacity Unit: L, ml, kg, Piece, Other.

Warranty: None, Active, Expired, Seller Warranty, Manufacturer Warranty.

## Subcategory Attributes

### 01 — Luggage & Suitcases

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-01-ATTR-001 | Luggage Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-01-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-01-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-01-ATTR-004 | Size / Cabin Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-01-ATTR-005 | Number of Wheels | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-01-ATTR-006 | Wheel Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-01-ATTR-007 | Lock Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-01-ATTR-008 | Expandable | text | No | No | No | No | Free text |
| CAT-017-01-ATTR-009 | Handle Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-01-ATTR-010 | TSA Lock | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 02 — Backpacks & Travel Bags

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-02-ATTR-001 | Bag Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-02-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-02-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-02-ATTR-004 | Laptop Compartment | text | No | No | No | No | Free text |
| CAT-017-02-ATTR-005 | Laptop Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-02-ATTR-006 | Water Resistant | boolean | No | Yes | No | No | true / false |
| CAT-017-02-ATTR-007 | Number of Compartments | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-02-ATTR-008 | Carrying Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Travel Organizers & Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-03-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-03-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-03-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-03-ATTR-004 | Number of Compartments | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-03-ATTR-005 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-017-03-ATTR-006 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-03-ATTR-007 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 04 — Travel Clothing & Footwear

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-04-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-04-ATTR-002 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-04-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-04-ATTR-004 | Gender | text | No | No | No | No | Free text |
| CAT-017-04-ATTR-005 | Season | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-04-ATTR-006 | Weather Suitability | text | No | No | No | No | Free text |
| CAT-017-04-ATTR-007 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-017-04-ATTR-008 | Intended Activity | text | No | No | No | No | Free text |

### 05 — Camping & Travel Gear

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-05-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-05-ATTR-002 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-05-ATTR-003 | Persons | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-05-ATTR-004 | Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-05-ATTR-005 | Packed Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-05-ATTR-006 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-017-05-ATTR-007 | Season Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-05-ATTR-008 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-017-05-ATTR-009 | Setup Required | boolean | No | Yes | No | No | true / false |

### 06 — Travel Electronics & Gadgets

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-06-ATTR-001 | Device Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-06-ATTR-002 | Brand | text | No | No | Yes | No | Free text |
| CAT-017-06-ATTR-003 | Model | text | No | No | Yes | No | Free text |
| CAT-017-06-ATTR-004 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-06-ATTR-005 | Battery Capacity | boolean | No | Yes | No | No | true / false |
| CAT-017-06-ATTR-006 | Voltage | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-06-ATTR-007 | Connectivity | text | No | No | No | No | Free text |
| CAT-017-06-ATTR-008 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-06-ATTR-009 | Accessories | text | No | No | No | Yes | Free text |

### 07 — Travel Safety & Security

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-07-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-07-ATTR-002 | Security Function | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-07-ATTR-003 | Lock Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-07-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-07-ATTR-005 | TSA Compatible | boolean | No | Yes | No | Yes | true / false |
| CAT-017-07-ATTR-006 | Alarm | text | No | No | No | No | Free text |
| CAT-017-07-ATTR-007 | Connectivity | text | No | No | No | No | Free text |
| CAT-017-07-ATTR-008 | Battery Required | boolean | No | Yes | No | No | true / false |

### 08 — Passport & Document Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-08-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-08-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-08-ATTR-003 | Number of Compartments | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-08-ATTR-004 | Card Slots | text | No | No | No | No | Free text |
| CAT-017-08-ATTR-005 | RFID Protection | text | No | No | No | No | Free text |
| CAT-017-08-ATTR-006 | Passport Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-08-ATTR-007 | Waterproof | boolean | No | Yes | No | No | true / false |

### 09 — Neck Pillows & Travel Comfort

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-09-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-09-ATTR-003 | Filling | text | No | No | No | No | Free text |
| CAT-017-09-ATTR-004 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-017-09-ATTR-005 | Washable | boolean | No | Yes | No | No | true / false |
| CAT-017-09-ATTR-006 | Inflatable | text | No | No | No | No | Free text |
| CAT-017-09-ATTR-007 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-09-ATTR-008 | Carry Bag Included | boolean | No | Yes | No | No | true / false |

### 10 — Travel Toiletry & Personal Care Kits

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-10-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-10-ATTR-002 | Container Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-10-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-10-ATTR-004 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-10-ATTR-005 | Number of Pieces | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-10-ATTR-006 | Leak Resistant | boolean | No | Yes | No | No | true / false |
| CAT-017-10-ATTR-007 | TSA / Travel Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 11 — Car Travel Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-11-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-11-ATTR-002 | Vehicle Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-11-ATTR-003 | Installation Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-11-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-11-ATTR-005 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-11-ATTR-006 | Universal / Model Specific | text | No | No | Yes | No | Free text |
| CAT-017-11-ATTR-007 | Safety Feature | text | No | No | No | No | Free text |

### 12 — Motorcycle Travel Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-12-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-12-ATTR-002 | Motorcycle Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-12-ATTR-003 | Mounting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-12-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-12-ATTR-005 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-017-12-ATTR-006 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-12-ATTR-007 | Safety Feature | text | No | No | No | No | Free text |

### 13 — Outdoor & Adventure Travel Gear

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-13-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-13-ATTR-002 | Activity | text | No | No | No | No | Free text |
| CAT-017-13-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-13-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-13-ATTR-005 | Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-13-ATTR-006 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-13-ATTR-007 | Waterproof | boolean | No | Yes | No | No | true / false |
| CAT-017-13-ATTR-008 | Safety Equipment | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-13-ATTR-009 | Skill Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 14 — Travel Souvenirs & Memorabilia

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-14-ATTR-001 | Item Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-14-ATTR-002 | Origin / Destination | text | No | No | No | No | Free text |
| CAT-017-14-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-14-ATTR-004 | Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-017-14-ATTR-005 | Handmade | text | No | No | No | No | Free text |
| CAT-017-14-ATTR-006 | Theme | text | No | No | No | No | Free text |
| CAT-017-14-ATTR-007 | Dimensions | text | No | No | No | No | Free text |

### 15 — Business Travel Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-15-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-15-ATTR-002 | Laptop Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-15-ATTR-003 | Device Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-15-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-15-ATTR-005 | Compartments | text | No | No | No | No | Free text |
| CAT-017-15-ATTR-006 | RFID Protection | text | No | No | No | No | Free text |
| CAT-017-15-ATTR-007 | Carrying Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-15-ATTR-008 | Business / Professional Use | text | No | No | No | No | Free text |

### 16 — Other Travel Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-017-16-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-16-ATTR-002 | Intended Travel Use | text | No | No | No | No | Free text |
| CAT-017-16-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-16-ATTR-004 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-017-16-ATTR-005 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange, Wanted, Free, Rent (limited), Offer. Lease, Service and Job are not applicable.

## Implementation Rules

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