# Quiz for Week 7

## Databases

1. What are the benefits of utilizing MySQL over PostGres or vice versa?

-

2. Explain in as much detail as you can what connection Pooling is.

-

3. What steps (if any) need to be take to store passwords in a database?

-

4. What is a document in a NoSQL database?

-

5. If you remove an object attribute from mongodb, is it deleted from the database?

-

6. What is your favorite type of database?

-

7. In a NoSQL Database, what happens if you try to add a key to a schema after you have created some documents?

-

8. What is CRUD and when/how would you use each part?

- `C`
- `R`
- `U`
- `D`

9. Explain the pros and cons for SQL and NoSQL Databases.

-

10. Which is better in your opinion: MySQL, PostGres?

-

11. How would you find all users based off a username in an SQL database? (Assume you have a users table with `id`, `username`, and `email` columns)

```SQL

```

12. What are joins in SQL?

-

13. In MySQL what type would you use to store only a `true` or `false` value? What about in PostGres?

- `MySQL` -
- `PostGres` -

14. What are constraints?

-

15. What are foreign keys and primary keys and when/why would you use them?

- `Foreign Keys` -
- `Primary Keys` -

16. If you need to store user information, all the blog posts from a user, and all their friends, how would you structure that in SQL?

-

17. List the different types of joins.

-

18. How would you get all users from a database (use column names of your choice) sorted in descending order from oldest to youngest?

```SQL

```

19. What is the difference between `HAVING someColumn < 10` and `WHERE someColumn <10`?

- `HAVING` -
- `WHERE` -

20. How would you add up all numbers in a column for all the rows that match the same criteria?

- ``

21. Assuming you have a column name of `userID` but you wanted it to appear as `uID` in your output, how would you do that?

- ``

## API Creation and Express

1. How do you serve static files with express and what does that mean?

```javascript

```

2. What steps do you need to take to ensure that data can be posted to the backend?

-
-

3. How do you setup SQL queries in an express api?

-

4. How would you prepare a React application to be served via an express backend?

-

5. If you wanted to develop a backend and frontend concurrently what are some ways you could do that?

-

6. In express how and why would you implement a middleware?

-

7. What is the `next()` function and why should or shouldn't you use it?

-

8. What are the main http verbs and when would you use each?

-
-
-
-
-

9. Explain an http header and what some of the things you can send in them?

-

10. What is a restful API and what are your experiences with their construction/ use?

-

11. What is package.json? What is it used for?

-

12. Write the steps for setting up an Express JS application?

-

13. What function arguments are available to Express JS route handlers and what are they?

-
-
-

14. Explain routing in express.js and how you would utilize different files

-

15. Explain a good folder structure for express.

-

16. How would you get query params or route params from a route?

- `query params` -
- `route params` -

17. How would you set a status and send a response?

- ``

18. Will the following code cause any errors if a user went to that route? Explain why or why not. _4_
    ```javascript
    route.get("/route", (req, res) => {
      if (true) {
        res.send("Valid");
      }
      res.send("invalid");
    });
    ```
