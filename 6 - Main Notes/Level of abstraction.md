2024-11-08 16:37

Tags: [[Clean Code]]

---

- High level:
		-  Developer-defined function
		- Dont control how thing did, we just want it to do something
		- Easy to read, no need to interpret
- Low level: 
		- functions of languages (includes, indexOf,...)
		- We control how things done
		- Technically may be clear, but need to add interpretation by reader

==Function should do work that's one level of abstraction below their name==
## Good
```js
	function emailValid(email) {
		return email.includes('@')
	}
	// This function should retuen true false email includes @ or not => 1 level of abs
```
## Bad
```js
	function saveUser(email) {
		if (email.includes('@')) {
			db.save(user)
		}
	}
	// This function should save user information (1st level) if the email is valid, which mean 
    // email inclides @ (2nd level)
```
## Not mix levels of abstraction
```js
	// x
	if (!email.includes("@")) {
		console.log(email)
	} else {
		const user = ''
		user.save()
	}
	
	// o
	if (!isEmail(email)) {
		showErr()
	} else {
		saveUser()
	}
```


---
# References
- [[When not to split code]]