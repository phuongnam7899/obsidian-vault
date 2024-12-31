2024-12-31 13:46

Tags: [[Frontend]]

---

# Browser Cache
For static resources: We could tell the browser to cache static assets by setting the following header(s) for the response:
		- ![[Pasted image 20241231134333.png]]
# Browser Storages:
- Local Storage and Session Storage
	- ![[Pasted image 20241231134410.png]]
- IndexedDB: Another way to store data, but when compare to Local/Session Storage:
	- Advantage:
		- Can store more data (No strictly limited)
		- Can store unstructured data
		- Not block main thread (because the API is async)
		- Support advance queries and indexing
	- Disadvantages
		- A bit slower due to async nature
		- More complex to use
	- => Used to store large and complex data like API responses, offline resources

---
# References