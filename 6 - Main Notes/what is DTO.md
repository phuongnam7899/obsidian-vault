2025-01-15 14:57

Tags: 

---

- Stands for: Data Transfer Object
- Is a type of POJO
- Is simple object used to transfer data between layers/components
- Characteristic:
	- No business logic
	- Serializable
	- Has Getter and Setter methods
	- Simple structure: fields, constructor, getters and setters
- Example:
```java
public class FeatureDTO implements Serializable {
    private int code;
    private String name;
    private String description;

    // Default constructor
    public FeatureDTO() {}

    // Parameterized constructor
    public FeatureDTO(int code, String name, String description) {
        this.code = code;
        this.name = name;
        this.description = description;
    }

    // Getter and Setter methods
    public int getCode() {
        return code;
    }

    public void setCode(int code) {
        this.code = code;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getDescription() {
        return description;
    }

    public void setDescription(String description) {
        this.description = description;
    }
}
```

---
# References
- [[POJO class]]