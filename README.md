# Amazon India Sales Insights

An interactive Tableau dashboard analysing **1,351 Amazon India products** across pricing, discounts, ratings and estimated revenue.


## Project Goal

To understand how pricing, discounts and customer ratings relate across product categories on Amazon India, and which categories and price ranges dominate the catalogue.

## Business Questions

1. How many products are listed, and what is the typical rating and discount?
2. Which price ranges contain the most products?
3. Which categories generate the most estimated revenue?
4. Which sub-categories have the most products?
5. Do bigger discounts mean lower ratings?

## Key Findings

- **Products under ₹500 are the largest price group**, ahead of every other price range.
- **Electronics dominates estimated revenue**, at roughly ten times the next category.
- **USB Cables is the most crowded sub-category** with 233 products, followed by Smart Watches and Smartphones.
- **Heavier discounts go with slightly lower ratings.** Average rating falls from about 4.17 (0-20% discount) to about 3.98 (81-100% discount). The difference is small, about 0.2 stars.
- Across the catalogue, the **average rating is 4.10** and the **average discount is 47.7%**.

## Dashboard Contents

| Visual | What it shows |
|---|---|
| Total Products | Number of unique products (1,351) |
| Avg Rating | Average customer rating (4.10) |
| Avg Discount | Average discount percentage (47.7%) |
| Price Range | Number of products in each price band |
| Revenue by Categories | Estimated revenue per main category |
| Top 10 Sub Categories | Sub-categories with the most products |
| Discount vs Rating | Average rating for each discount band |

The dashboard is interactive: clicking a bar in one chart filters the other charts.

## Dataset

- **File:** `data/amazon.csv` (raw), `data/amazon_clean.csv` (cleaned)
- **Size:** 1,465 rows, 1,351 unique products
- **Main columns:** product name, category, discounted price, actual price, discount percentage, rating, rating count

## Data Cleaning

The raw file could not be used in Tableau directly, so I:

1. Converted prices (such as `₹1,099`) and discounts (such as `64%`) from text to numbers.
2. Split the single `category` column into `main_category`, `sub_category_1` and `sub_category`.
3. Converted rating counts from text to numbers and set one invalid rating (`|`) to blank.
4. Created `discount_band` and `price_band` columns for grouping.
5. Created `estimated_revenue` (see limitations below).
6. Counted products with **Count (Distinct)** on `product_id`, because some products appear more than once in the raw file.

## Limitations

- **Revenue is an estimate**, calculated as discounted price × number of ratings. The dataset has no actual sales figures, so this is a rough guide to relative size, not real revenue.
- Several categories contain only one or two products, so their averages are not reliable.
- The data is a snapshot, so prices and ratings may have changed since it was collected.
- The relationship between discount and rating is weak, so it should not be read as cause and effect.

## Tools Used

- **Tableau** (Tableau Public) for the dashboard
- **Python (pandas)** for data cleaning
- **Excel / CSV** for data handling

## Repository Structure

```
Amazon-India-Sales-Insights/
├── README.md
├── Amazon_India_Sales_Insights.twbx    # Tableau packaged workbook
├── data/
│   ├── amazon.csv                      # raw data
│   └── amazon_clean.csv                # cleaned data
└── screenshots/
    └── dashboard.png
```

## How to Open

1. Install [Tableau Public](https://public.tableau.com/) (free) or Tableau Desktop.
2. Open `Amazon_India_Sales_Insights.twbx`. The data is packaged inside the file.

## Author

**G Ram Prasad Rao**, aspiring Data Analyst

- LinkedIn: [g-ram-prasad-rao](https://www.linkedin.com/in/g-ram-prasad-rao-809006377)
- GitHub: [Ram-code-2004](https://github.com/Ram-code-2004)
