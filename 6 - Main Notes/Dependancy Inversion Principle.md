2024-11-04 13:47

Tags: [[Clean Code]]

---

==You should depen upon abstrctions, not concretions==

## Bad
```ts
	...[^1]
	class App {
		private db: SQLDatabase | InmemoryDatabase;
		// Problem: The more db type we have, the more if-else, the more complex
		constructor(db: SQLDatabase | InmemoryDatabase){
			if (db instanceof SQLDatabase)	{db.connect('url')}
			this.db = db
		}
		saveSetting() {
			this.db.storeData('data')
		}
	}
```
## Good
```ts
	...[^1]
	class App {
		private db: Database;
		// Problem: The more db type we have, the more if-else, the more complex
		constructor(db: Database){
			this.db = db
		}
		saveSetting() {
			this.db.storeData('data')
		}
	}


	const sqlDb = new SqlDb()
	sqlDb.connect();
	const App = new App(sqlDb)
```


---
# References