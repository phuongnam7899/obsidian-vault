2025-01-16 10:51

Tags: [[Java]] 

---

- Used to ==control access== to a ==method/code block== -> ensure ==only 1 thread could run== it at the same time
- Goal: ==prevent race condition== and ensure the ==thread safety==
```java
synchronized (lockObject) {
	 LOGGER.bridgeTo(getEndPointName());
}
```
---
# References