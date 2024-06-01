---
Title: DBS101 Flipped class 10 
categories: [DBS101, Flipped_Class10]
tags: [DBS101]
---

### Topic: Transaction
----
**Introduction to Transactions**
In DBMS, a transaction is any of a set of procedural steps that make up a single business operation. It is one of the most basic notions in computer programming, where it is used to guarantee reliability of detailed activities, like reading and writing data. A program can contain one or several transactions, and each transaction is based on a separate series of operations with the program’s data, which is marked by the commands like BEGIN TRANSACTION and END TRANSACTION.

**ACID Properties of Transactions**
The integrity and reliability of transactions are ensured by adhering to the ACID properties: To maintain the basic levels of transaction consistency, reliability, and integrity, systems implement the ACID properties:

1. Atomicity: This property ensures every activity that needs to be performed in a transaction takes place and is effected successfully, or else they do not take place at all. If something goes wrong, all modifications are reverted back to the system, restoring its status to the one it was before the change.

2. Consistency: This means they should modify some attributes of the database from one good state to another and verify whether it has violated its invariants. Any data written into the database should be valid based on certain defined constraints, cascades, and triggers among others.

3. Isolation: These transactions have to be conducted concurrently as evidenced below. The method of isolation ensures that any transaction made will not interfere with any other transaction. All the transactions have to be effected as if the only conceptual transaction that exists in the system.

4. Durability: Once they have committed a transaction, it cannot be rolled back, for instance in a system failure. It also means that the outcome of a particular transaction is safely stored within the database.

**Simple Transaction Model**
![Alt text](../assets/sml1.png)

Consider a transaction that transfers $50 from account A to account B. The operations involved would be:

1. Read the balance of account A.
2. Subtract $50 from account A.
3. Write the new balance of account A.
4. Read the balance of account B.
5. Add $50 to account B.
6. Write the new balance of account B.

**Ensuring ACID Properties**
Transaction atomicity is achieved by writing change logs so that in case of a failure, a rollback can be done to the pre-transaction state. 

Committing provides durability since updates are written out to the nonvolatile storage before a transaction’s commit phase. 

Concurrency control is maintained by using techniques such as locking or by numbering transactions, for instance by granting timestamps. 

This is done at the end of the transaction to ensure that the database constraints have not been broken.

**Isolation Levels**
The different levels offer diverse degrees of isolation:

- Serializable: Provides full isolation.
- Consistent read: Falls short of being fully serializable, but prevents reading dirty data.
- Non-repeatable reads are allowed but only committed data can be read => Read Committed.
- Read uncommitted: This allows reading inconsistent data.

**Isolation Example**
Transaction T1 computes A + B after reading A and B.
Based on conflicting values, concurrent transaction T2 changes A and B.
Use concurrency control or execute transactions in a serial fashion as a solution.

Next, we did this transaction in PostgreSQL.

![Alt text](../assets/create.png)

**Transaction Atomicity and Durability**
1. Although transactions can fail, atomicity makes sure that their consequences are totally reversed in the event that they are unsuccessful.
2. These errors are handled by recovery plans with the help of transaction logs.
3. Every database update is tracked in this log, along with the transaction, the data that was changed, and the old and new values.
4. The system ensures atomicity and makes sure committed changes are permanent by examining the log and doing redos or undos as necessary.

![Alt text](../assets/ato&du.png)

1. Active:
![a](/assets/lib/active.png)

2. Partially Committed:
![Alt text](../assets/par_committed.png)

3. Failed
![Alt text](../assets/failed.png)

4. Aborted
![Alt text](../assets/aborted.png)

5. Committed
![Alt text](../assets/committed.png)

# Serializability
Serializability is a key concept in databases that ensures the results of multiple transactions happening at the same time are the same as if they happened one after the other.

**Why Serializability is Important**
In some cases, data corruption may happen when several transactions happen concurrently, and they interconnect with one another, such as when money transfers between two accounts are initiated. This is done in such a way that the end-result is the same as would be obtained if the transaction was being done one at a time, a concept referred to as serializability that helps prevent this.

**Types of Schedules in Database Transactions**
In database systems, schedule refers to the sequence of operations of the transactions, which include operations like read and write. Understanding the types of schedules helps to guarantee that the database remains intact and that transaction cannot hinder the others in wrong ways.

1. Serial Schedules

A serial schedule is one where the transactions are run consecutively without being overlapped at any point. This means that a transaction initiates only after the completion of the previous one.

Example:

T1: R(A), W(A), R(B), W(B)

T2: READ(C), WRITE(C)

In a serial schedule, the activities represented by T1 would be finished before the activities of T2 commence.

2. Non-Serial Schedules

A non-serial schedule enables several transactions to run concurrently. Although it maximizes concurrency and resource sharing, it creates a problem of how to maintain data integrity.

Example:

T1: READ(A)

T2: READ(C)

T1: WRITE(A)

T2: WRITE(C)

In this non-serial schedule, the operations of T1 and T2 are performed in an overlapping manner.

**Conclusion**
Understanding transactions in databases involves ensuring they adhere to the ACID properties: Atomicity means all the operations in the transaction will be completed successfully or none at all; Consistency means that a transaction will bring the database from one consistent state to another; Isolation means that the transaction cannot affect other transactions occurring simultaneously; Durability means that once a transaction has been committed, its effects cannot be reversed or rolled back. The enforcement of serializability and different levels of isolation concerning transaction processing is important when handling transactions concurrently. Whether the schedule is serial or non-serial, conflict scheduling reduces the number of conflicts on the outcome and always produces the same outcome every time the database is under concurrent access.
