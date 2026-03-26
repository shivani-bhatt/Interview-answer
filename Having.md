
# SQL `HAVING` Clause with `GROUP BY`

## What is the `HAVING` Clause?

The **`HAVING`** clause in SQL is used to **filter results of a `GROUP BY` query** based on aggregate functions, like `COUNT()`, `SUM()`, `AVG()`, etc.

> Unlike `WHERE`, which filters individual rows **before aggregation**, `HAVING` filters **groups after aggregation**.

---

## Syntax

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1
HAVING condition;
```

---

## Example: Using `HAVING` with `GROUP BY`

Suppose we have a table `orders`:

| id | customer_id | amount |
| -- | ----------- | ------ |
| 1  | 101         | 50     |
| 2  | 102         | 200    |
| 3  | 101         | 100    |
| 4  | 103         | 150    |
| 5  | 102         | 300    |

We want to **find customers whose total orders exceed 250**.

```sql
SELECT customer_id, SUM(amount) AS total_amount
FROM orders
GROUP BY customer_id
HAVING SUM(amount) > 250;
```

### Result

| customer_id | total_amount |
| ----------- | ------------ |
| 102         | 500          |

---

## 🔹 Key Points

* `WHERE` → filters **individual rows** before grouping
* `HAVING` → filters **groups** after aggregation
* Often used with aggregate functions like `SUM`, `COUNT`, `AVG`, `MAX`, `MIN`

---

Scenario
---

We have an Order entity with the following fields:

id → primary key
customerId → ID of the customer
amount → order amount

We want to find customers whose total order amount exceeds 250, just like the SQL example.




