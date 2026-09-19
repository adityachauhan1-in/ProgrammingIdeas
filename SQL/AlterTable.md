# ALTER TABLE in SQL

`ALTER TABLE` changes the structure of an existing table.

## Add a column

```sql
ALTER TABLE employees
ADD email VARCHAR(255);
```

## Drop a column

```sql
ALTER TABLE employees
DROP COLUMN email;
```

## Modify a column

```sql
-- MySQL
ALTER TABLE employees
MODIFY salary DECIMAL(10, 2);

-- PostgreSQL
ALTER TABLE employees
ALTER COLUMN salary TYPE DECIMAL(10, 2);
```

## Rename a column

```sql
ALTER TABLE employees
RENAME COLUMN name TO full_name;
```

## Rename a table

```sql
ALTER TABLE employees
RENAME TO staff;
```

## Add or remove a constraint

```sql
ALTER TABLE orders
ADD CONSTRAINT fk_customer
FOREIGN KEY (customer_id) REFERENCES customers(id);

ALTER TABLE orders
DROP CONSTRAINT fk_customer;
```

Always back up important data and check database-specific syntax before making structural changes.
