# Primary Key and Auto Increment
# Primary Key is a field in a table which uniquely identifies each row/record in that table. Primary keys must contain unique values, and cannot contain NULL values. A table can have only one primary key, which may consist of single or multiple columns.
# Auto Increment is a feature in some database management systems that automatically generates a unique number for each new row inserted into a table. It is often used in conjunction with a primary key to ensure each row has a unique identifier.

# Syantax for creating a table with a primary key and auto increment:

```sql  
CREATE TABLE table_name (
    column1 datatype PRIMARY KEY AUTO_INCREMENT,
    column2 datatype,
    ...
);
```
Example:

```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL
);
```

# Difference b/w Primary Key and Unique constraint:
- **Primary Key**: A primary key is a column or a set of columns that uniquely identifies each row in a table. It cannot contain NULL values and there can only be one primary key in a table.
- **Unique Constraint**: A unique constraint is a rule that ensures that all values in a column or a set of columns are unique across the table. Unlike primary keys, unique constraints can allow NULL values (depending on the database system), and a table can have multiple unique constraints.

# Can I delete a primary key from a table?
Yes, you can delete a primary key from a table using the `ALTER TABLE` statement.
But be careful, as deleting a primary key may affect the integrity of your data and any relationships with other tables. Here's how you can delete a primary key:

```sql
ALTER TABLE table_name DROP PRIMARY KEY;
```
# AutoIncrement oftenly starts from 1 and increments by 1 for each new record. However, you can specify a different starting point and increment value if needed.

# to change increment value we can use the following command:

```sql  
ALTER TABLE table_name AUTO_INCREMENT = value;
```
Exqmple:

```sql
ALTER TABLE users AUTO_INCREMENT = 1000;
```