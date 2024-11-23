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

| Method | Description |
| ------ | ----------- |
|        |             |


---
# References

[^1]: [[Common HTTP Methods]]