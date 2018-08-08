# OMG, FML, WTF is a DDL/DML/CTE :weary:
![](https://media.giphy.com/media/njl60xjwgrkWY/giphy.gif)
Don't worry we'll explain it all! :kissing_heart:

## DDL/DML, Database Transactions and CTE


### What is the difference between DDL and DML?

**DDL is Data Definition Language** : it is used to *create* and *define* the DB structure.
* For example, with SQL, it would be instructions such as `create table`, `alter table`, ...
* DDL statements affect the table as a whole
* DDL statements cannot use the WHERE clause - makes sense, as they affect the table as a whole
* Cannot be rolled back/part of a commit/part of a transation
* Do not result in any triggers being fired (or do they... 🙀)
    * PostgreSQL provides "event triggers" which, unlike regular triggers, are global and can therefore capture DDL events

![](https://media.giphy.com/media/3o751XCnKoIwchqtEs/giphy.gif)

**DML is Data Manipulation Language** : it is used to manipulate data itself.
* For example, with SQL, it would be instructions such as `insert`, `update`, `delete`, ...
* DML statements affect one or more rows
* Most DML support filtering with the WHERE clause
* Transactions (commits/rollbacks) are supported, i.e. you can insert data into two tables, and commit both these changes as part of one transaction
* Can result in relevant triggers being fired
    * (Need to spend more time understanding trigger functions! [Some more info here](http://www.sqlteam.com/article/an-introduction-to-triggers-part-i))
    * "A trigger is a special type of stored procedure that automatically executes when an event (e.g. `INSERT`, `UPDATE`, `DELETE`) occcurs in the DB server"
* DMLs can be procedural or declarative
    * Nice extra info [here](https://www.quora.com/What-is-the-difference-between-non-procedural-DML-and-procedural-DML)
    * Procedural: user specifies what data is needed and how to get it
    * Non-procedural: user only specifies what data is needed... 🕵️ 🤷

(Thanks to [this great Quora answer](https://www.quora.com/What-are-the-differences-between-DDL-and-DML))

Starting to make a bit of sense? 
![Ron doing something](https://media.giphy.com/media/X7byz3vE1NRGU/giphy.gif)


### What are some key DDL and DML commands?
#### DDL Statements:
* `CREATE` creates objects like Databases and Tables
* `ALTER` changes the database structure
* `RENAME` renames an object
* `TRUNCATE` removes all records from a table
* `DROP` delete all objects from a table

#### DML Statements:
* `SELECT` used to read data
* `INSERT` used to save data
* `DELETE` used to delete data
* `MERGE` insert or update data
* `CALL` used to call an already created Function
* `EXPLAIN` provides information about an object

#### DCL  ( DATA CONTROL LANGUAGE )
Statements that are used to manage and control the access of users on database objects
* `GRANT`  allow user acces to read/write on certain database objects
* `REVOKE`  removes user access from read/write permission on database objects.


![](https://media.giphy.com/media/rKzxE0Q5EQKFq/giphy.gif)


#### TCL ( TRANSACTION CONTROL LANGUAGE )
SQL Statements that allows you to control and manage transactions to maintain the integrity of data within SQL statements.

#### Useful resources / read more: 
- [SQL Queries Practice with Commands](https://https://bitalksbi.com/sql-queries-practice/)

### :money_with_wings: What are transactions? :moneybag:
* A transaction is a single unit of work on a database :toilet: :wrench::nut_and_bolt:
* :heart: **If successful**: All modifications will become a permanent part of the database
* :broken_heart: **If unsuccessful**: All modifications are erased

### What have transactions ever done for me? 
* Transactions (modifications to a database) can be controlled 
    * `BEGIN` starts the modifications
    * `COMMIT` saves changes
    * `ROLLBACK` can revert to your last saved database
    * `SAVEPOINT` set points to which your database will be restored on ROLLBACK
    * `RELEASE SAVEPOINT` removes a save point
    * `SET TRANSACTION` name your transaction


![](https://media.giphy.com/media/BNFJsNITqUj4Y/giphy.gif)


### Q: What are CTEs?

#### A: Cute Turtles Exploring

![](https://media.giphy.com/media/ObwD52ubZXcA0/giphy.gif)


#### SQL A: Common Table Expressions

**AKA** - `WITH` Queries

CTEs / `WITH` provides a way to write helper statements for use in a larger query. These statements, which are often referred to as Common Table Expressions or CTEs, can be thought of as _defining temporary tables that exist just for one query_. 

CTEs are defined **within** the statement (before the semicolon!) using the **WITH** operator.

e.g.
```
WITH Employee_CTE (EmployeeNumber, Title)
AS
(SELECT NationalIDNumber,
        JobTitle
 FROM   HumanResources.Employee)
```
using CTE...
```
SELECT EmployeeNumber,
       Title
FROM   Employee_CTE
```

You can imagine these as similar to 'views'.

_[Optional Demo here]_

[Postgres Docs on WITH](https://www.postgresql.org/docs/9.1/static/queries-with.html)

#### Why might you want to use CTEs?

* Readability!
* Say goodbye to nested `SELECT` :tada: :tada: :tada:
* You can substitute a CTE for a view. This is handy if you don’t have permissions to create a view object or you don’t want to create one as it is only used in this one query. Don't worry about views.
* CTEs can be used to create recursive queries, which is good for hierarchical data.

### Recursion...
![](https://media.giphy.com/media/aFTt8wvDtqKCQ/giphy.gif)


Yay for CTEs!!

![Happy Ron](https://media3.giphy.com/media/VwUquCGtIatGg/giphy.gif)

( Dom === Ron )


# OMG, FML, WTF this is DDL/DML/TCL!  :heart_eyes:
![](https://i0.wp.com/bitalksbi.com/wp-content/uploads/2018/02/WhatIsDDLDML.png?w=551&ssl=1)

[The most important SQL commands according to w3schools](https://www.w3schools.com/sql/sql_syntax.asp)


## Sources

[Article on CTEs](https://www.essentialsql.com/introduction-common-table-expressions-ctes/)

[Blog on DBMS](https://bitalksbi.com/ddldml/)
