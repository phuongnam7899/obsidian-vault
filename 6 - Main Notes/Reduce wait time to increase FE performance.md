2024-12-31 13:51

Tags: [[Frontend Optimization]]

---

# Technique 1: Pre-X

- In restaurants, not all dishes are cooked right after customers ordering moment.
- Some dishes are usually partially or fully prepared ahead.
- The idea of this technique is exactly the same.
![[Pasted image 20241231135321.png]]
>[!w] Consider which dishes to prepare wisely, otherwise they will become waste

- You can let browser preprocess all or some steps of [[Process of loading resources in browser]]
	- ![[Pasted image 20241231135530.png]]
- Each pre-X triggeed in different moment:
	- ![[Pasted image 20241231135612.png]]
- Code example:
	- ![[Pasted image 20241231135640.png]]
- Some framework like NextJS even have built-in pre-fetch feature:
	- ![[Pasted image 20241231135653.png]]
# Technique 2: Async/Defer
- Imagine we have a HTML file that contains `<script>` tag, here’s how the browser parsing process:
	- ![[Pasted image 20241231135939.png]]
	- ![[Pasted image 20241231135817.png]]
- Here’s when we use `<script async>`:
	- ![[Pasted image 20241231135900.png]]
- And here’s `<script defer>`
	- ![[Pasted image 20241231135923.png]]

---
# References
- [[Use case for each script load type]]