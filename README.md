# PinkTaxWatch — Open Data

> ⚠️ **Status (October 2026):** The website [pinktaxwatch.com](https://pinktaxwatch.com) is currently offline while it is being updated. All published data is available in this repository.

📌 **Edition:** 2026-06 · Methodology v1.0
🌍 **Coverage:** 9 European markets · 60 retail price observations · Hungarian deep-dive (pink tax, contraception, gynaecology)
📊 **License:** Data CC-BY-4.0 · Code MIT

PinkTaxWatch is an independent, bilingual (Hungarian–English) open price observatory. It measures what it costs to be a woman, starting with the price of menstrual products across Europe. We measure; we don't campaign.

---

## Contents

- [Key findings](#key-findings)
- [Data files](#data-files)
- [European menstrual basket](#european-menstrual-basket)
- [Hungary deep-dive](#hungary-deep-dive)
- [Anonymisation](#anonymisation)
- [Known limitations](#known-limitations)
- [Sources](#sources) · [License](#license) · [Citation](#citation) · [Contact](#contact)

---

## Key findings

- **Same basket, twice the price.** A month of own-brand menstrual products costs €2.21 in the UK and €4.72 in the Netherlands. Denmark, where no own-brand products were available, comes to €9.36 with international brands.
- **VAT varies from 0% to 27%.** The UK, Ireland, Belgium and Austria apply 0%. Hungary applies 27%, the highest rate in the EU.
- **No measurable pink tax in Hungarian drugstores.** Across 22 matched women's and men's personal-care product pairs, the median unit-price difference is **0%**. 32% of pairs are dearer for women, 45% show no meaningful difference (±2%), and 23% are cheaper.
- **Gynaecological screening is the expensive part.** A complete private screening basket (exam + cytology + HPV) in Budapest costs **52,400–77,000 Ft** across 7 providers.

---

## Data files

```
data/
├── europe/
│   ├── dataset-2026-06.csv               # 60 raw retail observations (source of truth)
│   ├── observations-2026-06.json         # same rows + unit prices and quality flags
│   └── country-summary-2026-06.json      # published per-country results
└── hungary/
    ├── pinktax-product-pairs-hu-2026-06.csv     # 48 rows, 24 matched F/M pairs
    ├── contraception-cost-hu-2026-06.csv        # 29 rows, 5 methods
    ├── womens-health-basket-hu-2026-06.csv      # 71 rows, 23 providers
    └── hungary-womens-cost-summary-2026-06.json # headline summary
```

Files carry a `-YYYY-MM` suffix. A published edition is frozen and is never overwritten: corrections go into a new file and are listed in the changelog.

---

## European menstrual basket

### Results

| Market | VAT on menstrual products | Monthly basket (€) | Lifetime (€) | Retailers | Observations | Confidence |
|---|---:|---:|---:|---:|---:|---|
| 🇬🇧 United Kingdom | 0% | 2.21 | 1,033 | 1 | 6 | Medium |
| 🇮🇪 Ireland | 0% | 2.65 | 1,239 | 1 | 6 | Medium |
| 🇧🇪 Belgium | 0% | 3.73 | 1,743 | 1 | 6 | Medium |
| 🇩🇪 Germany | 7% | 3.88 | 1,814 | 2 | 14 | High |
| 🇦🇹 Austria | 0% | 4.38 | 2,048 | 1 | 6 | Medium |
| 🇭🇺 Hungary | 27% | 4.38 | 2,050 | 1 | 5 | Medium |
| 🇨🇿 Czech Republic | 12% | 4.40 | 2,058 | 1 | 6 | Medium |
| 🇳🇱 Netherlands | 9% | 4.72 | 2,211 | 1 | 7 | Medium |
| 🇩🇰 Denmark ¹ | 25% | 9.36 | 4,379 | 1 | 4 | Medium |

¹ Denmark had no own-brand menstrual products on sale, so its basket uses international-brand products and is not directly comparable with the other markets.

### How the basket is built

- **Contents:** 20 pads + 20 tampons, representing one month.
- **Product:** a fixed, comparable own-brand product in every market (a normal winged pad + a normal applicator tampon), so the comparison is like-for-like across markets and over time.
- **Price:** standardised price = pack price ÷ units in pack × 20, VAT-inclusive shelf price.
- **Currency:** non-EUR prices are converted to EUR.
- **Lifetime cost:** monthly basket × 12 months × 39 years (menarche ~12 to menopause ~51).
- **Confidence:** *High* means several retailers were observed; *Medium* means a single retailer.

Income (Eurostat `earn_nt_net`, single worker, family case A1, annual ÷ 12) is used as a reference figure in the personal impact calculator. It is deliberately not a female-only wage series, so the gender pay gap is not folded into the price comparison.

### Field reference: `dataset-2026-06.csv`

| Column | Meaning |
|---|---|
| `country` | Market code |
| `retailer` | Anonymised retailer code, e.g. `DE-DR1` (drugstore 1), `UK-GR1` (grocery 1) |
| `product_category` | `pad` / `tampon` |
| `product_type` | `own_brand`, `international_brand`, `international_brand_fallback` (DK) |
| `search_keyword` | Standardised product description (absorbency, format) |
| `darab` | Pack size (`16 ct` = 16 units) |
| `ar_local` / `ar_eur` | Shelf price in local currency / EUR |
| `notes` | Observation notes (e.g. `cotton_variant`) |

`observations-2026-06.json` adds `unit_price_eur`, `standardized_price_eur`, `data_quality` (`observed` / `carried_forward`) and `availability` (`in_stock` / `oos_price_shown`).

---

## Hungary deep-dive

*"A női lét ára Magyarországon"*: measurable extra costs for women in Hungary. All prices are in HUF and were collected on 2026-06-10.

### Pink tax: matched product pairs

Women's and men's versions of the same product type at the same drugstore, compared on unit price (Ft/unit or Ft/100 ml).

| Category | Valid pairs | Median premium for women |
|---|---:|---:|
| Razors | 5 | +0.7% |
| Shower gel | 5 | −1.6% |
| Deodorant | 4 | 0% * |
| Shaving products | 4 | +8.8% * |
| Shampoo | 4 | 0% * |
| **All categories** | **22** | **0%** |

\* Fewer than 5 valid pairs: shown for transparency, but not published as a category finding.

Rows marked `substitute` (format or tier mismatch) stay in the file but are excluded from the premium calculation.

### Contraception

29 price observations across five methods (pill, hormonal IUD, copper IUD, condom, emergency). The annual cost of the pill ranges from **37,076 to 61,295 Ft** (6 clean observations). Annual cost = cost per 28-day cycle × 13.

### Gynaecological screening

71 service prices from 23 named providers in Budapest and other regions (*vidék*). Prices from insurance-based networks are kept as a separate band and are never mixed with private (*magán*) prices.

| Scope | Complete baskets | Price range |
|---|---:|---|
| Budapest, private (exam + cytology + HPV) | 7 | 52,400–77,000 Ft |

### Field notes

- `confidence`: `clean` = directly comparable observed price · `substitute` = format/tier mismatch, excluded from calculations · `modelled` = computed value, not a shelf price
- `match_pair_id`: links the F and M rows of a pair (e.g. `razor-01`)
- `unit_price_huf`: Ft per unit for `unit=db` rows, Ft per 100 ml for `unit=ml` rows
- `price_type`: `magan` (private) or `biztositas-alapu` (insurance-based)
- `basket_complete`: `true` only when exam, cytology and HPV are all itemised

---

## Anonymisation

A two-tier rule applies throughout:

- **Retailers and pharmacies are anonymised.** They appear only as coded labels (`DE-DR1`, `Drogéria A`, `Patika B`) with no source URLs. The product is the unit of measurement, not the shop. Brand names are product attributes and remain visible.
- **Health providers are named.** Gynaecology rows carry the provider's real name and a link to its published price list, because these are public service prices and attribution is what makes them verifiable.

Prices were collected by hand from retailer and provider websites and checked against the original listing. No automated scraping was used.

---

## Known limitations

We publish these openly rather than smoothing them over.

- **Carried-forward prices.** Five rows were not observed in June and were carried forward from the previous collection (`data_quality = carried_forward`). One of these is the tampon leg of the **Hungarian basket**. The others are two DE-DR2 rows and the two Hungarian international-brand rows.
- **Denmark** uses international-brand products, and no normal applicator tampon was available. Its basket is therefore an approximation and should not be ranked alongside the own-brand markets.
- **Netherlands:** the published €4.72 comes from floating-point rounding. Rounding the raw data half-up gives €4.73.
- **Exchange rates** were applied at collection time, but the rate used is not stored per row. `ar_eur` is the converted value.
- **Single-retailer coverage:** eight of nine markets rest on one retailer, which is why they are rated *Medium* confidence.
- **International-brand baskets** are recorded as observations but not published as summary figures (`null` in the country summary).
- **Hungarian period basket:** the HUF observation series is still being collected, so `period_monthly_basket_huf` is `null` in the summary.

---

## Sources

| Source | Used for |
|---|---|
| Retail observations | Menstrual product and personal-care prices (anonymised) |
| Provider price lists | Gynaecological service prices (named, linked) |
| European Commission TEDB | VAT rates on menstrual products |
| Eurostat `earn_nt_net` | Net earnings reference (single worker, case A1) |
| European Central Bank | EUR reference exchange rates |

---

## License

- **Data:** [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/). You are free to use, share and adapt it for any purpose, including commercially, with attribution.
- **Code:** [MIT](https://opensource.org/licenses/MIT), as it is published.

## Citation

> PinkTaxWatch (2026). *European Menstrual Affordability Index and Hungary women's cost data, 2026-06 edition*. Methodology v1.0. https://github.com/PinkTaxWatch/pinktaxwatch-data

## Contact

- **Data corrections, source flags, methodology questions:** [open an Issue](https://github.com/PinkTaxWatch/pinktaxwatch-data/issues)
- **Editorial inquiries:** info@pinktaxwatch.eu

Every correction is checked against the original source before a published edition is amended.

---

*PinkTaxWatch is an independent, non-commercial public-interest project. It is not affiliated with any retailer, tax authority, health provider or advocacy organisation referenced in the dataset.*
