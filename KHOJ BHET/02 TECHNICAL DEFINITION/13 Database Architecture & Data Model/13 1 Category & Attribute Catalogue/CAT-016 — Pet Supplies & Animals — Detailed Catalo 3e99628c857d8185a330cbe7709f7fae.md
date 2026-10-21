# CAT-016 — Pet Supplies & Animals — Detailed Catalogue

**Catalogue ID:** CAT-016

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope Boundary

CAT-016 covers pet-related products and animal listings. Agricultural livestock and poultry remain CAT-014. Veterinary, grooming and training services remain CAT-009 Services.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-016-01 | Dog Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-02 | Cat Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-03 | Bird Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-04 | Fish &amp; Aquarium Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-05 | Small Animal Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-06 | Reptile &amp; Exotic Pet Supplies | Primary catalogue scope for this subcategory. |
| CAT-016-07 | Pet Food &amp; Treats | Primary catalogue scope for this subcategory. |
| CAT-016-08 | Pet Grooming &amp; Hygiene Products | Primary catalogue scope for this subcategory. |
| CAT-016-09 | Pet Health &amp; Wellness Products | Primary catalogue scope for this subcategory. |
| CAT-016-10 | Pet Beds, Cages &amp; Housing | Primary catalogue scope for this subcategory. |
| CAT-016-11 | Pet Toys &amp; Enrichment | Primary catalogue scope for this subcategory. |
| CAT-016-12 | Pet Travel &amp; Safety | Primary catalogue scope for this subcategory. |
| CAT-016-13 | Aquarium &amp; Aquatic Equipment | Primary catalogue scope for this subcategory. |
| CAT-016-14 | Pets for Sale / Adoption | Primary catalogue scope for this subcategory. |
| CAT-016-15 | Pet Accessories &amp; Apparel | Primary catalogue scope for this subcategory. |
| CAT-016-16 | Other Pet Supplies &amp; Animals | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| PET-ATTR-001 | Product / Animal Name | text | Yes | Yes | Yes | No |
| PET-ATTR-002 | Item / Animal Type | select | Yes | Yes | Yes | No |
| PET-ATTR-003 | Brand / Producer | text | No | Yes | Yes | No |
| PET-ATTR-004 | Condition | select | No | Yes | No | No |
| PET-ATTR-005 | Species | select | No | Yes | No | No |
| PET-ATTR-006 | Breed / Variety | select | No | Yes | No | No |
| PET-ATTR-007 | Age | decimal | No | Yes | No | No |
| PET-ATTR-008 | Age Unit | select | No | Yes | No | No |
| PET-ATTR-009 | Gender / Sex | select | No | Yes | No | No |
| PET-ATTR-010 | Material | select | No | Yes | No | Yes |
| PET-ATTR-011 | Size | select | No | Yes | No | No |
| PET-ATTR-012 | Quantity | integer | No | Yes | No | No |
| PET-ATTR-013 | Weight | decimal | No | Yes | No | No |
| PET-ATTR-014 | Weight Unit | select | No | Yes | No | No |
| PET-ATTR-015 | Seller Notes | text | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Needs Repair, Refurbished, Used.

Age Unit: Days, Weeks, Months, Years.

Sex: Male, Female, Unknown.

Weight Unit: g, kg, lb.

## Subcategory Attributes

### 01 — Dog Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-01-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-01-ATTR-002 | Dog Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-01-ATTR-003 | Breed Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-01-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-01-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-01-ATTR-006 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-01-ATTR-007 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-016-01-ATTR-008 | Washable | boolean | No | Yes | No | No | true / false |

### 02 — Cat Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-02-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-02-ATTR-002 | Cat Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-02-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-02-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-02-ATTR-005 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-02-ATTR-006 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-016-02-ATTR-007 | Washable | boolean | No | Yes | No | No | true / false |
| CAT-016-02-ATTR-008 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Bird Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-03-ATTR-001 | Bird Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-03-ATTR-002 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-03-ATTR-003 | Cage Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-03-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-03-ATTR-005 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-03-ATTR-006 | Compatible Species | boolean | No | Yes | No | Yes | true / false |
| CAT-016-03-ATTR-007 | Indoor / Outdoor | text | No | No | No | No | Free text |

### 04 — Fish & Aquarium Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-04-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-04-ATTR-002 | Aquarium Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-04-ATTR-003 | Tank Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-04-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-04-ATTR-005 | Compatible Species | boolean | No | Yes | No | Yes | true / false |
| CAT-016-04-ATTR-006 | Freshwater / Saltwater | text | No | No | No | No | Free text |
| CAT-016-04-ATTR-007 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-04-ATTR-008 | Power Requirement | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 05 — Small Animal Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-05-ATTR-001 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-05-ATTR-002 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-05-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-05-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-05-ATTR-005 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-05-ATTR-006 | Compatible Species | boolean | No | Yes | No | Yes | true / false |
| CAT-016-05-ATTR-007 | Indoor / Outdoor | text | No | No | No | No | Free text |

### 06 — Reptile & Exotic Pet Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-06-ATTR-001 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-06-ATTR-002 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-06-ATTR-003 | Habitat Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-06-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-06-ATTR-005 | Temperature Requirement | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-06-ATTR-006 | Humidity Requirement | text | No | No | No | No | Free text |
| CAT-016-06-ATTR-007 | Lighting Requirement | text | No | No | No | No | Free text |
| CAT-016-06-ATTR-008 | Compatible Species | boolean | No | Yes | No | Yes | true / false |

### 07 — Pet Food & Treats

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-07-ATTR-001 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-07-ATTR-002 | Food Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-07-ATTR-003 | Brand | text | No | No | Yes | No | Free text |
| CAT-016-07-ATTR-004 | Ingredients | text | No | No | No | Yes | Free text |
| CAT-016-07-ATTR-005 | Age Group | text | No | No | No | No | Free text |
| CAT-016-07-ATTR-006 | Weight / Pack Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-07-ATTR-007 | Expiry Date | text | No | No | No | No | Free text |
| CAT-016-07-ATTR-008 | Flavor | text | No | No | No | No | Free text |
| CAT-016-07-ATTR-009 | Special Diet | text | No | No | No | No | Free text |

### 08 — Pet Grooming & Hygiene Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-08-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-08-ATTR-002 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-08-ATTR-003 | Material / Ingredients | text | No | No | No | Yes | Free text |
| CAT-016-08-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-08-ATTR-005 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-016-08-ATTR-006 | Fragrance | text | No | No | No | No | Free text |
| CAT-016-08-ATTR-007 | Intended Use | text | No | No | No | No | Free text |
| CAT-016-08-ATTR-008 | Age Suitability | text | No | No | No | No | Free text |

### 09 — Pet Health & Wellness Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-09-ATTR-002 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-09-ATTR-003 | Intended Use | text | No | No | No | No | Free text |
| CAT-016-09-ATTR-004 | Ingredients / Material | select | No | Yes | No | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-09-ATTR-005 | Size / Dosage Form | text | No | No | No | No | Free text |
| CAT-016-09-ATTR-006 | Expiry Date | text | No | No | No | No | Free text |
| CAT-016-09-ATTR-007 | Manufacturer | text | No | No | No | No | Free text |
| CAT-016-09-ATTR-008 | Certification / Documentation | text | No | No | No | No | Free text |

### 10 — Pet Beds, Cages & Housing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-10-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-10-ATTR-002 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-10-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-10-ATTR-004 | Dimensions | text | No | No | No | No | Free text |
| CAT-016-10-ATTR-005 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-10-ATTR-006 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-016-10-ATTR-007 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-016-10-ATTR-008 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-016-10-ATTR-009 | Assembly Required | boolean | No | Yes | No | No | true / false |

### 11 — Pet Toys & Enrichment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-11-ATTR-001 | Toy Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-11-ATTR-002 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-11-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-11-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-11-ATTR-005 | Interactive | text | No | No | No | No | Free text |
| CAT-016-11-ATTR-006 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-016-11-ATTR-007 | Battery Required | boolean | No | Yes | No | No | true / false |
| CAT-016-11-ATTR-008 | Recommended Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 12 — Pet Travel & Safety

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-12-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-12-ATTR-002 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-12-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-12-ATTR-004 | Weight Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-12-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-12-ATTR-006 | Vehicle Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-12-ATTR-007 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-016-12-ATTR-008 | Safety Feature | text | No | No | No | No | Free text |

### 13 — Aquarium & Aquatic Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-13-ATTR-001 | Equipment Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-13-ATTR-002 | Aquarium Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-13-ATTR-003 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-13-ATTR-004 | Power Rating | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-13-ATTR-005 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-13-ATTR-006 | Freshwater / Saltwater | text | No | No | No | No | Free text |
| CAT-016-13-ATTR-007 | Flow Rate | text | No | No | No | No | Free text |
| CAT-016-13-ATTR-008 | Temperature Range | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-016-13-ATTR-009 | Compatibility | select | No | Yes | Yes | Yes | RESOLVED — Phase 3B Option Registry §43 |

### 14 — Pets for Sale / Adoption

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-14-ATTR-001 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-14-ATTR-002 | Species | text | No | No | No | No | Free text |
| CAT-016-14-ATTR-003 | Breed | text | No | No | No | No | Free text |
| CAT-016-14-ATTR-004 | Age | text | No | No | No | No | Free text |
| CAT-016-14-ATTR-005 | Sex | text | No | No | No | No | Free text |
| CAT-016-14-ATTR-006 | Vaccination Status | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-14-ATTR-007 | Health Documentation | text | No | No | No | No | Free text |
| CAT-016-14-ATTR-008 | Sterilization Status | boolean | No | Yes | No | No | true / false |
| CAT-016-14-ATTR-009 | Temperament | text | No | No | No | No | Free text |
| CAT-016-14-ATTR-010 | Location | text | No | No | No | No | Free text |
| CAT-016-14-ATTR-011 | Adoption / Sale Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 15 — Pet Accessories & Apparel

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-15-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-15-ATTR-002 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-15-ATTR-003 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-15-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-15-ATTR-005 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-15-ATTR-006 | Adjustable | boolean | No | Yes | No | No | true / false |
| CAT-016-15-ATTR-007 | Washable | boolean | No | Yes | No | No | true / false |
| CAT-016-15-ATTR-008 | Seasonal / Occasion | text | No | No | No | No | Free text |

### 16 — Other Pet Supplies & Animals

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-016-16-ATTR-001 | Item / Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-016-16-ATTR-002 | Species | text | No | No | No | No | Free text |
| CAT-016-16-ATTR-003 | Breed / Variety | text | No | No | No | No | Free text |
| CAT-016-16-ATTR-004 | Intended Use | text | No | No | No | No | Free text |
| CAT-016-16-ATTR-005 | Key Features | text | No | No | No | Yes | Free text |

Sale, Wanted, Exchange (limited), Free, Rent (limited), Offer. Lease is not applicable. Service and Job are not applicable.

## Implementation Rules

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