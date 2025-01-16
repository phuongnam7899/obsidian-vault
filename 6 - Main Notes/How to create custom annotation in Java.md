2025-01-16 08:52

Tags: [[Java]] 

---

# 1. Define annotation interface
- `@interface` keyword to mark as annotation
- `@Retention`: retention policy - when the annotation is available (fop example at runtime)
- `@Target`: which element could the annotation applied to (method, class, argument)
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
# 2. Use the annotation
```java
public class MyClass {
    @MyCustomAnnotation(value = "example value")
    public void myMethod() {
        // Method implementation
    }
}
```

# 3. Process the annotation
- At runtime:
```java
import java.lang.reflect.Method;

public class AnnotationProcessor {

    public static void main(String[] args) {
        // Get the class object
        Class<MyClass> obj = MyClass.class;

        // Iterate through all methods
        for (Method method : obj.getDeclaredMethods()) {
            // Check if the method is annotated with MyCustomAnnotation
            if (method.isAnnotationPresent(MyCustomAnnotation.class)) {
                // Get the annotation
                MyCustomAnnotation annotation = method.getAnnotation(MyCustomAnnotation.class);
                // Print the value of the annotation
                System.out.println("Method: " + method.getName() + ", Annotation value: " + annotation.value());
            }
        }
    }
}
```

---
# References