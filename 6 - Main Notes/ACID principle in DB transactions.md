2024-12-24 09:34

Tags: [[Database]] 

---

# A - Atomicity
- Make sure ==all== steps of transaction will ==success==, ==or nothing==
# Consistency
- DB before and after transaction still keeps valid state
- Example: No constraints (unique, positive value) is broken
# Isolation
- Ensure concurrent transactions not interfere each other by:
	- execute sequentially
	- lock mechanism
- 4 levels:
	- Read uncommitted: allow dirty read
	- Read committed: prevent dirty read
	- Repeatable read: Prevents non-repeatable reads
	- Serializable: Fully isolated
# Durability
- Ensure that when a transaction committed, data is permanently saved (even if system crash)
	- Data is written into log file to recover when system up

---
# References