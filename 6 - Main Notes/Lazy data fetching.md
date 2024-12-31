2024-12-31 13:24

Tags: [[Frontend Optimization]]

---

- The weak point of lazy rendering is that the whole dataset need to be loaded -> Slow when the dataset is extremely large.
- The idea of the solution is only to fetch a small part of the dataset, and only fetch more when we know that the user needs more
- This technique requires the backend to support getting the data partially
- Common ways:
	- Pagination
		- ![[Pasted image 20241231132623.png]]
	- Infinity scroll: when use scroll to some part -> fetch more data (the implementation varies by the current technology used, example in React: react-infinite-scroll-component)
---
# References