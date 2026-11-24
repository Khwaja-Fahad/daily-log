# Day 34 - 2026-11-24

## Database SQL Basics (TryHackMe)
Room completed: 100% (all 4 tasks)

## The idea
When a business grows, keeping data in paper notebooks or simple files becomes slow and confusing. A **database** stores information in an organised way, so a computer can search, count and sort it in seconds. **SQL** is the language used to ask a database questions.

## What I learned

### Data and databases
- **Data** is recorded information (orders, names, prices, times). When a computer is switched off, data in memory is lost, so it has to be stored somewhere permanent.
- A **database** is like a digital notebook that never runs out of pages. It stores data in an organised structure and finds answers quickly, even with thousands of records.
- Example: a café that sells drinks can ask "how many coffees were sold today?" without counting pages by hand.

### Tables, rows and columns
| Term | Meaning |
|------|---------|
| **Table** | A "spreadsheet" inside the database that holds one kind of information |
| **Column** | The title at the top. It describes one type of information (for example name or price) |
| **Row** | One complete record, with a value for each column |
- Adding a record adds one row. Removing a record removes only that row, and the rest of the table stays the same.
- A database can have several tables, and they can be related to each other (a **relational database**).

### SQL and queries
- **SQL** (Structured Query Language) is a language used to query relational databases. It is not a full programming language, and it is used to ask questions.
- A **query** is a question to the database. A query that only reads data does not change it.

### The four core parts
| Keyword | Job |
|---------|-----|
| `SELECT` | Choose which columns to show (`*` means all columns) |
| `FROM` | Choose which table to use |
| `WHERE` | Keep only the rows that match a condition |
| `ORDER BY` | Sort the results (ascending by default, add `DESC` for highest first) |

Examples of my own, using a made-up table called `logins` (columns: `id`, `username`, `status`, `source_ip`, `time`):
```sql
SELECT * FROM logins;
SELECT username, source_ip FROM logins;
SELECT * FROM logins WHERE status = 'failed';
SELECT * FROM logins WHERE status = 'failed' ORDER BY time DESC;
```
- Text values go in single quotes, and a query ends with a semicolon.
- **Step by step:** start simple (`SELECT * FROM table;`), look at the data, then add `WHERE` and `ORDER BY` one at a time.
- If I don't know what values exist, I first look at the table to check.

## Connection to what I already know
- This is the same "ask the data questions" skill as reading logs, only faster. A SQL query on a login table does what `grep` and counting do on a log file.
- **Client-server model:** a web application sends queries to a database server, and the database server answers.
- **Python and pandas:** filtering and sorting data frames is the same idea as `WHERE` and `ORDER BY`.
- **CIA Triad:** the room ended with a question: what happens if someone can change or remove records without permission? That is a **confidentiality** and **integrity** problem (and **availability** if data is deleted), so databases need access control.
- **Permissions and least privilege:** database users should only get the access they need (read-only for reporting, for example).

## Why this matters for security
- **Logs and security data often live in databases.** SIEM tools and many investigation platforms are searched with query languages similar to SQL, so basic queries help me filter alerts and events.
- **SQL injection:** if a web application puts user input straight into a query, an attacker can change the meaning of the query to read or alter data they should not see. This is a well-known web attack, and it is one reason input must be validated and queries must be built safely (for example with prepared statements).
- **Stolen databases** expose personal data and password hashes, which is why they are encrypted, backed up and protected.
- **Access control:** limit who can read, change or delete records, and log who does.
- **Backups** protect availability and integrity if data is damaged or deleted.
- I only practise on lab databases or my own, and never run queries against systems I'm not authorised to use.

## Full forms
- **SQL:** Structured Query Language (often said "sequel")
- **DB:** Database
- **DBMS:** Database Management System
- **SIEM:** Security Information and Event Management
- **CIA:** Confidentiality, Integrity, Availability
- **IP:** Internet Protocol

## Practice (from memory)
1. Write a query to show all rows of a table.
2. Write a query to show only two columns.
3. Write a query that filters on one value, then sort the result highest first.
4. Explain in one sentence the difference between a row and a column.
5. Explain in one sentence why a web application must not trust user input in a database query.

## Time and completion
- Time spent: 30 minutes
- Room completed: 100%
