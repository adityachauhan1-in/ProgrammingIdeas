# MySQL Data Types and Constraints

## 1. CREATE TABLE Syntax

CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    column3 datatype constraints
);

Order:
Table Name → Column Name → Data Type → Constraints


## 2. MySQL Data Types

### A. Numeric Data Types

| Data Type | Description | Storage | Example |
|---|---|---|---|
| TINYINT | Very small integer | 1 byte | 25 |
| SMALLINT | Small integer | 2 bytes | 1000 |
| MEDIUMINT | Medium integer | 3 bytes | 500000 |
| INT / INTEGER | Standard integer | 4 bytes | 100 |
| BIGINT | Very large integer | 8 bytes | Large IDs |
| DECIMAL(M,D) | Exact decimal number | Variable | 999.99 |
| NUMERIC(M,D) | Same as DECIMAL | Variable | 100.50 |
| FLOAT | Approximate decimal number | 4 bytes | 3.14 |
| DOUBLE | Double-precision decimal | 8 bytes | 12345.6789 |
| BIT(M) | Stores bit values | Variable | b'1010' |

Important:

INT:
    Stores whole numbers.

DECIMAL(M,D):
    M = Total number of digits.
    D = Number of digits after decimal point.

Example:
    DECIMAL(10,2) → 99999999.99

Use:
    DECIMAL → Money / Prices
    FLOAT   → Approximate measurements
    DOUBLE  → Scientific calculations


### B. String Data Types

| Data Type | Description | Maximum Size |
|---|---|---|
| CHAR(n) | Fixed-length string | 255 characters |
| VARCHAR(n) | Variable-length string | Subject to row-size limits |
| TINYTEXT | Very small text | 255 bytes |
| TEXT | Normal text | 65,535 bytes |
| MEDIUMTEXT | Large text | 16,777,215 bytes |
| LONGTEXT | Very large text | 4GB approximately |
| BINARY(n) | Fixed-length binary data | 255 bytes |
| VARBINARY(n) | Variable-length binary data | Subject to row-size limits |
| TINYBLOB | Small binary object | 255 bytes |
| BLOB | Binary large object | 65,535 bytes |
| MEDIUMBLOB | Medium binary object | 16,777,215 bytes |
| LONGBLOB | Large binary object | 4GB approximately |

Important:

CHAR(n):
    Fixed-length character string.

VARCHAR(n):
    Variable-length character string.

Use VARCHAR for:
    Names, emails, usernames, phone numbers.


### C. Date and Time Data Types

| Data Type | Description | Example |
|---|---|---|
| DATE | Date only | '2026-09-12' |
| TIME | Time only | '14:30:00' |
| DATETIME | Date and time | '2026-09-12 14:30:00' |
| TIMESTAMP | Date and time with time-zone handling | '2026-09-12 14:30:00' |
| YEAR | Year only | 2026 |

Use:

DATE:
    Date of birth, joining date.

DATETIME:
    Event date and time.

TIMESTAMP:
    created_at, updated_at.


### D. Boolean Data Type

BOOLEAN / BOOL:
    MySQL treats BOOLEAN as an alias for TINYINT(1).

Example:

is_active BOOLEAN DEFAULT TRUE;

Common values:
    TRUE  → 1
    FALSE → 0


### E. JSON Data Type

JSON:
    Stores valid JSON objects and arrays.

Example:

preferences JSON;

Example JSON value:

{
    "theme": "dark",
    "notifications": true
}


### F. Spatial Data Types

| Data Type | Description |
|---|---|
| GEOMETRY | General geometric data |
| POINT | A point with coordinates |
| LINESTRING | A sequence of points |
| POLYGON | A closed geometric shape |
| MULTIPOINT | Collection of points |
| MULTILINESTRING | Collection of lines |
| MULTIPOLYGON | Collection of polygons |
| GEOMETRYCOLLECTION | Collection of geometric objects |


## 3. MySQL Constraints

Constraints are rules applied to columns to maintain data integrity.

| Constraint | Purpose |
|---|---|
| PRIMARY KEY | Uniquely identifies each row |
| FOREIGN KEY | Maintains relationships between tables |
| NOT NULL | Prevents NULL values |
| UNIQUE | Prevents duplicate non-NULL values |
| CHECK | Enforces a condition |
| DEFAULT | Provides an automatic value |


## 4. PRIMARY KEY

Purpose:
    Uniquely identifies every row.

Rules:
    - Must be unique.
    - Cannot contain NULL.
    - A table can have only one PRIMARY KEY constraint.
    - Can contain one or multiple columns.

Syntax:

column_name INT PRIMARY KEY;

Example:

CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);


### Composite PRIMARY KEY

A primary key made of multiple columns.

Example:

CREATE TABLE Enrollment (
    student_id INT,
    course_id INT,
    PRIMARY KEY (student_id, course_id)
);

The combination of student_id and course_id must be unique.


## 5. FOREIGN KEY

Purpose:
    Establishes a relationship between two tables.

Syntax:

FOREIGN KEY (column_name)
REFERENCES parent_table(parent_column);

Example:

CREATE TABLE Departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(100)
);

CREATE TABLE Employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    department_id INT,

    FOREIGN KEY (department_id)
        REFERENCES Departments(department_id)
);

Here:
    Employees.department_id
    references
    Departments.department_id


### Foreign Key Actions

| Action | Meaning |
|---|---|
| CASCADE | Propagates supported updates or deletes |
| RESTRICT | Prevents operation if related rows exist |
| NO ACTION | Behaves like RESTRICT in MySQL InnoDB |
| SET NULL | Sets the foreign key to NULL |
| SET DEFAULT | Not supported as an enforced action by InnoDB |

Example:

FOREIGN KEY (department_id)
REFERENCES Departments(department_id)
ON DELETE SET NULL
ON UPDATE CASCADE;


## 6. NOT NULL

Purpose:
    Prevents a column from containing NULL.

Syntax:

column_name datatype NOT NULL;

Example:

CREATE TABLE Students (
    id INT,
    name VARCHAR(100) NOT NULL
);

Invalid:

INSERT INTO Students (id, name)
VALUES (1, NULL);


## 7. UNIQUE

Purpose:
    Prevents duplicate non-NULL values.

Syntax:

column_name datatype UNIQUE;

Example:

CREATE TABLE Users (
    id INT PRIMARY KEY,
    email VARCHAR(150) UNIQUE
);

Duplicate email values are not allowed.

Important:
    MySQL generally allows multiple NULL values in a UNIQUE column.


### Composite UNIQUE Constraint

Ensures that a combination of columns is unique.

Example:

CREATE TABLE UserPhones (
    user_id INT,
    phone VARCHAR(20),

    UNIQUE (user_id, phone)
);


## 8. CHECK

Purpose:
    Ensures that a condition is satisfied.

Syntax:

column_name datatype CHECK (condition);

Example:

CREATE TABLE Students (
    id INT PRIMARY KEY,
    age INT CHECK (age >= 18)
);

Invalid:

INSERT INTO Students (id, age)
VALUES (1, 15);


### Table-Level CHECK

CREATE TABLE Products (
    product_id INT PRIMARY KEY,
    price DECIMAL(10,2),
    discount DECIMAL(10,2),

    CHECK (price >= 0),
    CHECK (discount >= 0 AND discount <= price)
);

Important:
    MySQL 8.0.16 and later enforce CHECK constraints.


## 9. DEFAULT

Purpose:
    Provides a value automatically when a column is omitted.

Syntax:

column_name datatype DEFAULT value;

Example:

CREATE TABLE Users (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    is_active BOOLEAN DEFAULT TRUE
);

Insert:

INSERT INTO Users (id, name)
VALUES (1, 'Aditya');

is_active automatically receives TRUE.


### More Examples

status VARCHAR(20) DEFAULT 'active';

created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP;


Important:
    DEFAULT does not prevent explicit NULL values.
    Use NOT NULL if NULL must be prohibited.


## 10. AUTO_INCREMENT

Purpose:
    Automatically generates sequential integer values.

Example:

CREATE TABLE Students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100)
);

Insert:

INSERT INTO Students (name)
VALUES ('Aditya');

The id is generated automatically.

Important:
    AUTO_INCREMENT is a column attribute, not a separate integrity constraint.


## 11. UNSIGNED

Purpose:
    Prevents negative values for supported numeric types.

Example:

age INT UNSIGNED;

Useful for:
    IDs, ages, quantities, positive counts.


## 12. Complete Example

CREATE TABLE Students (
    student_id INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,

    name VARCHAR(100) NOT NULL,

    email VARCHAR(150) NOT NULL UNIQUE,

    age TINYINT UNSIGNED CHECK (age >= 18),

    cgpa DECIMAL(4,2) CHECK (cgpa >= 0 AND cgpa <= 10),

    date_of_birth DATE,

    is_active BOOLEAN DEFAULT TRUE,

    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,

    address TEXT
);


## 13. Quick Revision

### Important Data Types

INT:
    Whole numbers.

VARCHAR:
    Variable-length text.

CHAR:
    Fixed-length text.

DECIMAL:
    Exact decimal values.

FLOAT / DOUBLE:
    Approximate decimal values.

DATE:
    Date only.

DATETIME:
    Date and time.

TIMESTAMP:
    Commonly used for record timestamps.

BOOLEAN:
    TRUE / FALSE values.

JSON:
    JSON objects and arrays.


### Important Constraints

PRIMARY KEY:
    Unique row identifier.

FOREIGN KEY:
    Relationship between tables.

NOT NULL:
    Value is mandatory.

UNIQUE:
    No duplicate non-NULL values.

CHECK:
    Condition must be satisfied.

DEFAULT:
    Automatic value when omitted.


## 14. Interview Answer

Question:
    How do you create a table in SQL?

Answer:
    We use the CREATE TABLE statement.
    First, we specify the table name.
    Then, we define each column with its name and data type.
    Finally, we apply constraints such as PRIMARY KEY,
    FOREIGN KEY, NOT NULL, UNIQUE, CHECK, and DEFAULT
    to maintain data integrity.