2025-04-05 10:30

Tags: [[Networking]]

---

- Also called [[subnet]] or [[CIDR range]]
- Is a group of consecutive [[IP address]] 
- Example: `192.168.1.0/24`:
	- `/24`: first 24 bits are fixed, last 8 (32 - 24) bits can varied -> it gives `2 ^ 8 = 256` addresses (from `192.168.1.0` to `192.168.1.255`)
- Common notation:
	- `/32`: Single IP address
	- `/24`: 256 addresses
	- `/16`: 2^16 addresses
	- `/8`: 2^24 addresses
	- `/0`: all addresses

---
# References
- [[IPv4]]
- [[IPv6]]