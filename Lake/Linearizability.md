**Linearizability** (aka **atomic consistency**, **strong consistency**, **external consistency**) - [[Consistency guarantees|consistency guarantee]], which abstracts the system as **if it had only one replica**. In fact, there may be multiple copies, but system looks like as if there were only a single so that app doesn't need to worry about multiple replicas.

Linearizability provides a **recency guarantee**, meaning that once some value was written or read, all subsequent reads will return latest written value until it is overwritten again.



