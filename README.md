# Data-Analysis-Project-Tableau-
Use Tableau to create dash board for sales insights of company, Use SQL database to get data.

# Sales Insights Data Analysis Project
Setting Up MySQL Locally

To get started with MySQL on your local machine, follow this 
## installation guide:- https://www.youtube.com/watch?v=WuBcTJnIuzo.

Install MySQL: Use the video tutorial to guide you through the installation process.
Import the Database: Download the db_dump.sql file from this repository. Follow the instructions in the tutorial to import this file into your MySQL database.

# SQL Data Analysis
Execute the following SQL queries for your data analysis:

## 1. Retrieve all customer records:
    SELECT * FROM customers;

## 2. Count the total number of customers:
    SELECT COUNT(*) FROM customers;

## 3. Get transactions for the Chennai market (market code: Mark001):
    SELECT * FROM transactions WHERE market_code = 'Mark001';

## 4. List distinct product codes sold in Chennai:
    SELECT DISTINCT product_code FROM transactions WHERE market_code = 'Mark001';

## 5. Fetch transactions where the currency is USD:
    SELECT * FROM transactions WHERE currency = 'USD';

## 6. Show 2020 transactions joined with the date table:
    SELECT transactions.*, date.* 
    FROM transactions 
    INNER JOIN date ON transactions.order_date = date.date 
    WHERE date.year = 2020;

## 7. Calculate total revenue for the year 2020:
    SELECT SUM(transactions.sales_amount) 
    FROM transactions 
    INNER JOIN date ON transactions.order_date = date.date 
    WHERE date.year = 2020 
     AND (transactions.currency = 'INR' OR transactions.currency = 'USD');
   
## 8. Calculate total revenue for January 2020:
    SELECT SUM(transactions.sales_amount) 
    FROM transactions 
    INNER JOIN date ON transactions.order_date = date.date 
    WHERE date.year = 2020 
     AND date.month_name = 'January' 
     AND (transactions.currency = 'INR' OR transactions.currency = 'USD');

## 9. Calculate total revenue in Chennai for 2020:
    SELECT SUM(transactions.sales_amount) 
    FROM transactions 
    INNER JOIN date ON transactions.order_date = date.date 
    WHERE date.year = 2020 
       AND transactions.market_code = 'Mark001';

   # Power BI Data Analysis
   To add a norm_amount column in Power BI, use this formula:
   = Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] = "USD#(cr)" then [sales_amount] * 75 else [sales_amount], type any)



    


