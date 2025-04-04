2025-01-15 14:13

Tags: [[Spring Framework]]

---

In Spring, `BeanFactory` and `ApplicationContext` represent IoC container

## Define

In Spring, beans can be defined in several ways:

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
    <bean id="featureService" class="com.example.feature.service.FeatureServiceImpl"/>
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

- Using `getBean()`:

```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class Mobile {
    public static void main(String[] args) {
        // Using ApplicationContext to implement Spring IoC
        ApplicationContext applicationContext = new ClassPathXmlApplicationContext("beans.xml");

        // Get the bean
        Sim sim = applicationContext.getBean("sim", Sim.class);

        // Calling the methods
        sim.calling();
        sim.data();
    }
}
```

---

# References
