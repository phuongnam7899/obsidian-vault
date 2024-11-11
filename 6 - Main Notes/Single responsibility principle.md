2024-11-09 15:57

Tags: [[Clean Code]] 

---


# ==A class should not be changed for more than one reason==
- One responsibility != On method
```js

// violating SRP
class ReportDocument {
	// 2 different un related actions
	generateReport() {}
	createPdf() {}
}

// Not violating
class User {
	login(){}
	signup(){}
	assignRole(){}
}

```


---
# References