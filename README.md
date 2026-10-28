# India Supermarket & Grocery Sales Analysis

Data cleaning and visualisation of store-level grocery sales across three sales channels (supermarket, online app, quick commerce) and three city tiers in India.

> **Note:** the dataset is **synthetic**. It was generated to follow the themes of the *Supermarket & Grocery Sales* market deck (India, October 2026): channel mix, city tiers, discount levels, private label and weekly KPIs. It is not real company data.

## Problem Statement

Retailers need clean, trustworthy sales data to answer questions such as: Which channel sells the most? How deep are the discounts in each channel? Which categories carry the highest private label share? Raw sales exports are rarely ready for this, as they contain duplicates, mixed date formats, inconsistent spellings and text-formatted numbers.

This project takes a deliberately **messy** sales dataset, cleans it step by step, and then analyses and visualises the **clean** result.

## Dataset

| Item | Detail |
|---|---|
| Source | Synthetic, generated in Python (`notebook/`), seed 42 |
| Period | 1 Apr 2026 to 30 Sep 2026 |
| Clean size | 5,000 order lines x 15 columns |
| Messy size | 5,210 rows x 15 columns |

**Files**
- `dataset/grocery_sales_messy.csv` - raw data with realistic problems
- `dataset/grocery_sales_clean.csv` - cleaned data

**Columns:** `order_id, order_date, store_id, city, city_tier, channel, category, product, brand_type, quantity, mrp, discount_pct, net_amount, payment_method, customer_id`

## Steps Followed

### 1. Data cleaning
| Problem in messy data | Fix |
|---|---|
| 150 duplicate rows | Dropped exact duplicates |
| 60 invalid rows (negative/zero/huge quantity, zero MRP, future dates) | Removed |
| 4 mixed date formats (`2026-06-10`, `04/05/2026`, `15-May-2026`, `March 12, 2026`) | Parsed into one date type |
| Inconsistent text (`Bengaluru`/`BLR`, `Q-Commerce`, `Bevarages`, extra spaces, random case) | Standardised with mapping tables |
| Numbers stored as text (`Rs.74`, `₹1,234.50`, `17 %`, `3 pcs`) | Stripped symbols, converted to numbers |
| Missing values (`N/A`, `-`, blank) | City and tier filled from `store_id`; discount or net amount recomputed from `quantity x mrp` |

Result: 5,210 rows reduced to 5,000. The cleaned data matches the original source data exactly. `customer_id` stays blank for walk-in customers.

### 2. Analysis
Net sales, discounts, private label share and payment mix were summarised by channel, city tier and category.

### 3. Visualisation
See the dashboard below. Code is in `notebook/`.

## Key Findings

- **Total net sales:** about Rs 15.5 lakh across 5,000 order lines.
- **Channel mix:** supermarkets 55.6%, online app 26.1%, quick commerce 18.3% of sales.
- **Discounts to MRP:** supermarket 17.8%, online app 16.7%, quick commerce 7.5%, in line with the deck.
- **Private label:** 27.8% of sales overall; highest in Fresh Produce (32.5%) and Beverages (31.0%), lowest in Staples (24.9%).
- **Categories:** Staples lead (about Rs 5.4 lakh); Snacks are smallest (about Rs 0.8 lakh).
- **City tiers:** Tier 2 cities (41.2%) and Metros (39.6%) are close; Tier 3 contributes 19.2%. Quick commerce is not present in Tier 3.
- **Payments:** online app and quick commerce are about 70% UPI; supermarkets are spread evenly across five methods.

## Visualisations

![Sales dashboard](visualizations/grocery_sales_charts.png)

Charts: monthly net sales by channel, average discount by channel, sales by city tier and channel, sales by category, private label share, and payment method mix.

## How to Run

**Google Colab (no uploads needed)**
1. Open [colab.research.google.com](https://colab.research.google.com) and choose *File > Upload notebook*.
2. Upload `notebook/grocery_sales_analysis.ipynb`.
3. Choose *Runtime > Run all*. The notebook generates the messy data, cleans it, draws the charts and downloads the CSVs and image.

**Locally**
```bash
pip install -r requirements.txt
python notebook/grocery_sales_analysis.py
```

## Repository Structure

```
grocery-sales-analysis/
├── dataset/
│   ├── grocery_sales_messy.csv
│   └── grocery_sales_clean.csv
├── notebook/
│   ├── grocery_sales_analysis.ipynb
│   └── grocery_sales_analysis.py
├── visualizations/
│   └── grocery_sales_charts.png
├── requirements.txt
└── README.md
```

## Tools Used
Python, pandas, NumPy, Matplotlib, Google Colab.
