# Retail Sales Analysis Using MySQL

## Project Overview
This project analyzes retail transaction data using MySQL to identify sales performance, monthly revenue trends, top-selling products, category performance, and customer value.

## Tools
- MySQL
- SQL
- GitHub

## Dataset
The dataset is a dummy retail transaction database consisting of:

- customers
- categories
- products
- orders
- order_items

## Skills Demonstrated
- SELECT, WHERE
- JOIN multi-table
- GROUP BY
- Aggregate functions
- Subquery
- CTE
- Window functions
- SQL View

## Database Schema

![Database Schema](screenshots/database_schema.png)

---

## Sample Data

### Customers Table

| customer_id | customer_name | city | gender |
|---|---|---|---|
| 1 | Customer 001 | Jakarta | Female |
| 2 | Customer 002 | Bandung | Male |
| 3 | Customer 003 | Surabaya | Female |

### Products Table

| product_id | product_name | category_id | price |
|---|---|---|---|
| 1 | Wireless Mouse | 1 | 85000 |
| 2 | Office Chair | 2 | 450000 |
| 3 | Notebook | 3 | 25000 |

## Analysis 1: Monthly Revenue Trend

### Business Question
How does monthly revenue change over time?

### SQL Query
SELECT 
    DATE_FORMAT(o.order_date, '%Y-%m') AS month,
    SUM(oi.quantity * oi.unit_price) AS total_revenue
FROM orders o
JOIN order_items oi ON o.order_id = oi.order_id
GROUP BY DATE_FORMAT(o.order_date, '%Y-%m')
ORDER BY month;
