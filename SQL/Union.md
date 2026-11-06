# Union and Union All
 

 # The UNION operator is used to combine the result sets of two or more SELECT statements. It removes duplicate rows from the result set. The UNION ALL operator, on the other hand, combines the result sets of two or more SELECT statements and includes all rows, including duplicates.

 Example:
 ```sql
SELECT column1, column2 FROM table1
UNION
SELECT column1, column2 FROM table2;
```
and for union all
```sql  
SELECT column1, column2 FROM table1
UNION ALL   
SELECT column1, column2 FROM table2;
```

# We can explicitly specify the order of the result set using the ORDER BY clause. The ORDER BY clause can be used with both UNION and UNION ALL operators to sort the combined result set based on one or more columns.
Example:
```sql
SELECT column1, column2 FROM table1
UNION   
SELECT column1, column2 FROM table2
ORDER BY column1 ASC;
```

# We can define column name as well for better understading of the result set . So anyone can easily understand the result set. which data is coming from which table. We can define column name using AS keyword.
Example:
```sql
SELECT column1 AS col1, column2 AS col2 FROM table1
UNION
SELECT column1 AS col1, column2 AS col2 FROM table2;
``` 
