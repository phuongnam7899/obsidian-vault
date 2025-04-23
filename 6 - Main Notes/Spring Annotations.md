2025-01-16 08:34

Tags: [[Spring Framework]]

---

There are 6 types of annotation in Spring

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
  - when you want to use other annotation only when certain profile is active

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
- `@ModelAttribute`
- `@CrossOrigin`

# Spring Boot Annotation

- `@SpringBootApplication`
- `@EnableAutoConfiguration`
- `@ConditionalOnClass` & `@ConditionalOnMissingClass`
- `@ConditionalOnBean` & `@ConditionalOnMissingBean`
- `@ConditionalOnProperty`
- `@ConditionalOnResource`
- `@ConditionalOn...`
- `@ConditionalExpression`
- `@Conditional`

# Spring Scheduling Annotation

- `@EnableAsync`
- `@EnableScheduling`
- `@Async`
- `@Scheduled`
- `@Schedules`

# Spring Data Annotation

- Provides an abstraction over data storage technologies
- Common Spring Data Annotations
  - `@Transactional`
  - `@NoRepositoryBean`
  - `@Param`
  - `@Id`
  - `@Transient`
  - `@CreatedBy`, `@LastModifiedBy`, `@CreatedDate`, `@LastModifiedDate`
- Spring Data JPA Annotations
  - `@Query`
  - `@Procedure`
  - `@Lock`
  - `@Modifying`
  - `@EnableJpaRepositories`
- Spring Data Mongo Annotations
  - `@Document`
  - `@Field`
  - `@Query`
  - `@EnableMongoRepositories`

# Spring Bean Annotation

- `@ComponentScan`
- `@Configuration`
- Stereotype Annotations - `@Component` - `@Service` - `@Repository` - `@Controller`
  ![[Pasted image 20250116104231.png]]

---

# References

- [[What is annotation in Java]]
