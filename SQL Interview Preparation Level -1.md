# SQL Interview Preparation — Data Analyst Role

A topic-wise prep sheet. Each section lists the key concepts to review, followed by interview questions to practice answering on your own (no answers included — this is meant for active recall).

---

## 1. Core Querying Fundamentals

**Key Concepts:**
- `SELECT`, `WHERE`, `ORDER BY`, `GROUP BY`, `HAVING`
- Logical order of execution of a SQL query
- `WHERE` vs `HAVING`

**Interview Questions:**
1. What is the logical order of execution of the clauses in a SQL `SELECT` statement?
2. Explain the difference between `WHERE` and `HAVING`. Can you use `HAVING` without `GROUP BY`?
3. Write a query to find all employees in the `IT` department earning more than 50,000, sorted by salary descending.
4. Why does `WHERE COUNT(*) > 5` throw an error, but `HAVING COUNT(*) > 5` doesn't?
5. Can you filter on an aggregated column using `WHERE`? Why or why not?

---

## 2. Joins

**Key Concepts:**
- `INNER`, `LEFT`, `RIGHT`, `FULL OUTER` joins
- Self-joins
- Multi-table joins and fan-out / row duplication

**Interview Questions:**
1. What is the difference between an `INNER JOIN` and a `LEFT JOIN`? Give an example where the results would differ.
2. How would you find employees who share the same manager using a self-join?
3. You join three tables and suddenly your row count triples. What likely happened, and how would you debug it?
4. When would you use a `FULL OUTER JOIN` over a `LEFT JOIN`?
5. Write a query to find customers who have never placed an order (using a join, not a subquery).
6. What's the difference between joining on `ON` conditions versus filtering in `WHERE` after a `LEFT JOIN` — why does it matter?

---

## 3. Aggregate Functions

**Key Concepts:**
- `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`
- `COUNT(*)` vs `COUNT(column)` vs `COUNT(DISTINCT column)`

**Interview Questions:**
1. What's the difference between `COUNT(*)`, `COUNT(column_name)`, and `COUNT(DISTINCT column_name)`?
2. If a column has NULL values, how does `AVG()` handle them — does it treat NULLs as zero?
3. Write a query to find the number of unique customers who placed an order in the last 30 days.
4. How would you calculate both the total revenue and the average order value in a single query?
5. What happens if you run `SUM()` on a column that is entirely NULL?

---

## 4. Window Functions

**Key Concepts:**
- `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`
- `LAG()` / `LEAD()`
- Running totals / moving averages with `SUM() OVER (PARTITION BY ... ORDER BY ...)`
- Top-N-per-group pattern

**Interview Questions:**
1. What is the difference between `ROW_NUMBER()`, `RANK()`, and `DENSE_RANK()` when there are ties?
2. Write a query to find the top 3 highest-paid employees in each department.
3. How would you calculate the difference in sales between the current month and the previous month using a window function?
4. What does `PARTITION BY` do differently from `GROUP BY`?
5. Write a query to compute a 7-day moving average of daily sales.
6. Can you use a window function in a `WHERE` clause directly? If not, how do you work around it?

---

## 5. Subqueries and CTEs

**Key Concepts:**
- Correlated vs non-correlated subqueries
- `WITH` clause (CTEs)
- Breaking down multi-step logic

**Interview Questions:**
1. What is a correlated subquery, and how is it different from a regular subquery? Give an example.
2. Why might a CTE be preferred over a nested subquery for readability?
3. Write a query using a CTE to find departments where the average salary is above the company-wide average.
4. Can you reference one CTE inside another CTE in the same `WITH` clause?
5. What are the performance implications of using a correlated subquery on a large table?

---

## 6. Set Operations

**Key Concepts:**
- `UNION` vs `UNION ALL`
- `INTERSECT`, `EXCEPT` / `MINUS`

**Interview Questions:**
1. What's the difference between `UNION` and `UNION ALL`? Why is `UNION ALL` generally faster?
2. What requirements must two queries meet to be combined with `UNION`?
3. Write a query to find customer IDs that appear in this year's order table but not last year's, using a set operation.
4. When would you use `INTERSECT` instead of an `INNER JOIN`?

---

## 7. Data Cleaning / Manipulation

**Key Concepts:**
- `CASE WHEN`
- `NULL` handling: `COALESCE`, `IS NULL` / `IS NOT NULL`
- String functions (`SUBSTRING`, `TRIM`, `CONCAT`)
- Date functions (`DATEDIFF`, `EXTRACT`, date truncation)

**Interview Questions:**
1. How does `NULL` behave differently from other values in comparisons (e.g., `NULL = NULL`)?
2. Write a query using `CASE WHEN` to bucket customers into "high", "medium", and "low" spenders based on total purchase amount.
3. What does `COALESCE()` do, and how would you use it to handle missing values in a report?
4. How would you extract the year and month from a timestamp column in a way that's portable across databases?
5. Why can `NOT IN` silently return zero rows if the subquery result contains a `NULL`?

---

## 8. Query Optimization Basics

**Key Concepts:**
- What an index is and why it speeds up lookups
- Reading a basic execution plan
- Why `SELECT *` is discouraged in production

**Interview Questions:**
1. What is an index, and how does it improve query performance? What's the trade-off of adding too many indexes?
2. Why is `SELECT *` considered bad practice in production queries?
3. How would you go about diagnosing why a query is running slowly?
4. What's the difference between a clustered and a non-clustered index (conceptually)?
5. Would adding an index always speed up a query? When might it not help, or even hurt?

---

## 9. Classic Interview Problem Types

**Interview Questions:**
1. Write a query to find the second-highest salary in the `employees` table.
2. Write a query to find duplicate rows in a table based on a specific set of columns.
3. Write a query to find employees who earn more than their manager.
4. Write a query to calculate a running total of sales ordered by date.
5. Write a query to calculate month-over-month or year-over-year growth in revenue.
6. Write a query to calculate what percentage of users from a signup cohort returned within 30 days (a basic retention/cohort query).
7. Write a query to find the Nth-highest value in a column without using `LIMIT`/`OFFSET`.

---

*How to use this sheet: go topic by topic, answer each question out loud or on a whiteboard before checking any reference material. If you get stuck, that's your signal for where to go deeper.*
