2024-11-01 22:25

Tags: [[Clean Code]]

---

## ==Try keeping function pure== 
- Pure = same input got same output => more predictable
```js
	// Pure
	function generateId(userName) {
		const id = 'id_' + userName;	
		return id;	
	}

	// Not pure
	function generateId(userName) {
		const id = userName + Math.random().toString();
		return id;
	}
```
- No side effect (An operation that does not act on function input to change output. Instead, it change the overall system/program state)
```js
	function createUser(email) {
		const user = new User(email);
		
		// Side effect -> X
		createLead(user)
		
		return user
	}
```

- Name of function should signal that side effect may occur


---
# References