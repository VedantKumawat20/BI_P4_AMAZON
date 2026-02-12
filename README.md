# BI_P4_AMAZON
Data Analysis Project 4 (Power BI)
---
# SALES ANALYSIS

## 📑 Table of Contents

1. [Domain](#domain)
2. [Problem Statement](#problem-statement)
3. [Aim](#aim)
4. [Key Challenges](#key-challenges)
5. [Dataset Overview](#dataset-overview)
6. [Data Structure](#data-structure)
7. [New Measures (DAX)](#new-measures-dax)
8. [Solution Approach](#solution-approach)
9. [Dashboard 1: Sales and Profit Performance](#dashboard-1-sales-and-profit-performance)
10. [Dashboard 2: Product and Category Profitability](#dashboard-2-product-and-category-profitability)
11. [Dashboard 3: Regional / Market Profitability](#dashboard-3-regional--market-profitability)
12. [Dashboard 4: Customer and Transaction Profit Insights](#dashboard-4-customer-and-transaction-profit-insights)
13. [Where We Can Apply](#where-we-can-apply)
14. [Expected Business Impact](#expected-business-impact)
15. [Future Scope & Advanced Analytics](#future-scope--advanced-analytics)
16. [Conclusion](#conclusion)

---

## Domain

**AMAZON Sales Analytics**

This project analyses synthetic e-commerce sales dataset that mimics Amazon-style order-level transactional data. Power BI is used to evaluate sales performance, revenue trends, product category demand, regional and category-wise performance, and customer feedback in order to support data-driven decision-making and profitability optimization.

---

## Problem Statement

Amazon operates across multiple regions, product categories, and payment methods. The business has high transaction volumes but key insights remain hidden.

Decision-makers often lack clear insights into:

* True profitability versus sales volume
* Impact of discounting on margins
* Regional and category performance gaps
* Relationship between customer experience and profit

---

## Aim

By transforming raw transactional data into interactive, decision-ready dashboards, uncover patterns in payment methods, sales performance, customer ratings, profitability, revenue trends over time, and addressing region-level behaviour.

This project enables:

* Better strategic planning
* Margin control
* Business growth

---

## Key Challenges

* Difficulty in identifying top-performing vs underperforming categories.
* Uneven sales and profit performance across regions.
* Risk of over-discounting without understanding margin impact.
* Difficulty linking ratings & reviews with profitability.
* Time-based sales and margin trend analysis complexity.
* Large volumes of data with hidden insights.
* Decision-making driven by assumptions instead of structured analytics.

---

## Dataset Overview

This dataset is a **synthetic** e-commerce sales dataset generated using AI tools for **educational and analytical practice purposes**. The structure mimics Amazon-style order-level transactional data to simulate real-world business scenarios.

* **Granularity:** Order-Level transactional data
* **Time Period:** 2022 – 2024
* **Records:** ~1000 orders
* **Tool Used:** Power BI

---

## Data Structure

| Variable                  | Meaning                    | Formula / Logic                           |
| ------------------------- | -------------------------- | ----------------------------------------- |
| order_id                  | Unique order identifier    | System generated                          |
| order_date                | Date of order              | Transaction date                          |
| product_id                | Unique product code        | Master data                               |
| product_category          | Product classification     | Categorical                               |
| price                     | Original price per unit    | Given                                     |
| discount_percent          | Discount applied (%)       | Given                                     |
| discounted_price_per_unit | Final price after discount | Price – discount%                         |
| quantity_sold             | Units sold                 | Given                                     |
| total_revenue             | Net revenue per order      | Discounted_price × quantity               |
| cost_per_unit             | Cost per unit              | Given                                     |
| total_order_cost          | Total cost per order       | Cost_per_unit × quantity                  |
| profit                    | Net profit                 | Total_revenue – total_order_cost          |
| customer_region           | Geographic region          | Asia, Europe, Middle East, North America  |
| payment_method            | Mode of payment            | COD, Credit Card, Debit Card, Wallet, UPI |
| rating                    | Customer rating            | 1–5 scale                                 |
| review_count              | Volume of feedback         | Count                                     |

---

## New Measures (DAX)

```DAX
AVG COST = AVERAGE(Sheet1[total order cost])

AVG DISCOUNT = AVERAGE(Sheet1[DISCOUNT GIVEN])

AVG DISCOUNT % = AVERAGE(Sheet1[discount_percent])

AVG PROFIT = AVERAGE(Sheet1[profit])

AVG PROFIT PER UNIT =
DIVIDE(SUM(Sheet1[profit]), SUM(Sheet1[quantity_sold]))

AVG RATING = AVERAGE(Sheet1[rating])

AVG REVENUE PER ORDER =
DIVIDE([SUM OF TOTAL REVENUE],
DISTINCTCOUNT(Sheet1[order_id]))

DISCOUNT GIVEN =
(Sheet1[price]*Sheet1[quantity_sold]) - Sheet1[total_revenue] 

DISTINCT ORDER = DISTINCTCOUNT(Sheet1[order_id])

ORDER COUNT = COUNT(Sheet1[order_id])

PROFIT MARGIN % =
DIVIDE([SUM OF PROFIT],
[SUM OF TOTAL REVENUE], 0) * 100

SUM OF PROFIT = SUM(Sheet1[profit])

SUM OF QUANTITY SOLD = SUM(Sheet1[quantity_sold])

SUM OF TOTAL REVENUE = SUM(Sheet1[total_revenue])
```

---

## Solution Approach

* Data cleaning, inspection and validation
* Feature engineering
* Creation of calculated measures using DAX
* KPI development using iterator logic (SUMX, COUNTX)
* Interactive Power BI dashboards with slicers and drill-downs
* Comparative and trend-based analysis

---

## Dashboard 1: Sales and Profit Performance
<img width="1408" height="869" alt="DB1" src="https://github.com/user-attachments/assets/2782ba61-64fb-46e2-b9e0-eda8fc90c890" />

### What It Shows

* Total Revenue: ₹19.70M
* Total Profit: ₹7.73M
* Profit Margin: 39.23%
* Quantity Sold: 12K units
* Average Revenue per Order: ₹19.70K
* Average Discount: 35.28%

### Key Insights

* Revenue and profit declined over time
* Profit margin improved consistently
* Quantity sold dropped sharply in 2024
* Strong profitability, but limited sales volume
* Margin improvement driven by cost control and pricing discipline
* Revenue and profit decline over time, but profit margin improves
* Revenue contraction is driving overall performance decline.
* Discount optimization is required at category level.
* Performance varies significantly by region.

### Key Recommendations

* Prioritize demand revival through targeted marketing and offers, not further margin tightening and discounting.
* Reduce blanket discounting
* Reduce ineffective discounting and apply category-specific discounts.
* Investigate recent demand slowdown urgently
* Replicate high-performing regional strategies (Europe) in weaker regions
* Balance margin protection with volume growth for sustainable performance

---

## Dashboard 2: Product and Category Profitability
<img width="1395" height="847" alt="DB2" src="https://github.com/user-attachments/assets/e531d871-7bf1-4062-aa7c-3ac8996df7c4" />

### Key Insights

* Home & Kitchen and Sports generate highest revenue
* Electronics has lowest margin
* High revenue does not always translate into highest profit.
* Higher-rated categories generate higher profit
* High discounts do not guarantee higher profitability
* Profitability varies strongly by product category
* Premium categories drive value per order even after discounts.
* Some categories are cost-heavy with weaker profit efficiency.
* Discounting impact is limited and inconsistent.
* Customer satisfaction positively influences profitability.
* Categories with better margins and ratings perform more efficiently.
* Electronics shows lower margin, lower ratings, and weaker efficiency.

### Key Recommendations

* Optimize cost structure in Electronics
* Reduce blanket discounting, apply category-specific discount strategies
* Focus on high-margin categories (Home & Kitchen, Beauty)
* Increase profit margin of categories (fashion and books) which have higher rating but lower profit.
* Improve cost efficiency and customer experience in low-margin categories
* Leverage customer ratings and reviews to drive profitable growth
* Focus decision-making on profit contribution, not just revenue, and re-evaluate pricing for low-profit categories.
* Prioritize marketing and visibility for high AOV categories to maximize revenue efficiency.
* Improve unit economics through cost control or price adjustments instead of pushing higher volumes.
* Optimize cost structure or reprice Electronics.
* Invest in product quality and customer experience to drive sustainable profitability and to reduce discount dependency.
* Scale high-profit categories, reprice margin-risk categories, and reassess underperformers.
---

## Dashboard 3: Regional / Market Profitability
<img width="1404" height="847" alt="DB3" src="https://github.com/user-attachments/assets/1944e737-e1a3-4a79-a7c5-ff07a617d21a" />

### Key Insights

* Europe is strongest region (highest revenue & profit)
* Asia underperforms (low volume + high discounts)
* Margins stable across regions
* Discounts do not improve regional profitability
* Lower volumes directly impact Asia’s revenue and profit
* Business is shrinking in terms of market share or volume but successfully increasing efficiency, cutting cost, improving margins.
* Europe has a more balanced and diversified profit mix.
* Europe is the strongest region.
* Europe + Middle East contribute over 55% of total profit
* Asia underperforms despite having sales volume

### Key Recommendations


* Replicate Europe’s pricing and sales strategy in weaker regions.
* Reduce excessive discounting in Asia.Target discounting to specific customer segment rather than blanket offers.
* Maintain margin discipline
* Prioritize investment in Europe and the Middle East
* Use region-specific pricing strategies instead of uniform discounts.
* Improve Asia’s unit economics and pricing strategy.

---

## Dashboard 4: Customer and Transaction Profit Insights
<img width="1405" height="849" alt="DB4" src="https://github.com/user-attachments/assets/28db36a4-0f6d-48d4-a860-da6539ceb627" />

### Key Insights

* No single payment method dominates profit.
* Profit risk is well diversified.
* Customer satisfaction positively impacts profitability.
* Discounting is not a key profit driver across payment methods.
* Payment method choice does not significantly impact margins.
* Engagement and trust influence profit outcomes.
* Credit Card and Debit Card are most profitable.
* higher discounts reduce profit.
* Customer ratings and reviews influence profitability more than payment choice
* High discounts do not improve payment-method profitability
* Profit risk diversified (17–21% contribution each)

### Key Recommendations

* Maintain diversified payment mix
•	Improve customer experience and profit margin to lift ratings and profit respectively.
* Set payment-method-specific discount caps
* Focus on trust and engagement over discounts
* Encourage high-margin payment methods using targeted incentives
* Improve post-purchase experience and actively drive customer feedback

---

## Where We Can Apply

* E-commerce platforms
* Retail & consumer goods companies
* Online marketplaces
* Sales & revenue management teams
* Business intelligence teams
* Consulting firms
* Digital startups

---

## Expected Business Impact

* Improved visibility into performance
* Optimized discount & pricing strategies
* Better regional decision-making
* Stronger linkage between customer experience & revenue
* Data-driven strategic planning
* Increased overall profitability

---

## Future Scope & Advanced Analytics

Next phase: Predictive & Prescriptive Analytics

### Future Business Questions

* Forecast revenue and profit (3–12 months)
* Predict regional & product demand
* Optimize pricing strategies
* Identify high-risk, low-margin orders

Implementation can include:

* Forecasting models
* Pricing optimization
* Automated Power BI alerts
* Model-driven decision systems

---

## Conclusion

This project demonstrates how Amazon sales data can be transformed into meaningful and actionable insights using Power BI and business analytics techniques.
By analysing sales, revenue, products, regions, and customer feedback, organizations move from descriptive reporting to insight-driven decision-making, enabling competitive advantage.
The project also includes recommendation-level prescriptive analytics, with future scope for optimization and simulation-based advanced analytics.



