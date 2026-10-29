# PinkTaxWatch — Open Data

> ⚠️ **Status (October 2026):** The website [pinktaxwatch.com](https://pinktaxwatch.com) is currently offline while it is being updated.

📊 **License:** Data CC-BY-4.0 · Code MIT
📌 **Latest edition:** 2026-06 (Snapshot One) · Methodology v1.0
🌍 **Coverage:** 9 European markets · 60 retailer observations

This repository holds the open, auditable documentation behind the **European Menstrual Affordability Index**. The index is a cross-country measure of what menstrual essentials cost relative to net income across nine observed European markets.

---

## What PinkTaxWatch measures

The **Affordability Index** is a single comparable figure: the cost of a standardised monthly basket of essential menstrual products, expressed as a share of net monthly income in each observed market.

Results are reported in three forms:

| Metric | What it shows |
|---|---|
| **% of monthly salary** | Headline affordability metric |
| **Hours of work per year** | Annual time-cost equivalent at typical working hours |
| **Lifetime cost (39-year cohort)** | Cumulative cost across a standard reproductive span |

**Lifetime cost assumptions:** 39 years, from menarche (~age 12) to menopause (~age 51), at 13 cycles per year, which gives ≈ 507 cycles in total.

---

## Observed markets

United Kingdom · Ireland · Belgium · Germany · Austria · Hungary · Czech Republic · Netherlands · Denmark

A market is added only when every upstream source covers it reliably.

---

## Methodology in one sentence

> **Affordability Index = Monthly basket price (VAT-inclusive) ÷ Net monthly income × 100**

The basket is the same in every observed market: 20 pads + 20 tampons, priced at the cheapest recorded own-brand unit price per market. Prices are observed at mainstream retail and converted to EUR using ECB reference rates.

Income normalisation uses the total-population net monthly wage (Eurostat `earn_nt_net`, Family Case A1). A female-only wage series is deliberately not used, so that the gender pay gap is not folded into the affordability index itself.

---

## Reproducing a snapshot

1. Take the recorded retail observations for the edition: country, retailer, product, pack format, units per pack, sticker price, currency, observation date, brand type, confidence tier.
2. Convert each product to a per-unit price (pack price ÷ unit count).
3. Build the basket from 20 pads + 20 tampons at the cheapest own-brand unit price per market.
4. Convert non-EUR prices using the end-of-month ECB reference rate for the snapshot month.
5. Divide by the net monthly wage (Eurostat `earn_nt_net`, Family Case A1, latest harmonised release) and multiply by 100.

Retail prices are collected manually and checked against the source retailer listing. No automated scraping is used. Published snapshots are frozen, and each one will be versioned in this repository once the data files are released.

---

## Upstream sources

The index does not generate primary data. It aggregates, normalises, and presents data from four source types:

| Source | Used for | Dataset / reference |
|---|---|---|
| **Eurostat** | Net monthly income | `earn_nt_net` (Family Case A1) |
| **European Commission TEDB** | Standard VAT rates and sanitary product classification | TEDB live database |
| **European Central Bank** | EUR reference exchange rates | ECB FX reference rates |
| **Retail observations** | Own-brand menstrual product pricing at major retailers | Manually collected and validated |

Each snapshot is timestamped against the date of every upstream source it uses.

---

## Planned cadence (once the project resumes)

- **Per snapshot:** retail basket observations, ECB FX conversion, publication
- **Quarterly:** TEDB VAT rate audit
- **Annual:** Eurostat income data refresh
- **As needed:** VAT change log, updated when a member state changes a rate

---

## Roadmap

- [ ] Bring the website back online with the updated data layer
- [ ] Publish Snapshot One data files in this repository
- [ ] Publish pipeline code (collection, normalisation, index calculation)
- [ ] Snapshot Two with expanded product coverage
- [ ] Change tracking between snapshots
- [ ] Expand market coverage beyond the initial nine
- [ ] Machine-readable API / stable data URLs

---

## License

- **Data:** [Creative Commons Attribution 4.0 International (CC-BY-4.0)](https://creativecommons.org/licenses/by/4.0/). Free to use, share, and adapt for any purpose, including commercially, with attribution.
- **Code:** [MIT License](https://opensource.org/licenses/MIT), applied as code is published (see Roadmap).

---

## Citation

If you use PinkTaxWatch data in research, journalism, or analysis, please cite:

> PinkTaxWatch (2026). *European Menstrual Affordability Index, 2026-06 snapshot*. Methodology v1.0. https://github.com/PinkTaxWatch/pinktaxwatch-data

---

## Contributing & contact

- **Data corrections, source flags, methodology questions:** [open an Issue](https://github.com/PinkTaxWatch/pinktaxwatch-data/issues)
- **Editorial inquiries:** info@pinktaxwatch.eu

Every correction is checked against the upstream source before a published snapshot is amended, and amendments are recorded in the changelog.

---

*PinkTaxWatch is an independent, non-commercial public-interest project. It is not affiliated with any retailer, tax authority, or advocacy organisation referenced in the dataset.*
