# Indexes : Indexes are special lookup tables that the database search engine can use to speed up data retrieval. In essence, an index is a pointer to data in a table. An index is created on a table column(s) and can be used to quickly locate data without having to search every row in a database table every time a database table is accessed.
for example, if you have a table with 1 million rows and you want to find a specific row, without an index, the database would have to scan all 1 million rows to find the desired data. However, with an index, the database can quickly locate the data by using the index, which significantly reduces the amount of time it takes to retrieve the data.

# To check , On which fields indexes are created in a table, you can use the following SQL command:

```sql 
SHOW INDEX FROM table_name;
```

# To create an index on a table, you can use the following SQL command:

```sql
CREATE INDEX index_name ON table_name (column1, column2, ...);
```
# For single column index, you can use the following SQL command:

```sql
CREATE INDEX index_name ON table_name (column_name);
```

# For multi-column index, you can use the following SQL command:

```sql
CREATE INDEX index_name ON table_name (column1, column2, ...);
```
# To delete an index from a table, you can use the following SQL command:

```sql
DROP INDEX index_name ON table_name;
```

# For multi-column index, Order of columns in the index matters. The order of the columns in the index should match the order of the columns in the WHERE clause of the query for optimal performance. If the order of the columns in the index does not match the order of the columns in the WHERE clause, the database may not be able to use the index effectively, resulting in slower query performance.

# and if you made multi-column index but you want to use only one column in the WHERE clause, the database will still be able to use the index, but it may not be as efficient as using the index with both columns. In this case, the database will have to scan through all the rows that match the first column in the index and then filter those rows based on the second column in the WHERE clause. This can result in slower query performance compared to using an index that matches the order of the columns in the WHERE clause.