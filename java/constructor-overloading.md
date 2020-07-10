# Constructor overloading

- Sometimes we need to initialize all fields of an object when creating it, but other times it might be appropriate to initialize only one or several fields.
- Cannot define two constructors with the same number, types, and order of the parameters!
- Statement for invoking a constructor should be the first statement in the body of a caller constructor.

```java
public class Robot {
    String name;
    String model;
    int lifetime;
 
    public Robot() {
        this.name = "Anonymous";
        this.model = "Unknown";
    }
	 
		// We can also invoke a constructor from another one. 
		// It allows us to initialize one part of an object by one constructor and another part by another constructor.
    public Robot(String name, String model) {
        this(name, model, 20);
    }
 
    public Robot(String name, String model, int lifetime) {
        this.name = name;
        this.model = model;
        this.lifetime = lifetime;
    }
}
```