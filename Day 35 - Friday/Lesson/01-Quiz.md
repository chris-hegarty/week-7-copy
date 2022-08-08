# Quiz for Week 7

## Databases

1. What are the benefits of utilizing MySQL over PostGres or vice versa?

PROS
-Has tabular data where the schema is set.
-Has "vertical scalability" where the data is all in one server and grows "Vertically" with more tables/places/containers.
-Simple to use data queries with semantic keywords.
CONS
-NoSQL allows you a collection of data to be spread across multiple locations. (But PostGres is not NoSQL.)
-PostGres is an alternate implementation of more complex data.

2. Explain in as much detail as you can what connection Pooling is.

## Pooling allows for multiple connections to the database. Otherwise, for every query, you have to connect, make the query, then disconnect. You can take advantage of one of the already open questions.

3. What steps (if any) need to be take to store passwords in a database?

-They need to be "Hashed"

4. What is a document in a NoSQL database?

-A document is where data, instead of being stored in tables/rows/columns, is stored in a folder/file like format.

5. If you remove an object attribute from mongodb, is it deleted from the database?

-Yes. It is removed from the document, but not from ALL documents. But if you remove a column, its gone for everyone.

6. What is your favorite type of database?

-mySQL

7. In a NoSQL Database, what happens if you try to add a key to a schema after you have created some documents?

-You can add it with the Schema add method in Mongo. It gets added for any new entries. But the current documents are unchanged. In SQL, it adds the column for EVERYONE. In Mongo, it doesnt automatically add it for all entries.

8. What is CRUD and when/how would you use each part?

- `C`- Create
- `R`- Read
- `U`- Update
- `D`- Delete
  Use each to do its respective function for data in your database.

9. Explain the pros and cons for SQL and NoSQL Databases.

-SQL is less flexible but more straightforward.
-NoSQL is more flexible.
-NoSQL can require more work to query data as the DB gets more complex.
-NoSQL is optimized for faster queries. SQL can require joins from multiple tables, which can get expensive.
-According to Mongo docs, NoSQL can be mapped to application code.
-SQL is better for highly-structured data where storage is optimized and ensure data integrity.
-SQL = Better at ACID (Atomicity, Consistency, Integrity and Durability) crucial for financial transactions.

10. Which is better in your opinion: MySQL, PostGres?

- Hmm. MySQL is relational. PostGres is object relational.
  -PostGres has more data types for more complex applications. Better for enterprise level.
  MySQL is going to be better for me and my projects in the forseeable future.

11. How would you find all users based off a username in an SQL database? (Assume you have a users table with `id`, `username`, and `email` columns)

```SQL
SELECT * FROM users WHERE users.username="[enter username here]"
```

12. What are joins in SQL?

-Matching or weeding out data from two different tables. Backbone of the relational structure of SQL.

13. In MySQL what type would you use to store only a `true` or `false` value? What about in PostGres?

- `MySQL` - 0 for false, 1 for true. (tinyint) (No such thing as a boolean. You can select a boolean, but it will turn it into a 0 or 1.)
- `PostGres` - true, false or unknown. (boolean)

14. What are constraints?

-Used to specify rules for data in a table. They can be
-NOT NULL
-UNIQUE - All values in a column will be different.
-PRIMARY KEY - Uniquely identifies each row in a table.
-FOREIGN KEY - Links data in different tables.
-CHECK - Check that values in a column satify a specific condition
-DEFAULT - Set a default value.
-CREATE INDEX

15. What are foreign keys and primary keys and when/why would you use them?

- `Foreign Keys` - A FOREIGN key is a field that refers to the primary key in another table.
- `Primary Keys` - A unique identifer of a row in a table. They can't be null. They are often auto-incremented.
  You set a foreign key for data (like a user_id for example) that may be used in different tables.

16. If you need to store user information, all the blog posts from a user, and all their friends, how would you structure that in SQL?

-user table - with id, username, password
-blog posts table (WITH A FOREIGN KEY TYING IT TO A USER) - with id, blog_id, user_id, title, excerpt, content, date, date modified, url, status, revisions, comments, comment count
-friends - id, friend_id, name, picture, link?

17. List the different types of joins.

- INNER: Match records in both tables.
- LEFT: All records from one table, matching records from the other. (Most common.)
- FULL: All records that match, whether the other table matches or not

18. How would you get all users from a database (use column names of your choice) sorted in descending order from oldest to youngest?

```SQL
SELECT * FROM database ORDER BY age DESC
```

19. What is the difference between `HAVING someColumn < 10` and `WHERE someColumn <10`?

- `HAVING` - If your column is "item_quantity" it will return any number greater than 10.
- `WHERE` - select from products where price < 10 returns prices less than 10.
  WHERE keyword cannot be used with aggregate functions. Can be used with SELECT, UPDATE, DELETE
  HAVING can only be used with SELECT and GROUP BY clause.
  (WHERE IS USED BEFORE A GROUP BY)
  WHERE = GRAB THE ROWS
  HAVING - Like GROUP BY sales order by order numbers. Group things together then do having.

20. How would you add up all numbers in a column for all the rows that match the same criteria?

It has to be used with some kind of GROUP BY. Otherwise all the rows are in the computation.

21. Assuming you have a column name of `userID` but you wanted it to appear as `uID` in your output, how would you do that?
    userID AS uDI
    SELECT userID AS from users.

- ``

## API Creation and Express

1. How do you serve static files with express and what does that mean?
   Install express, import it, create an "app" server with it, and add it to your build folder.
   It allows express to build "Static" files like html files.
   (You dont have to have a build folder.)
   Serving static files means sending non-JSON files to the front end. (HTML, Javascript, images, etc...) app.use(express.static(\_\_dirname + Location of file.))

```javascript
//import express
const express = require("express);
//Take express and create an app server
const app = express()
//Add these lines into the server file.
app.use(express.static(__dirname + "/build"));
app.get("*", (req, res) => {
    return res.sendFile("/build/index.html", { root: __dirname + "/" });
});

```

2. What steps do you need to take to ensure that data can be posted to the backend?
   Set up express server and any routes for posted data.
   app.use(express.json()) is needed toward the top of the server file.
   That line will be needed to handle PUT, POST and PATCH requests.

My answer:
-Set up a database config file.
-import mysql
-set up your pool of connections.
-allow your queries to be async with
const query = util.promisify(pool.query).bind(pool);
module.exports = query;
-set up route with a verify data function and your GET, POST, PUT queries you are receiving
-build models with your SQL queries to the database.

3. How do you setup SQL queries in an express api?
   Make individual functions to handle specific querieus in a model file.
   Also need to set up a connection to a DB via a config file.
   Step back and look at all the steps. Need to set up routes, can't query models without connecting to a database.

-Make an async function with a try/catch pattern in a model file.

4. How would you prepare a React application to be served via an express backend?
   You first need to make a production build of the React app, which can be done with "npm run build"

-Set up a server.js file in your main app folder and import express.
-Set up an env file with your database credentials, and add the file to the .gitignore list

5. If you wanted to develop a backend and frontend concurrently what are some ways you could do that?

   1. You would need two terminal windows...one to run your app, and one for your server.
   2. You would also beed to add a "proxy" line to package.json.
      "proxy": "http://localhost:8080"

6. In express how and why would you implement a middleware?
   Whenever you want something to happen between the request and the route handler sending a response.
   -set up a middleware folder for any needed middleware files.
   -set it up in server file with app.use (can be in the route handler itself.) OR between the route and the route handler.
   -call it in the routes file.
   You'd set this up for things like checking authentication (maybe an API key) while logging in users.

7. What is the `next()` function and why should or shouldn't you use it?

   It is used in middleware functions/functionality to tell the server that the function is done, and it can move on the "next" one.
   If you don't use it, the server won't exit your piece of middleware and the app will never send a response.

-

8. What are the main http verbs and when would you use each?

-GET - Get information from a database, or something stored on a server. Like an html file or an image file.
-PUT - Create entries if they dont already exist. or update (overwrite) data in database. Uses "UPDATE" query.
-DELETE - Remove data.
-POST - Send data to a database or server. Not necessarily updating or editing the DB.
-PATCH - Apply partial modifications. Only change the fields you want, like an email or an address.

-

9. Explain an http header and what some of the things you can send in them?
   More context or info about res/req. Format, authentication info.
   If you are not using Axios, it's the stuff you would have to spell out in an API request.

-They hold request and response information. Name/value pairs in request/response messages.
media types: Accept:text/html
set cookies/cookies: Set-Cookie: UserID=JohnDoe (in response)
origin - requests cross origin resource sharing (CORS)
Access-Control-Allow-Origin: website
\*\*\*\*STATUS in the response.

10. What is a restful API and what are your experiences with their construction/ use?
    Representational State Transfer
    Application Programming Interface
    You can use them to get data from specifically constructed APIs. From a website like Giphy or Twitter, or a standalone API someone created. There's also the DOM, which is basically an API for interacting with websites. (SOAP uses xml)

-

11. What is package.json? What is it used for?

-It lists/stores the packages your app depends on. When you run npm i, it reaches out and installs them.

12. Write the steps for setting up an Express JS application?

-install any needed packages
-Set up env file and add to gitignore
-Set up server.js and server files.
-Set up server boilerplate
-Set up any needed files. (routes/models, etc...)

13. What function arguments are available to Express JS route handlers and what are they?

-req
-res
-next

14. Explain routing in express.js and how you would utilize different files

- The route you want a certain things to happen in.
  Things like user.routes.js would be imported into the server file.
  If they make a GET/POST request, do this thing.
  Export the file and use them in the server file.

15. Explain a good folder structure for express.

-routes/models/config/middleware. Keep like things together

16. How would you get query params or route params from a route?

- `query params` - built with ? and & and can get them from the resObject
- `route params` - route params are built into and required as part of the route. You can get them offf the request object with request.params.

example: router.get("/user/:user_id", async (req, res) => { });

17. How would you set a status and send a response?

- `` Use res dot something.
  res.status.(STATUS CODE).send(RESPONSE TO SEND)

18. Will the following code cause any errors if a user went to that route? Explain why or why not.

On the front end it won't.
On teh back end it will because it is trying to send a response twice.
Every next or res.send has to have a return.

`javascript route.get("/route", (req, res) => { if (true) { res.send("Valid"); } res.send("invalid"); }); `
