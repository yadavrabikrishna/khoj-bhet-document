# CAT-022 — Religious, Spiritual & Cultural Items — Detailed Catalogue

**Catalogue ID:** CAT-022

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

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
| CAT-022-01 | Religious Statues &amp; Idols | Primary catalogue scope for this subcategory. |
| CAT-022-02 | Puja &amp; Worship Supplies | Primary catalogue scope for this subcategory. |
| CAT-022-03 | Prayer &amp; Meditation Items | Primary catalogue scope for this subcategory. |
| CAT-022-04 | Religious Clothing &amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-022-05 | Prayer Mats, Carpets &amp; Floor Items | Primary catalogue scope for this subcategory. |
| CAT-022-06 | Rosaries, Mala &amp; Prayer Beads | Primary catalogue scope for this subcategory. |
| CAT-022-07 | Incense, Lamps &amp; Ritual Burning Items | Primary catalogue scope for this subcategory. |
| CAT-022-08 | Religious Vessels &amp; Ritual Utensils | Primary catalogue scope for this subcategory. |
| CAT-022-09 | Temple, Shrine &amp; Home Altar Items | Primary catalogue scope for this subcategory. |
| CAT-022-10 | Religious Flags, Banners &amp; Symbols | Primary catalogue scope for this subcategory. |
| CAT-022-11 | Festival &amp; Cultural Celebration Items | Primary catalogue scope for this subcategory. |
| CAT-022-12 | Traditional &amp; Cultural Handicrafts | Primary catalogue scope for this subcategory. |
| CAT-022-13 | Spiritual &amp; Meditation Equipment | Primary catalogue scope for this subcategory. |
| CAT-022-14 | Cultural Musical Instruments | Primary catalogue scope for this subcategory. |
| CAT-022-15 | Religious Gift &amp; Devotional Items | Primary catalogue scope for this subcategory. |
| CAT-022-16 | Other Religious, Spiritual &amp; Cultural Items | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| CULT-ATTR-001 | Brand / Manufacturer / Maker | text. | No | Yes | Yes | No |
| CULT-ATTR-002 | Product Name / Model | text | Yes | Yes | Yes | No |
| CULT-ATTR-003 | Product Type | select | Yes | Yes | Yes | No |
| CULT-ATTR-004 | Tradition / Cultural Context | select. | No | No | No | No |
| CULT-ATTR-005 | Religion / Spiritual Tradition | select | No | Yes | No | Yes |
| CULT-ATTR-006 | Material | select | No | Yes | No | Yes |
| CULT-ATTR-007 | Condition | select. | No | No | No | No |
| CULT-ATTR-008 | Color | select | No | Yes | No | Yes |
| CULT-ATTR-009 | Size / Dimensions | text. | No | No | No | No |
| CULT-ATTR-010 | Weight | decimal. | No | No | No | No |
| CULT-ATTR-011 | Weight Unit | select. | No | No | No | No |
| CULT-ATTR-012 | Quantity | decimal. | No | No | No | No |
| CULT-ATTR-013 | Quantity Unit | select. | No | No | No | No |
| CULT-ATTR-014 | Handmade | boolean. | No | No | No | No |
| CULT-ATTR-015 | Accessories Included | multi_select | No | Yes | No | Yes |
| CULT-ATTR-016 | Seller Notes | text. | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Used, Damaged, Restored.

Weight Unit: g, kg, lb, Other.

Quantity Unit: Piece, Set, Pack, Pair, Dozen, Meter, Other.

Religion / Spiritual Tradition: Hindu, Buddhist, Muslim, Christian, Jain, Sikh, Kirat, Indigenous / Local Tradition, Interfaith, Spiritual / Meditation, Other.

## Subcategory Attributes

### 01 — Religious Statues & Idols

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-01-ATTR-001 | Deity / Figure | text | No | No | No | No | Free text |
| CAT-022-01-ATTR-002 | Tradition | text | No | No | No | No | Free text |
| CAT-022-01-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-01-ATTR-004 | Height | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-01-ATTR-005 | Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-01-ATTR-006 | Finish | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-01-ATTR-007 | Handmade | text | No | No | No | No | Free text |
| CAT-022-01-ATTR-008 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-022-01-ATTR-009 | Base / Stand Included | boolean | No | Yes | No | No | true / false |

### 02 — Puja & Worship Supplies

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-02-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-02-ATTR-002 | Ritual Use | text | No | No | No | No | Free text |
| CAT-022-02-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-02-ATTR-004 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-02-ATTR-005 | Tradition | text | No | No | No | No | Free text |
| CAT-022-02-ATTR-006 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-022-02-ATTR-007 | Included Components | boolean | No | Yes | No | Yes | true / false |
| CAT-022-02-ATTR-008 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Prayer & Meditation Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-03-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-03-ATTR-002 | Intended Practice | text | No | No | No | No | Free text |
| CAT-022-03-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-03-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-03-ATTR-005 | Portability | text | No | No | No | No | Free text |
| CAT-022-03-ATTR-006 | Handmade | text | No | No | No | No | Free text |
| CAT-022-03-ATTR-007 | Accessories | text | No | No | No | Yes | Free text |
| CAT-022-03-ATTR-008 | Suitable User Group | text | No | No | No | No | Free text |

### 04 — Religious Clothing & Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-04-ATTR-001 | Clothing / Accessory Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-04-ATTR-002 | Tradition | text | No | No | No | No | Free text |
| CAT-022-04-ATTR-003 | Gender / Target Group | text | No | No | No | Yes | Free text |
| CAT-022-04-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-04-ATTR-005 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-04-ATTR-006 | Color | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-04-ATTR-007 | Occasion | text | No | No | No | No | Free text |
| CAT-022-04-ATTR-008 | Handmade | text | No | No | No | No | Free text |

### 05 — Prayer Mats, Carpets & Floor Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-05-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-05-ATTR-002 | Tradition | text | No | No | No | No | Free text |
| CAT-022-05-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-05-ATTR-004 | Length | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-05-ATTR-005 | Width | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-05-ATTR-006 | Thickness | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-05-ATTR-007 | Pattern | text | No | No | No | No | Free text |
| CAT-022-05-ATTR-008 | Foldable | boolean | No | Yes | No | No | true / false |
| CAT-022-05-ATTR-009 | Washable | boolean | No | Yes | No | No | true / false |

### 06 — Rosaries, Mala & Prayer Beads

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-06-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-06-ATTR-002 | Tradition | text | No | No | No | No | Free text |
| CAT-022-06-ATTR-003 | Bead Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-06-ATTR-004 | Bead Count | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-06-ATTR-005 | Bead Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-06-ATTR-006 | String Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-06-ATTR-007 | Handmade | text | No | No | No | No | Free text |
| CAT-022-06-ATTR-008 | Pendant / Tassel Included | boolean | No | Yes | No | No | true / false |

### 07 — Incense, Lamps & Ritual Burning Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-07-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-07-ATTR-002 | Fuel / Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-07-ATTR-003 | Fragrance | text | No | No | No | No | Free text |
| CAT-022-07-ATTR-004 | Burn Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-07-ATTR-005 | Burn Time | text | No | No | No | No | Free text |
| CAT-022-07-ATTR-006 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-07-ATTR-007 | Reusable | boolean | No | Yes | No | No | true / false |
| CAT-022-07-ATTR-008 | Intended Use | text | No | No | No | No | Free text |

### 08 — Religious Vessels & Ritual Utensils

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-08-ATTR-001 | Vessel Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-08-ATTR-002 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-08-ATTR-003 | Capacity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-08-ATTR-004 | Capacity Unit | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-08-ATTR-005 | Ritual Use | text | No | No | No | No | Free text |
| CAT-022-08-ATTR-006 | Finish | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-08-ATTR-007 | Set Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-08-ATTR-008 | Handmade | text | No | No | No | No | Free text |

### 09 — Temple, Shrine & Home Altar Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-09-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-09-ATTR-002 | Tradition | text | No | No | No | No | Free text |
| CAT-022-09-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-09-ATTR-004 | Dimensions | text | No | No | No | No | Free text |
| CAT-022-09-ATTR-005 | Mounting / Placement Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-09-ATTR-006 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-022-09-ATTR-007 | Assembly Required | boolean | No | Yes | No | No | true / false |
| CAT-022-09-ATTR-008 | Included Components | boolean | No | Yes | No | Yes | true / false |

### 10 — Religious Flags, Banners & Symbols

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-10-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-10-ATTR-002 | Symbol / Design | text | No | No | No | No | Free text |
| CAT-022-10-ATTR-003 | Tradition | text | No | No | No | No | Free text |
| CAT-022-10-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-10-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-10-ATTR-006 | Indoor / Outdoor | text | No | No | No | No | Free text |
| CAT-022-10-ATTR-007 | Mounting Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-10-ATTR-008 | Weather Resistant | boolean | No | Yes | No | No | true / false |

### 11 — Festival & Cultural Celebration Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-11-ATTR-001 | Festival / Occasion | text | No | No | No | No | Free text |
| CAT-022-11-ATTR-002 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-11-ATTR-003 | Tradition / Community | text | No | No | No | No | Free text |
| CAT-022-11-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-11-ATTR-005 | Theme | text | No | No | No | No | Free text |
| CAT-022-11-ATTR-006 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-022-11-ATTR-007 | Reusable / Disposable | boolean | No | Yes | No | No | true / false |
| CAT-022-11-ATTR-008 | Intended Use | text | No | No | No | No | Free text |

### 12 — Traditional & Cultural Handicrafts

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-12-ATTR-001 | Craft Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-12-ATTR-002 | Cultural / Regional Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-12-ATTR-003 | Maker | text | No | No | No | No | Free text |
| CAT-022-12-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-12-ATTR-005 | Handmade | text | No | No | No | No | Free text |
| CAT-022-12-ATTR-006 | Technique | text | No | No | No | No | Free text |
| CAT-022-12-ATTR-007 | Dimensions | text | No | No | No | No | Free text |
| CAT-022-12-ATTR-008 | Intended Use | text | No | No | No | No | Free text |

### 13 — Spiritual & Meditation Equipment

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-13-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-13-ATTR-002 | Meditation / Practice Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-13-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-13-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-13-ATTR-005 | Power Source | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-13-ATTR-006 | Portable | boolean | No | Yes | No | No | true / false |
| CAT-022-13-ATTR-007 | Sound / Vibration Feature | text | No | No | No | No | Free text |
| CAT-022-13-ATTR-008 | Accessories | text | No | No | No | Yes | Free text |

### 14 — Cultural Musical Instruments

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-14-ATTR-001 | Instrument Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-14-ATTR-002 | Cultural / Regional Tradition | text | No | No | No | No | Free text |
| CAT-022-14-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-14-ATTR-004 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-14-ATTR-005 | Acoustic / Electronic | text | No | No | No | No | Free text |
| CAT-022-14-ATTR-006 | Skill Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-14-ATTR-007 | Handmade | text | No | No | No | No | Free text |
| CAT-022-14-ATTR-008 | Accessories / Case | text | No | No | No | Yes | Free text |

### 15 — Religious Gift & Devotional Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-15-ATTR-001 | Gift Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-15-ATTR-002 | Tradition | text | No | No | No | No | Free text |
| CAT-022-15-ATTR-003 | Occasion | text | No | No | No | No | Free text |
| CAT-022-15-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-15-ATTR-005 | Theme | text | No | No | No | No | Free text |
| CAT-022-15-ATTR-006 | Customizable | text | No | No | No | No | Free text |
| CAT-022-15-ATTR-007 | Packaging Included | boolean | No | Yes | No | No | true / false |
| CAT-022-15-ATTR-008 | Recipient Group | text | No | No | No | No | Free text |

### 16 — Other Religious, Spiritual & Cultural Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-022-16-ATTR-001 | Product Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-16-ATTR-002 | Tradition / Cultural Context | text | No | No | No | No | Free text |
| CAT-022-16-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-16-ATTR-004 | Intended Use | text | No | No | No | No | Free text |
| CAT-022-16-ATTR-005 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-022-16-ATTR-006 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange, Wanted, Free (limited), Rent (limited), Offer. Lease is not ordinary. Service and Job are not applicable.

## Implementation Rules

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