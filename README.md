 task-6

 SalesTrendAnalysis
Sales Trend Analysis using SQL 

📌 Objective
To analyze monthly revenue and order volume using SQL aggregate functions such as SUM(), COUNT(), GROUP BY, and ORDER BY.

📂 Dataset Used
Table Name: orders
Columns:
order_id
order_date
product_id
amount
🛠 SQL Queries Used
📌 1. Monthly Revenue and Order Volume
SELECT
    STRFTIME('%Y', order_date) AS year,
    STRFTIME('%m', order_date) AS month,
    SUM(COALESCE(amount, 0)) AS monthly_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM orders
WHERE order_date IS NOT NULL
GROUP BY year, month
ORDER BY year, month;

📌 2. Top 3 Months with Highest Revenue
sql
Copy code
SELECT
    year,
    month,
    monthly_revenue
FROM (
    SELECT
        STRFTIME('%Y', order_date) AS year,
        STRFTIME('%m', order_date) AS month,
        SUM(COALESCE(amount, 0)) AS monthly_revenue
    FROM orders
    GROUP BY year, month
) AS summary
ORDER BY monthly_revenue DESC
LIMIT 3;


