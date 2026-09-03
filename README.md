# E-commerce Discount Strategy Analysis — Eniac

Data analysis project for WBS Coding School, evaluating whether Eniac's discounting strategy helps or hurts the business.

## 🎯 Project Overview

Eniac, an e-commerce tech retailer, is debating whether discounting products is good for the business. Marketing believes discounts drive customer acquisition and growth; the Board is worried that recent quarters show rising order volume but falling revenue, and prefers a quality-segment positioning over competing on price. Using Python (pandas, matplotlib/seaborn) on ~2 years of internal order data, we cleaned a corrupted dataset, built a product category taxonomy, and analyzed discount depth, seasonality, and category-level revenue to settle the debate.

**Bottom line: discounts are working, and they are not the aggressive kind the Board feared.**

## 📊 Dataset & Sources

- **Source:** Internal Eniac data (not public — provided for the WBS Coding School exercise; not included in this repo, see `data/raw/`)
- **Files:** `orders.csv`, `orderlines.csv`, `products.csv`, `brands.csv`
- **Period:** ~January 2017 – March 2018
- **Key features:** order state and totals, per-line unit price and quantity, product base/promo price, brand, and product category
- **Data quality:** the raw data was corrupted — missing values, wrong datatypes, duplicate rows, and inconsistent encodings. A full data quality assessment and cleaning pass was required before analysis (see `notebooks/01_data_cleaning.ipynb` and `notebooks/02_quality_assessment.ipynb`) and its limitations are documented there.

## 🚀 Key Findings & Results

- **Discounting is the norm, not the exception:** between 81% and 97% of order lines were sold at a discount every single month of the period, with no month falling below 80%.
- **Discounts are moderate, not aggressive:** most discounts fall between 11% and 30%, peaking around 15–20%. Very few sales carry discounts above 60%.
- **No revenue was lost to discounting overall:** orders and revenue per order move together through most of the year, both peaking sharply around Black Friday (Nov 2017) — there's no sign of the "more orders, less revenue" pattern across the whole dataset.
- **Seasonality drives sales far more than discount depth:** Black Friday revenue spikes to ~9.6x an average day, and Christmas to ~2.6x — but discount rates during these peaks stay around the same ~20% average as the rest of the year, so the spike is about seasonal demand, not deeper price cuts.
- **Revenue is concentrated in a few categories:** storage and smartphones are the top two revenue-generating categories; storage in particular pairs a moderate ~17% average discount with the highest total revenue (€2.3M), out-earning categories with steeper discounts — the exception to an otherwise clear "more discount → less category revenue" trend.
- **High-end tech (desktops, laptops, smartphones, iPads, iPods) earns more when discounted**, similar to the rest of the catalog, but still contributes far less total revenue than the core categories — so it isn't yet the company's revenue driver despite being the strategic "quality segment" focus.

**Recommendation to the Board:** keep discounts around the current ~20% average — there's no evidence it's cannibalizing revenue — and grow high-end tech's share of sales to strengthen the quality-segment position, rather than cutting discounts across the board.

## 🛠️ Technologies Used

- **Programming:** Python
- **Libraries:** pandas, numpy, matplotlib, seaborn
- **Environment:** Jupyter / Google Colab

## 📁 Project Structure

```
data/
  raw/            original CSV exports (orders, orderlines, products, brands)
  processed/      cleaned and quality-assessed data, plus the category taxonomy
notebooks/
  01_data_cleaning.ipynb          data quality assessment & cleaning
  02_quality_assessment.ipynb     further quality checks post-cleaning
  03_category_creation.ipynb      building a human-readable product category taxonomy
  04_data_analysis_part1.ipynb    discounts, seasonality, category revenue analysis
  05_data_analysis_part2.ipynb    supporting/secondary analysis and category-level detail
reports/
  figures/         all charts generated during analysis
  presentation/    final slide deck presented to the Eniac board
```

## 📈 Visualisations

![Distribution of discount size](reports/figures/highlight_discount_distribution.png)
*Most discounts fall between 11–30%, peaking around 15–20% — a moderate, predictable range rather than aggressive price-cutting.*

![Daily revenue with Black Friday and Christmas highlighted](reports/figures/highlight_seasonality_black_friday_christmas.png)
*Revenue spikes sharply around Black Friday (~9.6x an average day) and rises more moderately over the Christmas period (~2.6x) — seasonality, not discount depth, drives these peaks.*

![Top 10 categories by revenue](reports/figures/highlight_top_categories_by_revenue.png)
*Storage and smartphones lead category revenue; storage earns the most overall despite only a moderate ~17% average discount.*

All other charts generated during the analysis are in `reports/figures/`.

## 🔗 How to Use This Project

1. **Start here:** `notebooks/01_data_cleaning.ipynb` to see the data quality issues and how they were resolved.
2. **Main analysis:** `notebooks/04_data_analysis_part1.ipynb` and `05_data_analysis_part2.ipynb` contain the business-question analysis and all charts.
3. **Full findings & recommendation:** `reports/presentation/eniac-discount-strategy-presentation.pptx`.
4. **Dependencies:** standard data science stack — pandas, numpy, matplotlib, seaborn. No special setup required; open the notebooks in Jupyter or Google Colab and run all cells in order.

## 🚀 Future Work

- **Data collection improvements:** the raw data had missing values, duplicate rows, wrong datatypes, and inconsistent encodings — better pipeline validation and stricter schema checks at the point of collection would remove much of the cleaning overhead.
- **Customer-level data:** the current dataset has no customer identifiers or demographics, which limits any acquisition/retention analysis — adding this would let us directly test Marketing's claim that discounts drive retention.
- **Human-readable product categories at the source:** categories currently have to be reconstructed from SKU/type codes; storing them directly would simplify all future reporting.
- **A/B testing:** design controlled discount experiments (e.g. varying discount depth by category) to establish causality rather than correlation between discount level and revenue.

## 👥 Authors

Ciba · Javier · Robert · Tatiana — WBS Coding School, Data Analytics bootcamp
