---
Title : DBS101 Flipped class 9 
categories : [DBS101, Flipped_Class9]
tags : [DBS101]
---

### Topic : Concurrency Control
----
**Introduction to Concurrency Control**

Concurrency control is a concept that is related to the Transactions in a database system. It is a procedure in DBMS which helps in management of two simultaneous process to execute without facing any problems between each other. Concurrency control is important for making sure that it is reliable and it's correctness of transaction in a multi-user database environment. By using many different techniques such as locking protocols, timestamp ordering and optimistic control methods, DBMS can handle problems associated with it, prevent data inconsistencies and maintain data integrity.

**Locks**

Locks are a fundamental part of concurrency control in a DBMS which helps manage data access by allowing transation to acquire and release locks on data items, ensuring conflict prevention and isolation enforcement.

Types of Locks

1. Shared Lock (S): Allows transation to read the data items.

2. Exclusive Lock (X): Allows a transaction to read and write a data item.

**Why should we lock resources?**

Locking resources in database system is important in maintaining data consistency, integrity and isolaion so that concurrent transation is executed safely. It also guarantees that specific data items are locked individually one at a time.

**Lock Management**

Locking management is a process in which it helps us to regulate access to data items. The lock manager provides access if they don't conflict with existing locks; otherwise, it detects conflicts and resolves them.

**Two-Phase Locking (2PL)**
Two-phase locking (2PL) is a basic concurrency control strategy used by Database management systems for the sake of making sure that the set of transactions is serializable. It operates in two phases: the cooperative growth phase and a declining phase.

Growing Phase: That’s why during this phase of the transaction, it can only make take locks, and cannot commit any lock that it has taken, however. In other words, when a transaction is looking to perform a certain operation it is allowed to acquire locks on data items but at the same time it cannot relinquish these locks for the next phase of the transaction.

Shrinking Phase: The moment the first lock is obtained, a transaction is adjusted to what is termed as the shrinking phase. In this phase, the transaction can commit and unlock a potentially shared resource but cannot input a lock on a potentially exclusive resource. There is however a shortcoming of this lock, once a lock is released it cannot be acquired again.

**Advantages of Two-Phase Locking**

Serializability: Two-Phase Locking guarantees that when the above mentioned multiple transactions are executed concurrently, the results obtained by their interleaved execution would be equivalent to results of some sequential execution of those transactions and thus the integrity of the data is maintained.

Deadlock Prevention: It is ensuring that Two-Phase Locking protocols are followed so that deadlocks do not happen in the system. A deadlock state is defined as a condition when transactions wait for requested locks with other transactions that have locks reserved. In 2PL locks are acquired before any release hence excluding deadlocks cannot occur.

Simplicity: Hence, the protocol is easy to implement and comprehend, putting it among the most favored in the database systems.

**Deadlocks**
Deadlock Deadlocks are situations whereby transactions wait for other transactions to release their locks and releases its owns in the process leading to a loop.

Deadlock Detection: The system performs a test periodically to look for cycles in the waits-for graph and then picks a transaction to rollback in an effort to break the deadlock.

Deadlock Prevention: It is also noted that there are priorities assigned to the transactions. This happens when a transaction that has a higher priority for the resource it requires seeks to obtain a lock held by a transaction that has a lower priority for the same resource; the low priority transaction is rolled back.

**Lock Granularity Granularity refers to the scope of locks**

Fine-Grained Locks: The transactions for which such as on individual tuples offer high concurrency while incurring more overhead.

Coarse-Grained Locks: In cases where they are used on entire tables, it lowers overheads while at the same time it lowers concurrency.

Lock Escalation: There may be many low-level locks to be managed; therefore, the system can escalate to the higher level of lock, for instance, from row level to table level.

**Optimistic Concurrency Control This method assumes conflicts are rare**

They happen normally and are only checked for conflicts when a transaction is committed.

This is so because in the event of conflicts, transactions are rolled back and then restarted.

**Timestamp-Based Concurrency Control Transactions are ordered using timestamps to ensure serializability**

Transactions read and write in consecutive order based on their time stamp to conform with Principle of Temporal Consistency.

The Thomas Write Rule thus provides that some writes can be ignored to reduce chances of aborts.

**Multi-Version Concurrency Control (MVCC) MVCC allows multiple versions of a data item to exist**

Writers write new versions, all the while readers get the most current selected version at the time of the start of the transaction.

This approach makes it possible for readers and the writers to operate at the same time and without interfering with each other.

**Intention Locks**
Intention locks make it possible to lock nodes at the higher levels of a database lock hierarchy in shared or exclusive mode without having to complete all their sub-nodes. They show that some transaction is performing explicit locking at a lower level of the tree. ”

**Types of Intention Locks:**

1. Intention-Shared (IS): SThis sort of intention lock shows that blatant locking is taking place at another tier in the level of DBMS hierarchy employing the shared (S) lock.

Non-exclusive locked status A transaction that uses a read phase will ‘lock Intent’ for shared permission on a more detailed level that means that data can be read by other transactions while they cannot be written.

In IS locks, to some extent, one IS lock can be compatible with another IS lock or an S lock to enable multiple transactions at the same time.

2. Intention-Exclusive (IX): It is an intention-exclusive lock indication that an intent of actual locking is being applied on lower level by employing exclusive (X) locks.

They signify the desire to obtain greater exclusivity on the database, and allow a transaction to read as well as write lock the data.

IX locks can be used with other IX locks and X locks but this is not applicable with IS locks, thus guaranteeing the data exclusive right of access.

3. Shared+Intention-Exclusive (SIX): This type of intention lock shows that a specific subtree with the node as its root is specifically locked in shared mode or S but at an underlying level, the lock is specifically in exclusive mode or X.

SIX locks there is possible that some part of data set can be read or updated by many clients while others part of data set is protected and can be read or updated only by one client.

They enable transactions sharing and also exclusive locking in a way that allows multiple transactions to run concurrently while at the same time some data remains locked.

Compatibility Matrix: This matrix probably outlines how standard lock and intention locks go together. This assists in making sure that later transactions can get locks for the transactions that they wish to do without creating a conflict with the locks already possessed by the preceding transactions.

Locking Protocol: Based on the locking protocol described it is clear that each transaction acquires the correct lock at the highest level of the database tree. In order to gain the S or IS lock on a node, the transaction must already have at least IS lock on the parent node. Likewise to obtain a value of X, IX or SIX on a node, the transaction must hold at least IX on the parent node.

Advanced Concurrency Control Techniques

Other database concurrency control approaches extend two-phase locking when strict serializability is not the only issue to be tackled. Thus, low-consistency models, like Degree-2 consistency or cursor stability, provide a higher level of concurrency at a lower consistency level. OCC lets transactions run without requesting locks, checking conflicts on the time of commitment. Thus, main-memory databases utilize course-grained latches or latch-free/lock-free data structures to enhance concurrency. Custom operations, for example, increment, improve parallelism of concurrency control while satisfying application restrictions. Real-time databases therefore categorize transactions by time, thereby preferring optimistic concurrency in a bid to avoid deadline misses. These techniques represent such changes towards more elastic frameworks, focusing on concurrency, performance, and consistency adjusted for various types of applications.