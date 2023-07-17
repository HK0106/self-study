## Database

### Table of Contents

| No. | Questions                                                                        |
|-----|----------------------------------------------------------------------------------|
| 1   | [What is database normalization?](#what-is-database-normalization)               |
| 2   | [What are database normalization forms?](#what-are-database-normalization-forms) |
| 3   | [What is Denormalization.](#what-is-denormalization)                             |

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

DeNormalization is a technique used to access the data from higher to lower normal forms of database. It is also process of introducing redundancy into a table by incorporating data from the related tables.

   **[⬆ Back to Top](#table-of-contents)**

---
