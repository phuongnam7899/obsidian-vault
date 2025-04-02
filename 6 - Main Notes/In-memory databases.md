2025-04-02 20:50

Tags: [[Database]]

---

- Store data in **RAM** rather than disk
- Much **faster** read/write data (10x-100x)
- Low latency for operations
- Use cases:
	- Caching
	- Realtime analytics
	- Session management
- Can be **volatile** (loss data on power loss) **or persistence** (with backup mechanism)
- Example: [[Redis]], [[Memcached]], [[H2 database]], [[HSQLDB]]
- Tradeoff: Speed vs Consistency/Capacity (RAM is more expensive and volatile when compare to disk)


---
# References