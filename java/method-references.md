# Method references

- Lambda expressions allow you to use code as data and pass it as a method's arguments
- The `Consumer` is a functional interface with a single abstract method `accept` which takes a value of type `T` and returns nothing.

```java
Consumer<String> printer = str -> System.out.println(str);

// reference to a method
Consumer<String> printer = System.out::println;

// base syntax
// something -> class name or a particular instance
something::methodName 
```

### Kinds of method references

There are four kinds of method references:

1. reference to a static method;

    ```java
    // className::staticMethodName
    Function<Double, Double> sqrt = Math::sqrt;
    sqrt.apply(100.0d);
    ```

2. reference to an instance method of an existing object;

    ```java
    // objectName :: instanceMethodName
    Scanner scanner = new Scanner(System.in); 
    Supplier<String> lineReader = scanner::nextLine; // method reference

    String firstLine = lineReader.get();
    String secondLine = lineReader.get();
    ```

3. reference to an instance method of an object of a particular type;

    ```java
    // ClassName :: instanceMethodName
    Function<Long, Double> converter = Long::doubleValue;
    converter.apply(100L);
    ```

4. reference to a constructor.

    ```java
    // ClassName :: new
    Supplier<String> generator = String::new;
    ```