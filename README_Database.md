## Database

### Table of Contents

| No. | Questions                                                                                                                                                       |
|-----|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1   | [What is database normalization?](#what-is-database-normalization)                                                                                              |
| 2   | [What are database normalization forms?](#what-are-database-normalization-forms)                                                                                |
| 3   | [What is Denormalization.](#what-is-denormalization)                                                                                                            |
| 4   | [When execute an insert query in SQL the data is not immediately saved to disk](#when-execute-an-insert-query-in-SQL-the-data-is-not-immediately-saved-to-disk) |
| 5   | [What is index?](#)                                                                                                                                             |
| 6   | [How index work?](#)                                                                                                                                            |
| 6   | [Why we need index?](#)                                                                                                                                         |
| 6   | [When we use index?](#)                                                                                                                                         |

1. ### What is database normalization

Database normalization is the process of organizing the fields and tables of a relational database to minimize redundancy and dependency. Normalization usually involves dividing large tables into smaller (and less redundant) tables and defining relationships among them. Normalization is a bottom-up technique for database design.

The evolution of Normalization theories is illustrated below:

• First Normal Form (1NF)

• Second Normal Form (2NF)

• Third Normal Form (3NF)

• Boyce-Codd Normal Form (BCNF)

• 4th Normal Form

• 5th Normal Form

• 6th Normal Form
**[⬆ Back to Top](#table-of-contents)**


---

2. ### What are database normalization forms

Normalization is the process of organizing data into a related table. it also eliminates redundancy and increases the
integrity which improves performance of the query. To normalize a database, we divide the database into tables and
establish relationships between the tables.

• First Normal Form (1st NF)

• Second Normal Form (2nd NF)

• Third Normal Form (3rd NF)

• Boyce-Codd Normal Form (BCNF)

• Fourth Normal Form (4th NF)

• Fifth Normal Form (5th NF)

First Normal Form (1NF):

This should remove all the duplicate columns from the table. Creation of tables for the related data and identification
of unique columns.

Second Normal Form (2NF):

Meeting all requirements of the first normal form. Placing the subsets of data in separate tables and Creation of
relationships between the tables using primary keys. Third Normal Form (3NF):

This should meet all requirements of 2NF. Removing the columns which are not dependent on primary key constraints.

Fourth Normal Form (3NF):

Meeting all the requirements of third normal form and it should not have multi- valued dependencies.

**[⬆ Back to Top](#table-of-contents)**

---

3. ### What is Denormalization

    DeNormalization is a technique used to access the data from higher to lower normal forms of database.
It is also process of introducing redundancy into a table by incorporating data from the related tables.

   **[⬆ Back to Top](#table-of-contents)**
   
---

4. ### When execute an insert query in SQL the data is not immediately saved to disk

    When you execute an INSERT query in MySQL to insert data into a table, the data is not immediately saved directly to the hard disk of the database. Instead, MySQL follows a process known as the ACID (Atomicity, Consistency, Isolation, Durability) properties to ensure data integrity and durability.
    
````
    When you execute the INSERT query, MySQL performs the following steps:

        1.Validates the query syntax and table structure.
        2.Checks for any constraints or triggers defined on the table.
        3.Writes the data to the database buffer cache in memory.
        4.The data in the buffer cache is periodically flushed to the disk based on various factors such as system load,
         configuration settings, or commit statements.
        5.MySQL uses a technique called write-ahead logging (WAL) to record changes to a transaction log file before writing them to disk.
         This log file ensures durability by allowing the database to recover data in case of system failures.
        6.Once the data is written to disk and the transaction is committed, it is considered durable and persistent.
````

   The actual timing and frequency of disk writes depend on various factors such as system configuration, workload, and storage engine settings. MySQL employs sophisticated mechanisms to optimize disk writes and ensure efficient data storage and retrieval.
    
   It's worth noting that some advanced configurations, such as using the MEMORY storage engine or using a RAID controller with a battery-backed cache, can impact the behavior of data writes and caching. However, in a typical MySQL setup, the data is first stored in memory and then periodically flushed to disk to ensure durability.

**[⬆ Back to Top](#table-of-contents)**

---