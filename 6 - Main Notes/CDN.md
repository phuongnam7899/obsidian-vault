2025-09-01 14:30

Tags: 

---

- Content Delivery Network
- Is a geographically distributed network of servers which designed to serve content based on user location
- Content included:
	- Images
	- Videos
	- PDF
	- Document
	- HTML/CSS
- Why it could help?
	- When user need to load content, the longer the distance, the slower loading speed
	- The CDN stored copies of the content at the Edge servers around the world
- Benefit:
	- Reduce latency
	- Reduce website load because the content loaded by CDN -> reduce the web server traffic
	- Scalability
	- Reliability: when a edge server failed, others can serve the content
- Behind the scene:
	- Origin server: where the content lie at
	- Point of present (PoP): Are servers located around the world to serve the content
	- Cache Invalidation: process of remove outdated content to ensure user get the latest one
	- Flow:
		- User request content
		- DNS lookup -> The nearest edge server's IP will be the result of the DNS resolution
		- Edge server check the cache
			- If cache hit -> Serve
			- If cache missed -> Edge server retrieve from origin server -> Serve and cache

---
# References