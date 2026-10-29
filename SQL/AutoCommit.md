# AutoCommit is the default mode of operation for most relational database management systems (RDBMS). In AutoCommit mode, each individual SQL statement is treated as a separate transaction and is automatically committed to the database upon successful execution. This means that changes made by each statement are immediately saved and cannot be rolled back unless explicitly wrapped in a transaction block.

# to disable AutoCommit mode, you can use the following SQL command:

```sql  
SET autocommit = 0;  
```  
// now autocommit is disabled, and you can manually control transactions using the `COMMIT` and `ROLLBACK` statements.

Make changes and operations within a transaction block will not be permanently saved to the database until you explicitly issue a `COMMIT` command. If you encounter an error or decide to discard the changes, you can use the `ROLLBACK` command to undo all changes made within the transaction block.

# To re-enable AutoCommit mode, you can use the following SQL command:

```sql
SET autocommit = 1;  
```

# Use this auto-commit mode with caution, especially in scenarios where multiple related operations need to be treated as a single unit of work. Disabling AutoCommit allows for better control over transactions and ensures data integrity in complex operations.
# Use it when you afraid that correct data should be safe if i mistakenly execute a wrong command, and you want to rollback the changes.