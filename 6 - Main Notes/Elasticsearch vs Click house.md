2025-01-12 15:32

Tags: [[Database]]

---

Click House is more Effective with large data like Game management system (4.8M records):
- Click House: 0.1s
- Elastic search: 2.5s

# Why?
The way of organize data is different
- Click house: OLAP (Online Analytical Processing):
	- Optimize for reading
	- Columnar storage: only read the needed columns -> increase speed



---
# References
- [[What is columnar storage]]