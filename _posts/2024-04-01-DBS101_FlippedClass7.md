---
Title : DBS101 Flipped class 7 
categories : [DBS101, Flipped_Class7]
tags : [DBS101]
---

### Topic : Building a relational database system from scratch
----

In today's class, i learned about the storage and buffer management which are diviided in to three parts that is simulate disk blocks, RAID configurations, and buffer pools.

Disk Block Management is considered really important because it manages the space on a disk efficiently to store and get back data as fast as possible. Which clearly includes putting data in order, getting rid of blocks we don't need anymore and tidying up the disk to keep things neat and tidy.

1. We create a DiskBlock instance with 10 blocks of size 512 bytes.
2. We allocate contiguous blocks for data1 and read/write data to those blocks.
3. After deallocating data1, we allocate new blocks for data3.
4. Finally, we defragment the disk, which consolidates the allocated blocks for data3.

RAID Configuration and Management is important because we get to know about different types of RAID setups. From RAID setup, RAID 0 can make things faster because the computer can read and write multiple disks at once. RAID 1 can make many copies of the data on multiple disks ensuring the safety of the data even if many things occur as the system can automatically fix things itself. 

1. We create a RAIDArray instance with 4 disks, block size 512 bytes, and RAID level 0 (striping).
2. We write data to the RAID 0 array and read it back.
3. We create another RAIDArray instance with 4 disks, block size 512 bytes, RAID level 1 (mirroring), and 1 spare disk.
4. We write data to the RAID 1 array, read it back, simulate a disk failure, and rebuild the array using the spare disk.

Buffer Pool Management: Managing a buffer pool efficiently is important for improving data access speed and overall system performance. As we can Initialize the buffer pool with an appropriate size to balance memory usage and performance. We can implement mechanisms to fetch and update pages efficiently which includes eviction policies such as least recently used (LRU) eviction. And integrating buffer pool management with disk I/O operations to minimize latency and optimize resource utilization.

1. BufferPool class represents the buffer pool with methods to fetch pages.
2. init method initializes the buffer pool with a specified size.
3. fetch_page method is responsible for fetching a page from the buffer pool. If the page is already in the buffer, it updates its usage count.
4. If not, it fetches the page from disk (not implemented in this example) and adds it to the buffer pool. If the buffer is full, it evicts the least recently used page.

According to the relevant materials given, it introduces chidb, a quarter-long C programming project in which the students implement a basic relational database management system from scratch. Here's an outline of the important procedures to be followed when building a relational database system from scratch, along with the data structures used and their importance:

1. **File Format Definition:**
   -It efficiently store tables, indexes, and schema information. It also establishes a structured way to store data on disk and enabling retrieval using specific layouts.

2. **Data Structure Selection:**
   - It should choose appropriate data structures to represent tables and indexes. So B-trees are a common choice as they provide fast access to data by keeping it sorted and enabling efficient insertions and deletions.

3. **Database Machine (DBM) Design:**
   - It specially designs a virtual machine specifically for operating on the database files.
   - Has 36 demand instruction which includes instructions for low-level operations like data manipulation and high-level database-specific tasks like table creation.

4. **SQL Compiler Development:**
   - It create a compiler that can parses SQL statements into a usable format as the compiler translates user-friendly SQL queries into instructions the DBM can execute.

5. **API Design:**
   - Provides a well-defined API for external programs to interact with the database system as it also allows other applications to create, access, and manipulate data using the database.

**Importance of Each Procedure:**

- **File Format Definition and Data Structure Selection:** Establish a foundation for data storage and retrieval, impacting performance and scalability.
- **Database Machine Design:** Enables execution of database operations and bridges the gap between high-level SQL and low-level data structures.
- **SQL Compiler Development:** Makes the system user-friendly by allowing interaction through SQL queries.
- **API Design:** Provides a layer of abstraction for external programs to interact with the database system.

By following these procedures and using appropriate data structures, you can build a functional relational database system from scratch. This approach offers a comprehensive understanding of how database systems work internally.