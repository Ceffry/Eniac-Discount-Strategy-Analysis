# Eniac's Discount Strategy Analysis

## Project Overview

Eniac, a European e-commerce company specialising in tech products, is debating whether discounting its products is beneficial for the business. The Marketing Team believes discounts drive customer acquisition, satisfaction, and retention. The Board is concerned: a recent quarter showed an increase in orders placed alongside a decrease in total revenue, and prefers Eniac to compete in the quality segment rather than on price.

This project analyses ~2 years of Eniac's internal order and product data using Python (pandas, matplotlib, seaborn) to determine whether discounting is actually hurting revenue, how large and how frequent discounts really are, and how seasonality and product category affect the picture. The raw data was corrupted on arrival, so a full data cleaning and quality assessment process was required before any analysis could begin. Based on the findings, we recommend keeping discounts at their current level and growing high-end tech sales to reinforce Eniac's quality positioning.

---

## Dataset & Sources

- **Source:** Eniac's internal order management database (provided as part of the WBS Coding School case study)
- **Time period:** ~January 2017 – March 2018
- **Files:** `orders.csv`, `orderlines.csv`, `products.csv`, `brands.csv`
- **Key data:** Order timestamps and states, order line quantities and unit prices, product base/promo prices, brand codes, and product type
- **Data quality:** the raw data was corrupted — missing values, wrong datatypes, duplicate rows, and inconsistent encodings — requiring a full cleaning and quality assessment pass before analysis
- **Tools:** Python (pandas, numpy, matplotlib, seaborn), Jupyter/Google Colab

---

## Key Findings & Results

### Discounting Is the Norm

92.8% of order lines were sold at a discount — discounting is standard practice at Eniac, not an occasional promotion.

![Share of orderlines with vs. without discount](reports/figures/01_share_orderlines_with_without_discount.png)

Revenue tells the same story: discounted products generate far more monthly revenue than full-price products, every single month of the period.

![Monthly revenue with vs. without discount](reports/figures/02_monthly_revenue_with_vs_without_discount.png)

### No Revenue Was Lost to Discounting

Orders and revenue per order move together across the full period — there is no sign of the "more orders, less revenue" pattern the Board flagged in one quarter. Both peak sharply in November 2017 (Black Friday) and decline together afterwards.

![Orders vs revenue per order, monthly](reports/figures/03_orders_vs_revenue_per_order.png)

### Discounts Are Moderate, Not Aggressive

The middle 50% of discounts fall between 11% and 30%, peaking around 15–20%. Steep discounts above 60% are rare.

![Distribution of discount size](reports/figures/04_distribution_of_discount_size.png)

The overall average discount across the whole period is 21.6%, and monthly averages stay close to that line all year — there's no aggressive escalation over time.

![Monthly discount compared with the average](reports/figures/05_monthly_discount_vs_average.png)

### High-End Tech Underperforms on Volume

High-end tech (desktops, laptops, smartphones, iPads, iPods) earns more revenue when discounted, the same pattern as the rest of the catalogue — but it still contributes far less total revenue than Eniac's other products. It is not yet the company's revenue driver, despite being the strategic "quality segment" focus.

![Monthly revenue by product type and discount](reports/figures/06_revenue_by_product_type_and_discount.png)

### Seasonality Drives Sales, Not Discount Depth

Revenue spikes sharply around Black Friday and rises again around Christmas — but the average discount during these peaks (23.3% for Black Friday, 20.8% for Christmas) stays close to the yearly average of 21.6%. Customers buy seasonally, not because of deeper price cuts.

![Daily revenue with average discount, Black Friday and Christmas highlighted](reports/figures/07_seasonality_black_friday_christmas.png)

---

## Summary

| Topic | Finding |
|---|---|
| Discount prevalence | 92.8% of order lines sold at a discount |
| Discount size | Middle 50% between 11–30%, peaking at 15–20% |
| Yearly average discount | 21.6% |
| Revenue vs. orders | Move together — no revenue lost to discounting |
| Black Friday discount | 23.3% average — close to the yearly average |
| Christmas discount | 20.8% average — close to the yearly average |
| High-end tech | Discount-responsive, but low revenue share |
| Data quality | Corrupted on arrival — missing values, duplicates, wrong types, bad encodings |

---

## Recommendation

### Keep discounts around the current ~21.6% average, and grow high-end tech's share of sales.

Based on the analysis, we found no evidence that discounting is hurting Eniac's revenue. The pattern the Board was worried about does not hold up across the full dataset — orders and revenue move together, and the seasonal spikes in sales are not driven by deeper discounting.

We therefore recommend:

1. **Keep discounts around 21.6%.** There's no sign it's cannibalising revenue, and cutting it risks losing the sales volume it currently supports.
2. **Grow high-end tech's share of sales.** To reinforce Eniac's quality-segment positioning, high-end tech needs to become a larger part of the revenue mix — not just a discount-responsive niche.

We also recommend improving data collection for future analyses:

- **Missing data:** tighter pipeline validation to reduce null/malformed values.
- **Customer data:** no customer identifiers or demographics currently exist, which blocks any direct test of whether discounts improve retention.
- **Human-readable product categories:** categories currently have to be reconstructed from SKU/type codes; storing them directly at the source would simplify future reporting.

---

## Technologies Used

- **Python**
  - pandas – data cleaning, quality assessment, aggregation
  - numpy – numerical operations
  - matplotlib / seaborn – data visualisation
- **Jupyter / Google Colab** – analysis environment

---

## Project Structure

```
├── README.md
├── data/
│   ├── raw/            original CSV exports (orders, orderlines, products, brands)
│   └── processed/      cleaned data, quality-assessed data, category taxonomy
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_quality_assessment.ipynb
│   ├── 03_category_creation.ipynb
│   ├── 04_data_analysis_part1.ipynb
│   └── 05_data_analysis_part2.ipynb
└── reports/
    ├── figures/         the charts used in the board presentation
    └── presentation/    final slide deck presented to the Eniac board
```

## Authors

Ciba · Javier · Robert · Tatiana — WBS Coding School, Data Analytics bootcamp
