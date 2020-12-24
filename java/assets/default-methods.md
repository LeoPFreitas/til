# Default methods

- Default methods have an implementation
- Since interface methods are abstract by default, you need to put the default keyword before methods with body
- Can't invoke default methods directly from an interface. an object of a class that implement the interface is necessary in order to call the method

```java
interface Feature {
    default void action() {
        System.out.println("Default action");
    }
}

class FeatureImpl implements Feature {
}
...

Feature feature = new FeatureImpl();
feature.action(); // Default action
```

### The diamond problem

- Two interfaces with the same default methods (same signature) and different implementations. If some class implement these 2 interfaces, the programmer need to explicity implement the default method.