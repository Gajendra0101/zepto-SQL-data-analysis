# 🛒 Zepto E-Commerce SQL Data Analyst Portfolio Project

This is a complete, real-world data analyst portfolio project based on an e-commerce inventory dataset scraped from Zepto — one of India’s fastest-growing quick-commerce startups. This project simulates real analyst workflows, from raw data exploration to business-focused data analysis.

This project is perfect for:

📊 Data Analyst aspirants who want to build a strong Portfolio Project for interviews and LinkedIn
📚 Anyone learning SQL hands-on
💼 Preparing for interviews in retail, e-commerce, or product analytics

---

## 📌 Project Overview

### Key Goals

* Build and manage an e-commerce inventory database
* Perform Exploratory Data Analysis (EDA)
* Clean and transform raw data
* Analyze inventory, pricing, discounts, and stock availability
* Generate business insights using SQL queries

---

## 📁 Dataset Overview

The dataset was sourced from [Kaggle][https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset/data?select=zepto_v2.csv] and originally scraped from Zepto's product catalog.

Each row represents a unique SKU (Stock Keeping Unit). Duplicate product names may appear because products can exist in multiple package sizes, weights, pricing structures, and promotional listings.

🧾 Columns:

sku_id: Unique identifier for each product entry (Synthetic Primary Key)

name: Product name as it appears on the app

category: Product category like Fruits, Snacks, Beverages, etc.

mrp: Maximum Retail Price (originally in paise, converted to ₹)

discountPercent: Discount applied on MRP

discountedSellingPrice: Final price after discount (also converted to ₹)

availableQuantity: Units available in inventory

weightInGms: Product weight in grams

outOfStock: Boolean flag indicating stock availability

quantity: Number of units per package (mixed with grams for loose produce)

---

## 🔧 Project Workflow

Here’s a step-by-step breakdown of what we do in this project:

1. Database & Table Creation
We start by creating a SQL table with appropriate data types:
CREATE TABLE zepto (
    sku_id SERIAL PRIMARY KEY,
    category VARCHAR(120),
    name VARCHAR(150) NOT NULL,
    mrp NUMERIC(8,2),
    discountPercent NUMERIC(5,2),
    availableQuantity INTEGER,
    discountedSellingPrice NUMERIC(8,2),
    weightInGms INTEGER,
    outOfStock BOOLEAN,
    quantity INTEGER
);
```

---

## 📥 Data Import

The dataset was imported using PostgreSQL and pgAdmin.

### Using PostgreSQL COPY Command

```sql
\copy zepto(
    category,
    name,
    mrp,
    discountPercent,
    availableQuantity,
    discountedSellingPrice,
    weightInGms,
    outOfStock,
    quantity
)
FROM 'data/zepto_v2.csv'
WITH (
    FORMAT csv,
    HEADER true,
    DELIMITER ',',
    QUOTE '"',
    ENCODING 'UTF8'
);
```

### Common Issue

If you encounter UTF-8 encoding errors:

1. Open the CSV file in Excel.
2. Select **Save As**.
3. Choose **CSV UTF-8 (Comma Delimited)** format.
4. Re-import the dataset.

---

## 🔍 Exploratory Data Analysis (EDA)

The following analyses were performed:

* Total number of records
* Sample data inspection
* Null value checks
* Category exploration
* Stock availability analysis
* Duplicate product identification
* SKU distribution analysis

### Example Questions Answered

* How many products exist in the catalog?
* Which categories contain the most products?
* How many products are currently out of stock?
* Which products appear multiple times under different SKUs?

---

## 🧹 Data Cleaning

To improve data quality:

### Data Quality Checks

* Removed products with invalid pricing
* Removed rows where:

  * MRP = 0
  * Discounted Selling Price = 0

### Data Transformation

Converted monetary values from paise to rupees:

```sql
UPDATE zepto
SET
    mrp = mrp / 100.0,
    discountedSellingPrice = discountedSellingPrice / 100.0;
```

---

## 📊 Business Analysis & Insights

### 1. Top Discounted Products

Identify products offering the highest discounts.

### 2. Premium Products Out of Stock

Find high-value products currently unavailable.

### 3. Potential Revenue Analysis

Estimate inventory value by category.

### 4. Expensive Products with Low Discounts

Identify premium products with minimal promotional activity.

### 5. Categories with Highest Average Discounts

Rank categories by average discount percentage.

### 6. Best Value Products

Calculate price per gram to identify cost-effective products.

### 7. Product Weight Segmentation

Classify products into:

* Low Weight
* Medium Weight
* Bulk Weight

### 8. Inventory Weight Analysis

Measure total inventory weight across categories.

---

## 🛠️ Skills Demonstrated

### SQL Concepts

* SELECT Statements
* Filtering & Sorting
* Aggregate Functions
* GROUP BY
* HAVING Clause
* CASE Statements
* Data Cleaning
* Data Transformation
* Business Analytics Queries

### Analytical Skills

* Exploratory Data Analysis
* Inventory Analysis
* Pricing Analysis
* Discount Analysis
* Revenue Estimation
* Business Problem Solving

---

## 📂 Project Structure

```text
Zepto-SQL-Data-Analysis/
│
├── data/
│   └── zepto_v2.csv
│
├── zepto_SQL_data_analysis.sql
│
├── README.md
│
└── screenshots/
```

---

## 🚀 How to Run This Project

### Step 1

Clone the repository:

```bash
git clone https://github.com/yourusername/Zepto-SQL-Data-Analysis.git
```

### Step 2

Create a PostgreSQL database.

### Step 3

Run the table creation script.

### Step 4

Import the CSV dataset.

### Step 5

Execute the SQL analysis queries.

### Step 6

Review generated insights and results.

---

## 📈 Future Improvements

Potential enhancements include:

* Power BI Dashboard
* Tableau Dashboard
* Inventory Forecasting
* Customer Purchase Analysis
* Product Recommendation Analytics
* Advanced SQL using CTEs and Window Functions

---

## 📜 License

You are free to use, modify, fork and distribute this project for educational and portfolio purposes.

---

### Connect With Me

* 💼 LinkedIn: [LinkedIn][https://www.linkedin.com/in/gajendra01/]
* 📧 Email: 📧 Email: [Email](mailto:gajendra.262001@gmail.com)

---

⭐ If you found this project helpful, consider giving the repository a star and sharing it with others learning SQL and data analytics.
