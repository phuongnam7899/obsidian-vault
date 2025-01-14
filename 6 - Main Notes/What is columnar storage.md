2025-01-12 15:42

Tags:[[Database]] 

---

- Given the objects that needed to be saved to DB:
```json

[
	{
		"name": "Nam",
		"age": 26
	},
	{
		"name": "Norman",
		"age": 24
	},
]

```
- The data saved to DB will look like:

| name        | age    |
| ----------- | ------ |
| Nam, Norman | 26, 24 |

> [!s] When want to calculate values from columns, for example average age -> no need to load other columns

- Better for application that need to calculate much rely on columns
- Support indexing and partitioning
- Compress data: Store compressed data -> reduce I/O loa

---
# References