# SQL Injection (SQLi)

SQL Injection, also called **SQLi**, is one of the most common and dangerous web application vulnerabilities. It happens when user input is inserted directly into an SQL query without proper validation or safe handling.

In simple words, the attacker is able to interfere with the database query by sending specially crafted input. Because of this, the application may return data it should not, allow login without proper credentials, or even let the attacker modify or delete database records.

## What is SQL?

SQL stands for **Structured Query Language**. It is used to communicate with databases. With SQL, we can:

- read data
- insert data
- update data
- delete data
- search records

Example:

SELECT * FROM users WHERE username = 'john' AND password = '1234';

This query tells the database to find a user with the given username and password.

## What is SQL Injection?

SQL Injection happens when an application does not properly protect SQL queries from user input.

For example, if a website asks for a username, email, search term, or login information, and the developer directly adds that input into the SQL query, then the input can become part of the SQL command itself.

That means the attacker may change the meaning of the query.

## How SQL Injection happens

The main reason behind SQL Injection is **unsafe handling of input**.

Unsafe code may look like this:

query = "SELECT * FROM users WHERE username = '" + user_input + "';"

If the input is normal, the query works fine. But if the input contains malicious SQL code, the structure of the query can change.

This happens because the application trusts user input too much.

## Why SQL Injection is dangerous

SQL Injection is dangerous because it can give an attacker access to sensitive data and database operations.

It can be used to:

- bypass login pages
- steal usernames, emails, passwords, and other private data
- view admin-only information
- change records in the database
- delete important data
- damage the application
- sometimes move further inside the system

In serious cases, it can lead to complete database compromise.

## Common places where SQL Injection can happen

SQL Injection can happen anywhere user input is used inside a database query. Common places include:

- login forms
- search boxes
- URL parameters
- contact forms
- registration forms
- cookies
- hidden form fields
- API inputs

Basically, any input that reaches the database without proper protection can be risky.

## Types of SQL Injection

### 1. Error-based SQL Injection
In this type, the attacker tries to make the database return error messages. These errors may reveal useful information about the database structure or query behavior.

### 2. Union-based SQL Injection
Here the attacker uses the `UNION` operator to combine results from another query. This may allow them to extract data from different tables if the application displays query results.

### 3. Blind SQL Injection
This type is called “blind” because the attacker does not directly see database output. They figure things out by observing how the website behaves.

There are two common forms:

- **Boolean-based blind SQLi**: the attacker sends true/false conditions and compares responses
- **Time-based blind SQLi**: the attacker checks whether the response is delayed when a condition is true

### 4. Second-order SQL Injection
In this case, the malicious input is stored first and becomes dangerous later when the application uses it in another query. This makes it harder to detect.

## Example idea of SQL Injection

Suppose a login query is written like this:

SELECT * FROM users WHERE username = 'input' AND password = 'input';

If the application does not protect input correctly, an attacker may try to change the condition so the database returns a valid record even without the correct password.

That is why login forms are a common target.

## Signs that an application may be vulnerable

Some common signs of SQL Injection are:

- database error messages appear on the screen
- the page behaves differently after special input
- login works in a suspicious way
- search results are unusual
- the page becomes slow for certain inputs
- the application crashes after invalid input
- data appears that should not be visible

These signs do not always confirm SQL Injection, but they are strong warning signs.

## Real-world impact

A successful SQL Injection attack can cause serious damage.

The attacker may be able to:

- read confidential data
- change data
- delete tables or records
- access admin features
- steal password hashes
- disrupt the website
- damage trust in the system

This is why SQL Injection is considered a high-risk vulnerability.

## Prevention of SQL Injection

The best way to stop SQL Injection is to write safe database code.

### 1. Use parameterized queries
This is the strongest and most recommended defense.

Parameterized queries separate the SQL command from the user input. This means the input is treated as data, not as code.

Safe example:

cursor.execute("SELECT * FROM users WHERE email = ?", (email,))

This is much safer than joining strings directly.

### 2. Use prepared statements
Prepared statements work similarly to parameterized queries. They help the database handle user input safely.

### 3. Validate input
Always check whether the input makes sense.

For example:

- username should contain valid characters
- age should be a number
- email should follow email format

Validation alone is not enough, but it helps.

### 4. Limit database permissions
The database account used by the application should have only the permissions it actually needs.

For example:

- do not use admin-level database access for a normal web app
- do not give delete permission if the app only needs to read data

### 5. Avoid showing database errors
Do not display raw SQL errors to users.

Detailed error messages can help attackers understand the backend structure.

### 6. Use secure coding practices
Developers should always assume input is unsafe until it is properly handled.

### 7. Use a Web Application Firewall
A WAF can help block some suspicious requests, but it should not be the only protection.

### 8. Keep software updated
Old frameworks, plugins, and libraries may contain security weaknesses. Updates are important.

## Safe vs unsafe query handling

Unsafe:

query = "SELECT * FROM users WHERE username = '" + username + "';"

Safe:

query = "SELECT * FROM users WHERE username = ?"
cursor.execute(query, (username,))

The safe version prevents the input from changing the actual SQL structure.

## SQL Injection in login pages

Login pages are often targeted because they check credentials against the database.

If the login query is written unsafely, an attacker may try to manipulate it and gain access without knowing the real password.

This is why authentication code must always be protected carefully.

## SQL Injection vs other attacks

SQL Injection is different from other web attacks:

- **SQL Injection** targets the database
- **XSS** targets the browser and user side
- **CSRF** tricks a logged-in user into performing actions

Even though they are different, they all show how dangerous unsafe input handling can be.

## How security testers look for SQL Injection

In authorized testing, security testers may check:

- whether special characters cause errors
- whether input changes page output
- whether the response changes for true/false conditions
- whether time delays appear
- whether the application leaks database details

Testing should only be done on systems you are allowed to test.

## Important points to remember

- SQL Injection happens because of unsafe input handling.
- It can lead to data theft, login bypass, and database damage.
- Parameterized queries are the best defense.
- Input validation, least privilege, and hidden error messages also help.
- It is one of the most important topics in web security.

## Final summary

SQL Injection is a vulnerability where an attacker can interfere with SQL queries by sending malicious input. It is dangerous because it can expose data, break authentication, and harm the entire application.

The best protection is to use **parameterized queries**, avoid direct string concatenation, validate input properly, and keep database permissions limited.

If you understand SQL Injection well, you also understand one of the most important lessons in cybersecurity: **never trust user input**.