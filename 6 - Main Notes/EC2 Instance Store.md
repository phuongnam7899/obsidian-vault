2025-04-27 09:41

Tags: [[AWS EC2]] 

---

# Why?
- [[EBS]] volumes are network drive with limited performance
- If we need high-performance hardware disks, use EC2 Instance Store
# General
- Better I/O performance
- It loses their storage when stopped -> Risk of data loss -> often **used for short-term data**
- Use cases:
	- Buffer
	- Cache
	- Scratch data
	- Temporary content
- Backups and Repication are YOUR responsibility not AWS)

---
# References