Source link: https://www.youtube.com/watch?v=jJVAla0dWJo

Status: #source-eating 

---

# Clean architecture overview
![[Pasted image 20250106160246.png]]

Produce system that are:
- Independent of Framework
- Testable: business rule can be tested without UI, DB, web server, ...
- Independent of UI: UI can change easily without change the rest (web -> mobile -> console)
- Independent of DB
- Independent of external agency
![[Pasted image 20250106160432.png]]
# Project Structure
![[Pasted image 20250106161656.png]]
- `/app`: is Framework and Driver layer
- `/src`: contain other layers:
	- `application`: only contains interfaces
		![[Pasted image 20250106162233.png]]
		- `use-cases`
		- `services`
		- `repositories`
	- `entities`: contain entities
		![[Pasted image 20250106162409.png]]
	- `infrastructure`:  contain implementation of interfaces in `application`
		![[Pasted image 20250106162723.png]]
		- `repositories`
		- `services`
	- `interface-adapter`: 
		- `controllers`: 
			![[Pasted image 20250106162957.png]]
- `tests`:
	- `unit`: contain unit, follow same structure of `/src`
# Implementation Flow

---