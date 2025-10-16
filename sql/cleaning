--ORDER TABLE

-- Check duplicate order_id
SELECT order_id, COUNT(*) 
FROM orders 
GROUP BY order_id 
HAVING COUNT(*) > 1;

-- no duplicate

-- check for date format
SELECT created_at, returned_at, delivered_at
FROM orders
WHERE returned_at IS NOT NULL AND delivered_at IS NOT NULL
LIMIT 10;

-- ALL format is same

--CHECK logical date

-- check if there is order shipped before order bean created.
SELECT *
FROM orders
WHERE datetime(shipped_at) < datetime(created_at);
-- no error

--check if there is delivery before shipped
SELECT *
FROM orders
WHERE datetime(delivered_at) < datetime(shipped_at);
-- no error

-- check if return date happen before delivery
SELECT *
FROM orders
WHERE returned_at IS NOT NULL
  AND datetime(returned_at) < datetime(delivered_at);
-- no error

--check null VALUES
SELECT 
    SUM(created_at IS NULL) AS missing_created,
    SUM(returned_at IS NULL) AS missing_returned,
    SUM(shipped_at IS NULL) AS missing_shipped,
    SUM(delivered_at IS NULL) AS missing_delivered,
    SUM(gender IS NULL OR TRIM(gender) = '') AS missing_gender,
    SUM(num_of_item IS NULL) AS missing_num_of_item
FROM orders;

-- there is missing value at returned_at, shipped_at, and delivered_at which might indicate cancelled transaction, hence it let is as it is

--check for standardized value for status gender

SELECT DISTINCT status FROM orders;
-- only contain Cancelled, Complete, Processing, Returned, Shipped
SELECT DISTINCT gender FROM orders;
--only contain F and M

-- Check if there is 0 value in num_of_item
SELECT *
FROM orders
WHERE num_of_item <= 0;
-- no error
