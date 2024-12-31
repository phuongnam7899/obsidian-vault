2024-12-31 13:17

Tags: [[Frontend]] [[Optimization]]

---

- Imagine you want to have 2 buttons, each handles a calculation when clicked, and you implement like this:
![[Pasted image 20241231131857.png]]
- Problem: event if the user comes and only clicks 1 of those buttons, you still need to load both functions from beginning
- The solution for that problem is to split the code into smaller chunks:
![[Pasted image 20241231131931.png]]
	- The function is only imported when needed -> Reduce the amount of code need to be loaded from the beginning
- The cost is a small delay for each action -> Need to consider which part to be imported dynamically

---
# References