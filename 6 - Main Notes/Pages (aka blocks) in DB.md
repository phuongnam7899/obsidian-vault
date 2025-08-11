2025-08-11 09:13

Tags: [[Database]] 

---

- Is database's fixed-sized unit of storage and I/O
- Pages consists of:
	- Page header: metadata (LSN, checksums, free space)
	- Slot/line pointer array
	- Tuples/records: actual rows or index entries
	- Free space: use for inserts/updates 
- Each database can has different default page size, and might be configured

---
# References