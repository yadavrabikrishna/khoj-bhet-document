# CAT-013 — Food, Agriculture Products & Livestock — Detailed Catalogue

**Catalogue ID:** CAT-013

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Scope Boundary

CAT-011 covers land, farms, agricultural property and development land. CAT-009 covers agricultural services. CAT-013 covers physical food, agricultural products, planting materials and livestock.

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-013-01 | Grains &amp; Cereals | Primary catalogue scope for this subcategory. |
| CAT-013-02 | Pulses &amp; Legumes | Primary catalogue scope for this subcategory. |
| CAT-013-03 | Fruits | Primary catalogue scope for this subcategory. |
| CAT-013-04 | Vegetables | Primary catalogue scope for this subcategory. |
| CAT-013-05 | Spices &amp; Herbs | Primary catalogue scope for this subcategory. |
| CAT-013-06 | Dairy &amp; Dairy Products | Primary catalogue scope for this subcategory. |
| CAT-013-07 | Meat &amp; Poultry | Primary catalogue scope for this subcategory. |
| CAT-013-08 | Fish &amp; Seafood | Primary catalogue scope for this subcategory. |
| CAT-013-09 | Eggs &amp; Hatchery Products | Primary catalogue scope for this subcategory. |
| CAT-013-10 | Seeds &amp; Planting Materials | Primary catalogue scope for this subcategory. |
| CAT-013-11 | Animal Feed &amp; Fodder | Primary catalogue scope for this subcategory. |
| CAT-013-12 | Nursery Plants &amp; Saplings | Primary catalogue scope for this subcategory. |
| CAT-013-13 | Livestock &amp; Poultry | Primary catalogue scope for this subcategory. |
| CAT-013-14 | Processed &amp; Packaged Food | Primary catalogue scope for this subcategory. |
| CAT-013-15 | Organic &amp; Specialty Products | Primary catalogue scope for this subcategory. |
| CAT-013-16 | Other Food &amp; Agricultural Products | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| FOOD-ATTR-001 | Product Name | text | Yes | Yes | Yes | No |
| FOOD-ATTR-002 | Product Type | select | Yes | Yes | Yes | No |
| FOOD-ATTR-003 | Brand / Producer | text | No | Yes | Yes | No |
| FOOD-ATTR-004 | Origin / Production Location | json | No | Yes | Yes | No |
| FOOD-ATTR-005 | Condition / Freshness | select | Yes | Yes | No | No |
| FOOD-ATTR-006 | Quantity | decimal | Yes | Yes | No | No |
| FOOD-ATTR-007 | Quantity Unit | select | Yes | Yes | No | No |
| FOOD-ATTR-008 | Price | decimal | No | Yes | No | No |
| FOOD-ATTR-009 | Price Unit | select | No | Yes | No | No |
| FOOD-ATTR-010 | Production Date | date | No | Yes | Yes | No |
| FOOD-ATTR-011 | Expiry Date | date | No | Yes | No | No |
| FOOD-ATTR-012 | Packaging Type | select | No | Yes | Yes | No |
| FOOD-ATTR-013 | Storage Requirement | select | No | Yes | No | No |
| FOOD-ATTR-014 | Organic / Specialty Claim | select | No | Yes | No | No |
| FOOD-ATTR-015 | Seller Notes | text | No | No | No | No |

## Controlled Values

Condition / Freshness: Fresh, Recently Harvested, Frozen, Dried, Processed, Packaged, Live, Other.

Quantity Units: g, kg, Quintal, Metric Ton, Piece, Dozen, Crate, Sack, Packet, Liter, ml, Other.

Packaging: Loose, Sack, Bag, Box, Bottle, Jar, Can, Packet, Crate, Other.

Storage: Ambient, Refrigerated, Frozen, Dry Storage, Humidity Controlled, Other.

## Subcategory Attributes

### 01 — Grains & Cereals

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-01-ATTR-001 | Grain Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-01-ATTR-002 | Variety | text | No | No | No | No | Free text |
| CAT-013-01-ATTR-003 | Harvest Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-013-01-ATTR-004 | Moisture Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-01-ATTR-005 | Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-01-ATTR-006 | Processing Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-01-ATTR-007 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 02 — Pulses & Legumes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-02-ATTR-001 | Pulse Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-02-ATTR-002 | Variety | text | No | No | No | No | Free text |
| CAT-013-02-ATTR-003 | Harvest Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-013-02-ATTR-004 | Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-02-ATTR-005 | Processing Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-02-ATTR-006 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Fruits

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-03-ATTR-001 | Fruit Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-03-ATTR-002 | Variety | text | No | No | No | No | Free text |
| CAT-013-03-ATTR-003 | Harvest Season | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-03-ATTR-004 | Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-03-ATTR-005 | Ripeness | text | No | No | No | No | Free text |
| CAT-013-03-ATTR-006 | Organic Claim | text | No | No | No | No | Free text |
| CAT-013-03-ATTR-007 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 04 — Vegetables

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-04-ATTR-001 | Vegetable Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-04-ATTR-002 | Variety | text | No | No | No | No | Free text |
| CAT-013-04-ATTR-003 | Harvest Date | text | No | No | No | No | Free text |
| CAT-013-04-ATTR-004 | Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-04-ATTR-005 | Organic Claim | text | No | No | No | No | Free text |
| CAT-013-04-ATTR-006 | Growing Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-04-ATTR-007 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 05 — Spices & Herbs

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-05-ATTR-001 | Spice / Herb Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-05-ATTR-002 | Form | text | No | No | No | No | Free text |
| CAT-013-05-ATTR-003 | Variety | text | No | No | No | No | Free text |
| CAT-013-05-ATTR-004 | Processing | text | No | No | No | No | Free text |
| CAT-013-05-ATTR-005 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-05-ATTR-006 | Organic Claim | text | No | No | No | No | Free text |
| CAT-013-05-ATTR-007 | Purity / Blend Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 06 — Dairy & Dairy Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-06-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-06-ATTR-002 | Source Animal | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-06-ATTR-003 | Fat Content | text | No | No | No | No | Free text |
| CAT-013-06-ATTR-004 | Processing Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-06-ATTR-005 | Pasteurized | text | No | No | No | No | Free text |
| CAT-013-06-ATTR-006 | Storage Requirement | text | No | No | No | No | Free text |
| CAT-013-06-ATTR-007 | Expiry Date | text | No | No | No | No | Free text |

### 07 — Meat & Poultry

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-07-ATTR-001 | Meat Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-07-ATTR-002 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-07-ATTR-003 | Fresh / Frozen | text | No | No | No | No | Free text |
| CAT-013-07-ATTR-004 | Cut Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-07-ATTR-005 | Processing Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-07-ATTR-006 | Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-013-07-ATTR-007 | Packaging | text | No | No | No | No | Free text |
| CAT-013-07-ATTR-008 | Slaughter / Processing Date where applicable | text | No | No | No | No | Free text |

### 08 — Fish & Seafood

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-08-ATTR-001 | Species | text | No | No | No | No | Free text |
| CAT-013-08-ATTR-002 | Fresh / Frozen | text | No | No | No | No | Free text |
| CAT-013-08-ATTR-003 | Farmed / Wild | text | No | No | No | No | Free text |
| CAT-013-08-ATTR-004 | Size / Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-013-08-ATTR-005 | Processing Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-08-ATTR-006 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-08-ATTR-007 | Storage Requirement | text | No | No | No | No | Free text |

### 09 — Eggs & Hatchery Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-09-ATTR-002 | Bird Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-09-ATTR-003 | Egg Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-09-ATTR-004 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-013-09-ATTR-005 | Grade | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-09-ATTR-006 | Production Date | text | No | No | No | No | Free text |
| CAT-013-09-ATTR-007 | Hatchery Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 10 — Seeds & Planting Materials

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-10-ATTR-001 | Crop Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-10-ATTR-002 | Variety | text | No | No | No | No | Free text |
| CAT-013-10-ATTR-003 | Seed Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-10-ATTR-004 | Season | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-10-ATTR-005 | Germination Information | text | No | No | No | No | Free text |
| CAT-013-10-ATTR-006 | Certification | text | No | No | No | No | Free text |
| CAT-013-10-ATTR-007 | Harvest / Production Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-013-10-ATTR-008 | Treatment | text | No | No | No | No | Free text |

### 11 — Animal Feed & Fodder

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-11-ATTR-001 | Feed Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-11-ATTR-002 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-11-ATTR-003 | Form | text | No | No | No | No | Free text |
| CAT-013-11-ATTR-004 | Nutritional Specification | text | No | No | No | No | Free text |
| CAT-013-11-ATTR-005 | Protein Content | text | No | No | No | No | Free text |
| CAT-013-11-ATTR-006 | Packaging | text | No | No | No | No | Free text |
| CAT-013-11-ATTR-007 | Storage Requirement | text | No | No | No | No | Free text |

### 12 — Nursery Plants & Saplings

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-12-ATTR-001 | Plant Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-12-ATTR-002 | Species | text | No | No | No | No | Free text |
| CAT-013-12-ATTR-003 | Variety | text | No | No | No | No | Free text |
| CAT-013-12-ATTR-004 | Plant Age | text | No | No | No | No | Free text |
| CAT-013-12-ATTR-005 | Plant Height | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-013-12-ATTR-006 | Pot / Bare Root | text | No | No | No | No | Free text |
| CAT-013-12-ATTR-007 | Growing Condition | text | No | No | No | No | Free text |
| CAT-013-12-ATTR-008 | Suitable Climate | text | No | No | No | No | Free text |

### 13 — Livestock & Poultry

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-13-ATTR-001 | Animal Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-13-ATTR-002 | Breed | text | No | No | No | No | Free text |
| CAT-013-13-ATTR-003 | Age | text | No | No | No | No | Free text |
| CAT-013-13-ATTR-004 | Sex | text | No | No | No | No | Free text |
| CAT-013-13-ATTR-005 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-013-13-ATTR-006 | Purpose | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-13-ATTR-007 | Vaccination Status | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-13-ATTR-008 | Health Documentation | text | No | No | No | No | Free text |
| CAT-013-13-ATTR-009 | Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 14 — Processed & Packaged Food

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-14-ATTR-001 | Food Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-14-ATTR-002 | Brand | text | No | No | Yes | No | Free text |
| CAT-013-14-ATTR-003 | Ingredients | text | No | No | No | Yes | Free text |
| CAT-013-14-ATTR-004 | Net Weight | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-013-14-ATTR-005 | Packaging | text | No | No | No | No | Free text |
| CAT-013-14-ATTR-006 | Production Date | text | No | No | No | No | Free text |
| CAT-013-14-ATTR-007 | Expiry Date | text | No | No | No | No | Free text |
| CAT-013-14-ATTR-008 | Storage Requirement | text | No | No | No | No | Free text |
| CAT-013-14-ATTR-009 | Food Certification | text | No | No | No | No | Free text |

### 15 — Organic & Specialty Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-15-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-15-ATTR-002 | Certification | text | No | No | No | No | Free text |
| CAT-013-15-ATTR-003 | Certification Authority | text | No | No | No | No | Free text |
| CAT-013-15-ATTR-004 | Production Method | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-15-ATTR-005 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-15-ATTR-006 | Specialty Claim | text | No | No | No | No | Free text |
| CAT-013-15-ATTR-007 | Packaging | text | No | No | No | No | Free text |

### 16 — Other Food & Agricultural Products

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-013-16-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-16-ATTR-002 | Intended Use | text | No | No | No | No | Free text |
| CAT-013-16-ATTR-003 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-013-16-ATTR-004 | Key Features | text | No | No | No | Yes | Free text |

Sale, Wanted, Exchange (limited), Free, Offer. Rent, Lease, Service and Job are not applicable.

## Implementation Rules

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