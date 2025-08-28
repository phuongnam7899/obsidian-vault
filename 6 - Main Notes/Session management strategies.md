2025-08-24 20:36

Tags: [[Security]] 

---

# Session Resumption (TLS Session Tickets/RESUME)
- How it works:
	- Server sends a session ticket (encrypted session data) to client
	- Client stores this ticket
	- On next connection, client sends the ticket
	- Server can resume the previous session without full handshake
- Efficiency: 90% faster than full handshake

# Keep-Alive connection (HTTP/1.1)
- How it works:
	- Browser Request: GET /page.html
	- Server Response: HTML with 10 images, 5 CSS files, 3 JS files

	- Browser then makes 18 separate requests:
		1. GET /image1.jpg
		2. GET /image2.jpg  
		3. GET /image3.jpg
		... (one by one, sequentially)
		4. GET /script3.js
- Problem:
	- Head-of-line blocking: the following request need wait for the previous requests to be done first
	- Limit parallel connection of browser (6-8 connections per domain)
	- Redundant header: every request send same header

# HTTP/2 Multiplexing
- How it works:
	- Single Connection with Multiple Streams:
		- Stream 1: GET /page.html
		- Stream 2: GET /image1.jpg  
		- Stream 3: GET /image2.jpg
		- Stream 4: GET /style.css
		- Stream 5: GET /script.js
		... (all happening simultaneously)
	- The browser also know the resources dependencies to decide which resource to load

---
# References