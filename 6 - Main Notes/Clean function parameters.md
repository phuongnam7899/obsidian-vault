2024-11-02 14:22

Tags: [[Clean Code]]

---

## Input parameters
==Minimize the number of parameters==
- 0-1 parameter always good
- 2 parameters might ok if parameters can be easily guessed or no need to guess:
```js
	const login = (username, password) => {}
	const multiple = (firstNum, secondNum) => {}
```
- >3 parameters: recommend ==using object== to group related parameters (for no need to guess/check  the order of parameters)
```js
	// x
	const saveUser = (email, password,username, fullName) {
		const newUser = {email, password,username, fullName}
		db.save('user', newUser)
	}
	saveUser('test@test.com', '1234', 'test', 'Test Test')
	
	// o
	const saveUser = (newUser) {
		db.save('user', newUser)
	}
	saveUser(newUser)
	
	// ooo
	class User {
		constructor(){}
		save() {}
	}
	const newUser = new User({email, password,username, fullName})
	newUser.save()
	
```
- Dynamic number of parameters: use when all parameter are treated the same way
```js
	const sum(...numbers) {}
```

## Output paramters
- Avoid changing the arguments value unexpectedly
```js
	// x
	function createId(user) {
		user.id = ''
	}
	const user = {}
	createId(user)

	// o
	function addId(user) {}

	// ooo
	class User {}
	const user = new User()
	user.addId()
```


---
# References