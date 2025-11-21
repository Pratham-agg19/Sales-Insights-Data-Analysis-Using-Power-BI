# 📊 Sales Insights Data Analysis Using Power BI  
*A Complete BI Workflow: SQL Data Extraction → Transformation → Interactive Dashboards*

---

## 🌟 Introduction  
Welcome to the **Sales Insights Data Analysis** project!  
This repository contains a full **Business Intelligence (BI) pipeline** that transforms raw sales data into powerful, actionable insights using:

- 🗄️ **MySQL** – Data extraction, cleaning & transformation  
- 📈 **Power BI** – Interactive dashboarding & visualization  
- 🧩 **SQL Queries** – Core of analytical processing   

---

## 🔍 Project Overview

This project demonstrates how to turn unstructured sales data into meaningful business intelligence.  
The workflow includes:

### 🟦 **1. Data Extraction (SQL)**  
- Filtering sales transactions  
- Joining multiple relational tables  
- Handling missing and inconsistent data  
- Creating clean analytical datasets

### 🟧 **2. Data Transformation (SQL / Power BI)**  
- Outlier removal  
- Data smoothing  
- Defining calculated fields  
- Building measure tables in Power BI

### 🟩 **3. Data Visualization (Power BI)**  
- Dynamic dashboards  
- Slicers & interactive filters  
- Trend visuals for managerial decision-making

---

## 📊 Dashboard Highlights (Power BI)

✔ Total Revenue Overview  
✔ Sales Trends (Monthly / Quarterly / Yearly)  
✔ Top Customers & Top Markets  
✔ Product Performance Analysis  
✔ Region-Level Segmentation  


---

## 🛠️ SQL Setup (Optional)

To experiment with the dataset locally:

### 🧰 **Install MySQL**
- Install from official MySQL installer  
- Open **MySQL Workbench**  

### 📥 **Import the dataset**
1. Download the SQL dump file:  
   **`db_dump.sql`**  
2. In MySQL Workbench → `Server` → `Data Import`  
3. Import the file into a new schema  

### 📂  Data Analysis Using SQL
===========================

1. Show all customer records

    `SELECT * FROM customers;`

2. Show total number of customers

    `SELECT count(*) FROM customers;`

3. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

4. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

5. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

6. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

7. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
8. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

9. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


 📊 Data Analysis Using Power BI
==============================

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`


