## What if I want my SPA AND server code in the same folder?

- First you want to create the SPA folder in React. This can be a new React app via `create-react-app` or a preexisting app.
- Next you could copy over all of the server code into the folder. Make sure you don't copy over `package.json` or `package-lock.json`.

## How about running both simultaneously?

Usually the easiest way is to create two different terminals and run both your `npm start` and `nodemon server` (replace server with whatever your server's file name is).

nodemon means you are able to change the file node file without having to start and restart the serever.

Regardless, if you are running both, you need to add the following to your `package.json`:

`"proxy": "http://localhost:8080",` where `8080` is replaced with whatever port your server is running on.

If you also want to serve your React app when it's ready to deploy, you can add the following to your server file:

```javascript
app.use(express.static(__dirname + "/build")); // Allows for actual files to be served and not just trying to send JSON information

app.get("*", (req, res) => {
	// the build/index.html is replaced with the location of the built react index.html file. By default it would be as previously displayed
	return res.sendFile("/build/index.html", { root: __dirname + "/" });
});
```
