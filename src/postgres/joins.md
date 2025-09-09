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
2. Why do you think they are not in the result?
3. Which orders are not included in the result?
4. Why do you think they are not in the result?
5. When is a row from Customers or Orders included?
6. What is the meaning of INNER JOIN?

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
2. Which orders are not included in the result?
3. When is a row included?
4. What is the meaning of LEFT OUTER JOIN?

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
2. Which orders are not included in the result?
3. When is a row included?
4. What is the meaning of RIGHT OUTER JOIN?

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
2. Which orders are not included in the result?
3. When is a row included?
4. What is the meaning of FULL JOIN?

---

## Model 6

Confirm the above by creating the tables in Postgres and running the queries. Paste the SQL for creating and populating the tables below.

```sql

```
