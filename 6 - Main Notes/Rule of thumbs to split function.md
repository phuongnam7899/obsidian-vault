2024-11-11 21:18

Tags: [[Clean Code]]

---

- Extract code that work on the same functionality
```js

	// x
	user.setAge()
	user.setName()
	
	// o
	user.update({age, name})

```
- Extract code that require more interpation than surrounding code[^1]
```js
	// x
	if (!email.includes('@')) {...} // 2 level of abstraction

	if (!isValid(email)) {...} // bring to the same level of abstraction
	
```


---
# References
- [[When not to split code]]

[^1]: [[Level of abstraction]]