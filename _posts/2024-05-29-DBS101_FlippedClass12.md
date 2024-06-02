---
Title : DBS101 Flipped class 12 
categories : [DBS101, Flipped_Class12]
tags : [DBS101]
---

### Topic : Recovery System
----
 
**Why are recovery systems so important in DBMS ?**

Recovery techniques used in DBMS are some of the most crucial for the proper running of a database center and the fidality of the data stored. They make sure the database can come back to a certain state when different types of failures occur in the system; these may include application crashes, hardware breakdowns, or electricity power loss, thus providing the ACID properties — atomicity and durability — for the transactions. It reduces the amount of data that can be lost by processes such as transaction logging, checkpointing as well as backup processes, which allow the computers to recover such lost data with little involvement on the part of the administrators. This also tends to boost user confidence and credibility of the DBMS besides minimizing business interruption or data loss resulting from downtime or other malicious activities.

**Recovery algorithms in DBMS**

In DBMS, recovery algorithms help to put the lost data in their proper states after a break has occurred. All these algorithms deal with several failure situations so that the database is capable of trusting accurately and quickly.

1. Undo/Redo Logging: This technique involves keeping of ledgerbooks which contain records of all the transactions taking place. There are two types of logs: , the two most important are the undo logs, which undo the changes made by a non-logged or only partially logged transaction after it was aborted, and redo logs, which re-apply the changes made by a logged transaction when a crash occurred after the commit issuing. Failure recovery system employs these logs to rollback incomplete user committed transactions and to update completed uncommitted transactions making the database consistent.

2. Write-Ahead Logging (WAL): Since the changes made to the application are synchronized with WAL, all the changes made before the database is updated is logged. This ensures that in the contingency-devel circumstance, where the system can leverage the log to roll back uncommitted changes. There is one basic rule and it says that one should write the log before changing the database and this is useful both when doing the undo operation and redo operation.

3. Checkpointing: Every now and then, the DBMS takes a snapshot of a certain state of the database, and this is called check point. This also helps recovery by allowing a certain cluster point beyond which all the logs before this do not have to be evaluated because the data is already past a certain point in time. This contributes in reducing the possibility of transactions that have to be processed all over again in order to recover them, thus speeding up the recovery process.

4. ARIES: It employs the log based recovery technique called WAL for the recovery process to enhance the recovery process by checkpointing in the optimization of logs and selective logging of the logs for enhancing the overall recovery process of ARIES. It involves three main phases: It was noteworthy when identifying such words as analyze, redo, and undo, which may be unfamiliar to individuals who have never worked on the software. The analysis phase determines the transactions that need to be brought back, the redo phase replays all the changes made during the fraudulent transactions in the database, and the undo phase reverses all the changes made by all the other transactions.

**Recovery in main-memory databases**

Techniques of recovering data have to be adopted to ensure the functionality of main memory databases since RAM is volatile and clears data on crash. The methodologies of logging and checkpointing are redo and undo logs, and stored snapshots in the non-volatile storage to increase the lifetime of data, and perils of non-volatile memory together with persistent memory like NVM and PMEM. Application data can be configured as flash and disk data; other less important data, such as in-memory data, are stored on a disk; node replication helps increase storage availability and stability. Some of the techniques involves roll back to return to a steady state and other related tools like snapshot isolation and MVCC for increased data handling. Other forms of reliability also include very high levels of redundancy like RAID, redundant power supply options, and ECC memory.

**ARIES** 

ARIES means Algorithm for Recovery and Isolation Exploiting Semantics, is another effective recovery algorithm to handle the recovered failures that occur in a DBMS. Initially introduced in IBM by C. Mohan and his team in early 1990s, ARIES is also successful in maintaining database consistency and durability in a very efficient way. Here's an overview of ARIES, including its key concepts and mechanisms:Below, I briefly describe ARIES and the its main ideas and procedures: 
 
Key Concepts 
 
1. Write-Ahead Logging (WAL): ARIES implements the WAL protocol that ensures that the logs are made before the changes made are incorporated into the database. This is vital because the system have to have the log to perform a recovery function this way absolutely nothing is compromised. 
 
2. Logs: The logging in ARIES involves the same three types of logs as the evaluation, but all in one. 
 
 1. Redo Logs: These logs are generally kept to indicate the new values of the data after the changes have been made. 
 
 2. Undo Logs: Such logs retain the previous values through the instances of change or the time when change is due to take place. 
 
 3. Log Sequence Number (LSN): The record includes a Long-SQL Name which although may be trivial in some ways is important because it defines a order of events that were helpful when it came to reconstructions. 
 
3. Checkpoints: Thus, ARIES establishes some points at regular intervals; in this way the system limits the number of data operations that are candidates for backup, thereby limiting the amount of work that has to be done in the actual recovery process. A checkpoint secures the state of the system at the time of checkpointing, open transactions, position of the entities and the log. 
 
**Recovery Process**

The ARIES recovery process involves three main phases:There are three main stages in the concept of the ARIES recovery process mentioned above.

1. Analysis Phase:

This phase focuses on planning the situation of the system at the time of the crash.

In forward scanning it starts from the last checkpoint; it finds which transaction were active at that time and which page is dirty (In simple words, which all pages have been changed but not written onto the disk) and the minimum LSN (Log Sequence Number) of these pages.

2. Redo Phase:

The redo phase is to rewrite all the transactions and updates made by the commits in the logs to ensure that all the changes are contained in the database.

Starting from the least significant LSN derived from the analysis phase, the program re-processes every entry in the log in order to ensure that the log entries are idempotent, which merely implies that the same operation works only once, irrespective of whether it has been performing multiple times.

3. Undo Phase:

This phase Undoing affects restoring the system back to the state before the abnormal termination by undid the work of all incomplete transactions at the time of failure.

This method uses the undo logs to freeze the changes in an opposite manner to how the LSNs were employed as a way of making the database return back to its state as it was before the occurrence of the transactions.

**Advantages of ARIES**

Efficiency: RIC for redo and undo helps to avoid processing of the whole log and that is why recovery with ARIES becomes quicker.

Minimal Overhead: This relieves the normal run of business from the burden of numerous transactional concerns and on the other hand enriches the check point concept and the WAL protocol.

Fine-Grained Recovery: As it has already been noted, ARIES allows for the relatively slow and consistent recovery on the page level in large databases and does this gradually.

Support for Multiple Types of Failures: ARIES can deal with diverse failures such as system failures and media failures and has implemented multilevels of recovery.

Concurrency Control: ARIES has been designed that way to provide concurrent transaction processing with different levels of transaction, and to make the effect of recovery mechanism on the processing of transactions less severe.

**Write-Ahead Logging (WAL)**

Write-Ahead Logging (WAL) is a core concept employed in the DBMS to guarantee the coherence of information and support an organization’s ability to recover from failures or crashes. 
 
WAL’s primary concept is a record of changes before they are written to the database. This means that in situation where system fails, the database will be in a point where it could be restore by help of the log information kept. Here are the key aspects of WAL:Here are the key aspects of WAL: 
 
Key Principles 
 
 1. Logging Before Writing: It is the practice with many database systems to make a record of any alteration that is planned, in a separate log file before it is enacted. It also ensures that each operation in carrying out in such a way that there’s a back up in case of any mishap. 
 
 2. Sequential Logging: For the logging process, the log entries are recorded to stable storage successively; it implies that unlike the random writing to the database, the process is not vulnerable to performance issues. 
 
 3. Atomicity and Durability: WAL is useful in the atomicity and durability of transactions which means that either all of the transactions made are successfully completed or none is completed and that even if some of the transactions were committed, they cannot be rolled back. If a system has been involved in a crash then, through the work of WAL, every new committed transaction is replayed whereas every uncommitted transaction is rolled back. 
 
WAL Process 
 
1. Transaction Start: Before any activity in a transaction takes place, the system records a log that it is in a particular transaction. 
 
2. Operation Logging: For each operation that takes place in the database (update, insert, delete and etc. ), a new entry is created in the log. This entry includes: 
 
 1. The transaction ID. 
 
 2. The type of operation. 
 
 3. The data before the change is the information which was recorded before the application of the procedure. 
 
 4. The data after the change, redo information is the data when the change has already occurred.

3. Commit: If a transaction is prepared for commitment then a commit record is written in the log. After the commit record is safely put in the log, the system then considers the transaction as finally committed. 
 
4. Applying Changes: After logging the changes and the commit record, the actual change can be contemplated on the database, into which the values actually will change. The database system makes definite that the converts are relayed into the database pages. 
 
**Recovery Using WAL**
 
In the event of a system failure, WAL allows the database to recover to a consistent state through the following steps:In the event of a system failure, WAL allows the database to recover to a consistent state through the following steps: 
 
1. Analysis Phase: In recovery, the system scans through the log and finds out the failure point and which transactions were ongoing. 
 
2. Redo Phase: The system simply play back the Logged entries from the moment, the last checkpoint was taken to redo all committed transactions. This means that all committed transaction’s changes are always incorporated in the database. 
 
3. Undo Phase: This is done to any active but not committed transactions at the time of the crash, by utilizing the undo information stored in the log. This insulates the database from having half done updates that are created by uncommitted transactions from appearing in the database. 
 
**Benefits of WAL**
 
Efficiency: Sequential writes to the log are usually more time efficient than random writes to the database, enhance the systems performance. 
 
Consistency: This enables the database to be brought back to a consistent state after a failure through replay or undo of each of the transactions from the log.

Atomicity: This is because, generalizing from the specifics of the example, by writing the changes to the log before perhaps writing them to disk, that guarantees that a transaction is either committed, in the sense of being made permanently part of the database, or rolled back, in the sense of being undone entirely. 
 
Durability: Assurances that once data is written by a transaction it is recoverable and will remain so even in case of a failure. 
 
**DB Logging.**

Database logging is an element of a Database Management System (DBMS) that assist in maximizing security and credibility of the data kept in a database. Logging is a process by which information on modifications made on the database is stored in a log file before the modifications are effected on the database. This mechanism is crucial in as far as it is useful in enabling recovery procedures in the instance where the system has crashed. 
 
There are several objectives of logging in DBMS, and they form the foundation of effective way of maintaining data integrity and consistency as well as data recovery. Logging makes the system to record changes that are made to the database in a log that runs in a sequence before the changes are actually committed, this helps in failure situations such as system crashes or power failures. This enables the undo and redo methods to be implemented during the recovery, thus making sure that any transaction either gets fully committed, or fully rolled back, which is the ACID property of data. Moreover, it also plays a role of maintaining concurrency control since a record is kept detailing some of the activities in the database, for purpose of monitoring, analysis and forensic. In general, the use of this file is highly essential in ensuring the reliability, recoverability, and accountability of the databases in the present day computing structures. 
 
**Types of Logs**

Redo Logs: 
 
Redo logs contain the fresh values of data after the modification of the database. 
 
It holds details of the completed transactions and the changes that the latter has done on the data base. 
 
Redo Log: During recovery, it is used to rewrite the changes that decided transactions in order to say that no committed transaction is done. 
 
It is very important to have redo logs available because the committed changes can be replayed on the database to bring it back to a consistent state after a crash/failure. 
 
Undo Logs: 
 
Transactional logs store information on the prior values of data before changes are made to the database. 
 
They are used to reverse the consequences that relate to invalid or partially completed transactions during the recovery process. 
 
In case a transaction is initiated and has not made the commit statement at the time of the failure, then the changes made by the current transaction must be rolled back for proper integrity of the database. 
 
Undo logs contain all the changes that uncommitted transactions made, so the database can always return to an original conformed status. 
 
**Conclusion**
Recovery systems are essential in the management of databases since information management mostly comprises large amounts of data that cannot be afforded to be lost due to circumstances such as system crashes or power outages. These systems make it possible for databases to restore the data base to a certain common state after such incidents, thus ensuring atomicity and durability of the transactions. Such tools that support transaction log, checkpoints, and backups are undo/redo log, Write-Ahead Logging (WAL), and ARIES which help in the efficient recovery of phases. Recovery techniques in main-memory databases are similar to those used in recovery of logs as far as ensuring the durability of data is concerned, where the new technologies such as Non-Volatile Memory (NVM) and Persistent Memory (PMEM) are used. In sum, recovery systems are crucial to implementing guarantee solutions for data access, reducing time loss and providing credible means for the stored information.