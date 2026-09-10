# Customer Segmentation & RFM Analysis

## Project Overview

This project analyzes customer purchasing behavior using **SQL and Python** and groups customers into meaningful segments using **RFM analysis**.

The main goal was to understand which customers are highly valuable, which customers are likely to become loyal, and which customers may need to be re-engaged.

I used the **UCI Online Retail dataset**, which contains transaction-level data from a UK-based online retailer.

---

## Tools & Technologies

* **SQL** — data cleaning, filtering, aggregation and joining
* **DuckDB** — running SQL directly in Google Colab
* **Python** — analysis and data processing
* **Pandas** — data cleaning and RFM calculations
* **Matplotlib & Seaborn** — data visualization
* **Google Colab** — development environment

---

## Project Workflow

```text
Raw Transaction Data
        ↓
Data Quality Checks
        ↓
SQL Data Cleaning
        ↓
Customers + Orders Tables
        ↓
SQL Join & Customer Aggregation
        ↓
RFM Analysis using Python
        ↓
RFM Scoring (1–5)
        ↓
Customer Segmentation
        ↓
Visualization
        ↓
Business Insights & Recommendations
```

---

## Dataset

The project uses the **Online Retail dataset** from the UCI Machine Learning Repository.

The dataset contains approximately **541,000 transaction records** and includes information such as:

* Invoice number
* Product code
* Product description
* Quantity
* Invoice date
* Unit price
* Customer ID
* Country

---

## Data Preparation

Before performing the analysis, I checked the dataset for:

* Missing Customer IDs
* Cancelled transactions
* Invalid quantities
* Invalid prices
* Duplicate or unnecessary transaction-level records

For the customer analysis, transactions without a Customer ID were excluded.

Cancelled transactions and transactions with non-positive quantity or price were also removed.

I then created two logical tables using SQL:

### Customers

Contains unique customers and their country.

### Orders

Contains one row per order with:

* Invoice number
* Customer ID
* Order date
* Order amount

The order amount was calculated using:

```text
Quantity × Unit Price
```

This helped avoid treating individual product lines within the same invoice as separate purchases.

---

## RFM Analysis

RFM stands for:

### Recency

How recently a customer made a purchase.

A lower number of days means the customer is more recently active.

### Frequency

How often the customer purchased.

In this project, frequency represents the number of distinct orders.

### Monetary

How much the customer spent.

It was calculated from the total value of their purchases.

---

## RFM Scoring

Each customer received a score from **1 to 5** for Recency, Frequency and Monetary value.

* **Recency:** 5 = most recent customers
* **Frequency:** 5 = most frequent customers
* **Monetary:** 5 = highest spending customers

The three scores were combined to create an overall RFM score.

---

## Customer Segments

Based on the RFM scores, customers were grouped into six segments:

| Segment             | Description                                                            |
| ------------------- | ---------------------------------------------------------------------- |
| Champions           | Recent, frequent and high-value customers                              |
| Loyal Customers     | Customers who purchase regularly and spend well                        |
| Potential Loyalists | Recent customers with potential to become frequent buyers              |
| New Customers       | Recently acquired customers with limited purchase history              |
| At Risk             | Previously valuable/active customers who have become less recent       |
| Lost                | Customers with low activity and long periods since their last purchase |

---

## Key Findings

The analysis produced some interesting results.

### Champions

Only **919 customers** were classified as Champions, but they contributed approximately **64.15% of total revenue**.

This shows how strongly the business depends on a relatively small group of high-value customers.

### Loyal Customers

The Loyal Customer segment contained **362 customers** and contributed around **11.63% of revenue**.

These customers already demonstrate strong purchasing behavior and could be targeted for retention and loyalty programs.

### Potential Loyalists

There were **1,179 Potential Loyalists**, contributing approximately **9.30% of revenue**.

This segment represents an opportunity to convert relatively recent customers into more frequent buyers.

### At Risk Customers

The At Risk segment contained **780 customers** with an average recency of approximately **168 days**.

These customers could be targeted with re-engagement campaigns before they become completely inactive.

### Lost Customers

There were **789 Lost customers**, with an average recency of approximately **231 days**.

Rather than treating all of these customers equally, the business could prioritize those who previously had higher monetary value.

---

## Business Recommendations

Based on the segmentation, I would recommend:

### 1. Protect Champions

Use loyalty rewards, early access and personalized offers to retain high-value customers.

### 2. Convert Potential Loyalists

Encourage their second or third purchase through personalized recommendations and limited-time offers.

### 3. Re-engage At Risk Customers

Use targeted email campaigns, discounts or product recommendations based on their previous purchases.

### 4. Prioritize Lost Customers

Focus reactivation efforts on Lost customers who previously generated significant revenue instead of spending equally on every inactive customer.

### 5. Monitor New Customers

Track whether new customers make repeat purchases and move into the Potential Loyalist or Loyal Customer segments.

---

## Visualizations

The project includes visualizations for:

* Customer segment distribution
* Revenue contribution by segment
* Recency vs Monetary value
* RFM score comparison by segment

These visualizations help translate the customer-level analysis into information that can be used for marketing and customer-retention decisions.

---

## Project Structure

```text
Customer-Segmentation-RFM/
│
├── README.md
│
├── SQL/
│   └── customer_analysis.sql
│
├── Python/
│   └── customer_segmentation.ipynb
│
├── Data/
│   ├── customers.csv
│   └── orders.csv
│
├── Visualizations/
│   ├── segment_distribution.png
│   ├── revenue_by_segment.png
│   ├── rfm_scatter.png
│   └── rfm_segment_comparison.png
│
└── Insights/
    └── recommendations.md
```

---

## What I Learned

Through this project, I practiced:

* Writing SQL queries for real transaction data
* Creating customer-level datasets from raw transactions
* Using SQL joins and aggregations
* Handling missing and invalid data
* Performing RFM analysis with Pandas
* Creating customer segments based on business rules
* Visualizing customer behavior
* Translating analytical results into business recommendations

---

## Conclusion

This project helped me understand how customer transaction data can be converted into actionable customer segments.

Instead of looking at individual transactions, RFM analysis makes it possible to identify **who the most valuable customers are, who has growth potential, and who may be at risk of being lost**.
