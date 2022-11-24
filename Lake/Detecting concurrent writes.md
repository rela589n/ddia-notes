When two clients concurrently modify the same piece of data, some nodes may **receive updates in the different order**. 
- Node1 may receive update from client A, and not receive from B (due to network issue);
- Node2 may receive first update from A, then from B;
- Node3 may receive first update from B, then from A.

## Last write wins (discarding concurrent writes)

In #Cassandra this is the only conflict resolution method.
In #Riak this is optional method.

#LWW -  each write is associated with the timestamp. On conflict, writes 
with more **recent timestamp wins**. 

There may even be the cases when **LWW drops writes** which are **not concurrent**. Therefore, it should only be used where **lost writes are acceptable** (like caching).

> This method achieves **convergence** by the **cost of durability** - clients were informed that write was successful, though it is silently discarded later on.

## The "happens-before" relationship and concurrency

#causality

![[Happens-before relationship]]

![[Concurrent operations]]

## Capturing the happens-before relationship

The algorithm to **capture concurrent writes**:
- when the values are written, **version number is incremented**;
- during the read, all **not overwritten versions of data are returned** to the client;
- during the write, the **version used to read the data is sent**. Client is responsible for **merging the values returned by read** (different due to concurrency versions of data);
- when server receives write, it **overwrites** all values with **version less than or eq to the current one** (sent along with the write), but **keeps greater versions**, because they are concurrent to the current write.

## Merging concurrently written values

> **Siblings** - values written concurrently.

When it comes to merging the values, **siblings can't be rashly unioned**, because even though we can **easily merge added items**, there would be **issues when deleting items**. 

One sibling may remove the **deleted item from the collection**, while it will still be **kept in another sibling**. To allow deletion, [[Tombstone marker]] can be used.

Usually custom **merging code is error-prone**. The **automatic merge** is possible as well, **using CRDT**s, which merges siblings in sensible way including deletions.

## Version vectors

#TLDW

When there are multiple replicas with no leader, algorithm changes following way. 

The **version number** is maintained **per each replica** **per each key**. Each replica **increments it's own version** number. Also, it **keeps versions of other replicas**.

**Version vector** - collection of **versions from all replicas**.