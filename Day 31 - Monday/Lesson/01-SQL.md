# SQL CRUD and Database Design

We will be using MAMP for parts of this until we get to setting up actual databases online. You can find documentation [here](https://www.mamp.info/en/) about how to install and use it.

-Front-end should never connect directly to a database. You could see all the info about the DB and how to get into it.

## Different Types of Database Languages:

- NoSQL Databases:
  - With node, one of the biggest ones is MongoDB.
  - Allows for you to have a ton of flexibility in how you set up your Schema, OR how you change your schema depending on user/info given
  - Information can be stored as column-oriented, document-oriented, many others. (Document = more like folders/file structure)
  - Has easy horizontal scalability which means you can grow faster in some cases. Meaning - a collection can be spread across multiple tables/places/containers.
- SQL Databases:
  - Tabular data
  - Everything is interconnected (or can be).
  - Doesn't allow for easy changing of Schema, but easy to follow when the schema is well built.
  - Simple to use data queries that follow mostly semantic key words.
  - Vertical scalablilty - all in one server and that server has to grow with more tables/places/containers.

## How To SQL

- Depending on what you want to do you start your `query` with one of several keywords:
  - Select
  - Insert
  - Update
  - Create Table
  - Alter Table
  - Drop Table
- From there you can easily define what you're going to access by table, column name, or conditional options.
- Conditional Keywords:
  - NOT NULL
  - WHERE
  - IN (x,y,z,...) Example: WHERE something IN these columns.
  - HAVING
  - LIKE (%hi%) - Any number of chars, hi, followed by any num of chars.
- Join Tables using type Join keyword and the type of Join you want:

Left joins are most common.

[![](https://i.stack.imgur.com/UI25E.jpg)](https://i.stack.imgur.com/UI25E.jpg)

## MySQL vs. PostGres

Taken from the wiki for PostGres to highlight the major differences in syntax

In general, PostgreSQL makes a strong effort to conform to existing database standards, where MySQL has a mixed background on this. If you're coming from a background using MySQL or Microsoft Access, some of the changes can seem strange (such as not using double quotes to quote string values).

- MySQL uses nonstandard '#' to begin a comment line; PostgreSQL doesn't. Instead, use '--' (double dash), as this is the ANSI standard, and both databases understand it.
- MySQL uses ' or " to quote values (i.e. WHERE name = "John"). This is not the ANSI standard for databases. PostgreSQL uses only single quotes for this (i.e. WHERE name = 'John'). Double quotes are used to quote system identifiers; field names, table names, etc. (i.e. WHERE "last name" = 'Smith').
- MySQL uses ` (accent mark or backtick) to quote system identifiers, which is decidedly non-standard.
- PostgreSQL is case-sensitive for string comparisons. The field "Smith" is not the same as the field "smith". This is a big change for many users from MySQL and other small database systems, like Microsoft Access. In PostgreSQL, you can either:
  - Use the correct case in your query. (i.e. WHERE lname='Smith')
  - Use a conversion function, like lower() to search. (i.e. WHERE lower(lname)='smith')
  - Use a case-insensitive operator, like ILIKE or ~\*
- Database, table, field and columns names in PostgreSQL are case-independent, unless you created them with double-quotes around their name, in which case they are case-sensitive. In MySQL, table names can be case-sensitive or not, depending on which operating system you are using.
- PostgreSQL and MySQL seem to differ most in handling of dates, and the names of functions that handle dates.
- MySQL uses C-language operators for logic (i.e. 'foo' || 'bar' means 'foo' OR 'bar', 'foo' && 'bar' means 'foo' and 'bar'). This might be marginally helpful for C programmers, but violates database standards and rules in a significant way. PostgreSQL, following the standard, uses || for string concatenation ('foo' || 'bar' = 'foobar').
- There are other differences between the two, such as the names of functions for finding the current user. MySQL has a tool, Crash-Me, which can useful for digging this out. (Ostensibly, Crash-Me is a comparison tool for databases; however, it tends to seriously downplay MySQL's deficiencies, and isn't very objective in what it lists: the entire idea of having procedural languages (a very important feature for many users!) is relegated to a single line on the bottom fifth of the document, while the fact that MySQL allows you to use || for logical-or (definitely non-standard), is listed way before this, as a feature. Be careful about its interpretations.)

PATTERN:

SELECT what columns
FROM the table you want to get things from |
JOIN tablename on secondtablename.column = tablename.column |
WHERE some criteria (AND, OR, IN (LIST) LIKE %VALUE%) |
GROUP BY - If there are shared column values
ORDER BY - Column_name -- sorting

DELETE FROM table WHERE some criteria is met.
If you dont have a "WHERE", you'll delete the whole table.
