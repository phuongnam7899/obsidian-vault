2025-01-15 15:21

Tags: [[Spring Framework]] 

---

- BeanFactory is one of IoC container in Spring (along with ApplicationContext) to instantiate, configure and manage life cycle of beans
- Follow Factory Pattern

# Implementation
![[Pasted image 20250115154129.png]]
- Create POJO class:
```java
public class Student {

  // Member variables
  private String name;
  private String age;

  // Constructor 1
  public Student() {
  }

  // Constructor 2
  public Student(String name, String age) {
    this.name = name;
    this.age = age;
  }

  // Method inside POJO class
  @Override
  public String toString() {

    // Print student class attributes
    return "Student{" + "name='" + name + '\'' + ", age='" + age + '\'' + '}';
  }
}
```
- Config the bean in `bean-factory-demo.xml`:
```xml
<beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    <bean id="student" class="com.gfg.demo.domain.Student">
        <constructor-arg name="name" value="Tina"/>
        <constructor-arg name="age" value="21"/>
    </bean>
</beans>
```
- Use the bean:
```java
@SpringBootApplication
// Main class
public class DemoApplication 
{
// Main driver method
  public static void main(String[] args) 
  {
    // Creating object in a spring container (Beans)
    BeanFactory factory = new ClassPathXmlApplicationContext("bean-factory-demo.xml");
    Student student = (Student) factory.getBean("student");

    System.out.println(student);
  }
}

```

---
# References
- [[IoC in Spring]]
- [[POJO class]]