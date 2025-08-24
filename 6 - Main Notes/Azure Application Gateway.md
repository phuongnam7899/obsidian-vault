2025-08-24 19:53

Tags: [[Networking]] [[Azure Cloud]] 

---

- It works at the Application Layer of [[OSI Model]]
- Application Layer [[Load Balancer]]: Make routing decisions based on the content of ==web requests== (HTTP, HTTPS)
- Web traffic management: Primary purpose is to distribute incomming web traffic accross multiple backend servers -> ensure availability
- Beyond a load balancer:
	- Web application firewall (WAF)
	- URL-based routing
	- Cookie-base session affinity
	- ...
- Benefits:
	- Enhanced Performance: offload CPU-intensive tasks like [[TLS]]/[[SSL]] termination
	- Security first: built-in web application firewall
	- Smart routing
	- Scalability: easily to scale up/down based on traffic
- Use cases:
	- Micro-service architecture
	- High traffic web application
	- Web app security need

---
# References
- [[Gateway]]