2024-11-01 22:23

Tags: [[Clean Code]]

---
## 1. Just renaming operation
 
```js
	// x
	function saveUser(email, password) {
		const user = buildUser(email, password);
		user.save();
	}
		
	function buildUser(email, password) {
		return {
			email: email,
			password: password,
		};

	// o
	class User {
		constructor(email, password) {
			this.email = email;		
			this.password = password;
		}

		save() {
			database.insert(this);
		}
	}
	function saveUser(email, password) {
		const user = new User(email, password);
		user.save();
	}
```
## Finding new function take longer than reading extracted code
## Can not produce understandable name for extracted part

---
# References