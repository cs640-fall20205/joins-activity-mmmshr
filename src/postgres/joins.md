# Postgres JOINS (Customer & Orders Example with PK/FK)

## Learning Objectives

Able to...

1. Understand INNER, LEFT, RIGHT, and FULL JOINS in PostgreSQL

---

## Model 1

**Customers**

| customer_id | customer_name |
| ----------- | ------------- |
| c1          | Alice         |
| c2          | Bob           |
| c3          | Carol         |
| c4          | David         |

**Orders**

| order_id | customer_id |
| -------- | ----------- |
| o1       | c1          |
| o2       | c2          |
| o5       | c5          |
| o6       | c6          |

Questions

1. Which customers have matching orders?
    The customers Alice and Bob have matching orders.

2. Which customers do not have any orders?
    The customers Carol and David do not have any orders.

3. Which orders do not match any existing customers?
    The orders o5 and o6 do not have any existing customers.

---

## Model 2

Query

```sql
SELECT c.customer_id, c.customer_name, o.order_id
FROM Customers c
INNER JOIN Orders o ON c.customer_id = o.customer_id;
```

Result
| customer_id | customer_name | order_id |
| ----------- | ------------- | -------- |
| c1	        | Alice	        | o1       |
| c2	        | Bob	          | o2       |

Questions

1. Which customers are not included in the result?
    The customers Carol and David are not included in the result.

2. Why do you think they are not in the result?
    As these two do not have an existing orders, we do not see them in the result.

3. Which orders are not included in the result?
    The orders o5 and o6 are not included in the result.

4. Why do you think they are not in the result?
    As these two do not have an existing customers, we do not see them in the result.

5. When is a row from Customers or Orders included?
    When the row has an order and an existing customer with matching customer_id then it is shown.

6. What is the meaning of INNER JOIN?
    When the join has a row with matching condition and has filled all columns.

---

## Model 3

Query

```sql
SELECT c.customer_id, c.customer_name, o.order_id
FROM Customers c
LEFT OUTER JOIN Orders o ON c.customer_id = o.customer_id;
```

Result
| customer_id | customer_name | order_id |
| ----------- | ------------- | -------- |
| c1          | Alice	        | o1       |
| c2	        | Bob	          | o2       |
| c3	        | Carol	        |          |
| c4	        | David	        |          |

Questions

1. Which customers are not included in the result?
    There are no customers left from the result.

2. Which orders are not included in the result?
    Orders 05 and 06 are left from the ressult.

3. When is a row included?
    A row iss included if it is a row of the customer table.

4. What is the meaning of LEFT OUTER JOIN?
    It returns all rows from the lefthand-side table and all rows that are matching from the righthand-side table in the matching condition.

---

## Model 4

Query

```sql
SELECT c.customer_id, c.customer_name, o.order_id
FROM Customers c
RIGHT OUTER JOIN Orders o ON c.customer_id = o.customer_id;
```

Result
| customer_id | customer_name | order_id |
| ----------- | ------------- | -------- |
| c1          | Alice	        | o1       |
| c2	        | Bob	          | o2       |
|   	        |      	        | o5       |
|   	        |     	        | o6       |


Questions

1. Which customers are not included in the result?
    Customers Carol and David are missing from the result.

2. Which orders are not included in the result?
    All orders are inculded in the result.

3. When is a row included?
    A row is included if it is a row in the orders table.

4. What is the meaning of RIGHT OUTER JOIN?
    It returns all rows from the righthand-side table and all rows that are matching from the lefthand-side table in the matching condition.


---

## Model 5

Query

```sql
SELECT c.customer_id, c.customer_name, o.order_id
FROM Customers c
FULL JOIN Orders o ON c.customer_id = o.customer_id;
```

Result
| customer_id | customer_name | order_id |
| ----------- | ------------- | -------- |
| c1          | Alice	        | o1       |
| c2	        | Bob	          | o2       |
| c3	        | Carol	        |          |
| c4	        | David	        |          |
|   	        |      	        | o5       |
|   	        |     	        | o6       |

Questions

1. Which customers are not included in the result?
     All customers are inculded in the result.

2. Which orders are not included in the result?
     All orders are inculded in the result.

3. When is a row included?
    All rows of both the tables are included.

4. What is the meaning of FULL JOIN?
    It returns all rows from both tables and when a row from one table has no match in the other, the missing side is filled with NULL.
---

## Model 6

Confirm the above by creating the tables in Postgres and running the queries. Paste the SQL for creating and populating the tables below.

```
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(50)
);

CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT
    -- no foreign key, so we can insert orders with non-existing customers
);

-- Customers
INSERT INTO Customers (customer_id, customer_name) VALUES
(1, 'Alice'),
(2, 'Bob'),
(3, 'Carol'),
(4, 'David');

-- Orders
INSERT INTO Orders (order_id, customer_id) VALUES
(1, 1),
(2, 2),
(5, 5),
(6, 6);


```
