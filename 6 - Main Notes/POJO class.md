2025-01-15 14:52

Tags: [[Java]] 

---

- Stand for Plain Old Java Object
- Characteristic:
	- No inheritance
	- Fields are private
	- Has public getters or setters
	- No annotations
- Used for data objects like DTOs, entities,...
- Example
```java
package com.tth.psa.apps.mfm.model;

public class Feature {
    private int code;
    private String name;
    private String description;

    // Default constructor
    public Feature() {}

    // Parameterized constructor
    public Feature(int code, String name, String description) {
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
- [[what is DTO]]