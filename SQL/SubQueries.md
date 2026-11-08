# Subqueries are queries nested inside another query. They can be used in various parts of a SQL statement, such as the SELECT, FROM, and WHERE clauses. Subqueries allow you to perform complex operations and retrieve data based on the results of another query.

Example of a subquery in the SELECT clause:

```sql
SELECT employee_id, first_name, last_name,
       (SELECT department_name
        FROM departments
        WHERE departments.department_id = employees.department_id) AS department    
FROM employees;
```

or 

```sql
SELECT employee_id, first_name, last_name,
       (SELECT department_name
        FROM departments
        WHERE departments.department_id = employees.department_id) AS department
FROM employees;
