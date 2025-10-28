# 📜 SQL Cheatsheet

This cheatsheet focuses on the core commands for managing data and schema, perfect for working with backend APIs.
[PostgreSQL SQL Documentation](https://www.postgresql.org/docs/current/sql.html)

## Data Definition Language (DDL)

```sql
-- Creating and Deleting Structures

-- Create a new database table
CREATE TABLE table_name (
    column_name1 data_type [CONSTRAINTS], -- e.g., INTEGER PRIMARY KEY, NOT NULL
    column_name2 data_type [CONSTRAINTS],
    -- Example column with common constraints:
    user_id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    created_at TIMESTAMP WITHOUT TIME ZONE DEFAULT NOW()
);

-- Change the structure of an existing table
ALTER TABLE table_name
ADD COLUMN new_column_name data_type;

ALTER TABLE table_name
DROP COLUMN column_to_drop;

ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;

-- Delete an entire table (schema and data)
DROP TABLE table_name;

-- Remove all data from a table, but keep the structure
TRUNCATE TABLE table_name;
```

## Data Manipulation Language (DML)

```sql
-- CRUD Operations (Create, Read, Update, Delete)

-- C - Create/Insert: Add new rows to a table
INSERT INTO table_name (column1, column2)
VALUES (value1, value2), (value3, value4);

-- R - Read/Select: Retrieve data from a table
SELECT column1, column2 FROM table_name
WHERE condition -- Optional: Filter the rows
ORDER BY column1 DESC -- Optional: Sort the results (ASC is default)
LIMIT 10 -- Optional: Restrict the number of rows returned
OFFSET 5; -- Optional: Skip a number of rows

-- Select all columns
SELECT * FROM table_name;

-- U - Update: Modify existing data
UPDATE table_name
SET column1 = new_value, column2 = another_new_value
WHERE condition; -- Crucial: Specify which rows to update

-- D - Delete: Remove rows from a table
DELETE FROM table_name
WHERE condition; -- Crucial: Specify which rows to delete
```

## Data Filtering, Joins, and Grouping

```sql
-- Filtering with WHERE
SELECT * FROM users
WHERE age > 25 AND city = 'New York';

SELECT * FROM products
WHERE category IN ('Electronics', 'Apparel');

SELECT * FROM orders
WHERE order_date BETWEEN '2025-01-01' AND '2025-12-31';

SELECT * FROM customers
WHERE email LIKE '%@gmail.com'; -- Wildcard matching

-- Joining Tables
-- Retrieve users and their corresponding orders (only matching records)
SELECT u.username, o.order_id, o.amount
FROM users u
INNER JOIN orders o ON u.user_id = o.user_id;

-- Retrieve all users, and their orders if they have any (users without orders will show NULL for order columns)
SELECT *
FROM users u
LEFT JOIN orders o ON u.user_id = o.user_id;

-- Aggregation and Grouping
-- Count the total number of orders per user
SELECT user_id, COUNT(order_id) AS total_orders
FROM orders
GROUP BY user_id
HAVING COUNT(order_id) > 5; -- Filter groups (after aggregation)
```

## Common Built-in Functions

```sql
# PostgreSQL (and most SQL dialects) offers useful functions for data manipulation.

-- String Functions
SELECT UPPER(product_name), LENGTH(product_name) FROM products;
SELECT TRIM(leading ' ' FROM '  data ');

-- Numeric/Math Functions
SELECT ROUND(price, 2) FROM products;
SELECT AVG(price) AS average_price FROM products;
SELECT SUM(quantity) AS total_sold, MAX(price) AS max_price FROM order_items;

-- Date and Time Functions (PostgreSQL examples)
SELECT NOW(); -- Current date and time
SELECT CURRENT_DATE; -- Current date
SELECT EXTRACT(YEAR FROM order_date) AS order_year FROM orders;
SELECT order_date + INTERVAL '1 day' FROM orders; -- Add one day
```
