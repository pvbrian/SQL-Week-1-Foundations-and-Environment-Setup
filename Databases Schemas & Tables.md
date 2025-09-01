# Database, Schema, and Data Types in SQL

### 1. Database defined:
- A database is like a container that stores and organizes data.
Think of it as a filing cabinet → inside, you have folders (schemas), and inside folders you have files (tables).
- In SQL, everything you query or create lives inside a database.

##### Creating a Database (PostgreSQL example):
```sql
-- Create a new database called 'shop_db'
CREATE DATABASE shop_db;

-- Switch to that database (in psql)
\c shop_db
```
### 2. Schema defined:
- A schema is a namespace inside a database that holds tables, views, functions, etc.
Think of it as a folder inside the filing cabinet.
- Helps organize objects logically (e.g., you might have a sales schema and a marketing schema in the same database).
#### Creating a Schema:
```sql
-- Inside 'shop_db', create a schema called 'sales'
CREATE SCHEMA sales;

-- Create another schema for HR
CREATE SCHEMA hr;
```
### 3. Creating a Table with Data Types

#### A. Let's talk about data types in SQL:
##### Essential SQL Data Types

Every column in a SQL table must have a defined **data type**. This ensures data integrity, optimizes storage efficiency, and enables correct operations.

1) Numeric Data Types

| Data Type | Storage | Description | Signed Range | Example Use Case |
|:----------|:--------|:------------|:-------------|:-----------------|
| **`TINYINT`** | 1 byte | A very small integer. Ideal for flags or status codes. | -128 to 127 | `status_code` (e.g., 1=active, 0=inactive) |
| **`SMALLINT`** | 2 bytes | A small integer. More efficient than `INT` for smaller numbers. | -32,768 to 32,767 | `age`, `small_quantity`, `year` |
| **`INT`** / **`INTEGER`** | 4 bytes | A standard whole number. The default choice for most integers. | -2.1B to 2.1B | `user_id`, `product_id`, `order_quantity` |
| **`BIGINT`** | 8 bytes | A very large integer. Use when `INT`'s range is insufficient. | -9.2Q to 9.2Q | `population_count`, `large_transaction_id` |
| **`SERIAL`**<br>(PostgreSQL) | 4 bytes | An auto-incrementing integer. **Perfect for primary keys.** | 1 to 2.1B | `id SERIAL PRIMARY KEY` |
| **`NUMERIC(p, s)`**<br>**`DECIMAL(p, s)`** | variable | Precise numbers with fixed decimal places. `p` = total digits, `s` = decimal digits. | Up to 131072 digits before decimal | `price NUMERIC(10, 2)`, `exchange_rate` |

2) Character/String Data Types

| Data Type | Description | Example Use Case |
|:----------|:------------|:-----------------|
| **`VARCHAR(n)`**<br>(**V**ariable **Char**acter) | Variable-length text with a maximum length `n`. **The best choice for most text.** | `username VARCHAR(50)`, `email VARCHAR(255)` |
| **`TEXT`** | Variable-length text with effectively no limit. Use for large blocks of text. | `product_description TEXT`, `blog_post TEXT` |
| **`CHAR(n)`**<br>(**Char**acter) | Fixed-length text. Always reserves space for `n` characters. Less common. | `country_code CHAR(2)` (e.g., 'US') |

3) Date/Time Data Types

| Data Type | Description | Example Format | Example Use Case |
|:----------|:------------|:---------------|:-----------------|
| **`DATE`** | Stores a date (year, month, day) without a time. | `'YYYY-MM-DD'` | `birth_date DATE`, `order_date DATE` |
| **`TIMESTAMP`** | Stores a date **and** a time (often with fractional seconds). | `'YYYY-MM-DD HH:MI:SS'` | `created_at TIMESTAMP`, `login_time` |
| **`TIMESTAMPTZ`**<br>(PostgreSQL) | Stores a timestamp with a **time zone**. | `'YYYY-MM-DD HH:MI:SS+TZ'` | `event_time TIMESTAMPTZ` for global apps |
| **`TIME`** | Stores a time of day without a date. | `'HH:MI:SS'` | `business_opening_time TIME` |

4) Other Essential Types

| Data Type | Description | Example Use Case |
|:----------|:------------|:-----------------|
| **`BOOLEAN`** | Represents a logical truth value. | `is_active BOOLEAN`, `is_completed BOOLEAN` |
| **`NULL`** | A special marker meaning "unknown" or "missing data." It is not zero or an empty string. | A `middle_name` column for a user who doesn't have one. |

---

#### Key Considerations:

*   **Storage:** Choose the smallest data type that comfortably fits your data (e.g., use `SMALLINT` for an "age" column). This improves performance.
*   **Integrity:** Data types prevent invalid data. You cannot insert the text "hello" into an `INT` column.
*   **`VARCHAR` vs. `TEXT`:** For short strings (names, emails), use `VARCHAR(n)`. For potentially very long text, use `TEXT`.
*   **Phone Numbers & ZIP Codes:** Always store these as `VARCHAR`, not a numeric type, to preserve formatting (dashes, plus signs, leading zeros).

#### B. Creating Tables in SQL
Example
```sql
CREATE TABLE school.students (
    student_id SERIAL PRIMARY KEY,  -- Auto-generated ID
    first_name VARCHAR(50) NOT NULL, -- String up to 50 characters
    last_name VARCHAR(50) NOT NULL,
    admission_date DATE NOT NULL,         -- Stores date
    age SMALLINT,     
    is_active BOOLEAN DEFAULT TRUE   -- True/False
);
```

#### C. Inserting Data Into Tables
Example
```sql
INSERT INTO students (first_name, last_name, admission_date, age, is_active)
VALUES
('Celestine', 'Mwende', '2025-01-01', 25, TRUE),
('Collins', 'Kilonzo', '2025-01-31', 27, TRUE),
('Brian', 'Otieno', '2025-04-28', 27, FALSE)
```


