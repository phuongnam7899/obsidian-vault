2025-04-07 15:26

Tags: [[AWS]] [[Networking]] 

---

- Public IP: 
	- can be access through the internet
	- must be unique through the whole web
	- can be geo-located easily
- Private IP: 
	- can only be access in private network
	- be unique only in private network
	- machines connect to WWW using [[Internet Gateway]]
	- only a specified range of  IPs can be used as private IP
- Elastic IP:
	- When restart EC2 instance -> public IP is changed -> if you need fixed public IP -> using Elastic IP
	- With elastic IP address, you can mask the failure of an instance by remapping that IP with other instance
	- 1 account can has maximum 5 elastic IP (can ask AWS to change that)
	- Overall, try to avoid using it because:
		- it reflects poor architectural decision
	- Instead:
		- using random public IP and register DNS name to it
		- using Load Balancer and don't use public IP (best practice)

---
# References