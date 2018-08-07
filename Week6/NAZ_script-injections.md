# Script injections / safety issues

### What is a script injection and how do these happen?

There are several types of script injection:

- [SQL injection](https://www.owasp.org/index.php/SQL_Injection)
- [Cross site scripting (XSS)](https://www.owasp.org/index.php/Cross-site_Scripting_)
- [File upload](https://www.owasp.org/index.php/Unrestricted_File_Upload)
- [Cross site request forgery](<https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)>)
  ![](https://i.imgur.com/V2Bi7f5.png =600x)

**We will be focusing on SQL injections**

**What is a SQL injection?**
A SQL injection attack consists of insertion of a SQL query via the input data from the client to the application. A successful SQL injection can read or modify sensitive data from the database, modify database data.

## How would you prevent script injections?

#### Defense Option 1: Prepared Statements

Parameterized queries force the developer to first define all the SQL code, and then pass in each parameter to the query later. This coding style allows the database to distinguish between code and data, regardless of what user input is supplied.
Example for PostGreSQL using PG module

```javascript
const pool = require('./db_connection');
// The username and pass will be evaulated in the array before running the SQL statement. It will return an error
const login = (username,password,cb) => {
    pool.query("SELECT * FROM users WHERE
    username = $1 AND password = $2;",
    [username,password], (err,res) =>
    cb(err,res));
}
// The username and pass will be directly put in to the query without checking for SQL injections
const login = (username,password,cb) => {
    pool.query('SELECT * FROM users WHERE
    username = ${username} AND
    password = ${password};'', (err,res) =>
    cb(err,res));
}
```

#### Defense Option 2: White List & Black List Input Validation

Blacklist validation tests the external input against a set of known malicious inputs. An application compiles a list of all malicious inputs, and then verifies the external input against the compiled list. Therefore, it’s easy for an attacker to bypass blacklist validation since they can come up with multiple variants of malicious input that may not be part of the complied blacklist.

Whitelisting is a much better approach to mitigate the risk of SQL injection. Whitelist validation tests an external input against a set of known, approved input. With whitelist input validation, the application knows exactly what’s desired and rejects other input values that fail a test against the known, approved input.

Validation for node.js can be helped using libraries such as [validator.js](https://www.npmjs.com/package/validator).

#### Principle of least privilage

This is a standard security control that helps minimize the potential damage of a successful SQL injection attack. Application accounts shouldn’t assign DBA or admin type access onto the database server. Additionally, depending on access requirements, they should be restricted to least privileged access. For example, accounts that only require read access are only granted read access to the table they need to access. This ensures that if an application is compromised, an attacker won’t have the rights to the database through the compromised application.

#### Customise your errors

- Errors passed on to the client will provide information about the system. System information revealed in errors are highly valuable to users with malicious intent.
- Ensure any errors passed on to the client contain no specific information

#### Try to attack yourself

Try to attack yourself. Running your own attacks may be difficult. Thankfully you can use white-hat automated SQL injection attack tools like:

- JSQL (git hub) https://github.com/ron190/jsql-injection
- SQLmaps:- http://sqlmap.org/.
- tyrant SQL(gui version) https://sourceforge.net/projects/tyrantsql/?source=directory
- havji:-search on your own acord (dark web detected)

More information
https://www.sitepoint.com/how-to-protect-your-website-against-sql-injection-attacks/

#### Demonstration

https://www.hackthis.co.uk/levels/sqli/1

https://sqlzoo.net/hack/

#### Useful links:

https://www.owasp.org/index.php/SQL_Injection_Prevention_Cheat_Sheet

https://www.w3schools.com/sql/sql_injection.asp

https://www.linkedin.com/pulse/protecting-your-postgresql-database-from-sql-attack-rogers-iii
