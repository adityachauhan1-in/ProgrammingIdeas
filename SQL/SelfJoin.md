# Self Join : A self join is a regular join, but the table is joined with itself. It can be useful for comparing rows within the same table.
# in this example we have a table called employees with columns id, name, and manager_id. We want to find the names of employees along with their managers' names.
Example:
```sql
SELECT e1.name AS employee_name, e2.name AS manager_name
FROM employees e1
JOIN employees e2 ON e1.manager_id = e2.id;
``` 
SELECT a.id,a.name AS user_name , 
b.name AS referred_by_name FROM users a LEFT JOIN users b ON a.referred_by = b.id;
SELECT * FROM users;
# if you do left join then it will show all the records from left table and if there is no match in right table then it will show null value.

# But generally we use inner join to get the records which are matched in both tables. So if you want to get the records which are matched in both tables then you can use inner join.
SELECT a.id,a.name AS user_name , 
b.name AS referred_by_name FROM users a INNER JOIN users b ON a.referred_by = b.id;
SELECT * FROM users;