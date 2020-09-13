# Functional interfaces

- It is an interface with a single abstract method (SAM)
- Static and default methods are allowed
- There is a special annotation `@FunctionalInterface` that marks functional interfaces and indicates if the interface doesn't satisfy the requirements of a functional interface (compile-time error).

```java
@FunctionalInterface 
interface Func<T, R> { 

    R apply(T val);

    static void doNothingStatic() {

    }

    default void doNothingByDefault() {

    } 
}
```

### Implementing functional interfaces

- Need to implement the interface and then create an instance of the concrete class.

**1) Anonymous class.** Create an anonymous class and override the method apply. The overridden method calculates the square of a given value.

```java
Func<Long, Long> square = new Func<Long, Long>() {
    @Override
    public Long apply(Long val) {
        return val * val;
    }
};

long val = square.apply(10L); // the result is 100L
```

2) **Lambda expression.** Besides, the functional interfaces can be implemented and instantiated using a lambda expression.

- A functional interface can be instanced using a lambda expression because the interface has a single abstract method (non-default and non-static)

```java
Func<Long, Long> square = val -> val * val; // the lambda expression

long val = square.apply(10L); // the result is 100L
```

### Lambda expressions

- **BiFunction<T, U, R>** is a standard functional interface representing a function with two arguments of types T
 and U. It returns a value of type R.
- **Function<T, R>** is also a standard functional interface, but it has only one argument of type T and returns a
 value of type R.

```java
// a simple way to write a lambda expression with two parameters
BiFunction<Integer, Integer, Integer> sum = (x, y) -> x + y;

// if it has only one argument "()" are optional
Function<Integer, Integer> identity1 = x -> x;

// it's valid too
Function<Integer, Integer> identity2 = (x) -> x;

// without type inference
Function<Integer, Integer> mult = (Integer x) -> x * 2;

// with multiple statements
Function<Integer, Integer> adder = (x) -> {
    x += 5;
    x += 10;
    return x;
};
```