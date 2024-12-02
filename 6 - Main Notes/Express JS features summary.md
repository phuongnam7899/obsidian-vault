2024-11-22 12:56

Tags: [[Backend]] [[JS]]

---

# Routing
- Routing = define how application endpoints response to the request from client
- The ==app "listen"== for requests that match ==route== and ==method== -> call a ==callback== function
## Method Syntax
- There are many methods[^1]
```js

app.get('/', (req, res) => {
  res.send('GET request to the homepage')
})

// POST method route
app.post('/', (req, res) => {
  res.send('POST request to the homepage')
})

```
## Path Syntax
Could be
- Strings: `/about`, `/home`
- String pattern: `/ab?cd` (acd or abcd)
- Regex: `/.*fly$/` (butterfly, dragonfly,...)
## Route parameters
```javascript
app.get('/users/:userId/books/:bookId', (req, res) => {
  res.send(req.params) // {userId: "", bookId: ""}
})
```
## Route handler
- Can pass multiple callbacks to a route define -> previous one behave like a middleware
```js
app.get('/example/b', (req, res, next) => {
  console.log('the response will be sent by the next function ...')
  next()
}, (req, res) => {
  res.send('Hello from B!')
})
```
## Response methods

| Method         | Description                                                          |
| -------------- | ------------------------------------------------------------------- |
| res.download() | Start a file downlo                                                  |
| res.end()      | Just end the response proc                                           |
| res.json()     | Response a                                                           |
| res.redirect() | Redirect request to other                                      te    |
| res.render()   | Render a view te                                                     |
| res.send()     | Response odd vario                                                   |
| res.sendFile() | Send file as a octet st                                     m[^2]    |
| res.sta Set response status code and send its string representation as body and send  |
## Define multiple methods for one route 
- Use `app.route()`
```js
app.route('/book')
  .get((req, res) => {
    res.send('Get a random book')
  })
  .post((req, res) => {
    res.send('Add a book')
  })
  .put((req, res) => {
    res.send('Update the book')
  })
```
## Router
- Router could be called "mini-app"
- Usually contains routes related to a module
```js
const express = require('express')
const router = express.Router()

// middleware that is specific to this router
const timeLog = (req, res, next) => {
  console.log('Time: ', Date.now())
  next()
}
router.use(timeLog)

// define the home page route
router.get('/', (req, res) => {
  res.send('Birds home page')
})
// define the about route
router.get('/about', (req, res) => {
  res.send('About birds')
})

module.exports = router
```
- To use the router in main app:
```js
const birds = require('./birds')

// ...


app.use('/birds', birds)
```

# Middleware
## Overview
- Is like a gate-keeper for routes
- Can access to `request`, `response`, `next` to:
	- Make change to request/response
	- Call the next middleware (the process only continue when `next()` called
	- End the request-response process
	- Execute any other code
- Use cases:
	- Logging
	- Body parsing
	- Authentication and Authorization
	- Error handling
	- CORS handling
	- Serve static files
	- Validation
	- Caching
	- Ratelimiting
	- Manage session
	- Compress response
- Types of middleware
	- Application-level
	- Router-level
	- Error handling: (always take 4 arguments)
	- Built-in (`static`, `json`, `urlencoded`)
	- 3rd party (from installed package like c`ookie-parser` )



---
# References

[^1]: [[Common HTTP Methods]]
[^2]: [[What is octet stream]]