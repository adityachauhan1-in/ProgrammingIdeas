# to insert the data in table 

# 1 --> Insert into table 
  INSERT INTO table_name VALUE (
    now those values like (i.e 'aditya', 'aditya@gmail.com' , True)
  )

# 2 ---> Insertt into specific columns of the talbe
 
 INSERT INTO table_name (column_names) VALUE(
    now insert those values which come in those table 
    // keep in mind : insert those values definitely which must defined (not null and not default) 
 )
 


 # INSERT INTO — DEFAULT Values

## 1. Insert Without Specifying Column Names

When you don't specify column names, you must provide a value for **every column** in the correct order.

```sql
INSERT INTO clients VALUES
(DEFAULT, 'chinki', 'chinki@gmail.com', 'FEMALE', DEFAULT, TRUE);
```

Here, `DEFAULT` must be written explicitly for columns where you want MySQL to use the column's default value.

### Multiple Rows

```sql
INSERT INTO clients VALUES
    (DEFAULT, 'chinki', 'chinki@gmail.com', 'FEMALE', DEFAULT, TRUE),
    (DEFAULT, 'ashok', 'ashok@gmail.com', 'MALE', DEFAULT, FALSE);
```

**Structure:**

```sql
INSERT INTO table_name VALUES
    (row1_value1, row1_value2, ...),
    (row2_value1, row2_value2, ...);
```

---

## 2. Insert Into Selected Columns

When you specify the columns, you only provide values for those columns.

```sql
INSERT INTO clients (name, email, gender)
VALUES ('chinki', 'chinki@gmail.com', 'FEMALE');
```

The columns that are **not specified** are handled automatically by MySQL.

### What happens to omitted columns?

| Column condition        | What MySQL does                   |
| ----------------------- | --------------------------------- |
| Has `DEFAULT`           | Uses the default value            |
| `AUTO_INCREMENT`        | Generates the value automatically |
| Allows `NULL`           | Can use `NULL`                    |
| `NOT NULL` + no default | Usually gives an error            |

### Example

Suppose the table has:

```text
id          → AUTO_INCREMENT
name        → VARCHAR
email       → VARCHAR
gender      → VARCHAR
created_at  → DEFAULT CURRENT_TIMESTAMP
active      → DEFAULT TRUE
```

You can write:

```sql
INSERT INTO clients (name, email, gender)
VALUES ('chinki', 'chinki@gmail.com', 'FEMALE');
```

MySQL automatically handles:

```text
id          → automatically generated
name        → chinki
email       → chinki@gmail.com
gender      → FEMALE
created_at  → CURRENT_TIMESTAMP
active      → TRUE
```

---

## ⭐ Key Rule

> **Specified column → You provide its value.**
> **Omitted column → MySQL uses its DEFAULT/automatic value if available.**

---

## Recommended Practice

Prefer specifying column names:

```sql
INSERT INTO clients (name, email, gender)
VALUES ('chinki', 'chinki@gmail.com', 'FEMALE');
```

Instead of:

```sql
INSERT INTO clients VALUES
(DEFAULT, 'chinki', 'chinki@gmail.com', 'FEMALE', DEFAULT, TRUE);
```

### Why?

* You don't need to remember column order.
* Safer if the table structure changes.
* Easier to read.
* You can let `DEFAULT` and `AUTO_INCREMENT` work automatically.

---

## VALUE vs VALUES

MySQL supports:

```sql
INSERT INTO clients VALUE (...);
```

But the commonly used form is:

```sql
INSERT INTO clients VALUES (...);
```

Use **`VALUES`** in your notes and code.
