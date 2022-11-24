Scaling the read requests makes **synchronous replication almost unusable**, because single node outage would lead to completely blocked writes.

When application **reads from async follower**, the **data may differ** from if it was read **from the leader**. Though, if for example stop all writes, wait a while, then all nodes will become consistent. This is called **eventual consistency**.

Issues with replication lag:
- [[Reading your own writes]];
- [[Monotonic reads]];
- [[Consistent prefix reads]].

### Solutions for Replication Lag

It should be anticipated how system has to operate when the replication lag is couple of minutes (possibly, hours). If the *eventual consistency* is enough, - that's great. If not, it would make sense to implement *read-after-write* strategy.

Though, sorting out replication issues on application code level is really complex and easy to get wrong. It would be much simpler if the database could handle such complexity for us. 

The **transactions** were brought in to simplify the application code development. They are usual for single-node database systems. But for distributed systems, some alterative mechanisms may be used (covered in Chapter 7, 9 and part 3)