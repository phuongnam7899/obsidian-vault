2024-11-02 15:07

Tags: [[Clean Code]]

---

# Bad comments
- Most of time, should avoid comments => The code should explain itself
- Comments = more text to read
- Types of bad comments:
	- Redundant information
```js
	// CLASSES
	class Class1 {}
	class Class2
```
- Divider / Block marker
```
    // ****************
    
    const a = 5
    
    // ****************
```
- Misleading
```js
	users.add(...) //update user
```
- Commented-out code
```js
	const findOne = () => {}

	// findOneOld = () => {}
```
=> Just delete it, can retrieve after using git

# Good comments
- Legal information: creator,...
- To explain code that hard to explain itself by naming
```js
	// accepts [text]@[text].[text]	
	const emailRegex = /\S+@\S+\.\S+/
```
- Warning:
```
	// Only work in browser environment
	localStorage.setItem(...)
```
- Todo:
```
	const findOne = () => {
	// TODO: Need implementd
	}
```
- Documentation comment (if want to share the code to others)

---
# References