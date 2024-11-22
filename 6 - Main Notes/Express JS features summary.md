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
  res.send(req.params)
})
```


---
# References

[^1]: [[Common HTTP Methods]]