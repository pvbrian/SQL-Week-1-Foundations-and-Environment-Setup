# Introduction to SQL

## 1. What is SQL?
- SQL (*Structured* Query Language) is a programming language used to communicate with databases.
- It helps you store, retrieve, manipulate, and manage data in a structured way.
* Think of it as the “language of data” – if data lives in a database, SQL is how you talk to it.*

## 2. Why SQL Matters
### For Data Analysts:
- Access to raw data from the database/warehouse: Analysts spend most of their time exploring and querying data to answer business questions.
- Faster insights: Instead of waiting for IT teams, analysts with SQL can directly pull data and create adhoc reports.
- Foundational skill for other tools: Almost all BI tools (Tableau, Power BI, Superset, Looker, Metabase) are powered by SQL.
- Universal language: Once you know SQL, you can work with most relational databases (MySQL, PostgreSQL, Snowflake, BigQuery, SQL Server).

### For Data Engineers:
- Data pipelines: Engineers use SQL in ETL/ELT processes to clean, transform, and load data.
- Modeling data: SQL is used to build clean, structured datasets for analysts and business users.
- Integration with tools: Modern tools like dbt, Airflow, SparkSQL, and BigQuery all rely heavily on SQL.
- Performance tuning: Engineers must write optimized SQL for large-scale data.

👉 In short:
- Analysts use SQL to consume data (analysis, reporting).
- Engineers use SQL to prepare data (pipelines, transformations).

## 3. Core SQL Concepts

### A. Relational Databases 
Data is stored in tables (Just like Excel sheets). These tables have rows (individual records) and columns (attributes of those records). 
In SQL, multiple tables are linked together through relationships using keys (e.g. a user_id in an orders table links back to a users table). This structure is what makes it "relational."

### B. The Four Core Operations in SQL: CRUD
Almost everything you (will) do in SQL falls into one of four categories:

- Create: INSERT data into a table.
- Read: SELECT data from a table (This is ~80% of what analysts do!).
- Update: UPDATE existing data in a table.
- Delete: DELETE data from a table.

### C. The SELECT Statement
This is your most important command. Its basic structure is logical and reads almost like English:
```sql
SELECT column_name1, column_name2   -- What do you want to see?
FROM table_name                      -- Where are you getting it from?
WHERE conditions;                    -- How do you want to filter it?
``` 
After that, We will build incredibly from this foundation by adding:

- JOIN: To combine data from two or more tables based on a related column. (e.g., Join orders with customers to see customer names next to their orders).
- AGGREGATION: Functions like COUNT(), SUM(), AVG(), MAX(), MIN() to perform calculations on groups of data.
- GROUP BY: To group rows that have the same values and run aggregates on them (e.g., "Total sales per country").
- HAVING: To filter the results of a GROUP BY (because you can't use WHERE on aggregated fields).
- ORDER BY: To sort your final results.
- LIMIT: To only return a specific number of rows (great for testing!).
- OFFSET: To remove a specific number of rows (depending on the order).

