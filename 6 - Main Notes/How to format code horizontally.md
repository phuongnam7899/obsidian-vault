2024-11-08 10:49

Tags: [[Clean Code]] 

---

# Avoid long "sentences"
- Avoid scrolling-needed when read code line
## By using indentation
- Technically, it may not be required (in some language, yes), but should use multiple lines with indentation for hierarchy
## Break long statements into multiple shorter ones
### Bad
```js
	const data = await fetch(`http://randomapi/person?key={apiKey}&sort=asd`, {
		method,
		...config
	})
```
### Better
```js
	const apiUrl = `http://randomapi/person?key={apiKey}&sort=asd`
	const data = await fetch(apiUrl, {
		method,
		...config
	})
```
## Use clear and readable long name
```
	// x
	const aVariableToStoreTheApiUrlToGetRandomUser = `http://randomapi/person`
	// o
	const randomPersonApi = `http://randomapi/person`


---
```

# References
- [[Vertical formatting]]