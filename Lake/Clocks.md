**Clocks** are used for **duration measurement** (e.g. request-response) and to describe **points in time** (e.g. created_at field, scheduled email).

In distributed systems it is **hard to tell if one event occured before another**, because of **network delays** and the fact that **each node has its own clock**.

Each computer has **two clocks**:
- [[Wall-clocks|time-of-day clocks]]; ![[Wall-clocks#^69c3a4]]
- [[Monotonic clocks|monotonic clocks]]. ![[Monotonic clocks#^4b7ce2]]


