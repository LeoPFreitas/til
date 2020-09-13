# Callback and Closure

- It's possible to pass a lambda expression to a method if the method takes an object of type a suitable functional interface.
- In functional programming, a function (including methods in Java) that accepts or returns another function is called a higher-order function.

```java
public static void acceptFunctionalInterface(Function<Integer, Integer> f) {
   System.out.println(f.apply(10));
}

// it returns the next value
Function<Integer, Integer> f = (x) -> x + 1;

acceptFunctionalInterface(f); // it prints 11

// or even without a reference
acceptFunctionalInterface(x -> x + 1); // the result is the same: 11
```

### Callback

> "a callback is a piece of executable code that is passed as an argument to other code, which is expected to call back (execute) the argument at some convenient time."

### Closures

- In the body of a lambda expression, it's possible to capture values from a context where the lambda is defined (closure)
- Lambda expression can capture the final variable

```java
final String hello = "Hello, ";
Function<String, String> helloFunction = (name) -> hello + name;

System.out.println(helloFunction.apply("John"));
System.out.println(helloFunction.apply("Anastasia"));

// without final
int constant = 100;
Function<Integer, Integer> adder = x -> x + constant;

System.out.println(adder.apply(200));
System.out.println(adder.apply(300));
```