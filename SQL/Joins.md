# JOINS : 
Joins are used to combine rows from two or more tables, based on a related column between them. There are several types of joins in SQL, including INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN.
# 1. INNER JOIN :
The INNER JOIN keyword selects records that have matching values in both tables.

```sql
Syntax:
SELECT columns  FROM table1
INNER JOIN table2 ON table1.column = table2.column;
```
For example, if you have two tables, `employees` and `departments`, and you want to retrieve a list of employees along with their department names, you can use an INNER JOIN:

```sql
SELECT employees.name, departments.name
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
``` 

SELECT users.name ,users.salary,  addresses.city , addresses.pincode , users.id AS user_ID FROM users 
INNER JOIN addresses ON users.id = addresses.user_id;

# LEfT JOIN :
The LEFT JOIN keyword returns all records from the left table (table1), and the matched records
from the right table (table2). The result is NULL from the right side, if there is no match.

```sql
Syntax:
SELECT columns FROM table1
LEFT JOIN table2 ON table1.column = table2.column;
```
Example:
```sql
SELECT users.name ,users.salary,  addresses.city , addresses.pincode , users.id AS user_ID FROM users
LEFT JOIN addresses ON users.id = addresses.user_id;

# RIGHT JOIN :
The RIGHT JOIN keyword returns all records from the right table (table2), and the matched records       
from the left table (table1). The result is NULL from the left side, when there is no match.

```sql
Syntax:
SELECT columns FROM table1
RIGHT JOIN table2 ON table1.column = table2.column;
```
Example:
```sql
SELECT users.name ,users.salary,  addresses.city , addresses.pincode , users.id AS user_ID FROM users
RIGHT JOIN addresses ON users.id = addresses.user_id;   
