2025-01-16 08:34

Tags: [[Spring Framework]] 

---

There're 6 types of annotation in Spring

# Spring Core Annotation
## DI related
- `@Autowired`
	- To mark the dependency to be injected by the Spring container
	- Could be applied to fields, setters, constructor
- `@Qualifier`
- `@Primary`
- `@Bean`
- `@Lazy`
- `@Required`
- `@Value`
- `@Scope`
- `@Lookup`
## Context configuration
- `@Profile`
	- when want to use other annotation only when certain profile is active 
```java
@Component
@Profile("developer")
public class Employee {}
```
- `@Import`
- `@ImportResource`
- `@PropertySource`
# Spring Web Annotation
- `@RequestMapping`
- `@RequestBody`
- `@PathVariable`
- `@RequestParam`
- `@ResponseBody`
- `@ExceptionHandler`
- `@ResponseStatus`
- `@Controller`
- `@RestController`
- `@ModelAtrribute`
- `@CrossOrigin`
# Spring Boot Annotation
# Spring Scheduling Annotation
# Spring Data Annotation
# Spring Bean Annotation
---
# References
- [[What is annotation in Java]]