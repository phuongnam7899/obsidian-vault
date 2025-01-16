2025-01-16 08:52

Tags: [[Java]] 

---

# 1. Define annotation interface
- `@interface` keyword to mark as annotation
- `@Retention`: 
- `@Target`
```java
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

// Define the custom annotation
@Retention(RetentionPolicy.RUNTIME) // The annotation will be available at runtime
@Target(ElementType.METHOD) // The annotation can be applied to methods
public @interface MyCustomAnnotation {
    String value() default "default value"; // Define an element with a default value
}
```

---
# References