Source link: https://react.dev/reference/rsc/server-components

Status: #source-eating 

---

## Overview
- Server component is component that ==rendered before bundling==, in a ==separated environment== (called "server") from client or SSR server
- SC could run:
	- once at build time (on CI server)
	- before each request (using web server)
## Server Components without a Server
