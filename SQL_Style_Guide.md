# Table of Contents
1. [Introduction](#1-introduction)
2. [Principles and Goals](#2-principles-and-goals)
3. [Capitalization and Case Rules](#3-capitalization-and-case-rules)
4. [Naming Conventions](#4-naming-conventions)
5. [Formatting Queries](#5-formatting-queries)
6. [Comments and Documentation](#6-comments-and-documentation)
7. [Wring secure and perfomant SQL](7-#wring-secure-and-perfomant-sql)
8. [Tooling and Automation](#8-tooling-and-automation)
9. [Common Pitfalls and Anti-Patterns](#9-common-pitfalls-and-anti-patterns)

10.[Glossary and Resources](#10-glossary-and-resources)


## 1. Introduction
SQL (Structured Query Language) is the backbone of data manipulation in relational databases. It powers everything from dashboards to real-time analytics and machine learning feature engineering. Poorly written SQL can degrade performance, increase debugging time, and introduce subtle bugs into your data products.

This guide promotes writing SQL that is:

- Clear to read and reason about
- Consistent across teams and projects
- Performant even on large datasets
- Easily maintainable and testable


## 2. Principles and Goals
- Clarity over cleverness
- Consistency over convenience
- Documentation is not optional
- Simplicity scales


## 3. Capitalization and Case Rules
- ✅ SQL keywords in UPPERCASE
- ✅ Identifiers in snake_case

-- Good
```sql 
SELECT user_id, full_name FROM users WHERE is_active = TRUE;
```

-- Bad
``` sql 
select UserID, FullName from Users where IsActive = true;
```


## 4. Naming Conventions
| Type    | Convention     | Example                  |
|---------|----------------|--------------------------|
| Table   | singular, noun | order, user              |
| Column  | snake_case     | created_at               |
| Boolean | is_, has_      | is_active, has_paid      |
| Index   | idx_ prefix    | idx_orders_user_id       |



## 5. Formatting Queries

Structure queries with indentation and clarity:
```sql
SELECT
    o.order_id,
    o.total_amount,
    u.email
FROM
    orders o
INNER JOIN users u ON o.user_id = u.user_id
WHERE
    o.status = 'delivered'
    AND o.created_at >= CURRENT_DATE - INTERVAL '30 days'
ORDER BY
    o.created_at DESC;
```


## 6. Comments and Documentation

- Use -- for line comments. Explain intent, not syntax:

```sql
-- Get total revenue for the last 30 days
SELECT SUM(total_amount) FROM orders WHERE created_at > CURRENT_DATE - INTERVAL '30 days';
```

- Use Block comments /* block texts */

```sql
/*Calculates LTV for customers acquired in the last year
   Uses first 365 days of revenue as a proxy */
WITH yearly_revenue AS (
    SELECT
        user_id,
        SUM(amount) AS revenue_365d
    FROM transactions
    WHERE transaction_date <= DATE_ADD(signup_date, INTERVAL 365 DAY)
    GROUP BY user_id
)
SELECT
    cohort_year,
    AVG(revenue_365d) AS avg_ltv
FROM yearly_revenue
```


## 7.Writing Secure and Performant SQL
- Avoid SELECT *
- Never trust user input in raw SQL
- Use LIMIT when exploring data to avoid huge scans


## 8. Tooling and Automation
- SQLFluff — syntax linter and formatter
- DBT — analytics engineering framework
- DBeaver/DataGrip — SQL IDEs
- Airflow — orchestration
- Metabase/Superset — BI dashboards


## 9. Common Pitfalls and Anti-Patterns
- SELECT * ❌
- Complex logic in JOIN ON ❌
- Not handling NULL explicitly ❌
- Unindexed filter columns ❌
- Using aggregation but missing grouping columns ❌


## 10.Glossary and Abbreviations
- DDL: Data Definition Language
- DML: Data Manipulation Language
- CTE: Common Table Expression
- PK: Primary Key
- FK: Foreign Key
- CRUD: Create Read Update Delete







