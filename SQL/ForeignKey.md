# Foreign Key : It is the key which is used to link two tables together. A foreign key in one table points to a primary key in another table. It is a field (or collection of fields) in one table that refers to the primary key in another table. The foreign key establishes and enforces a link between the data in the two tables.

# Syntax

```sql
CREATE TABLE table_name (
    column1 datatype PRIMARY KEY,
    column2 datatype,
    ...
    FOREIGN KEY (column_name) REFERENCES other_table (column_name)
);
```
// add constraint to existing table

```sql
ALTER TABLE table_name
ADD CONSTRAINT fk_name  

// it is recommended to use a naming convention for foreign keys, such as fk_table1_table2_columnname . 

# add constraint while creating a table

```sql
CREATE TABLE table_name (
    column1 datatype PRIMARY KEY,
    column2 datatype,
    ...
    CONSTRAINT fk_name FOREIGN KEY (column_name) REFERENCES other_table (column_name)
);
```

// drop constraint from existing table

```sql
ALTER TABLE table_name
DROP CONSTRAINT fk_name;
```

// even if you forget to add constraint while creating a table, you can add it later using ALTER TABLE statement. Or MySQL also allows you to add a foreign key constraint while creating a table using the REFERENCES keyword.

# Delete or Update a Foreign Key

When you delete or update a record in the parent table, you can specify what happens to the related records in the child table using `ON DELETE` and `ON UPDATE` clauses.

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
    ON DELETE CASCADE
    ON UPDATE CASCADE
);
```
# Deleting a record in the parent table will automatically delete the related records in the child table if `ON DELETE CASCADE` is specified. Similarly, updating a record in the parent table will automatically update the related records in the child table if `ON UPDATE CASCADE` is specified.

# to prevent deletion or update of a record in the parent table if there are related records in the child table, you can use `ON DELETE RESTRICT` and `ON UPDATE RESTRICT` clauses.

```sql

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
    ON DELETE RESTRICT
    ON UPDATE RESTRICT
);
```
