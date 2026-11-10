# GROUP BY : is used to group rows that have the same values into summary rows, like "find the number of customers in each country". GROUP BY is often used with aggregate functions (COUNT, MAX, MIN, SUM, AVG) to group the result-set by one or more columns.

syntax:
```
SELECT column_name(s), aggregate_function(column_name)
FROM table_name
WHERE condition
GROUP BY column_name(s);

Example:
```
sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country; 

# HAVING : is used to filter records that work on summarized GROUP BY results. The HAVING clause was added to SQL because the WHERE keyword could not be used with aggregate functions.

Example:
```
sql
SELECT COUNT(CustomerID), Country   
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5;

# WHERE is used before GROUP BY to filter records before grouping, while HAVING is used after GROUP BY to filter groups based on aggregate functions.
