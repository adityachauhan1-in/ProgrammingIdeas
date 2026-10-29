# To update the data in a table, you can use the `UPDATE` statement. The basic syntax for the `UPDATE` statement is as follows:

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
# The `UPDATE` statement is used to modify existing records in a table. You can specify which columns to update and the new values for those columns. The `WHERE` clause is used to specify which records should be updated; if you omit the `WHERE` clause, all records in the table will be updated.

# if you want to update the salary(+10000) of employees , whose salary is less than 50000, you can use the following SQL statement:

```sql  
UPDATE employees
SET salary = salary + 10000
WHERE salary < 50000;
```