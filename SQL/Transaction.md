# Transaction 

A transaction is a sequence of operations performed as a single logical unit of work in a database. It ensures that all the operations within the transaction are completed successfully, or if any operation fails, the entire transaction is rolled back to maintain data integrity.

# The ACID properties of transactions are:
ACID stands for Atomicity, Consistency, Isolation, and Durability. These properties ensure that database transactions are processed reliably.
These terms are as folows:
- **Atomicity**: Ensures that all operations within a transaction are treated as a single unit. If any operation fails, the entire transaction is rolled back, and no changes are made to the database.
- **Consistency**: Ensures that a transaction brings the database from one valid state to another valid state, maintaining the integrity of the data.
- **Isolation**: Ensures that concurrent transactions do not interfere with each other. Each transaction    should be executed in isolation, as if it were the only transaction in the system.  
- **Durability**: Ensures that once a transaction is committed, its changes are permanent and will survive any subsequent system failures.

    # for this the command we use are   
- `BEGIN TRANSACTION` or `START TRANSACTION`: This command marks the beginning of a transaction block. All subsequent operations will be part of this transaction until it is either committed or rolled back.
- `COMMIT`: This command is used to save all changes made during the transaction to the database. Once a transaction is committed, the changes become permanent and cannot be rolled back.
- `ROLLBACK`: This command is used to undo all changes made during the transaction. If any operation within the transaction fails or if you decide to discard the changes, you can use `ROLLBACK` to revert the database to its previous state before the transaction began.    
