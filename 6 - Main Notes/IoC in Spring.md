2025-01-15 14:13

Tags: [[Java]] 

---

IoC can be implement in Spring in 2 ways

# Bean
## Define
In Spring, beans could be defined in some ways
### Annotations
When using following annotation, Spring will scan and register them as beans: `@Component`, `@Service`, `@Repository`, `@Controller`

```java
@Service
public class FeatureServiceImpl implements FeatureService {
    // Class implementation
}
```
### @Bean annotation
- Must use in a configuration class
```java
@Configuration
public class AppConfig {

    @Bean
    public FeatureService featureService() {
        return new FeatureServiceImpl();
    }
}
```
### XML configuration
```xml
<beans>
    <bean id="featureService" class="com.tth.psa.apps.tma.ms.pilotmgt.feature.service.FeatureServiceImpl"/>
</beans>
```
## Usage
- Using `@Autowired`
```java
package com.tth.psa.apps.mfm.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api/features")
public class FeatureController {

    @Autowired
    private FeatureService featureService;

    @GetMapping("/{code}")
    public ResponseEntity<Feature> getFeatureByCode(@PathVariable int code) {
        Feature feature = featureService.lookUpBycode(code);
        return ResponseEntity.ok(feature);
    }
}
```

# Dependency Injection

---
# References