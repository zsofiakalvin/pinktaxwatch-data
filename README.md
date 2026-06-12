# PinkTaxWatch — Open Data Pipeline

🔗 **Live site:** [pinktaxwatch.com](https://pinktaxwatch.com)
📊 **License:** Data CC-BY-4.0 · Code MIT
🗓️ **Cadence:** Monthly snapshots, published on the 17th
📌 **Current edition:** 2026-06 · Methodology v1.0
🌍 **Coverage:** 9 European markets · 60 retailer observations

Open, auditable data behind the **European Menstrual Affordability Index** — a monthly cross-country measure of how much menstrual essentials cost relative to net income across nine observed European markets.

This repository documents the methodology, upstream sources, and licensing for the public index. Every figure on the live site is reproducible from publicly available data using the formula and source mapping below.

---

## What PinkTaxWatch measures

PinkTaxWatch publishes a monthly **Affordability Index** — a single comparable figure expressing the cost of a standardised monthly basket of essential menstrual products as a share of net monthly income in each observed European market.

Results are reported in three forms:

| Metric | What it shows |
|---|---|
| **% of monthly salary** | Headline affordability metric |
| **Hours of work per year** | Annual time-cost equivalent at typical working hours |
| **Lifetime cost (39-year cohort)** | Cumulative real-terms cost across a standard reproductive span |

**Lifetime cost assumption set:** 39 years from menarche (~age 12) to menopause (~age 51), 13 cycles per year, ≈ 507 cycles total. See the [methodology page](https://www.pinktaxwatch.com/data-observatory) for full derivation.

---

## Observed markets

United Kingdom · Ireland · Belgium · Germany · Austria · Hungary · Czech Republic · Netherlands · Denmark

Markets are added when all upstream sources provide reliable coverage. See [Roadmap](#roadmap) for planned expansion.

---

## Methodology in one sentence

> **Affordability Index = Monthly basket price (VAT-inclusive) ÷ Net monthly income × 100**

The basket is standardised across all observed markets: 20 pads + 20 tampons, calculated from the cheapest recorded own-brand unit price per market, observed at mainstream retail and converted to EUR using ECB reference rates.

Income normalisation uses the total-population net monthly wage (Eurostat `earn_nt_net`, Family Case A1) — deliberately not a female-only wage series, to avoid folding the gender pay gap into the affordability index itself. Full derivation, confidence tiers, and known limitations: [methodology page](https://www.pinktaxwatch.com/data-observatory).

---

## Reproducing a snapshot

1. Take the recorded retail observations for the edition (country, retailer, product, pack format, units per pack, sticker price, currency, observation date, brand type, confidence tier)
2. Convert each product to a per-unit price (pack price ÷ unit count)
3. Build the basket: 20 pads + 20 tampons at the cheapest own-brand unit price per market
4. Convert non-EUR prices using the end-of-month ECB reference rate for the snapshot month
5. Divide by the net monthly wage (Eurostat `earn_nt_net`, Family Case A1, latest harmonised release) and multiply by 100

Every snapshot is versioned and frozen; older snapshots remain downloadable so reproducibility is preserved. Every row is validated against the source retailer listing and reviewed by a second observer before publication.

---

## Upstream sources

The index does not generate primary data. It aggregates, normalises, and presents data from four source types:

| Source | Used for | Dataset / reference |
|---|---|---|
| **Eurostat** | Net monthly income | `earn_nt_net` (Family Case A1) |
| **European Commission TEDB** | Standard VAT rates and sanitary product classification | TEDB live database |
| **European Central Bank** | EUR reference exchange rates | ECB FX reference rates |
| **Retail observations** | Own-brand menstrual product pricing at major retailers | Curated monthly, manually validated |

Every monthly snapshot is timestamped against the snapshot date of each upstream source.

---

## Update cadence

- **Monthly** — retail basket observations, ECB FX conversion, snapshot publication (17th of each month)
- **Quarterly** — TEDB VAT rate audit
- **Annual** — Eurostat income data refresh
- **Continuous** — VAT change log updated whenever a member state changes a rate

---

## Roadmap

- [ ] Publish pipeline code (collection, normalisation, index calculation)
- [ ] Expand market coverage beyond the initial nine
- [ ] Month-over-month change tracking (from Snapshot Two onward)
- [ ] Machine-readable API / stable data URLs

---

## License

- **Data** — published under [Creative Commons Attribution 4.0 International (CC-BY-4.0)](https://creativecommons.org/licenses/by/4.0/). Free to use, share, and adapt for any purpose, including commercially, with attribution.
- **Code** — released under the [MIT License](https://opensource.org/licenses/MIT) as it is published (see Roadmap).

---

## Citation

If you use PinkTaxWatch data in research, journalism, or analysis, please cite as:

> PinkTaxWatch (2026). *European Menstrual Affordability Index, 2026-06 snapshot*. Methodology v1.0. https://github.com/PinkTaxWatch/pinktaxwatch-data

See also: [pinktaxwatch.com/cite](https://www.pinktaxwatch.com/cite)

---

## Contributing & contact

- **Data corrections, source flags, methodology questions:** [open an Issue](https://github.com/PinkTaxWatch/pinktaxwatch-data/issues)
- **Project site:** [pinktaxwatch.com](https://pinktaxwatch.com)
- **Editorial inquiries:** [info@pinktaxwatch.eu](mailto:info@pinktaxwatch.eu)

Corrections are reviewed against the upstream source before any published snapshot is amended; amendments are recorded in the changelog.

---

*PinkTaxWatch is an independent, non-commercial public-interest project. Not affiliated with any retailer, tax authority, or advocacy organisation referenced in the dataset.*
