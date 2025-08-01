# Sales-Insights-Data-Analysis-Using-Power-BI
Welcome to the Sales Data Analysis  project! This repository contains a complete data analysis workflow involving SQL for data extraction and transformation, and Power BI for interactive visualization and dashboarding.

## 🔍 Project Overview

This project showcases a data-driven approach to analyzing sales performance using structured queries and visual analytics. The main objective is to gain meaningful business insights from raw sales data through the following steps:

- Extracting and analyzing data using SQL
- Designing a clean and insightful Power BI dashboard



### Instructions to setup mysql on your local computer

1. Install mysql on your local computer

2. SQL database dump is in db_dump.sql file above. Download `db_dump.sql` file to your local computer and import it into mysql workbench.

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


