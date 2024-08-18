# Walmart Sales Data Analysis

## Project Overview

This project is an in-depth analysis of Walmart's sales data, aimed at understanding the top-performing branches and products, sales trends, and customer behavior. By analyzing this data, we aim to identify strategies for improving and optimizing sales. The dataset used in this project was obtained from the [Kaggle Walmart Sales Forecasting Competition](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting).

The dataset includes historical sales data for 45 Walmart stores located in different regions, each containing multiple departments. The challenge lies in projecting sales for each department in each store, taking into account selected holiday markdown events known to affect sales.

## Objectives

The primary objective of this project is to gain insights into Walmart's sales data to understand the various factors affecting sales across different branches.

### Specific Goals:
- Analyze product performance across different branches.
- Understand sales trends and their impact on revenue.
- Explore customer segments and their purchasing behavior.

## Dataset Information

The dataset comprises sales transactions from three different Walmart branches located in Mandalay, Yangon, and Naypyitaw. It contains 17 columns and 1000 rows, with the following attributes:

| Column                  | Description                             | Data Type      |
|-------------------------|-----------------------------------------|----------------|
| invoice_id              | Invoice of the sales made               | VARCHAR(30)    |
| branch                  | Branch at which sales were made         | VARCHAR(5)     |
| city                    | The location of the branch              | VARCHAR(30)    |
| customer_type           | The type of the customer                | VARCHAR(30)    |
| gender                  | Gender of the customer making purchase  | VARCHAR(10)    |
| product_line            | Product line of the product sold        | VARCHAR(100)   |
| unit_price              | The price of each product               | DECIMAL(10, 2) |
| quantity                | The amount of the product sold          | INT            |
| VAT                     | The amount of tax on the purchase       | FLOAT(6, 4)    |
| total                   | The total cost of the purchase          | DECIMAL(10, 2) |
| date                    | The date on which the purchase was made | DATE           |
| time                    | The time at which the purchase was made | TIMESTAMP      |
| payment_method          | Payment method used                     | VARCHAR(30)    |
| cogs                    | Cost Of Goods Sold                      | DECIMAL(10, 2) |
| gross_margin_percentage | Gross margin percentage                 | FLOAT(11, 9)   |
| gross_income            | Gross Income                            | DECIMAL(10, 2) |
| rating                  | Rating given by the customer            | FLOAT(2, 1)    |

## Analysis Overview

### Product Analysis
- **Objective:** Understand product lines' performance and identify areas for improvement.
- **Key Questions:** 
  - What is the most selling product line?
  - Which product lines perform better than average?

### Sales Analysis
- **Objective:** Analyze sales trends to measure the effectiveness of sales strategies.
- **Key Questions:** 
  - What is the total revenue by month?
  - Which month had the largest COGS?
  - Which branch sold more products than the average?

### Customer Analysis
- **Objective:** Uncover customer segments, purchase trends, and profitability.
- **Key Questions:** 
  - Which customer type brings the most revenue?
  - What is the gender distribution per branch?
  - Which time of the day do customers give the most ratings?

## Revenue and Profit Calculations

The following formulas were used to calculate revenue and profit:

- **COGS (Cost of Goods Sold):** `COGS = unit_price * quantity`
- **VAT (Value Added Tax):** `VAT = 5% * COGS`
- **Total Revenue:** `total = VAT + COGS`
- **Gross Profit:** `gross_income = total - COGS`
- **Gross Margin Percentage:** `gross_margin_percentage = gross_income / total * 100`

### Example Calculation

Given:
- **Unit Price:** 45.79
- **Quantity:** 7

**Steps:**
1. Calculate COGS: `COGS = 45.79 * 7 = 320.53`
2. Calculate VAT: `VAT = 5% * 320.53 = 16.0265`
3. Calculate Total: `total = VAT + COGS = 336.5565`
4. Calculate Gross Margin Percentage: `gross_margin_percentage = 16.0265 / 336.5565 ≈ 4.7619%`

## Database Setup

The following SQL commands were used to create the database and table for storing the Walmart sales data:

```sql
-- Create database
CREATE DATABASE IF NOT EXISTS walmartSales;

-- Create table
CREATE TABLE IF NOT EXISTS sales(
	invoice_id VARCHAR(30) NOT NULL PRIMARY KEY,
    branch VARCHAR(5) NOT NULL,
    city VARCHAR(30) NOT NULL,
    customer_type VARCHAR(30) NOT NULL,
    gender VARCHAR(30) NOT NULL,
    product_line VARCHAR(100) NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    quantity INT NOT NULL,
    tax_pct FLOAT(6,4) NOT NULL,
    total DECIMAL(12, 4) NOT NULL,
    date DATETIME NOT NULL,
    time TIME NOT NULL,
    payment VARCHAR(15) NOT NULL,
    cogs DECIMAL(10,2) NOT NULL,
    gross_margin_pct FLOAT(11,9),
    gross_income DECIMAL(12, 4),
    rating FLOAT(2, 1)
);
```

## Conclusion

This project provides valuable insights into Walmart's sales data, helping to identify key trends and factors that influence sales performance across different branches and products. These insights can inform future strategies to optimize sales and improve customer satisfaction.
