# CAT-005 — Fashion & Clothing — Detailed Catalogue

**Project:** KHOJ BHET

**Catalogue ID:** CAT-005

**Status:** APPROVED — 2026-09-28

**Version:** 1.0

**Owner:** KHOJ BHET Product & Engineering

**Last Reviewed:** 2026-09-28

**Parent:** 13.1 Category & Attribute Catalogue

## 1. Subcategories

- CAT-005-01 Men's Clothing
- CAT-005-02 Women's Clothing
- CAT-005-03 Kids' Clothing
- CAT-005-04 Traditional & Ethnic Wear
- CAT-005-05 Footwear
- CAT-005-06 Fashion Bags & Wallets
- CAT-005-07 Watches
- CAT-005-08 Jewelry & Accessories
- CAT-005-09 Wedding & Occasion Wear
- CAT-005-10 Sportswear & Activewear
- CAT-005-11 Baby & Infant Clothing
- CAT-005-12 Uniforms & Workwear
- CAT-005-13 Fashion Accessories
- CAT-005-14 Other Fashion & Clothing

## 2. Common Fashion & Clothing Attributes

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

## 3. Subcategory Attributes

### CAT-005-01 Men's Clothing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| MEN-001 | Clothing Type | select | Yes | Yes | Yes | No | Shirt, T-Shirt, Polo Shirt, Pants, Jeans, Trousers, Shorts, Jacket, Coat, Sweater, Hoodie, Blazer, Suit, Kurta, Daura Suruwal, Vest, Underwear, Other |
| MEN-002 | Sleeve Type | select | No | Yes | Yes | No |  |
| MEN-003 | Fit Type | select | No | Yes | Yes | No | Slim, Regular, Relaxed, Oversized, Other |
| MEN-004 | Collar Type | select | No | Yes | Yes | No |  |
| MEN-005 | Occasion | select | No | Yes | No | Yes | Casual, Formal, Office, Party, Wedding, Traditional, Sports, Other |

</table>

### CAT-005-02 Women's Clothing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| WOMEN-001 | Clothing Type | select | Yes | Yes | Yes | No | Saree, Kurta, Kurti, Salwar Suit, Lehenga, Dress, Gown, Blouse, Top, T-Shirt, Shirt, Jeans, Pants, Skirt, Jacket, Coat, Sweater, Hoodie, Shawl, Other |
| WOMEN-002 | Sleeve Type | select | No | Yes | Yes | No |  |
| WOMEN-003 | Fit Type | select | No | Yes | Yes | No | Slim, Regular, Relaxed, Oversized, Other |
| WOMEN-004 | Length Type | select | No | Yes | Yes | No | Crop, Waist, Hip, Knee, Midi, Ankle, Full Length, Other |
| WOMEN-005 | Occasion | select | No | Yes | No | Yes |  |

</table>

### CAT-005-03 Kids' Clothing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| KIDS-001 | Clothing Type | select | Yes | Yes | Yes | No | T-Shirt, Shirt, Pants, Jeans, Shorts, Dress, Skirt, Frock, Kurta, Jacket, Sweater, Hoodie, School Wear, Other |
| KIDS-002 | Age Range | select | No | Yes | No | No |  |
| KIDS-003 | Size | select | No | Yes | No | No |  |
| KIDS-004 | Occasion | select | No | Yes | No | Yes |  |
| KIDS-005 | Gender | select | No | Yes | No | No |  |

</table>

### CAT-005-04 Traditional & Ethnic Wear

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ETHNIC-001 | Wear Type | select | Yes | Yes | Yes | No | Saree, Daura Suruwal, Kurta Suruwal, Dhoti, Lehenga, Sherwani, Kurti, Salwar Suit, Tharu Wear, Maithili Wear, Newari Wear, Other |
| ETHNIC-002 | Cultural / Regional Style | select | No | Yes | Yes | Yes |  |
| ETHNIC-003 | Embroidery | boolean | No | Yes | No | No | true / false |
| ETHNIC-004 | Handmade | boolean | No | Yes | No | No | true / false |
| ETHNIC-005 | Occasion | select | No | Yes | No | Yes |  |

</table>

### CAT-005-05 Footwear

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| FOOT-001 | Footwear Type | select | Yes | Yes | Yes | No | Sports Shoes, Running Shoes, Sneakers, Formal Shoes, Sandals, Slippers, Boots, Heels, Flats, Loafers, School Shoes, Safety Shoes, Traditional Footwear, Other |
| FOOT-002 | Size | select | Yes | Yes | No | No |  |
| FOOT-003 | Gender | select | No | Yes | No | No |  |
| FOOT-004 | Sole Material | select | No | Yes | No | No |  |
| FOOT-005 | Closure Type | select | No | Yes | Yes | No | Lace, Velcro, Buckle, Slip-on, Zip, Other |
| FOOT-006 | Waterproof | boolean | No | Yes | No | No | true / false |

</table>

### CAT-005-06 Fashion Bags & Wallets

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| BAG-001 | Bag Type | select | Yes | Yes | Yes | No | Backpack, Handbag, Shoulder Bag, Sling Bag, Laptop Bag, School Bag, Wallet, Purse, Briefcase, Sports Bag, Other |
| BAG-002 | Material | select | No | Yes | No | No |  |
| BAG-003 | Capacity | decimal | No | Yes | No | No |  |
| BAG-004 | Capacity Unit | select | No | Yes | No | No |  |
| BAG-005 | Number of Compartments | integer | No | Yes | No | No |  |
| BAG-006 | Waterproof | boolean | No | Yes | No | No | true / false |

</table>

### CAT-005-07 Watches

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| WATCH-001 | Watch Type | select | Yes | Yes | Yes | No | Analog, Digital, Smartwatch, Chronograph, Luxury, Sports, Other |
| WATCH-002 | Movement | select | No | Yes | No | No | Quartz, Mechanical, Automatic, Solar, Other |
| WATCH-003 | Display Type | select | No | Yes | Yes | No | Analog, Digital, Analog-Digital |
| WATCH-004 | Strap Material | select | No | Yes | No | No |  |
| WATCH-005 | Water Resistance | boolean | No | Yes | No | No | true / false |
| WATCH-006 | Smart Features | multi_select | No | Yes | No | Yes | Bluetooth, GPS, Heart Rate, Fitness Tracking, Calling, Notifications, Sleep Tracking, Other |

</table>

### CAT-005-08 Jewelry & Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| JEW-001 | Jewelry Type | select | Yes | Yes | Yes | No | Ring, Necklace, Chain, Bracelet, Bangle, Earrings, Pendant, Anklet, Brooch, Nose Ring, Traditional Jewelry, Other |
| JEW-002 | Material | select | No | Yes | No | No |  |
| JEW-003 | Gemstone | select | No | Yes | No | Yes |  |
| JEW-004 | Purity | select | No | Yes | No | No | 24K, 22K, 18K, 14K, 10K, Other |
| JEW-005 | Handmade | boolean | No | Yes | No | No | true / false |
| JEW-006 | Certificate Available | boolean | No | Yes | No | No | true / false |

</table>

### CAT-005-09 Wedding & Occasion Wear

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| OCC-001 | Wear Type | select | Yes | Yes | Yes | No | Wedding Dress, Lehenga, Saree, Sherwani, Suit, Gown, Party Dress, Traditional Wear, Other |
| OCC-002 | Gender | select | No | Yes | No | No |  |
| OCC-003 | Occasion | select | No | Yes | No | Yes | Wedding, Engagement, Reception, Festival, Party, Formal Event, Traditional Ceremony, Other |
| OCC-004 | Embroidery | boolean | No | Yes | No | No | true / false |
| OCC-005 | Custom Made | boolean | No | Yes | No | No | true / false |
| OCC-006 | Rental Available | boolean | No | Yes | No | No | true / false |

</table>

### CAT-005-10 Sportswear & Activewear

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SPORT-001 | Sportswear Type | select | Yes | Yes | Yes | No | Jersey, Tracksuit, Shorts, Sports T-Shirt, Sports Shoes, Compression Wear, Sports Jacket, Other |
| SPORT-002 | Sport | select | No | Yes | No | Yes |  |
| SPORT-003 | Size | select | No | Yes | No | No |  |
| SPORT-004 | Gender | select | No | Yes | No | No |  |
| SPORT-005 | Team / Club | text | No | Yes | No | No |  |

</table>

### CAT-005-11 Baby & Infant Clothing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| BABY-001 | Clothing Type | select | Yes | Yes | Yes | No | Bodysuit, Romper, Frock, T-Shirt, Pants, Jacket, Sweater, Sleepwear, Traditional Wear, Set, Other |
| BABY-002 | Age Range | select | No | Yes | No | No |  |
| BABY-003 | Size | select | No | Yes | No | No |  |
| BABY-004 | Gender | select | No | Yes | No | No |  |
| BABY-005 | Material | select | No | Yes | No | No |  |
| BABY-006 | Set Quantity | integer | No | Yes | No | No |  |

</table>

### CAT-005-12 Uniforms & Workwear

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UNI-001 | Uniform Type | select | Yes | Yes | Yes | No | School Uniform, College Uniform, Hospital Uniform, Security Uniform, Corporate Uniform, Industrial Workwear, Hospitality Uniform, Sports Uniform, Other |
| UNI-002 | Profession / Institution | select | No | Yes | No | No |  |
| UNI-003 | Size | select | No | Yes | No | No |  |
| UNI-004 | Gender | select | No | Yes | No | No |  |
| UNI-005 | Customization Available | boolean | No | Yes | No | No | true / false |
| UNI-006 | Bulk Quantity Available | integer | No | Yes | No | No |  |

</table>

### CAT-005-13 Fashion Accessories

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ACC-001 | Accessory Type | select | Yes | Yes | Yes | No | Belt, Tie, Scarf, Cap, Hat, Sunglasses, Gloves, Socks, Hair Accessories, Hair Clip, Headband, Wallet, Keychain, Other |
| ACC-002 | Material | select | No | Yes | No | No |  |
| ACC-003 | Gender | select | No | Yes | No | No |  |
| ACC-004 | Compatibility / Intended Use | text | No | No | Yes | No |  |

</table>

### CAT-005-14 Other Fashion & Clothing

| Attribute ID | Attribute | Data Type | Required | Filterable | Searchable | Multi-value | Options / Value Rule |
| --- | --- | --- | --- | --- | --- | --- | --- |

</table>

## 4. Listing-Type Applicability

- Clothing, Footwear, Fashion Bags & Wallets, Watches, Jewelry & Accessories, Sportswear, Baby Clothing, Uniforms & Workwear, Fashion Accessories, and Other Fashion: **Sale, Exchange, Wanted**.
- Wedding & Occasion Wear: **Sale, Exchange, Wanted, Rent**.
- Lease, Service, Job, and Offer are not initially exposed.

## 5. Implementation Rules

- Common fashion attributes inherit into applicable subcategories.
- Size is category-specific; footwear size is not treated as a generic clothing size.
- Jewelry purity and gemstone information apply only to relevant jewelry.
- Multi-value attributes create multiple attribute rows.
- Single-value attributes allow at most one value.
- Option-backed values must match valid catalogue options.
- Required/filterable/searchable/multi-value flags are authoritative.
- Seller-provided authenticity/originality claims are not independently verified merely because they are stored.

## Catalogue-Wide Effective Flag Policy — 2026-10-21

Apply the parent catalogue §46 as the effective flag policy across all 25 categories: Required = No by default; Filterable = Yes and Searchable = Yes by default. Search must respect the attribute data type (text matching for text, normalized exact matching for options/booleans, typed comparisons for numeric/date values). This policy supersedes legacy Filterable = No / Searchable = No cells in this page unless an explicit, documented technical exception is approved. Preserve each attribute's explicit type, multi-value behavior, and approved option set.