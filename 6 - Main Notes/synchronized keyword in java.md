2025-01-16 10:51

Tags: [[Java]]

---

- Used to ==control access== to a ==method/code block== -> ensure ==only 1 thread can run== it at the same time
- Goal: ==prevent race condition== and ensure ==thread safety==

```java
// Example: Synchronizing a method call to prevent concurrent access
synchronized (lockObject) {
    LOGGER.bridgeTo(getEndPointName());
}
```

---

# References
