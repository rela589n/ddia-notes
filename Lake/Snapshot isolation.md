**Snapshot isolation** (**repeatable read**) - each **transaction sees** rows in the sate **committed before the beginning** of the transaction. Hence, it prevents [[Non-reepeatable read (Read skew)|read skew]].

See [[Implementing Snapshot Isolation]] for internal details.

> ?? How does it all work if we don't wrap reads into a transaction. I assume each operation is a separate transaction?

## Snapshot isolation and naming confusion

**[[Snapshot isolation|Snapshot isolation]]** is called **serializable** in Oracle and **repeatable read** in PostgreSQL and MySQL. In IBM DB2 **repeatable read** refers to **serializability**.
