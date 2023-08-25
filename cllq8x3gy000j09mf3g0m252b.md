---
title: "SQLite 101"
datePublished: Fri Aug 25 2023 07:02:56 GMT+0000 (Coordinated Universal Time)
cuid: cllq8x3gy000j09mf3g0m252b
slug: sqlite-101
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692946940445/4e422e8e-1ec2-470c-b48d-337790585eb9.jpeg
tags: sql, sqlite

---

SQLite is a lightweight, serverless, and self-contained relational database management system. It's often used in applications that need a local database. To perform basic queries in SQLite, you can use the SQL language.

# Installation

To install SQLite, you generally don't need to perform a separate installation step because SQLite is often included with many programming languages and platforms. Here are instructions for installing SQLite on various platforms:

1. **Linux/macOS**: Most Linux distributions and macOS come with SQLite pre-installed. You can access it from the command line using the `sqlite3` command. Open a terminal and type `sqlite3` to start the SQLite shell.
    
2. **Windows**: Windows doesn't have SQLite pre-installed, but you can easily download the command-line shell for SQLite from the official SQLite website:
    
    * Visit the SQLite download page: [**https://www.sqlite.org/download.html**](https://www.sqlite.org/download.html)
        
    * Scroll down to the "Precompiled Binaries for Windows" section.
        
    * Download the "[sqlite-tools-win32-x86-\*.zip](http://sqlite-tools-win32-x86-*.zip)" file.
        
    * Extract the contents of the downloaded ZIP file to a directory of your choice.
        
    * Open a Command Prompt and navigate to the directory where you extracted the files.
        
    * Run `sqlite3` to start the SQLite shell.
        
3. **Programming Languages and Frameworks**: If you're planning to use SQLite with a specific programming language or framework (like Go, Python, Node.js, etc.), you might not need to install SQLite separately. Many programming languages provide libraries or packages that include SQLite bindings. For example, in Go, you can use the "[github.com/mattn/go-sqlite3](http://github.com/mattn/go-sqlite3)" package to work with SQLite databases.
    

# Basic SQL Queries

Here's how you can execute some basic SQL queries using the SQLite3 command-line tool:

### Opening a Database

You can open an existing SQLite database or create a new one using the following command:

```bash
$ sqlite3 mydatabase.db
```

### Creating a Table

To create a new table, you can use the `CREATE TABLE` statement. For example, to create a simple "users" table:

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    username TEXT,
    email TEXT
);
```

### Inserting Data

You can use the `INSERT INTO` statement to add data to your table:

```sql
INSERT INTO users (username, email) VALUES ('john_doe', 'john@example.com');
```

### Querying Data

To retrieve data from a table, you can use the `SELECT` statement:

```sql
SELECT * FROM users;
```

SELECT \* FROM users WHERE username = 'john\_doe';

```sql
SELECT * FROM users WHERE username = 'john_doe';
```

### Updating Data

Use the `UPDATE` statement to modify existing records:

```sql
UPDATE users SET email = 'new_email@example.com' WHERE id = 1;
```

### Deleting Data

To delete records, use the `DELETE FROM` statement:

```sql
DELETE FROM users WHERE id = 1;
```

### Closing the Database

After you're done working with the database, you can close it by typing `.exit` or press Ctrl+D.

# Conclusion

Remember that these are just basic examples. SQL supports a wide range of operations, including joining tables, grouping data, using aggregate functions, and more. Make sure to refer to the SQLite documentation or other SQL resources for more advanced queries and concepts.

If you're working with SQLite in a programming language, you'll typically use libraries that provide an interface to SQLite (e.g., SQLite3 library in Python) to execute SQL queries programmatically.