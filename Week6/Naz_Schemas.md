> **SQL**(Structured Query Language)is a standard language for storing, manipulating and retrieving data in databases.

>**PostgreSQL** is a general purpose and object-relational database management system, the most advanced open source database system.



##  Schemas & Relationships - SQL
++What is a schema and why/when would you need one?++

++A database++ is the main container, it contains the data and log files, and all the schemas within it. You always back up a database, it is a discrete unit on its own.

* ++Schemas++ are like folders within a database, and are mainly used to group logical objects together, which leads to ease of setting permissions by schema.

  * A schema is a collection of database objects associated with one particular database username. This username is called the schema owner, or the owner of the related group of objects.

  * A schema can consist of a single table and has no limits to the number of objects that it may contain, unless restricted by a specific database implementation.

Say you have been issued a database username and password by the database administrator.
Your username is USER1.
Suppose you log on to the database and then create a table called EMPLOYEE_TBL.
According to the database, your table's actual name is USER1.EMPLOYEE_TBL.
The schema name for that table is USER1, which is also the owner of that table. You have just created the first table of a schema.

*The good thing about schemas is that when you access a table that you own (in your own schema), you do not have to refer to the schema name. For instance, you could refer to your table as either one of the following:*
```
EMPLOYEE_TBL
USER1.EMPLOYEE_TBL
```
*The first option is preferred because it requires fewer keystrokes. If another user were to query one of your tables, the user would have to specify the schema, as follows:*
```
USER1.EMPLOYEE_TBL
```
#  Two schemas in a relational database

There are two user accounts in the database that own tables: USER1 and USER2. Each user account has its own schema. Some examples for how the two users can access their own tables and tables owned by the other user follow:

|USER1 accesses own TABLE1:|TABLE1|
| -------- | -------- |
|**USER1 accesses own TEST:**|**Test**|
|**USER1 accesses USER2's TABLE10:**|**USER2.TABLE10**|
|**USER1 accesses USER2's TEST:**|**USER2.TEST**|


*In this example, both users have a table called TEST. Tables can have the same names in a database as long as they belong to different schemas.*

*If you look at it this way, table names are always unique in a database because the schema owner is actually part of the table name. For instance, USER1.TEST is a different table than USER2.TEST.*

#### *If you do not specify a schema with the table name when accessing tables in a database, the database server looks for a table that you own by default.*
--------------------------
### Ownership and User-Schema Separation in SQL Server
**User-Schema Separation:**
User-schema separation allows for more flexibility in managing database object permissions.
++A schema is a named container for database objects++, which allows you to group objects into separate namespaces. For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.
```
The four-part naming syntax for referring to objects specifies the schema name:

                  Server.Database.DatabaseSchema.DatabaseObject  
```

**Schema Owners and Permissions:**
Schemas can be owned by any database principal, and a single principal can own multiple schemas.
You can apply security rules to a schema, which are inherited by all objects in the schema.
Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.
Users can be assigned a default schema, and multiple database users can share the same schema.

++By default++ ,when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.
Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.
A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.
Objects can be moved between schemas, and schema ownership can be transferred between principals. Database users can be dropped without affecting schemas.

**Built-In Schemas:**
SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles. These exist mainly for backward compatibility. You can drop the schemas that have the same names as the fixed database roles if you do not need them. You cannot drop the following schemas:

```
* dbo
```
```
* guest
```
```
* sys
```
```
* INFORMATION_SCHEMA
```
*If you drop them from the model database, they will not appear in new databases.*

***Note:***
>*The **sys** and **INFORMATION_SCHEMA** schemas are reserved for system objects. You cannot create objects in these schemas and you cannot drop them.*

## The dbo Schema:
The dbo schema is the default schema for a newly created database. The dbo schema is owned by the dbo user account. By default, users created with the CREATE USER Transact-SQL command have dbo as their default schema.

Users who are assigned the dbo schema do not inherit the permissions of the dbo user account. No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.

***Note:***
>*When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema. If the object is not found there, SQL Server looks next in the dbo schema. If the object is not in the dbo schema, an error is returned.*
_______________________________________

# SQL PRIMARY KEY Constraint:
1. The PRIMARY KEY constraint uniquely identifies each record in a database table.

2. Primary keys must contain UNIQUE values, and cannot contain NULL values.

3. A table can have only one primary key, which may consist of single or multiple fields.

>A Primary Key is always a Candidate Key, by definition. Other Candidate Keys may be realized as Unique Constraints/Indexes. (Candidate Keys establish cardinality/normalization and identifying them is useful, even if they are not "used").

## Candidate Key:
++A Candidate Key++ can be any column or a combination of columns that can qualify as unique key in database. There can be multiple Candidate Keys in one table. Each Candidate Key can qualify as Primary Key.


++A Primary Key++ is a column or a combination of columns that uniquely identify a record.
Only one Candidate Key can be Primary Key.

***One needs to be very careful in selecting the Primary Key as an incorrect selection can adversely impact the database architect and future normalization. For a Candidate Key to qualify as a Primary Key, it should be Non-NULL and unique in any domain.***

>*2 Links are provided below for understanding what Primary keys are.*
---------------------------------------
# SQL FOREIGN KEY Constraint
1. A FOREIGN KEY is a key used to link two tables together.

2. A FOREIGN KEY is a field (or collection of fields) in one table that refers to the PRIMARY KEY in another table.

3. The table containing the foreign key is called the child table, and the table containing the candidate key is called the referenced or parent table.

---------------------------------------
![](https://i.imgur.com/ytnPiXD.png)

![](https://i.imgur.com/UDg7c0q.png)


---------------------------------------
## What is the difference between SQL, NoSQL, MySQL, and PostgreSQL?
### ++SQL++

Short for Structured Query Language, it is the standard language you use to interact with a relational database. It has commands like SELECT, UPDATE, INSERT, and DELETE to tell the database exactly what you want to do with the data.

### ++MySQL, PostgreSQL++

Both of these are types of relational database management systems. These are applications that govern the database, providing and regulating access to the data. Both MySQL and PostgreSQL are free, open source systems. There are other popular types of relational DBMSs, including Oracle and SQL Server.

### ++NoSQL++

NoSQL is a very broad term, but it generally refers to non-relational database management systems. These systems usually have query languages of their own, but they may also support SQL queries. NoSQL databases have different strengths and weaknesses from relational databases, and may be faster or slower depending on what exactly you need to do. The most popular NoSQL database is MongoDB.
_______________________________________
# Links:
* What is postgreSQL & what do you use it for?
  The link provided below explains it all :
https://www.postgresql.org/about/
http://www.postgresqltutorial.com/what-is-postgresql/

* Install SQL(postgreSQL) Server and create a database on Ubuntu/macOS:

  * Ubuntu 18.04
  https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04

  * (MacOS & Ubuntu users): https://github.com/macintoshhelper/learn-sql/blob/master/postgresql/setup.md#linux-instructions

* INTRO TO SQL: QUERYING AND MANAGING DATA:(Recommended)
https://www.khanacademy.org/computing/computer-programming/sql/sql-basics/v/welcome-to-sql

* What Primary Keys are :(Recommended)
https://www.youtube.com/watch?v=E3Bs3H14C8Y
https://www.w3schools.com/sql/sql_primarykey.asp

* Mock Schema:(SQL)
https://www.sswug.org/bentaylor/editorials/implement-sql-mocks-using-a-schema/

>PL/pgSQL - SQL Procedural Language
