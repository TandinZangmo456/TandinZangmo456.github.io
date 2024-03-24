---
Title : DBS101 Flipped class 4 
categories : [DBS101, Flipped_Class4]
tags : [DBS101]
---

### Topic : Ranking, Windowing, Pivoting, Rollup and Cube.
----

Normalization in DBMS
Normalization in DBMS is organizing the information in different categories so that it is easy to manage and makes sense. Normalization works by avoiding repetition, keeps thing neatly and makes relationships clear. We need normalization beacuse it avoids messy works, consistency, less usage of space and flexibility. If we don't normalize the data will be messy, datas can't be added normally without risks, need to see through all the datas risking missing of datas and we might accidentally delete other related datas. There are different levels of organization called normal forms, each with its own rules to make sure the data is properly organized. They start from First Normal Form (1NF) and go up to Fifth Normal Form (5NF). Each higher level builds upon the previous one, making the data even more organized and efficient.

First normal form 
In First Normal Form, each column should contain only one piece of information. So, each cell in your table should have only one value, like choosing one color for each one of the friend as an example.

Second normal form
The Second Normal Form (2NF) is a level of organization in database design that makes sure that the data's integrity and minimizes redundancy. To qualify for 2NF, a table must meet two criteria: the table should be in first normal form and no partial dependency(where an attribute depends on only part of the primary key). To remove partial dependency and bring the table into 2NF, we need to remove the attribute that depends on only part of the primary key.

Third normal form 
The Third Normal Form (3NF) is another level of organization in database design which builds upon the principles of the First Normal Form (1NF) and Second Normal Form (2NF).
To be in 3NF, a table must meet the following criteria: First Normal Form (1NF) and Second Normal Form (2NF) must be satisfied.there should not be Transitive Dependency.

Boyce-Codd Normal Form
Boyce-Codd Normal Form (BCNF) is a higher level of normalization in database design which builds upon the principles of the Third Normal Form (3NF). 

BCNF is an advanced level of normalization beyond 3NF. While 3NF resolves many issues related to data redundancy and anomalies, BCNF takes it a step further to handle additional anomalies. For each functional dependency (X → Y), X should be a super key or should uniquely identify every tuple in the table. It helps in addressing anomalies such as insertion, update, and deletion anomalies, ensuring data integrity and consistency.BCNF ensures that the table structure is optimized and free from certain types of anomalies that might still exist in 3NF tables.

The Fourth Normal Form 
The Fourth Normal Form (4NF) is a level of organization in database design where a table must meet two important conditions. First, it needs to already be in the Boyce-Codd Normal Form (BCNF), which is a more basic form of normalization. Second, the table should not exhibit what we call Multi-Valued Dependency. Multi-Valued Dependency occurs when certain data dependencies within the table lead to unnecessary repetition and complexity. 4NF ensures that the table structure is optimized and free from certain types of anomalies, leading to more efficient data storage and retrieval. It's like ensuring that everything is neatly organized and there's no redundant information floating around, making it easier to manage and maintain the database.

Fifth Normal Form
Fifth Normal Form (5NF) is the highest and most advanced level of organizing data in a database. When a database is in 5NF, it's super optimized and streamlined. By smoothing out these connections, 5NF ensures that the database runs smoothly and efficiently. Plus, it reduces data redundancy and fixing update anomalies. 