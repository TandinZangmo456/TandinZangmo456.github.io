---
Title : DBS101 Flipped class 9 
categories : [DBS101, Flipped_Class9]
tags : [DBS101]
---

### Topic : Query Optimization
----
In this Flipped class we learned about Query optimization. Query optimization through materialized views is a technique used to improve the performance of database queries by calculating and saving complex results in advance.

**What are Materialized Views?**

Materialized views are like saved snapshots of answers to questions in a database. In this materialized view instead of finding out the answer again and again, the answer is already saved, so that we can get it quickly without doing or solving the work again. They are different from regular views because in this it is more like live streams of data. 

**Benefits of Materialized Views**

1. **Improved Performance:** Since materialized views save already figured-out answers. So that's why asking for information can be quicker than figuring out the answer from the beginning.

2. **Reduced Workload:** By saving those answers, materialized view reduces the workload which leads to better overall performance and scalability.

3. **Offline Access:** We can still get the information stored in materialized views even if the main database has heavy workload or while we are not connected to the internet

4. **Support for Complex Queries:** This helps us make complicated questions easier to answer because the results are already saved and can retrieve it easily.

5. **Caching:** It act as a cache for frequently accessed data in which it reduces the need to execute resource-intensive queries repeatedly.

**How Query Optimization Works with Materialized Views:**

1. **Finding Hard Queries**: First, it tries to spot the queries which takes lots of time and resources to run it from the database.Which makes it faster.

2. **Making Materialized Views**: It create special views in the database using specific instructions in SQL. These views store the results of complex calculations. 

3. **Changing Queries Automatically**: The databases can automatically change how it looks for information. Instead of searching through the main data, it can use the saved answers in materialized views. This happens without the user noticing.

4. **Updating the Views**: Depending on how the system is set up:
   - **On Demand**: Users or administrators can update the views manually when they need to.
   - **Scheduled**: Views get updated regularly, like every day or every hour.
   - **Instantly**: Views get updated automatically whenever the main data changes.



**Considerations and Best Practices**
1. Storage Costs: Materialized views take up extra space in your database so therefore it is important to balance the speed benefits they bring with the space they use up.

2. Refresh Overhead: Refreshing materialized views can take up a lot of computer resources, especially if it is done often. So, pick a refresh plan that fits how fresh your data needs to be and how much your system can handle.

3. Choosing the Right Materialized Views: Not all queries get a big boost from materialized views. It's smart to focus on the ones that are used the most and are the slowest to run.

4. Indexing: Just like regular tables, you can add indexes to materialized views to make your queries even faster.

**Advanced Query Optimization in DBMS**
Optimizing queries is essential in managing databases, especially when dealing with large amounts of data. Advanced techniques in query optimization focus on improving query performance by reducing the time and resources needed to execute them efficiently. Here are some advanced topics you might encounter:

1. **Cost-Based Optimization**: This method determines the costs of different query execution plans and selects the one with the lowest cost, considering disk usage, CPU usage, and memory consumption.
2. **Query Rewriting**: Techniques like query rewriting adjust queries to increase efficiency, simplify complex expressions, remove unnecessary operations, and restructure queries to utilize existing indexes.
3. **Merge Techniques**: Combining data in relational databases can lead to slow performance. Advanced methods for joining data, such as nested loop joins, hash joins, and merge joins, have been developed to improve the performance of joins by leveraging data distributions and indexes.
4. **Indexing Techniques**: Indexes are crucial for improving query efficiency. Advanced indexing techniques such as composite indexes, covering indexes, and partial indexes optimize query execution by efficiently retrieving relevant data subsets.
5. **Simultaneous Query Processing**: Using multiple CPU cores or distributed processing frameworks can improve query speed for large datasets. Sophisticated techniques carry out queries simultaneously, guaranteeing data consistency and decreasing overhead.
6. **Materialized Views**: These store precalculated query outcomes, making it simpler to access frequently requested data. Advanced methods involve selecting and maintaining materialized views based on query patterns and workload features.
7. **Query Savings**: Keeping track of query results reduces the computational effort required for running the same queries again. Advanced caching methods consist of approaches like cache partitioning, invalidating query results, and utilizing adaptive caching policies to improve cache effectiveness.
8. **Improving Query Optimization using Statistics**: This technique improves cost estimation and optimization decisions by incorporating statistical information about data distributions and query patterns.
9. **Query Compilation**: Compiling queries involves creating executable code to minimize interpretation overhead and enable optimizations at the bytecode or machine code level.
10. **Utilizing Machine Learning for Optimization**: Machine learning techniques are employed to gather optimization strategies from data.Advanced methods involve training models to predict the efficiency of searches, select optimal execution strategies, or adjust optimization settings based on workload characteristics.
