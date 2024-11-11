2024-11-08 10:57

Tags: [[Clean Code]] 

---

## Using Guards
- Adding an invert condition right before the main condition
- In the body of condition:
	- Run the "else" body if has
	- If the condition is not in a loop: return 
	- If in the loop: continue
- Signal to use: when body of if statemane
### From
```js
	if (transaction && transactions.length > 0) {
		// Handle logic
	} else {
		// Handle else logic
	}
```
### To
```js
	if (!transaction || transactions.length === 0) {
		// Handle else logic
		return;
	}
	// Handle logic
```
## Handle shared logic/condition
- If same things (conditon/logic) run in both if and else body=> Move it outside
## Prefer using positive phrases in condition
- isEmpty > !hasNoElements => easier to read
## Extract condition to functions
## Use &&/|| when possible
### &&
```js
	// x
	if (isOk) {
		process()
	}
	// o
	isOk && process()
```
### ||
```js
	// x
	let number;
	if (newNumber) {
		number = newNumber
	} else {
		number = defaultNumber
	}

	// o
	let number = newNumber || defaultNumber
```


---
# References