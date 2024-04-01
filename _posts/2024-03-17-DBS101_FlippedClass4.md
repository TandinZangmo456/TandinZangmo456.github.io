---
Title : DBS101 Flipped class 4 
categories : [DBS101, Flipped_Class4]
tags : [DBS101]
---

### Topic : Ranking, Windowing, Pivoting, Rollup and Cube.
----
The RANK function assigns a position to each value in a list, like ranking basketball players based on their scores. PERCENT_RANK tells us the percentage of values lower than a particular one to where you stand in your class based on test scores. CUME_DIST shows our position in a line based on a characteristic, such as height in a group. DENSE_RANK is like regular ranking, but if two values are the same, they share the same rank. FIRST_VALUE retrieves the first value in a specified window, useful for analyzing data like order values. Lastly, ROW_NUMBER assigns unique numbers to each row based on certain criteria, such as regional office and name. These functions help organize and analyze data efficiently in SQL.

Windowed aggregations in SQL help us do calculations on groups of data in a query. They are made up of three parts: PARTITION BY divides data into groups, ORDER BY sets the order for calculations, and ROWS BETWEEN or RANGE BETWEEN defines the rows we're looking at for each calculation. We use WINDOW clauses to define these parts and reuse them in our query. For example, we can calculate averages over specific groups of data. These windowed aggregations give us a powerful tool to analyze data in SQL, making complex calculations easier.

PIVOT in SQL helps us transform rows into columns in our query results. For example, if we have data showing products and their sales across different regional offices, initially listed row by row, PIVOT allows us to display the same information with each office's sales for each product listed in separate columns. This makes it easier to compare sales across different regions for each product. The PIVOT clause consists of three parts: the value being aggregated, the column being replaced by multiple columns, and the specified values from that column becoming new columns. It's important to note that PIVOT can't be used with WHERE, GROUP BY, or HAVING after the PIVOT clause.

ROLLUP and CUBE are tools in SQL that help organize and summarize data for detailed reporting. ROLLUP groups data hierarchically based on specified columns in the GROUP BY clause, providing summary totals for each level of the hierarchy. It can show total sales by region and then by sales agent. On the other hand, CUBE considers all possible combinations of values, useful for comparing different aspects of data without a strict hierarchy. It can display the total sales for each product and each sales agent. These tools make it easier to analyze and understand complex datasets, providing insights for decision-making.