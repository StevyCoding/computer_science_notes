# FreeCodeCamp Course (6-hour) | Based on "Grokking Relational Database Design"

**Authors:** Dr. Qiang Hao & Dr. Michael Tsikerdekis (Western Washington University)

---
## Table of content

- [[#1. SQL Fundamentals|1. SQL Fundamentals]]
	- [[#1. SQL Fundamentals#🔹 Basic SQL Commands|🔹 Basic SQL Commands]]
		- [[#🔹 Basic SQL Commands#Tables, Entities, and Keys|Tables, Entities, and Keys]]
		- [[#🔹 Basic SQL Commands#SQL Filtering & Aggregation|SQL Filtering & Aggregation]]
		- [[#🔹 Basic SQL Commands#SQL Table Commands|SQL Table Commands]]
	- [[#1. SQL Fundamentals#🔹 Foreign Keys in SQL|🔹 Foreign Keys in SQL]]
	- [[#1. SQL Fundamentals#🔹 How SQL JOINs Work|🔹 How SQL JOINs Work]]
- [[#2. Database Design Goals & Lifecycle|2. Database Design Goals & Lifecycle]]
	- [[#2. Database Design Goals & Lifecycle#🎯 Database Design Goals|🎯 Database Design Goals]]
	- [[#2. Database Design Goals & Lifecycle#🔄 Database Design Lifecycle|🔄 Database Design Lifecycle]]
	- [[#2. Database Design Goals & Lifecycle#📝 From Real-World Ideas to Tables|📝 From Real-World Ideas to Tables]]
- [[#3. Entity-Relationship (ER) Modeling|3. Entity-Relationship (ER) Modeling]]
	- [[#3. Entity-Relationship (ER) Modeling#🔸 ER Diagram Components|🔸 ER Diagram Components]]
	- [[#3. Entity-Relationship (ER) Modeling#🔸 Connecting Entities in an ER Diagram|🔸 Connecting Entities in an ER Diagram]]
	- [[#3. Entity-Relationship (ER) Modeling#🔸 One-to-One Relationships (1:1)|🔸 One-to-One Relationships (1:1)]]
	- [[#3. Entity-Relationship (ER) Modeling#🔸 One-to-Many Relationships (1:N)|🔸 One-to-Many Relationships (1:N)]]
	- [[#3. Entity-Relationship (ER) Modeling#🔸 Many-to-Many Relationships (M:N)|🔸 Many-to-Many Relationships (M:N)]]
	- [[#3. Entity-Relationship (ER) Modeling#🔸 Strong vs Weak Entities|🔸 Strong vs Weak Entities]]
- [[#4. Keys & Constraints|4. Keys & Constraints]]
	- [[#4. Keys & Constraints#🔑 Types of Keys|🔑 Types of Keys]]
		- [[#🔑 Types of Keys#Primary Key, Candidate Key, and Super Key|Primary Key, Candidate Key, and Super Key]]
		- [[#🔑 Types of Keys#Composite Keys|Composite Keys]]
	- [[#4. Keys & Constraints#🔒 Constraints|🔒 Constraints]]
		- [[#🔒 Constraints#Primary Key vs Unique Constraints|Primary Key vs Unique Constraints]]
		- [[#🔒 Constraints#Foreign Key Constraints - ON DELETE & ON UPDATE|Foreign Key Constraints - ON DELETE & ON UPDATE]]
		- [[#🔒 Constraints#Other Constraints: NOT NULL, DEFAULT, and CHECK|Other Constraints: NOT NULL, DEFAULT, and CHECK]]
- [[#5. Data Types|5. Data Types]]
	- [[#5. Data Types#⚠️ Common Data Type Mistakes|⚠️ Common Data Type Mistakes]]
		- [[#⚠️ Common Data Type Mistakes#Don't Use the Wrong SQL String Type|Don't Use the Wrong SQL String Type]]
		- [[#⚠️ Common Data Type Mistakes#The FLOAT Mistake That Crashed a Stock Exchange|The FLOAT Mistake That Crashed a Stock Exchange]]
		- [[#⚠️ Common Data Type Mistakes#SQL Date and Time Types Explained|SQL Date and Time Types Explained]]
- [[#6. Normalization (1NF → BCNF)|6. Normalization (1NF → BCNF)]]
	- [[#6. Normalization (1NF → BCNF)#📐 Anomalies (Problems Normalization Solves)|📐 Anomalies (Problems Normalization Solves)]]
	- [[#6. Normalization (1NF → BCNF)#1️⃣ First Normal Form (1NF)|1️⃣ First Normal Form (1NF)]]
	- [[#6. Normalization (1NF → BCNF)#2️⃣ Second Normal Form (2NF)|2️⃣ Second Normal Form (2NF)]]
	- [[#6. Normalization (1NF → BCNF)#3️⃣ Third Normal Form (3NF)|3️⃣ Third Normal Form (3NF)]]
	- [[#6. Normalization (1NF → BCNF)#🔺 Boyce-Codd Normal Form (BCNF) - The Untold Story|🔺 Boyce-Codd Normal Form (BCNF) - The Untold Story]]
	- [[#6. Normalization (1NF → BCNF)#📊 Normalization Quick Reference|📊 Normalization Quick Reference]]
- [[#7. Indexing Strategies|7. Indexing Strategies]]
	- [[#7. Indexing Strategies#📇 What is an Index?|📇 What is an Index?]]
	- [[#7. Indexing Strategies#🌲 B-Tree vs Full-Text Indexes|🌲 B-Tree vs Full-Text Indexes]]
		- [[#🌲 B-Tree vs Full-Text Indexes#B-Tree Indexes (Default)|B-Tree Indexes (Default)]]
		- [[#🌲 B-Tree vs Full-Text Indexes#Full-Text Indexes|Full-Text Indexes]]
	- [[#7. Indexing Strategies#🎯 Indexing Best Practices|🎯 Indexing Best Practices]]
- [[#8. Security & Access Control|8. Security & Access Control]]
	- [[#8. Security & Access Control#🔐 Access Control, Hashing & Encryption|🔐 Access Control, Hashing & Encryption]]
		- [[#🔐 Access Control, Hashing & Encryption#User Management & Privileges|User Management & Privileges]]
		- [[#🔐 Access Control, Hashing & Encryption#Password Hashing|Password Hashing]]
		- [[#🔐 Access Control, Hashing & Encryption#Encryption|Encryption]]
		- [[#🔐 Access Control, Hashing & Encryption#SQL Injection Prevention|SQL Injection Prevention]]
- [[#9. Query Optimization|9. Query Optimization]]
	- [[#9. Query Optimization#⚡ Denormalization|⚡ Denormalization]]
	- [[#9. Query Optimization#🚀 General Query Optimization Tips|🚀 General Query Optimization Tips]]
- [[#📝 How to Learn SQL on Your Own|📝 How to Learn SQL on Your Own]]
	- [[#📝 How to Learn SQL on Your Own#🎓 Learning Roadmap|🎓 Learning Roadmap]]
	- [[#📝 How to Learn SQL on Your Own#🛠️ Recommended Tools|🛠️ Recommended Tools]]
	- [[#📝 How to Learn SQL on Your Own#📚 Learning Resources|📚 Learning Resources]]
	- [[#📝 How to Learn SQL on Your Own#💡 Study Tips|💡 Study Tips]]
- [[#🎯 Summary: Database Design Principles|🎯 Summary: Database Design Principles]]
	- [[#🎯 Summary: Database Design Principles#✅ DO's|✅ DO's]]
	- [[#🎯 Summary: Database Design Principles#❌ DON'Ts|❌ DON'Ts]]
- [[#🔍 Quick Reference Tables|🔍 Quick Reference Tables]]
	- [[#🔍 Quick Reference Tables#SQL Command Categories|SQL Command Categories]]
	- [[#🔍 Quick Reference Tables#Normal Forms Summary|Normal Forms Summary]]
	- [[#🔍 Quick Reference Tables#Join Types Quick Reference|Join Types Quick Reference]]
	- [[#🔍 Quick Reference Tables#Constraint Types|Constraint Types]]
- [[#🎓 Final Exam Self-Check|🎓 Final Exam Self-Check]]
- [[#🎉 Conclusion|🎉 Conclusion]]

## 1. SQL Fundamentals

### 🔹 Basic SQL Commands

#### Tables, Entities, and Keys

**Table:** A structured collection of data organized in rows and columns

- **Row (Record/Tuple):** A single entry in a table
- **Column (Attribute/Field):** A property or characteristic of the entity

```sql
-- CREATE TABLE syntax
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(10, 2),
    stock INT DEFAULT 0
);
```

#### SQL Filtering & Aggregation

```sql
-- WHERE clause - filtering
SELECT name, price 
FROM products 
WHERE price > 20;

-- Aggregate functions
SELECT 
    COUNT(*) as total_products,
    AVG(price) as avg_price,
    MAX(price) as max_price,
    MIN(price) as min_price,
    SUM(stock) as total_stock
FROM products;

-- GROUP BY - grouping data
SELECT category, COUNT(*) as count
FROM products
GROUP BY category
HAVING COUNT(*) > 5;

-- ORDER BY - sorting
SELECT name, price
FROM products
ORDER BY price DESC, name ASC;
```

#### SQL Table Commands

```sql
-- ALTER TABLE - modify structure
ALTER TABLE products
ADD COLUMN description TEXT;

ALTER TABLE products
DROP COLUMN description;

ALTER TABLE products
MODIFY COLUMN price DECIMAL(12, 2);

-- DROP TABLE - delete table
DROP TABLE products;

-- TRUNCATE - remove all data but keep structure
TRUNCATE TABLE products;

-- INSERT - add data
INSERT INTO products (name, price, stock)
VALUES ('Widget', 19.99, 100);

-- UPDATE - modify data
UPDATE products
SET price = price * 1.1
WHERE category = 'Electronics';

-- DELETE - remove data
DELETE FROM products
WHERE stock = 0;
```

### 🔹 Foreign Keys in SQL

**Foreign Key:** A field that links one table to another by referencing a primary key

```sql
-- Creating a table with foreign key
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

-- Foreign key with actions
CREATE TABLE order_items (
    item_id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    FOREIGN KEY (order_id) 
        REFERENCES orders(order_id)
        ON DELETE CASCADE
        ON UPDATE CASCADE,
    FOREIGN KEY (product_id)
        REFERENCES products(product_id)
        ON DELETE RESTRICT
        ON UPDATE CASCADE
);
```

**ON DELETE/UPDATE Actions:**

- `CASCADE`: Automatically delete/update related rows
- `SET NULL`: Set foreign key to NULL
- `SET DEFAULT`: Set to default value
- `RESTRICT/NO ACTION`: Prevent deletion/update if referenced

### 🔹 How SQL JOINs Work

```sql
-- INNER JOIN - only matching records
SELECT o.order_id, c.name, o.order_date
FROM orders o
INNER JOIN customers c ON o.customer_id = c.customer_id;

-- LEFT JOIN - all from left table + matches from right
SELECT c.name, o.order_id
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id;

-- RIGHT JOIN - all from right table + matches from left
SELECT o.order_id, c.name
FROM orders o
RIGHT JOIN customers c ON o.customer_id = c.customer_id;

-- FULL OUTER JOIN - all records from both tables
SELECT c.name, o.order_id
FROM customers c
FULL OUTER JOIN orders o ON c.customer_id = o.customer_id;

-- CROSS JOIN - Cartesian product (all combinations)
SELECT p.name, c.color
FROM products p
CROSS JOIN colors c;

-- SELF JOIN - join table to itself
SELECT e1.name as employee, e2.name as manager
FROM employees e1
LEFT JOIN employees e2 ON e1.manager_id = e2.employee_id;
```

**JOIN Visual Summary:**

- **INNER JOIN:** A ∩ B (intersection)
- **LEFT JOIN:** A + (A ∩ B)
- **RIGHT JOIN:** B + (A ∩ B)
- **FULL OUTER JOIN:** A ∪ B (union)

---

## 2. Database Design Goals & Lifecycle

### 🎯 Database Design Goals

1. **Data Consistency:** Ensure data accuracy across all tables
2. **Data Integrity:** Maintain correctness and validity of data
3. **Maintainability:** Easy to update and modify schema
4. **Performance:** Fast queries and efficient data retrieval
5. **Security:** Protect data from unauthorized access
6. **Scalability:** Handle growing amounts of data

### 🔄 Database Design Lifecycle

**Phase 1: Requirements Analysis**

- Gather stakeholder requirements
- Identify subjects, characteristics, and relationships
- Document business rules

**Phase 2: Conceptual Design**

- Create Entity-Relationship (ER) diagrams
- Define entities and their relationships
- Identify attributes for each entity

**Phase 3: Logical Design**

- Convert ER diagram to tables
- Apply normalization (1NF → BCNF)
- Define primary keys, foreign keys

**Phase 4: Physical Design**

- Choose data types
- Define indexes
- Set up constraints
- Optimize for performance

**Phase 5: Implementation**

- Write DDL (Data Definition Language) scripts
- Create database and tables
- Set up users and permissions

**Phase 6: Testing & Refinement**

- Test queries and transactions
- Monitor performance
- Optimize based on usage patterns

### 📝 From Real-World Ideas to Tables

**Process:**

1. **Identify Entities:** Nouns in requirements (Customer, Order, Product)
2. **Identify Attributes:** Properties of entities (name, email, price)
3. **Identify Relationships:** How entities relate (Customer places Order)
4. **Determine Cardinality:** One-to-one, one-to-many, many-to-many
5. **Normalize:** Apply normal forms to eliminate redundancy

**Example:**

```
Requirement: "Customers place orders for products"

Entities:
- Customer (customer_id, name, email)
- Order (order_id, order_date, customer_id)
- Product (product_id, name, price)
- OrderItem (order_id, product_id, quantity) [junction table]
```

---

## 3. Entity-Relationship (ER) Modeling

### 🔸 ER Diagram Components

**Entity:** A thing or object (represented as rectangle) **Attribute:** Property of entity (represented as oval) **Relationship:** Connection between entities (represented as diamond)

**ER Diagram Notation:**

```
┌─────────────┐
│   Entity    │  Rectangle = Entity
└─────────────┘

    (Attr)       Oval = Attribute

◇───Relationship   Diamond = Relationship
```

### 🔸 Connecting Entities in an ER Diagram

**Cardinality Notation:**

- `1` : Exactly one
- `0..1` : Zero or one
- `1..*` : One or more
- `0..*` or `*` : Zero or more

### 🔸 One-to-One Relationships (1:1)

**Definition:** Each record in Table A relates to exactly one record in Table B

**Example:** Person ↔ Passport

```sql
CREATE TABLE persons (
    person_id INT PRIMARY KEY,
    name VARCHAR(100),
    birth_date DATE
);

CREATE TABLE passports (
    passport_id INT PRIMARY KEY,
    passport_number VARCHAR(20) UNIQUE,
    person_id INT UNIQUE,  -- UNIQUE ensures 1:1
    FOREIGN KEY (person_id) REFERENCES persons(person_id)
);
```

**When to Use:**

- Separate sensitive data (Person vs. PasswordHash)
- Optional extensions (Product vs. ProductDetails)
- Performance optimization (frequently vs. rarely accessed data)

### 🔸 One-to-Many Relationships (1:N)

**Definition:** Each record in Table A can relate to multiple records in Table B

**Example:** Customer → Orders (one customer has many orders)

```sql
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,  -- Foreign key (no UNIQUE = many allowed)
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

**Most Common Relationship Type**

### 🔸 Many-to-Many Relationships (M:N)

**Definition:** Records in Table A can relate to multiple records in Table B and vice versa

**Example:** Students ↔ Courses (students take many courses, courses have many students)

**Solution:** Create a **junction table** (also called associative table, bridge table)

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100)
);

-- Junction table breaks M:N into two 1:N relationships
CREATE TABLE enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    enrollment_date DATE,
    grade CHAR(2),
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id),
    UNIQUE(student_id, course_id)  -- Prevent duplicate enrollments
);
```

### 🔸 Strong vs Weak Entities

**Strong Entity:**

- Can exist independently
- Has its own primary key
- Example: Customer, Product

**Weak Entity:**

- Cannot exist without a strong entity (owner)
- Depends on another entity for identification
- Partial key + owner's key = composite primary key
- Example: OrderItem (depends on Order)

```sql
-- Order is a STRONG entity
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATE
);

-- OrderItem is a WEAK entity (depends on Order)
CREATE TABLE order_items (
    order_id INT,           -- Part of composite key (from owner)
    item_sequence INT,      -- Partial key (unique within order)
    product_id INT,
    quantity INT,
    PRIMARY KEY (order_id, item_sequence),  -- Composite key
    FOREIGN KEY (order_id) REFERENCES orders(order_id) ON DELETE CASCADE
);
```

**Characteristics of Weak Entities:**

- Always has a total participation in relationship with owner
- Uses double rectangle in ER diagrams
- DELETE CASCADE is typical (if owner deleted, weak entity deleted)

---

## 4. Keys & Constraints

### 🔑 Types of Keys

#### Primary Key, Candidate Key, and Super Key

**Super Key:**

- Any combination of columns that uniquely identifies a row
- Example: `{student_id}`, `{student_id, name}`, `{email}`, `{email, phone}`

**Candidate Key:**

- Minimal super key (no redundant columns)
- Example: `{student_id}`, `{email}` (but NOT `{student_id, name}`)

**Primary Key:**

- The chosen candidate key
- Only ONE per table
- Cannot be NULL
- Should be immutable (doesn't change)

```sql
-- Natural primary key (business meaning)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,  -- Natural key
    email VARCHAR(100) UNIQUE,    -- Candidate key
    ssn CHAR(11) UNIQUE           -- Candidate key
);

-- Surrogate primary key (no business meaning)
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,  -- Auto-increment surrogate key
    order_date DATE,
    customer_id INT
);
```

**Natural vs Surrogate Keys:**

- **Natural Key:** Has business meaning (SSN, email, ISBN)
    - Pros: Meaningful, self-documenting
    - Cons: Can change, may be lengthy
- **Surrogate Key:** Artificial identifier (auto-increment ID)
    - Pros: Immutable, short, simple
    - Cons: No business meaning

#### Composite Keys

**Definition:** Primary key made of multiple columns

```sql
CREATE TABLE course_enrollments (
    student_id INT,
    course_id INT,
    semester VARCHAR(20),
    grade CHAR(2),
    PRIMARY KEY (student_id, course_id, semester),
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

### 🔒 Constraints

#### Primary Key vs Unique Constraints

|Feature|PRIMARY KEY|UNIQUE|
|---|---|---|
|Nulls allowed|NO|YES (usually one NULL)|
|Per table|Only ONE|Multiple allowed|
|Creates index|YES (clustered)|YES (non-clustered)|
|Purpose|Main identifier|Alternative identifier|

```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY,        -- One primary key
    email VARCHAR(100) UNIQUE,      -- Multiple unique constraints OK
    username VARCHAR(50) UNIQUE,
    phone VARCHAR(20) UNIQUE
);
```

#### Foreign Key Constraints - ON DELETE & ON UPDATE

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
        ON DELETE CASCADE        -- If customer deleted, delete orders
        ON UPDATE CASCADE        -- If customer_id updated, update orders
);

CREATE TABLE products (
    product_id INT PRIMARY KEY,
    category_id INT,
    FOREIGN KEY (category_id) REFERENCES categories(category_id)
        ON DELETE SET NULL       -- If category deleted, set to NULL
        ON UPDATE RESTRICT       -- Prevent category_id updates if referenced
);
```

**Actions Explained:**

- `CASCADE`: Propagate change (delete/update child records)
- `SET NULL`: Set foreign key to NULL
- `SET DEFAULT`: Set to default value
- `RESTRICT`: Prevent parent change if children exist
- `NO ACTION`: Similar to RESTRICT (check at end of statement)

#### Other Constraints: NOT NULL, DEFAULT, and CHECK

```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,              -- NOT NULL constraint
    price DECIMAL(10,2) NOT NULL,
    stock INT DEFAULT 0,                     -- DEFAULT constraint
    rating DECIMAL(2,1) CHECK (rating BETWEEN 0 AND 5),  -- CHECK constraint
    status VARCHAR(20) CHECK (status IN ('active', 'discontinued')),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table-level CHECK constraint
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    birth_date DATE,
    hire_date DATE,
    salary DECIMAL(10,2),
    CHECK (hire_date > birth_date),          -- Multi-column check
    CHECK (salary > 0)
);
```

---

## 5. Data Types

### ⚠️ Common Data Type Mistakes

#### Don't Use the Wrong SQL String Type

**String Types Comparison:**

|Type|Max Length|Storage|Use Case|
|---|---|---|---|
|`CHAR(n)`|Fixed n|Padded with spaces|Fixed-length codes (state codes, country codes)|
|`VARCHAR(n)`|Variable up to n|Actual length + 1-2 bytes|Variable text (names, emails)|
|`TEXT`|~65,535 chars|Actual length + 2 bytes|Long text (descriptions, comments)|
|`MEDIUMTEXT`|~16 MB|Actual length + 3 bytes|Articles, large documents|
|`LONGTEXT`|~4 GB|Actual length + 4 bytes|Very large content|

**Best Practices:**

```sql
-- ❌ BAD: CHAR for variable-length data
name CHAR(100)  -- Wastes space if name is "Bob" (97 spaces wasted)

-- ✅ GOOD: VARCHAR for variable-length
name VARCHAR(100)

-- ❌ BAD: VARCHAR for fixed-length codes
country_code VARCHAR(2)  -- Adds overhead for 2 chars

-- ✅ GOOD: CHAR for fixed-length
country_code CHAR(2)

-- ❌ BAD: VARCHAR for very long text
article_content VARCHAR(10000)

-- ✅ GOOD: TEXT for long content
article_content TEXT
```

**Character Set & Collation:**

```sql
CREATE TABLE posts (
    post_id INT PRIMARY KEY,
    title VARCHAR(200) CHARACTER SET utf8mb4,  -- Support emoji & multilingual
    content TEXT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci
);
```

#### The FLOAT Mistake That Crashed a Stock Exchange

**The Problem:** Floating-point arithmetic is imprecise due to binary representation

```sql
-- ❌ DANGEROUS for money
CREATE TABLE accounts (
    balance FLOAT  -- 0.1 + 0.2 might equal 0.30000000000000004
);

-- ✅ SAFE for money
CREATE TABLE accounts (
    balance DECIMAL(15, 2)  -- Exact precision
);
```

**Numeric Types:**

|Type|Storage|Precision|Use Case|
|---|---|---|---|
|`INT`|4 bytes|Exact|Counts, IDs|
|`BIGINT`|8 bytes|Exact|Large counts|
|`DECIMAL(p,s)`|Variable|Exact|Money, precise values|
|`FLOAT`|4 bytes|Approximate (~7 digits)|Scientific data (acceptable error)|
|`DOUBLE`|8 bytes|Approximate (~15 digits)|Scientific calculations|

**Real-World Example: Vancouver Stock Exchange (1982)**

- Used FLOAT for stock index calculations
- Accumulated rounding errors
- Index dropped from 1000 to 524.88 (should have been 1009.81)
- Lost ~50% value due to floating-point errors!

```sql
-- Financial data - ALWAYS use DECIMAL
CREATE TABLE transactions (
    transaction_id BIGINT PRIMARY KEY,
    amount DECIMAL(15, 2) NOT NULL,  -- Exact to 2 decimal places
    tax DECIMAL(15, 2),
    total DECIMAL(15, 2)
);
```

#### SQL Date and Time Types Explained

**Date/Time Types:**

|Type|Format|Range|Use Case|
|---|---|---|---|
|`DATE`|YYYY-MM-DD|1000-01-01 to 9999-12-31|Birth dates, deadlines|
|`TIME`|HH:MM:SS|-838:59:59 to 838:59:59|Duration, time of day|
|`DATETIME`|YYYY-MM-DD HH:MM:SS|1000-01-01 to 9999-12-31|Local timestamps|
|`TIMESTAMP`|YYYY-MM-DD HH:MM:SS|1970-01-01 to 2038-01-19|UTC timestamps, auto-update|
|`YEAR`|YYYY|1901 to 2155|Just year|

```sql
CREATE TABLE events (
    event_id INT PRIMARY KEY,
    event_date DATE,                    -- Just the date
    event_time TIME,                    -- Just the time
    event_datetime DATETIME,            -- Date + time (no timezone)
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  -- Auto-set on insert
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP 
                        ON UPDATE CURRENT_TIMESTAMP  -- Auto-update
);
```

**DATETIME vs TIMESTAMP:**

- `DATETIME`: Stores what you give it (no timezone conversion)
- `TIMESTAMP`: Converts to UTC for storage, converts back to server timezone on retrieval
- `TIMESTAMP`: Limited to 2038-01-19 (32-bit Unix epoch limit)
- `DATETIME`: Preferred for most applications

**Working with Dates:**

```sql
-- Date functions
SELECT 
    NOW(),                          -- Current datetime
    CURDATE(),                      -- Current date
    CURTIME(),                      -- Current time
    DATE_ADD(order_date, INTERVAL 7 DAY),
    DATE_SUB(NOW(), INTERVAL 1 MONTH),
    DATEDIFF(end_date, start_date),
    EXTRACT(YEAR FROM birth_date),
    DATE_FORMAT(created_at, '%Y-%m-%d %H:%i:%s')
FROM orders;
```

---

## 6. Normalization (1NF → BCNF)

**Goal:** Eliminate redundancy and anomalies through decomposition

### 📐 Anomalies (Problems Normalization Solves)

**Update Anomaly:** Same data in multiple places; updating one place creates inconsistency **Insert Anomaly:** Cannot insert data without other required data **Delete Anomaly:** Deleting data unintentionally removes other important data

### 1️⃣ First Normal Form (1NF)

**Rules:**

1. Each column contains atomic (indivisible) values
2. Each column contains values of the same type
3. Each column has a unique name
4. Order of rows doesn't matter
5. No repeating groups

**Example - NOT in 1NF:**

```sql
-- ❌ Violation: phone_numbers contains multiple values
CREATE TABLE contacts (
    contact_id INT,
    name VARCHAR(100),
    phone_numbers VARCHAR(200)  -- "555-1234, 555-5678, 555-9012"
);
```

**Fixed - Now in 1NF:**

```sql
-- ✅ Atomic values
CREATE TABLE contacts (
    contact_id INT,
    name VARCHAR(100),
    PRIMARY KEY (contact_id)
);

CREATE TABLE phone_numbers (
    phone_id INT,
    contact_id INT,
    phone_number VARCHAR(20),
    phone_type VARCHAR(20),  -- 'mobile', 'home', 'work'
    PRIMARY KEY (phone_id),
    FOREIGN KEY (contact_id) REFERENCES contacts(contact_id)
);
```

### 2️⃣ Second Normal Form (2NF)

**Rules:**

1. Must be in 1NF
2. No partial dependencies (all non-key attributes must depend on the ENTIRE primary key)

**Only applies to tables with composite primary keys**

**Example - NOT in 2NF:**

```sql
-- ❌ Partial dependency: student_name depends only on student_id (part of key)
CREATE TABLE enrollments (
    student_id INT,
    course_id INT,
    student_name VARCHAR(100),  -- Depends on student_id only
    course_name VARCHAR(100),   -- Depends on course_id only
    grade CHAR(2),
    PRIMARY KEY (student_id, course_id)
);
```

**Fixed - Now in 2NF:**

```sql
-- ✅ Separate entities
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(100)
);

CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100)
);

CREATE TABLE enrollments (
    student_id INT,
    course_id INT,
    grade CHAR(2),
    PRIMARY KEY (student_id, course_id),
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

**Functional Dependency Notation:**

- `student_id → student_name` (student_id determines student_name)
- `{student_id, course_id} → grade` (composite key determines grade)

### 3️⃣ Third Normal Form (3NF)

**Rules:**

1. Must be in 2NF
2. No transitive dependencies (non-key attributes must not depend on other non-key attributes)

**Example - NOT in 3NF:**

```sql
-- ❌ Transitive dependency: city → state (non-key → non-key)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    city VARCHAR(50),
    state VARCHAR(50),      -- Depends on city (transitive)
    zip_code VARCHAR(10)    -- Depends on city (transitive)
);
```

**Fixed - Now in 3NF:**

```sql
-- ✅ Remove transitive dependencies
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    city_id INT,
    FOREIGN KEY (city_id) REFERENCES cities(city_id)
);

CREATE TABLE cities (
    city_id INT PRIMARY KEY,
    city_name VARCHAR(50),
    state VARCHAR(50),
    zip_code VARCHAR(10)
);
```

**Transitive Dependency:**

- `A → B` and `B → C`, then `A → C` (transitive)
- Example: `employee_id → city` and `city → state`, so `employee_id → state` (bad!)

### 🔺 Boyce-Codd Normal Form (BCNF) - The Untold Story

**Rules:**

1. Must be in 3NF
2. For every functional dependency `X → Y`, X must be a superkey

**3NF vs BCNF:** BCNF is stricter; catches edge cases where 3NF might miss

**Example - In 3NF but NOT in BCNF:**

```sql
-- ❌ professor → course (but professor is not a superkey)
CREATE TABLE teaching (
    student_id INT,
    course VARCHAR(50),
    professor VARCHAR(100),
    PRIMARY KEY (student_id, course),
    -- Constraint: Each professor teaches only one course
    -- But: professor → course violates BCNF (professor not a superkey)
);
```

**Fixed - Now in BCNF:**

```sql
-- ✅ Decompose to satisfy BCNF
CREATE TABLE student_courses (
    student_id INT,
    course VARCHAR(50),
    PRIMARY KEY (student_id, course)
);

CREATE TABLE course_professors (
    course VARCHAR(50) PRIMARY KEY,
    professor VARCHAR(100)
);
```

**BCNF Summary:**

- Most rigorous normal form in common use
- Eliminates all anomalies caused by functional dependencies
- May require sacrificing some JOINs for data integrity

### 📊 Normalization Quick Reference

| Normal Form | Key Rule                           | Example Violation                                  |
| ----------- | ---------------------------------- | -------------------------------------------------- |
| **1NF**     | Atomic values, no repeating groups | Phone: "555-1234, 555-5678"                        |
| **2NF**     | No partial dependencies            | student_name depends on only part of composite key |
| **3NF**     | No transitive dependencies         | employee_id → city → state                         |
| **BCNF**    | Every determinant is a superkey    | professor → course (professor not superkey)        |

---

## 7. Indexing Strategies

### 📇 What is an Index?

**Index:** A data structure that improves query speed at the cost of:

- Additional storage space
- Slower INSERT/UPDATE/DELETE operations

**Without Index:** Full table scan (check every row) **With Index:** Jump directly to matching rows

### 🌲 B-Tree vs Full-Text Indexes

#### B-Tree Indexes (Default)

**Structure:** Balanced tree (all leaf nodes at same depth)

- Self-balancing
- O(log n) search time
- Good for: equality, range queries, sorting

```sql
-- Create B-Tree index (default type)
CREATE INDEX idx_lastname ON employees(last_name);

-- Composite index (multi-column)
CREATE INDEX idx_name ON employees(last_name, first_name);

-- Unique index
CREATE UNIQUE INDEX idx_email ON users(email);

-- Index on expression
CREATE INDEX idx_lower_email ON users(LOWER(email));
```

**When B-Tree Helps:**

```sql
-- ✅ Uses index
SELECT * FROM employees WHERE last_name = 'Smith';
SELECT * FROM employees WHERE last_name LIKE 'Sm%';  -- Prefix
SELECT * FROM employees WHERE last_name BETWEEN 'A' AND 'M';
SELECT * FROM employees ORDER BY last_name;

-- ❌ Doesn't use index efficiently
SELECT * FROM employees WHERE last_name LIKE '%son';  -- Wildcard at start
SELECT * FROM employees WHERE YEAR(hire_date) = 2023;  -- Function on indexed column
```

**Composite Index Order Matters:**

```sql
CREATE INDEX idx_name_dept ON employees(last_name, department);

-- ✅ Uses index (left-most prefix)
SELECT * FROM employees WHERE last_name = 'Smith';
SELECT * FROM employees WHERE last_name = 'Smith' AND department = 'Sales';

-- ❌ Doesn't use index (skips first column)
SELECT * FROM employees WHERE department = 'Sales';
```

#### Full-Text Indexes

**Purpose:** Optimized for searching text content (articles, descriptions)

**Supports:**

- Natural language search
- Boolean search
- Relevance ranking

```sql
-- Create full-text index
CREATE FULLTEXT INDEX idx_content ON articles(title, body);

-- Natural language search
SELECT * FROM articles
WHERE MATCH(title, body) AGAINST ('database design');

-- Boolean mode (advanced)
SELECT * FROM articles
WHERE MATCH(title, body) AGAINST ('+database -oracle' IN BOOLEAN MODE);
-- + required word
-- - excluded word

-- WITH QUERY EXPANSION (finds related terms)
SELECT * FROM articles
WHERE MATCH(title, body) AGAINST ('database' WITH QUERY EXPANSION);
```

**B-Tree vs Full-Text:**

|Feature|B-Tree|Full-Text|
|---|---|---|
|Data types|Numeric, date, short strings|TEXT, VARCHAR|
|Search type|Exact match, prefix, range|Natural language, relevance|
|Use case|IDs, names, dates|Articles, descriptions, comments|
|Storage|Smaller|Larger|

### 🎯 Indexing Best Practices

**DO Index:**

- Primary keys (automatic)
- Foreign keys (for JOINs)
- Columns in WHERE clauses (frequently filtered)
- Columns in ORDER BY (frequently sorted)
- Columns in GROUP BY

**DON'T Over-Index:**

- Small tables (< 1000 rows)
- Columns with low cardinality (few distinct values: gender, boolean)
- Frequently updated columns (slows writes)

**Check Index Usage:**

```sql
-- Show indexes on table
SHOW INDEX FROM employees;

-- Explain query plan
EXPLAIN SELECT * FROM employees WHERE last_name = 'Smith';

-- Look for:
-- "key": idx_lastname (good - using index)
-- "type": ALL (bad - full table scan)
```

---

## 8. Security & Access Control

### 🔐 Access Control, Hashing & Encryption

#### User Management & Privileges

```sql
-- Create user
CREATE USER 'app_user'@'localhost' IDENTIFIED BY 'secure_password';

-- Grant privileges
GRANT SELECT, INSERT, UPDATE ON company_db.* TO 'app_user'@'localhost';
GRANT ALL PRIVILEGES ON company_db.employees TO 'hr_admin'@'localhost';

-- Revoke privileges
REVOKE INSERT, UPDATE ON company_db.* FROM 'app_user'@'localhost';

-- Show privileges
SHOW GRANTS FOR 'app_user'@'localhost';

-- Remove user
DROP USER 'app_user'@'localhost';
```

**Principle of Least Privilege:**

- Grant only necessary permissions
- Separate read-only vs read-write users
- Use role-based access control (RBAC)

```sql
-- Create roles (MySQL 8.0+)
CREATE ROLE 'app_readonly';
CREATE ROLE 'app_readwrite';

-- Grant privileges to roles
GRANT SELECT ON company_db.* TO 'app_readonly';
GRANT SELECT, INSERT, UPDATE, DELETE ON company_db.* TO 'app_readwrite';

-- Assign roles to users
GRANT 'app_readonly' TO 'analyst'@'localhost';
GRANT 'app_readwrite' TO 'developer'@'localhost';
```

#### Password Hashing

**NEVER store passwords in plain text!**

```sql
-- ❌ NEVER DO THIS
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    username VARCHAR(50),
    password VARCHAR(100)  -- Plain text = DISASTER
);

-- ✅ Store hashed passwords
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    username VARCHAR(50) UNIQUE,
    password_hash CHAR(60)  -- bcrypt hash
);
```

**Hashing Algorithms (ordered by security):**

1. **bcrypt** (recommended) - slow, adaptive, salt built-in
2. **scrypt** (recommended) - memory-hard, resistant to hardware attacks
3. **Argon2** (recommended) - modern, winner of password hashing competition
4. **PBKDF2** (acceptable) - widely supported
5. ❌ **SHA-256, MD5** (NEVER for passwords) - too fast, vulnerable

**Application-Level Hashing (Python example):**

```python
import bcrypt

# Hash password
password = "user_password"
hashed = bcrypt.hashpw(password.encode('utf-8'), bcrypt.gensalt())

# Verify password
if bcrypt.checkpw(password.encode('utf-8'), hashed):
    print("Password correct")
```

#### Encryption

**When to Encrypt:**

- Credit card numbers
- Social Security Numbers (SSN)
- Health records
- Personal identifiable information (PII)

**Types:**

1. **Symmetric Encryption:** Same key for encrypt/decrypt (AES)
2. **Asymmetric Encryption:** Public key encrypt, private key decrypt (RSA)

```sql
-- MySQL encryption functions
-- Symmetric encryption
SELECT AES_ENCRYPT('sensitive_data', 'encryption_key');
SELECT AES_DECRYPT(encrypted_column, 'encryption_key') FROM table;

-- Store encrypted data
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    username VARCHAR(50),
    ssn VARBINARY(256),  -- Store encrypted binary data
    credit_card VARBINARY(256)
);

-- Insert encrypted
INSERT INTO users (user_id, username, ssn)
VALUES (1, 'john', AES_ENCRYPT('123-45-6789', 'secret_key'));

-- Query decrypted
SELECT user_id, username, AES_DECRYPT(ssn, 'secret_key') AS ssn_decrypted
FROM users;
```

**Best Practices:**

- Use application-level encryption (more secure than database-level)
- Store encryption keys separately (not in database)
- Use environment variables or key management services (AWS KMS, Azure Key Vault)
- Encrypt data at rest and in transit (SSL/TLS)

#### SQL Injection Prevention

```sql
-- ❌ VULNERABLE to SQL injection
query = "SELECT * FROM users WHERE username = '" + username + "'"
-- If username = "admin' OR '1'='1", entire table exposed!

-- ✅ Use parameterized queries (prepared statements)
-- Python example
cursor.execute("SELECT * FROM users WHERE username = %s", (username,))

-- ✅ PHP example
$stmt = $pdo->prepare("SELECT * FROM users WHERE username = ?");
$stmt->execute([$username]);
```

---

## 9. Query Optimization

### ⚡ Denormalization

**Denormalization:** Intentionally adding redundancy to improve read performance

**When to Denormalize:**

- Read-heavy applications
- Complex JOINs causing performance issues
- Reporting/analytics queries
- Caching frequently accessed computed values

**Example - Normalized (slower reads):**

```sql
-- 3 table JOIN required
SELECT c.name, COUNT(o.order_id), SUM(oi.quantity * oi.price)
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
LEFT JOIN order_items oi ON o.order_id = oi.order_id
GROUP BY c.customer_id;
```

**Example - Denormalized (faster reads):**

```sql
-- Add redundant summary columns
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100),
    total_orders INT DEFAULT 0,        -- Denormalized
    total_spent DECIMAL(15,2) DEFAULT 0,  -- Denormalized
    last_order_date DATE
);

-- Update summary on each order
-- (Use triggers or application logic)
```

**Denormalization Strategies:**

1. **Add summary columns**

```sql
ALTER TABLE products
ADD COLUMN review_count INT DEFAULT 0,
ADD COLUMN avg_rating DECIMAL(2,1) DEFAULT 0;
```

2. **Duplicate frequently-joined data**

```sql
-- Include customer name in orders table (avoid JOIN)
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    customer_name VARCHAR(100),  -- Denormalized
    order_date DATE
);
```

3. **Materialized views / summary tables**

```sql
-- Pre-compute expensive aggregations
CREATE TABLE daily_sales_summary (
    summary_date DATE PRIMARY KEY,
    total_orders INT,
    total_revenue DECIMAL(15,2),
    avg_order_value DECIMAL(10,2)
);

-- Refresh daily via scheduled job
```

**Trade-offs:**

- ✅ Faster reads (fewer JOINs)
- ❌ Slower writes (update multiple places)
- ❌ Risk of inconsistency
- ❌ More storage

### 🚀 General Query Optimization Tips

**1. Use EXPLAIN to analyze queries**

```sql
EXPLAIN SELECT * FROM orders WHERE customer_id = 123;
```

**2. Avoid SELECT * (fetch only needed columns)**

```sql
-- ❌ Slow
SELECT * FROM users;

-- ✅ Fast
SELECT user_id, username, email FROM users;
```

**3. Use LIMIT for pagination**

```sql
-- Get first page
SELECT * FROM products ORDER BY created_at DESC LIMIT 20;

-- Get second page
SELECT * FROM products ORDER BY created_at DESC LIMIT 20 OFFSET 20;
```

**4. Optimize WHERE clauses**

```sql
-- ❌ Avoid functions on indexed columns
WHERE YEAR(order_date) = 2024

-- ✅ Use range instead
WHERE order_date >= '2024-01-01' AND order_date < '2025-01-01'
```

**5. Use EXISTS instead of IN for subqueries**

```sql
-- ❌ Slower (full subquery execution)
SELECT * FROM customers
WHERE customer_id IN (SELECT customer_id FROM orders WHERE total > 1000);

-- ✅ Faster (short-circuits)
SELECT * FROM customers c
WHERE EXISTS (SELECT 1 FROM orders o WHERE o.customer_id = c.customer_id AND o.total > 1000);
```

**6. Use JOINs instead of subqueries (when possible)**

```sql
-- ❌ Subquery
SELECT * FROM products
WHERE category_id = (SELECT category_id FROM categories WHERE name = 'Electronics');

-- ✅ JOIN
SELECT p.* FROM products p
JOIN categories c ON p.category_id = c.category_id
WHERE c.name = 'Electronics';
```

**7. Avoid cartesian products (unintentional CROSS JOINs)**

```sql
-- ❌ Missing join condition = cartesian product
SELECT * FROM customers, orders;  -- Returns customers × orders rows!

-- ✅ Proper JOIN
SELECT * FROM customers c
JOIN orders o ON c.customer_id = o.customer_id;
```

**8. Use UNION ALL instead of UNION (if duplicates OK)**

```sql
-- ❌ UNION removes duplicates (slower)
SELECT name FROM customers
UNION
SELECT name FROM suppliers;

-- ✅ UNION ALL keeps duplicates (faster)
SELECT name FROM customers
UNION ALL
SELECT name FROM suppliers;
```

**9. Cache computed values**

```sql
-- Add computed column with trigger/app logic
ALTER TABLE orders
ADD COLUMN total_amount DECIMAL(15,2);

-- Instead of computing every time
SELECT order_id, SUM(quantity * price) FROM order_items GROUP BY order_id;
```

**10. Partition large tables**

```sql
-- Partition by date range
CREATE TABLE orders (
    order_id BIGINT,
    order_date DATE,
    customer_id INT,
    total DECIMAL(15,2)
)
PARTITION BY RANGE (YEAR(order_date)) (
    PARTITION p2022 VALUES LESS THAN (2023),
    PARTITION p2023 VALUES LESS THAN (2024),
    PARTITION p2024 VALUES LESS THAN (2025),
    PARTITION p_future VALUES LESS THAN MAXVALUE
);
```

---

## 📝 How to Learn SQL on Your Own

### 🎓 Learning Roadmap

**Phase 1: Fundamentals (Weeks 1-2)**

- Basic SELECT, WHERE, ORDER BY
- Aggregate functions (COUNT, SUM, AVG, MAX, MIN)
- GROUP BY, HAVING
- Practice: Simple queries on sample database

**Phase 2: Intermediate (Weeks 3-4)**

- JOINs (INNER, LEFT, RIGHT, FULL)
- Subqueries
- CASE statements
- String and date functions
- Practice: Multi-table queries

**Phase 3: Advanced (Weeks 5-8)**

- Window functions (ROW_NUMBER, RANK, LEAD, LAG)
- CTEs (Common Table Expressions)
- Indexes and query optimization
- Transactions (BEGIN, COMMIT, ROLLBACK)
- Practice: Complex analytical queries

**Phase 4: Database Design (Weeks 9-12)**

- ER modeling
- Normalization (1NF → BCNF)
- Schema design
- Practice: Design databases for real-world scenarios

### 🛠️ Recommended Tools

**Online Practice:**

- [SQLite Online](https://sqliteonline.com/) - No installation needed
- [DB Fiddle](https://www.db-fiddle.com/) - Test queries in browser
- [LeetCode SQL](https://leetcode.com/problemset/database/) - SQL challenges
- [HackerRank SQL](https://www.hackerrank.com/domains/sql) - Graded exercises

**Desktop Tools:**

- **MySQL Workbench** - Full MySQL IDE
- **pgAdmin** - PostgreSQL management
- **DBeaver** - Universal database tool (supports all major DBs)

**Sample Databases:**

- **Chinook Database** - Music store (tracks, albums, customers, invoices)
- **Northwind** - Product sales (products, orders, customers)
- **AdventureWorks** - Bicycle manufacturer (complex schema)
- **Sakila** - DVD rental store (films, actors, rentals)

### 📚 Learning Resources

**Free Courses:**

- freeCodeCamp Relational Database Certification
- Khan Academy SQL Course
- SQLBolt (interactive tutorials)
- Mode Analytics SQL Tutorial

**Books:**

- "Grokking Relational Database Design" - Qiang Hao & Michael Tsikerdekis
- "SQL Performance Explained" - Markus Winand
- "Designing Data-Intensive Applications" - Martin Kleppmann
- "Database Design for Mere Mortals" - Michael Hernandez

**Practice Projects:**

1. **Personal Finance Tracker** - Track income, expenses, budgets
2. **Blog Platform** - Users, posts, comments, tags
3. **E-commerce Store** - Products, orders, customers, inventory
4. **Movie Database** - Films, actors, ratings, reviews
5. **Library System** - Books, authors, borrowers, loans

### 💡 Study Tips

1. **Practice daily** - Even 30 minutes/day
2. **Type queries manually** - Don't copy-paste
3. **Understand execution order** - FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY
4. **Read error messages** - Learn from mistakes
5. **Optimize queries** - Use EXPLAIN to understand performance
6. **Build projects** - Apply knowledge to real scenarios
7. **Join communities** - Stack Overflow, Reddit r/SQL, Discord servers
8. **Review regularly** - Spaced repetition for retention

---

## 🎯 Summary: Database Design Principles

### ✅ DO's

1. **Plan before coding** - Design schema on paper first
2. **Use meaningful names** - `customer_id` not `cid`
3. **Normalize to 3NF/BCNF** - Eliminate redundancy
4. **Choose appropriate data types** - DECIMAL for money, VARCHAR for text
5. **Define primary keys** - Every table needs one
6. **Use foreign keys** - Enforce referential integrity
7. **Add indexes strategically** - On frequently queried columns
8. **Document your schema** - ERD diagrams, comments
9. **Test with realistic data** - Don't just use test records
10. **Plan for growth** - Scalability from the start

### ❌ DON'Ts

1. **Don't store calculated values** - Unless denormalizing for performance
2. **Don't use generic names** - Avoid `data`, `info`, `value`
3. **Don't skip normalization** - Then denormalize only when needed
4. **Don't use FLOAT for money** - Use DECIMAL
5. **Don't over-index** - Slows writes
6. **Don't store passwords in plain text** - Always hash
7. **Don't ignore foreign keys** - They prevent orphaned records
8. **Don't use SELECT *** - Fetch only needed columns
9. **Don't premature optimize** - Get it working, then optimize
10. **Don't store files in database** - Store file paths, keep files separate

---

## 🔍 Quick Reference Tables

### SQL Command Categories

|Category|Commands|Purpose|
|---|---|---|
|**DDL** (Data Definition)|CREATE, ALTER, DROP, TRUNCATE|Define database structure|
|**DML** (Data Manipulation)|SELECT, INSERT, UPDATE, DELETE|Manipulate data|
|**DCL** (Data Control)|GRANT, REVOKE|Control access|
|**TCL** (Transaction Control)|BEGIN, COMMIT, ROLLBACK, SAVEPOINT|Manage transactions|

### Normal Forms Summary

|Form|Requirement|Example Fix|
|---|---|---|
|**1NF**|Atomic values, no repeating groups|Split multi-value columns|
|**2NF**|1NF + no partial dependencies|Create separate table for partial key|
|**3NF**|2NF + no transitive dependencies|Remove non-key → non-key dependencies|
|**BCNF**|3NF + every determinant is superkey|Further decompose edge cases|

### Join Types Quick Reference

```sql
-- INNER JOIN - matching records only
SELECT * FROM A INNER JOIN B ON A.id = B.id;

-- LEFT JOIN - all A + matching B
SELECT * FROM A LEFT JOIN B ON A.id = B.id;

-- RIGHT JOIN - all B + matching A
SELECT * FROM A RIGHT JOIN B ON A.id = B.id;

-- FULL OUTER JOIN - all from both
SELECT * FROM A FULL OUTER JOIN B ON A.id = B.id;

-- CROSS JOIN - cartesian product
SELECT * FROM A CROSS JOIN B;
```

### Constraint Types

|Constraint|Purpose|Example|
|---|---|---|
|`PRIMARY KEY`|Unique identifier|`id INT PRIMARY KEY`|
|`FOREIGN KEY`|Link to another table|`FOREIGN KEY (customer_id) REFERENCES customers(id)`|
|`UNIQUE`|No duplicates allowed|`email VARCHAR(100) UNIQUE`|
|`NOT NULL`|Value required|`name VARCHAR(100) NOT NULL`|
|`CHECK`|Custom validation|`CHECK (age >= 18)`|
|`DEFAULT`|Default value|`status VARCHAR(20) DEFAULT 'active'`|

---

## 🎓 Final Exam Self-Check

**Test your knowledge:**

1. What's the difference between CHAR and VARCHAR?
2. Why should you use DECIMAL instead of FLOAT for currency?
3. What are the three types of anomalies that normalization prevents?
4. What's the difference between 2NF and 3NF?
5. When should you use a composite primary key?
6. What's the difference between INNER JOIN and LEFT JOIN?
7. What does ON DELETE CASCADE do?
8. When should you create an index?
9. Why should passwords be hashed, not encrypted?
10. What's the difference between normalization and denormalization?

**Answers:**

1. CHAR is fixed-length (padded), VARCHAR is variable-length
2. FLOAT has rounding errors; DECIMAL is exact
3. Update, Insert, Delete anomalies
4. 2NF: no partial dependencies; 3NF: no transitive dependencies
5. Many-to-many junction tables or weak entities
6. INNER returns only matches; LEFT returns all from left + matches
7. Deletes child records when parent is deleted
8. Frequently queried columns, foreign keys, WHERE/ORDER BY clauses
9. Hashing is one-way (can't reverse); encryption is two-way
10. Normalization removes redundancy; denormalization adds it back for performance

---

## 🎉 Conclusion

**You now have a comprehensive understanding of:**

- SQL fundamentals (SELECT, JOIN, aggregate functions)
- Database design principles and lifecycle
- ER modeling and relationships
- Keys, constraints, and data types
- Normalization (1NF through BCNF)
- Indexing strategies (B-Tree and Full-Text)
- Security (access control, hashing, encryption)
- Query optimization and denormalization

**Next Steps:**

1. Build a real project using these principles
2. Practice with online SQL challenges
3. Study the companion book for deeper understanding
4. Join database communities and forums
5. Learn about specific RDBMS features (PostgreSQL, MySQL, SQL Server)

**Remember:** Database design is both science and art. Follow the principles, but also adapt to your specific use case. Good luck! 🚀

---

**Resources:**

- 📘 Book: [Grokking Relational Database Design](https://mng.bz/PRER)
- 🎥 Course: [FreeCodeCamp 6-hour video](https://youtu.be/26ls5lNiijk)
- 💻 GitHub: [Code examples & scripts](https://github.com/Neo-Hao/grokking-relational-database-design)
- 🌐 Practice: SQLite Online, DB Fiddle, LeetCode SQL

**Created with ❤️ for learners everywhere**