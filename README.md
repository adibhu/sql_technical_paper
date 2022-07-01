# sql_technical_paper
## ACID
- In order to maintain consistency in a database, before and after the transaction, certain properties are followed. These are called ACID properties.
### Atomicity
- The entire transaction takes place at once or does not happen at all.
### Consistency
- The database must be consistent before and after the transaction.
### Isolation
- Multiple transactions occur independently without interference.
### Durability
- The changes of the successful transaction occurs even if the system failure occurs.

## CAP theorem
- CAP theorem, also known as Brewer’s theorem, stands for Consistency, Availability and Partition Tolerance.
### Availability
- Imagine there is a very popular mobile operator in your city and you are its customer because of the amazing plans it offers. Besides that, they also provide an amazing customer care service where you can call anytime and get your queries and concerns answered quickly and efficiently. Whenever a customer calls them, the mobile operator is able to connect them to one of their customer care operators.

The customer is able to elicit any information required by her/him about his accounts like balance, usage, or other information. We call this Availability because every customer is able to connect to the operator and get the information about the user/customer.
### Consistency
- Now, you have recently shifted to a new house in the city and you want to update your address registered with the mobile operator. You decide to call the customer care operator and update it with them. When you call, you connect with an operator. This operator makes the relevant changes in the system. But once you have put down the phone, you realize you told them the correct street name but the old house number (old habits die hard!).

So you frantically call the customer care again. This time when you call, you connect with a different customer care operator but they are able to access your records as well and know that you have recently updated your address. They make the relevant changes in the house number and the rest of the address is the same as the one you told the last operator.

We call this as Consistency because even though you connect to a different customer care operator, they were able to retrieve the same information.

## Partial tolerance
- Recently you have noticed that your current mobile plan does not suit you. You do not access that much mobile data any longer because you have good wi-fi facilities at home and at the office, and you hardly step outside anywhere. Therefore, you want to update your mobile plan. So you decide to call the customer care once again.

On connecting with the operator this time, they tell you that they have not been able to update their records due to some issues. So the information lying with the operator might not be up to date, therefore they cannot update the information. We can say here that the service is broken or there is no Partition tolerance.

## Joins
- A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

 ### Inner join
 - Returns records that have matching values in both tables.

 ### LEFT (OUTER) JOIN
 - Returns all records from the left table, and the matched records from the right table.

 ### RIGHT (OUTER) JOIN
 - Returns all records from the right table, and the matched records from the left table.

 ### FULL (OUTER) JOIN
 - Returns all records when there is a match in either left or right table.

## Aggregations and filters
- Aggregation in SQL is, typically, used in conjunction with grouping. The Group By clause is used to arrange rows into groups in SQL. Aggregation, together with grouping, is key to generating quick reports and insights from a database. For example, an ecommerce company might want to see its highest spending customers over a given time period.

### Commonly Used SQL Aggregate Functions
- AVG: This calculates the average of all values in a group.
- MIN: It returns the lowest value in a group.
- MAX: MAX aggregate function in SQL returns the largest value in a group.
- COUNT: It is used to count the number of rows in a set. the COUNT function includes rows with NULL values.
- SUM: This is used to calculate the sum of all non-NULL values in a group.

### filters
- SQL filters are text strings that you use to specify a subset of the data items in an internal or SQL database data type. For SQL database and internal data types, the filter is an SQL WHERE clause that provides a set of comparisons that must be true in order for a data item to be returned.
#### Operators
- >
- <
- =
- <=
- =>
- !=
- LIKE

## Normalization
- Normalization is the process to eliminate data redundancy and enhance data integrity in the table. Normalization also helps to organize the data in the database. It is a multi-step process that sets the data into tabular form and removes the duplicated data from the relational tables.

Normalization organizes the columns and tables of a database to ensure that database integrity constraints properly execute their dependencies. It is a systematic technique of decomposing tables to eliminate data redundancy (repetition) and undesirable characteristics like Insertion, Update, and Deletion anomalies.

### 1 NF(first normal form)
- A table is referred to as being in its First Normal Form if atomicity of the table is 1.
- Here, atomicity states that a single cell cannot hold multiple values. It must hold only a single-valued attribute.
- The First normal form disallows the multi-valued attribute, composite attribute, and their combinations.

#### Candidate key
- A candidate key is a set of one or more columns that can identify a record uniquely in a table, and YOU can use each candidate key as a Primary Key.

#### Super Key
- Super key is a set of over one key that can identify a record uniquely in a table, and the Primary Key is a subset of Super Key.


### 2 NF (Second Normal Form)
- The first condition for the table to be in Second Normal Form is that the table has to be in First Normal Form. The table should not possess partial dependency. The partial dependency here means the proper subset of the candidate key should give a non-prime attribute.

### 3 NF (Third Normal Form)
- The first condition for the table to be in Third Normal Form is that the table should be in the Second Normal Form.
- The second condition is that there should be no transitive dependency for non-prime attributes, which indicates that non-prime attributes (which are not a part of the candidate key) should not depend on other non-prime attributes in a table. Therefore, a transitive dependency is a functional dependency in which A → C (A determines C) indirectly, because of A → B and B → C (where it is not the case that B → A).
- The third Normal Form ensures the reduction of data duplication. It is also used to achieve data integrity.

### Boyce CoddNormal Form (BCNF)
- Boyce Codd Normal Form is also known as 3.5 NF. It is the superior version of 3NF and was developed by Raymond F. Boyce and Edgar F. Codd to tackle certain types of anomalies which were not resolved with 3NF.
- The first condition for the table to be in Boyce Codd Normal Form is that the table should be in the third normal form. Secondly, every Right-Hand Side (RHS) attribute of the functional dependencies should depend on the super key of that particular table.

## Indexes
- A SQL index is a quick lookup table for finding records users need to search frequently. An index is small, fast, and optimized for quick lookups. It is very useful for connecting the relational tables and searching large tables. Notice that not only creating a primary key creates a unique SQL index.

### The CREATE INDEX Command
  CREATE INDEX index_name ON table_name;
### Single-Column Indexes
- A single-column index is created based on only one table column. The basic syntax is as follows.
  CREATE INDEX index_name
ON table_name (column_name);

### Unique Indexes
- Unique indexes are used not only for performance, but also for data integrity. A unique index does not allow any duplicate values to be inserted into the table. The basic syntax is as follows.
  CREATE UNIQUE INDEX index_name
on table_name (column_name);

### Composite Indexes
- A composite index is an index on two or more columns of a table. Its basic syntax is as follows.
  CREATE INDEX index_name
on table_name (column1, column2);

### The DROP INDEX Command
- An index can be dropped using SQL DROP command. Care should be taken when dropping an index because the performance may either slow down or improve.
  DROP INDEX index_name;

## Transactions
- A transaction is a unit of work that is performed against a database. Transactions are units or sequences of work accomplished in a logical order, whether in a manual fashion by a user or automatically by some sort of a database program.
- Transactions have the four standard properties, usually referred to by the acronym ACID.

## Locking mechanism
- Locks are held on SQL Server resources, such as rows read or modified during a transaction, to prevent concurrent use of resources by different transactions. For example, if an exclusive (X) lock is held on a row within a table by a transaction, no other transaction can modify that row until the lock is released.

## Database Isolation Levels
- As we know that, in order to maintain consistency in a database, it follows ACID properties. Among these four properties (Atomicity, Consistency, Isolation, and Durability) Isolation determines how transaction integrity is visible to other users and systems. It means that a transaction should take place in a system in such a way that it is the only transaction that is accessing the resources in a database system. 
Isolation levels define the degree to which a transaction must be isolated from the data modifications made by any other transaction in the database system. A transaction isolation level is defined by the following phenomena.
  - Dirty Read
      A Dirty read is a situation when a transaction reads data that has not yet been committed. For example, Let’s say transaction 1 updates a row and leaves it uncommitted, meanwhile, Transaction 2 reads the updated row. If transaction 1 rolls back the change, transaction 2 will have read data that is considered never to have existed.
      
  - Non Repeatable read
  Non Repeatable read occurs when a transaction reads the same row twice and gets a different value each time. For example, suppose transaction T1 reads data. Due to concurrency, another transaction T2 updates the same data and commit, Now if transaction T1 rereads the same data, it will retrieve a different value.
  
  - Phantom Read 
  Phantom Read occurs when two same queries are executed, but the rows retrieved by the two, are different. For example, suppose transaction T1 retrieves a set of rows that satisfy some search criteria. Now, Transaction T2 generates some new rows that match the search criteria for transaction T1. If transaction T1 re-executes the statement that reads the rows, it gets a different set of rows this time.
  
  Based on these phenomena, The SQL standard defines four isolation levels : 
  - Read Uncommitted 
    Read Uncommitted is the lowest isolation level. In this level, one transaction may read not yet committed changes made by other transactions, thereby allowing dirty reads. At this level, transactions are not isolated from each other.
  - Read Committed
  This isolation level guarantees that any data read is committed at the moment it is read. Thus it does not allow dirty read. The transaction holds a read or write lock on the current row, and thus prevents other transactions from reading, updating, or deleting it.
  - Repeatable Read
  This is the most restrictive isolation level. The transaction holds read locks on all rows it references and writes locks on referenced rows for update and delete actions. Since other transactions cannot read, update or delete these rows, consequently it avoids non-repeatable read.
  - Serializable
  This is the highest isolation level. A serializable execution is guaranteed to be serializable. Serializable execution is defined to be an execution of operations in which concurrently executing transactions appears to be serially executing.
  
## Triggers
- Triggers are the SQL codes that are automatically executed in response to certain events on a particular table. These are used to maintain the integrity of the data. A trigger in SQL works similar to a real-world trigger. For example, when the gun trigger is pulled a bullet is fired.
      Create Trigger Trigger_Name
    (Before | After)  [ Insert | Update | Delete]
    on [Table_Name]
    [ for each row | for each column ]
    [ trigger_body ]
    
 - Create Trigger
  These two keywords are used to specify that a trigger block is going to be declared. 
 - Trigger_Name
  It specifies the name of the trigger. Trigger name has to be unique and shouldn’t repeat.
 - ( Before | After )
  This specifies when the trigger will be executed. It tells us the time at which the trigger is initiated, i.e, either before the ongoing event or after.
 - Before Triggers are used to update or validate record values before they’re saved to the database. 
 - After Triggers are used to access field values that are set by the system and to effect changes in other records. The records that activate the after trigger are read-only. We cannot use After trigger if we want to update a record because it will lead to read-only error.
 -  [ Insert | Update | Delete ]
  These are the DML operations and we can use either of them in a given trigger.
 - on [ Table_Name ]
 We need to mention the table name on which the trigger is being applied. Don’t forget to use on keyword and also make sure the selected table is present in the database.
 - [ for each row | for each column ] 
  1. Row-level trigger gets executed before or after any column value of a row changes
  2. Column Level Trigger gets executed before or after the specified column changes
  
 - [ trigger_body]
     It consists of queries that need to be executed when the trigger is called.
     
     
## Conclusion
he breadth and scope of the SQL commands provide the capability to create and manipulate a wide variety of database objects using the various CREATE , ALTER , and DROP commands. Those database objects then can be loaded with data using commands such as INSERT .

## References
- https://www.w3schools.com/
- https://www.geeksforgeeks.org/
