# Function in SQL

Functions in SQL are reusable blocks of code that perform a specific task and return a single value. They can be used in SELECT, WHERE, and ORDER BY clauses.

## Types of Functions

### 1. Scalar Functions
Scalar functions return a single value based on the input provided.

### 2. Aggregate Functions
Aggregate functions perform a calculation on a set of values and return a single value.

## Common SQL Functions

### String Functions
- `CONCAT()`: Joins two or more strings.
- `UPPER()`: Converts a string to uppercase.
- `LOWER()`: Converts a string to lowercase.
- `SUBSTRING()`: Extracts a substring from a string.

### Numeric Functions
- `ROUND()`: Rounds a number to a specified number of decimal places.
- `ABS()`: Returns the absolute value of a number.
- `CEIL()`: Returns the smallest integer greater than or equal to a number.
- `FLOOR()`: Returns the largest integer less than or equal to a number.

### Date Functions
- `CURDATE()`: Returns the current date.
- `CURTIME()`: Returns the current time.
- `NOW()`: Returns the current date and time.
- `DATEDIFF()`: Calculates the difference between two dates.

## Creating Custom Functions

You can create custom functions in SQL using the CREATE FUNCTION statement.

# Example:
```sql
CREATE FUNCTION calculate_area(radius FLOAT)
RETURNS FLOAT
BEGIN
    DECLARE area FLOAT;
    SET area = PI() * radius * radius;
    RETURN area;
END;
``` 

# There are multiple types of constraints in SQL: UNIQUE, NOT NULL, PRIMARY KEY, FOREIGN KEY, CHECK, and DEFAULT.
 # The function are used to perform specific operations on the data in the database. They can be built-in functions provided by the SQL database or user-defined functions created by the user.

 # The built in functions are used to perform operations on the data in the database. They can be used in SELECT, WHERE, and ORDER BY clauses. The user-defined functions are created by the user to perform specific operations on the data in the database.
 # Built in functions are 
 Sum, Count, Avg, Min, Max, Round, Upper, Lower, Length, Now, DateAdd, DateDiff, etc.
 # --> UseCase:
 # 1. To calculate the total sales for a specific product, you can use the SUM function in a SELECT statement to add up the sales amounts for that product. 
 Example:
 ```sql 
SELECT SUM(sales_amount) AS total_sales
FROM sales
WHERE product_id = 123;
``` 
// where condition if for particular product id.(optional) 

// 2. To find the average salary of employees in a department, you can use the AVG function in a SELECT statement to calculate the average salary for that department.
Example:
```sql  
SELECT AVG(salary) AS average_salary
FROM employees
WHERE department_id = 456;
```
# for min , max , length , lower , upper , round , now , dateadd , datediff etc. we can use in the same way as above.

# Interesting , there is a function DateDiff which is used to calculate the difference between two dates. It can be used to find the number of days, months, or years between two dates.
Example:
```sql
SELECT DATEDIFF('2024-01-01', '2023-01-01') AS date_difference;
```

# Decimal value 'Floor' function is used to round down a decimal value to the nearest integer. It can be used to find the largest integer less than or equal to a given decimal value.
Example:
```sql
SELECT FLOOR(3.7) AS rounded_down_value;
```
return rounded_down_value;`(3)
# On the other side , 'Ceil' function is used to round up a decimal value to the nearest integer. It can be used to find the smallest integer greater than or equal to a given decimal value.
Example:
```sql
SELECT CEIL(3.2) AS rounded_up_value;
``` 
return rounded_up_value;`(4)