2025-08-11 09:00

Tags: [[Database]] 

---


- Is a mechanism to increase the performance (throughput and latency) of the queries
- Is an in-memory cache of DB pages/block
- Read flow:
	- On query, DB look for the page in the buffer pool first
	- If present -> return result from memory
	- If missing -> read from disk -> put to the buffer pool -> evict other page to make space (if need)
- Write flow:
	- On update, page is modified in memory (become dirty)
	- Changes logged to the [[WAL]]/redo log first
	- Dirty pages are flushed to disk by background writers/checkpoints
- Eviction mechanism
	- Least Recently Used (LRU) to choose pages to evict
	- Pinned pages cannot be evicted
---
# References
- [[Pages (aka blocks) in DB]]