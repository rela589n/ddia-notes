Race conditions arise when users access the same (or dependent) database rows. 
**Transaction isolation** was meant to **hide concurrency issues** from devs. 
**Serializable** level means that any **transactions** are executed **as if they were serial**, though it is rarely used because of 
**high performance penalty**.

Levels:
- Read Uncomitted (not used);
- [[Read Comitted]];
- [[Snapshot isolation]];
- [[Serializable]].
