Source link: https://www.youtube.com/watch?v=f7Su4KoqSio

Status: #source-eating 

---

# Dependency Inversion Principle
![[Pasted image 20250107105022.png]]
- The service should not be dependent on the concrete repository, because when you change the repository -> the service will break
- Instead,  the Repository should depend on an interface, then Service use that interface 
# Interface Adapter
![[Pasted image 20250107105553.png]]
# The modern take
![[Pasted image 20250107105848.png]]
- Infrastructure: contains interface for Database, event bus, mail sender,...
- Presentation: web, mobile, desktop, web api, cli,...
- Application: usually to create use cases
- Domain: contains entities and enterprise-wide logic
# The main component
![[Pasted image 20250107110757.png]]
- main component know everything
- bootstrap the application by managing the injection
# Components principles
- Reuse/release equivalence
- Common closure
- Acyclic dependency
- Common reuse
# Vertical slide architecture
![[Pasted image 20250107111749.png]]
# Side thought
- Can use dependency injection framework or factories function
# Code flow
- Create a `main.ts`
- Create a folder for each layer
- `application`:
	- Create a file for each use case
	- File should export a class that have 1 `execute()` method
	- Create an interface for `CreateLogBookDataTransferObject` -> use it for the `execute` argument
	- Create interface for `execute()`'s output
	- 
 




---