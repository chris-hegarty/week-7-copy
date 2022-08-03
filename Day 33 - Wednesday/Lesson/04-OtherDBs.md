## So what other options do you have for databases?

### PostGres

- [Overview](https://www.postgresql.org/about/)
- Used for more complex things that MySQL can't handle.
- Allows for more types of things stored
- Open source (unlike MySQL which is proprietary)
- Easy integration with Heroku
- Example with node:

```javascript
// In Connections File
const pg = require("pg");
const connectionString =
  process.env.DATABASE_URL || "postgres://localhost:5432/todo";

const client = new pg.Client(connectionString);
client.connect();
const query = client.query(
  "CREATE TABLE items(id SERIAL PRIMARY KEY, text VARCHAR(40) not null, complete BOOLEAN)"
);
query.on("end", () => {
  client.end();
});

// In Routes File
router.post("/api/v1/todos", (req, res, next) => {
  const results = [];
  // Grab data from http request
  const data = { text: req.body.text, complete: false };
  // Get a Postgres client from the connection pool
  pg.connect(connectionString, (err, client, done) => {
    // Handle connection errors
    if (err) {
      done();
      console.log(err);
      return res.status(500).json({ success: false, data: err });
    }
    // SQL Query > Insert Data
    client.query("INSERT INTO items(text, complete) values($1, $2)", [
      data.text,
      data.complete,
    ]);
    // SQL Query > Select Data
    const query = client.query("SELECT * FROM items ORDER BY id ASC");
    // Stream results back one row at a time
    query.on("row", (row) => {
      results.push(row);
    });
    // After all data is returned, close connection and return results
    query.on("end", () => {
      done();
      return res.json(results);
    });
  });
});
```
