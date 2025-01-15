2025-01-15 15:47

Tags: [[Spring Framework]] 

---

- 2 types: Setter Dependency Injection and Constructor Dependency Injection
# Setter Injection (SDI)
- Application
```java
package com.geeksforgeeks.org;

import com.geeksforgeeks.org.IGeek;
import org.springframework.beans.factory.annotation.Autowired;

public class GFG {

    // The object of the interface IGeek
    private IGeek geek;

    // Setter method for property geek with @Autowired annotation
    @Autowired
    public void setGeek(IGeek geek) {
        this.geek = geek;
    }
}
```
- Bean config:
```xml
<beans 
xmlns="http://www.springframework.org/schema/beans"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans-2.5.xsd">

    <bean id="GFG" class="com.geeksforgeeks.org.GFG">
        <property name="geek">
            <ref bean="CsvGFG" />
        </property>
    </bean>
    
<bean id="CsvGFG" class="com.geeksforgeeks.org.impl.CsvGFG" />
<bean id="JsonGFG" class="com.geeksforgeeks.org.impl.JsonGFG" />
    
</beans>
```
- By adding `Autowired`, Spring will auto inject the `CsvGFG` implementation into the `GFG` using `setGeek`
# Constructor Injection (CDI)

---
# References