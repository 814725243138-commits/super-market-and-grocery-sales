# Supermarket & Grocery Sales Analysis

A data project for exploring, analyzing, and visualizing sales performance at a supermarket / grocery retail chain. It helps answer questions like: *What sells best? When do customers shop? Which stores and categories drive profit?*

## Table of Contents

- [Overview](#overview)
- [Objectives](#objectives)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Analysis Workflow](#analysis-workflow)
- [Key Metrics](#key-metrics)
- [Sample Insights](#sample-insights)
- [Tools & Technologies](#tools--technologies)
- [Future Improvements](#future-improvements)
- [Contributing](#contributing)
- [License](#license)

## Overview

Supermarkets generate large volumes of transactional data every day. This project turns that raw data into actionable insights covering sales trends, product performance, customer behavior, inventory planning, and profitability.

## Objectives

- Analyze overall sales, revenue, and profit trends over time
- Identify top-selling and underperforming products and categories
- Understand customer purchasing patterns (basket size, peak hours, payment methods)
- Compare performance across branches, cities, and customer segments
- Support demand forecasting and inventory decisions
- Build clear dashboards and reports for decision makers

## Dataset

The dataset is expected to contain transaction-level records. A typical schema:

| Column | Description |
|---|---|
| `invoice_id` | Unique transaction/invoice number |
| `date` | Date of purchase |
| `time` | Time of purchase |
| `branch` | Store branch / outlet |
| `city` | City of the store |
| `customer_type` | Member / Normal |
| `gender` | Customer gender |
| `product_category` | e.g., Fruits & Vegetables, Dairy, Beverages, Snacks, Household |
| `product_name` | Name of the product |
| `unit_price` | Price per unit |
| `quantity` | Units purchased |
| `tax` | Tax amount (e.g., GST) |
| `total` | Total amount including tax |
| `payment_method` | Cash / Card / UPI / Wallet |
| `cogs` | Cost of goods sold |
| `gross_income` | Profit on the transaction |
| `rating` | Customer satisfaction rating |

> Place your data file in the `data/raw/` folder (e.g., `data/raw/supermarket_sales.csv`).

## Project Structure

```
supermarket-grocery-sales/
├── data/
│   ├── raw/                # Original, unmodified data
│   └── processed/          # Cleaned data ready for analysis
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_eda.ipynb
│   └── 03_visualization.ipynb
├── src/
│   ├── clean_data.py       # Cleaning & preprocessing functions
│   └── analysis.py         # Analysis helpers
├── reports/
│   └── figures/            # Exported charts and dashboards
├── requirements.txt
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.9+
- pip or conda

### Installation

```bash
# Clone the repository
git clone https://github.com/<your-username>/supermarket-grocery-sales.git
cd supermarket-grocery-sales

# (Optional) create a virtual environment
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Quick Start

```python
import pandas as pd

df = pd.read_csv("data/raw/supermarket_sales.csv", parse_dates=["date"])
print(df.head())
print(df.groupby("product_category")["total"].sum().sort_values(ascending=False))
```

## Analysis Workflow

1. **Data Cleaning** – handle missing values, remove duplicates, fix data types, standardize categories
2. **Feature Engineering** – extract month, weekday, hour; compute basket value and profit margin
3. **Exploratory Data Analysis (EDA)** – distributions, correlations, trend analysis
4. **Visualization** – sales trends, category share, heatmaps of peak hours, branch comparisons
5. **Insights & Recommendations** – summarize findings for business decisions

## Key Metrics

- **Total Revenue** – sum of all sales
- **Gross Profit / Margin** – `(Revenue − COGS) / Revenue`
- **Average Basket Value** – revenue per transaction
- **Units per Transaction** – average items purchased
- **Top Categories / Products** – by revenue and by quantity
- **Sales by Hour / Weekday / Month** – to identify peak periods
- **Customer Satisfaction** – average rating by branch or category

## Sample Insights

*(Replace with your actual findings.)*

- Sales peak during evenings and weekends
- Fruits & Vegetables and Dairy drive the highest transaction volume
- Members spend more per basket than non-members
- Digital payments (UPI/Card) account for a growing share of sales
- A few branches contribute a disproportionate share of profit

## Tools & Technologies

- **Python** – pandas, NumPy
- **Visualization** – Matplotlib, Seaborn, Plotly
- **Notebook** – Jupyter
- **Optional** – Power BI / Tableau / Excel for dashboards, scikit-learn / Prophet for forecasting

## Future Improvements

- Sales forecasting with time-series models
- Market basket analysis (association rules) for product bundling
- Customer segmentation (RFM / clustering)
- Inventory optimization and stock-out prediction
- Interactive dashboard (Streamlit / Power BI)

## Contributing

Contributions are welcome! Please fork the repo, create a feature branch, and open a pull request.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
