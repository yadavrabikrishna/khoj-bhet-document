# CAT-012 — Books, Media & Collectibles — Detailed Catalogue

**Catalogue ID:** CAT-012

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

## Subcategories

| Subcategory ID | Subcategory | Scope |
| --- | --- | --- |
| CAT-012-01 | Books &amp; Novels | Primary catalogue scope for this subcategory. |
| CAT-012-02 | Academic &amp; Educational Books | Primary catalogue scope for this subcategory. |
| CAT-012-03 | Religious &amp; Spiritual Books | Primary catalogue scope for this subcategory. |
| CAT-012-04 | Magazines, Newspapers &amp; Periodicals | Primary catalogue scope for this subcategory. |
| CAT-012-05 | Comics &amp; Graphic Novels | Primary catalogue scope for this subcategory. |
| CAT-012-06 | Music &amp; Audio Media | Primary catalogue scope for this subcategory. |
| CAT-012-07 | Movies &amp; Video Media | Primary catalogue scope for this subcategory. |
| CAT-012-08 | Collectibles | Primary catalogue scope for this subcategory. |
| CAT-012-09 | Antiques &amp; Vintage Items | Primary catalogue scope for this subcategory. |
| CAT-012-10 | Coins &amp; Currency Collectibles | Primary catalogue scope for this subcategory. |
| CAT-012-11 | Stamps &amp; Postal Collectibles | Primary catalogue scope for this subcategory. |
| CAT-012-12 | Art, Prints &amp; Posters | Primary catalogue scope for this subcategory. |
| CAT-012-13 | Trading Cards &amp; Memorabilia | Primary catalogue scope for this subcategory. |
| CAT-012-14 | Musical Instruments &amp; Accessories | Primary catalogue scope for this subcategory. |
| CAT-012-15 | Hobby &amp; Craft Collections | Primary catalogue scope for this subcategory. |
| CAT-012-16 | Other Books, Media &amp; Collectibles | Primary catalogue scope for this subcategory. |

## Common Attributes

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value |
| --- | --- | --- | --- | --- | --- | --- |
| MEDIA-ATTR-001 | Item Type | select | Yes | Yes | Yes | No |
| MEDIA-ATTR-002 | Title / Name | text | Yes | Yes | Yes | No |
| MEDIA-ATTR-003 | Author / Creator / Artist | text | No | No | No | Yes |
| MEDIA-ATTR-004 | Publisher / Manufacturer | text | No | No | No | No |
| MEDIA-ATTR-005 | Condition | select | Yes | Yes | No | No |
| MEDIA-ATTR-006 | Year / Publication Year | integer | No | Yes | No | No |
| MEDIA-ATTR-007 | Edition | text | No | No | No | No |
| MEDIA-ATTR-008 | Language | select | No | Yes | Yes | Yes |
| MEDIA-ATTR-009 | ISBN / Catalog Number | text | No | No | No | No |
| MEDIA-ATTR-010 | Material / Format | select | No | Yes | No | No |
| MEDIA-ATTR-011 | Quantity | integer | No | Yes | No | No |
| MEDIA-ATTR-012 | Signed / Autographed | boolean | No | Yes | No | No |
| MEDIA-ATTR-013 | Original / Authenticity Status | select | No | Yes | No | No |
| MEDIA-ATTR-014 | Certificate / Documentation | boolean | No | Yes | No | No |
| MEDIA-ATTR-015 | Seller Notes | text | No | No | No | No |

## Controlled Values

Condition: New, Like New, Good, Fair, Poor, Damaged, Restored, Used.

Language: Nepali, Maithili, Bhojpuri, Hindi, English, Urdu, Newari, Sanskrit, Other.

Authenticity Status: Original, Reproduction, Replica, Reprint, Unknown, Not Applicable.

## Subcategory Attributes

### 01 — Books & Novels

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-01-ATTR-001 | Genre | text | No | No | No | No | Free text |
| CAT-012-01-ATTR-002 | Author | text | No | No | No | No | Free text |
| CAT-012-01-ATTR-003 | Publisher | text | No | No | No | No | Free text |
| CAT-012-01-ATTR-004 | Edition | text | No | No | No | No | Free text |
| CAT-012-01-ATTR-005 | ISBN | text | No | No | No | No | Free text |
| CAT-012-01-ATTR-006 | Publication Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-01-ATTR-007 | Pages | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-01-ATTR-008 | Binding Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-01-ATTR-009 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 02 — Academic & Educational Books

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-02-ATTR-001 | Subject | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-02-ATTR-002 | Grade / Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-02-ATTR-003 | Curriculum | text | No | No | No | No | Free text |
| CAT-012-02-ATTR-004 | Academic Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-02-ATTR-005 | Edition | text | No | No | No | No | Free text |
| CAT-012-02-ATTR-006 | Publisher | text | No | No | No | No | Free text |
| CAT-012-02-ATTR-007 | ISBN | text | No | No | No | No | Free text |
| CAT-012-02-ATTR-008 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |

### 03 — Religious & Spiritual Books

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-03-ATTR-001 | Religion / Tradition | text | No | No | No | No | Free text |
| CAT-012-03-ATTR-002 | Text Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-03-ATTR-003 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-03-ATTR-004 | Author / Translator | text | No | No | No | No | Free text |
| CAT-012-03-ATTR-005 | Edition | text | No | No | No | No | Free text |
| CAT-012-03-ATTR-006 | Publisher | text | No | No | No | No | Free text |
| CAT-012-03-ATTR-007 | Script | text | No | No | No | No | Free text |

### 04 — Magazines, Newspapers & Periodicals

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-04-ATTR-001 | Publication Name | text | No | No | Yes | No | Free text |
| CAT-012-04-ATTR-002 | Issue Number | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-04-ATTR-003 | Publication Date | text | No | No | No | No | Free text |
| CAT-012-04-ATTR-004 | Frequency | text | No | No | No | No | Free text |
| CAT-012-04-ATTR-005 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-04-ATTR-006 | Publisher | text | No | No | No | No | Free text |
| CAT-012-04-ATTR-007 | Topic | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |

### 05 — Comics & Graphic Novels

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-05-ATTR-001 | Series | text | No | No | No | No | Free text |
| CAT-012-05-ATTR-002 | Volume | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-05-ATTR-003 | Issue Number | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-05-ATTR-004 | Character | text | No | No | No | No | Free text |
| CAT-012-05-ATTR-005 | Publisher | text | No | No | No | No | Free text |
| CAT-012-05-ATTR-006 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-05-ATTR-007 | Edition | text | No | No | No | No | Free text |
| CAT-012-05-ATTR-008 | Publication Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 06 — Music & Audio Media

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-06-ATTR-001 | Media Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-06-ATTR-002 | Artist | text | No | No | No | No | Free text |
| CAT-012-06-ATTR-003 | Album / Title | text | No | No | Yes | No | Free text |
| CAT-012-06-ATTR-004 | Genre | text | No | No | No | No | Free text |
| CAT-012-06-ATTR-005 | Format | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-06-ATTR-006 | Release Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-06-ATTR-007 | Number of Tracks | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-06-ATTR-008 | Original / Reissue | text | No | No | No | No | Free text |

### 07 — Movies & Video Media

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-07-ATTR-001 | Media Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-07-ATTR-002 | Title | text | No | No | Yes | No | Free text |
| CAT-012-07-ATTR-003 | Director | text | No | No | No | No | Free text |
| CAT-012-07-ATTR-004 | Genre | text | No | No | No | No | Free text |
| CAT-012-07-ATTR-005 | Language | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-07-ATTR-006 | Release Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-07-ATTR-007 | Format | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-07-ATTR-008 | Region | text | No | No | No | No | Free text |
| CAT-012-07-ATTR-009 | Edition | text | No | No | No | No | Free text |

### 08 — Collectibles

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-08-ATTR-001 | Collectible Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-08-ATTR-002 | Brand / Series | text | No | No | Yes | No | Free text |
| CAT-012-08-ATTR-003 | Collection | text | No | No | No | No | Free text |
| CAT-012-08-ATTR-004 | Production Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-08-ATTR-005 | Edition / Series Number | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-08-ATTR-006 | Rarity | text | No | No | No | No | Free text |
| CAT-012-08-ATTR-007 | Authenticity | text | No | No | No | No | Free text |
| CAT-012-08-ATTR-008 | Packaging | text | No | No | No | No | Free text |

### 09 — Antiques & Vintage Items

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-09-ATTR-001 | Item Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-09-ATTR-002 | Estimated Period | text | No | No | No | No | Free text |
| CAT-012-09-ATTR-003 | Origin | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-09-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-09-ATTR-005 | Maker / Artist | text | No | No | No | No | Free text |
| CAT-012-09-ATTR-006 | Restoration Status | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-09-ATTR-007 | Provenance / Documentation | text | No | No | No | No | Free text |
| CAT-012-09-ATTR-008 | Authenticity | text | No | No | No | No | Free text |

### 10 — Coins & Currency Collectibles

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-10-ATTR-001 | Country | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-10-ATTR-002 | Currency | text | No | No | No | No | Free text |
| CAT-012-10-ATTR-003 | Denomination | text | No | No | No | No | Free text |
| CAT-012-10-ATTR-004 | Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-10-ATTR-005 | Mint | text | No | No | No | No | Free text |
| CAT-012-10-ATTR-006 | Metal / Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-10-ATTR-007 | Grade / Condition | text | No | No | No | No | Free text |
| CAT-012-10-ATTR-008 | Serial Number | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-10-ATTR-009 | Commemorative | text | No | No | No | No | Free text |

### 11 — Stamps & Postal Collectibles

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-11-ATTR-001 | Country | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-11-ATTR-002 | Issue Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-11-ATTR-003 | Stamp Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-11-ATTR-004 | Denomination | text | No | No | No | No | Free text |
| CAT-012-11-ATTR-005 | Series | text | No | No | No | No | Free text |
| CAT-012-11-ATTR-006 | Perforation | text | No | No | No | No | Free text |
| CAT-012-11-ATTR-007 | Used / Unused | text | No | No | No | No | Free text |
| CAT-012-11-ATTR-008 | First Day Cover | text | No | No | No | No | Free text |
| CAT-012-11-ATTR-009 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |

### 12 — Art, Prints & Posters

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-12-ATTR-001 | Artwork Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-12-ATTR-002 | Artist | text | No | No | No | No | Free text |
| CAT-012-12-ATTR-003 | Medium | text | No | No | No | No | Free text |
| CAT-012-12-ATTR-004 | Subject | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-12-ATTR-005 | Dimensions | text | No | No | No | No | Free text |
| CAT-012-12-ATTR-006 | Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-12-ATTR-007 | Original / Print | text | No | No | No | No | Free text |
| CAT-012-12-ATTR-008 | Signed | text | No | No | No | No | Free text |
| CAT-012-12-ATTR-009 | Framed | text | No | No | No | No | Free text |

### 13 — Trading Cards & Memorabilia

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-13-ATTR-001 | Category | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-13-ATTR-002 | Player / Character | text | No | No | No | No | Free text |
| CAT-012-13-ATTR-003 | Team / Franchise | text | No | No | No | No | Free text |
| CAT-012-13-ATTR-004 | Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-13-ATTR-005 | Edition | text | No | No | No | No | Free text |
| CAT-012-13-ATTR-006 | Card / Item Number | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-13-ATTR-007 | Grading | text | No | No | No | No | Free text |
| CAT-012-13-ATTR-008 | Authenticity | text | No | No | No | No | Free text |
| CAT-012-13-ATTR-009 | Autographed | text | No | No | No | No | Free text |

### 14 — Musical Instruments & Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-14-ATTR-001 | Instrument Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-14-ATTR-002 | Brand | text | No | No | Yes | No | Free text |
| CAT-012-14-ATTR-003 | Model | text | No | No | Yes | No | Free text |
| CAT-012-14-ATTR-004 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-14-ATTR-005 | Size | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-14-ATTR-006 | Skill Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-14-ATTR-007 | Acoustic / Electric | boolean | No | Yes | No | No | true / false |
| CAT-012-14-ATTR-008 | Accessories | text | No | No | No | Yes | Free text |
| CAT-012-14-ATTR-009 | Case Included | boolean | No | Yes | No | No | true / false |

### 15 — Hobby & Craft Collections

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-15-ATTR-001 | Hobby Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-15-ATTR-002 | Collection Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-15-ATTR-003 | Material | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-15-ATTR-004 | Skill Level | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-15-ATTR-005 | Quantity | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-15-ATTR-006 | Complete / Partial Set | text | No | No | No | No | Free text |
| CAT-012-15-ATTR-007 | Accessories | text | No | No | No | Yes | Free text |
| CAT-012-15-ATTR-008 | Storage / Packaging | text | No | No | No | No | Free text |

### 16 — Other Books, Media & Collectibles

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CAT-012-16-ATTR-001 | Item Type | select | No | Yes | Yes | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-16-ATTR-002 | Creator / Maker | text | No | No | No | No | Free text |
| CAT-012-16-ATTR-003 | Year | decimal | No | Yes | No | No | Numeric value; unit separate where applicable |
| CAT-012-16-ATTR-004 | Material / Format | select | No | Yes | No | No | RESOLVED — Phase 3B Option Registry §43 |
| CAT-012-16-ATTR-005 | Intended Use | text | No | No | No | No | Free text |
| CAT-012-16-ATTR-006 | Key Features | text | No | No | No | Yes | Free text |

Sale, Exchange, Wanted, Free. Rent may apply to limited reusable items. Lease and Job are not applicable. Service is not applicable. Offer may be used where explicitly modeled.

## Implementation Rules

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