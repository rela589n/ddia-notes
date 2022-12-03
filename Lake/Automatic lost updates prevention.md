PostgreSQL, Oracle, Sql Server support automatic lost update detection when running in **[[Snapshot isolation]]** level. MySQL doesn't detect lost updates automatically.

If there were **concurrent transaction**, which **modified the same row as we**, DB will **roll back current transaction** and throw an error.
