# Function composition

- It is a mechanism for combining functions to obtain more complicated functions
- The functional interface `Function<T, R>` has two default method `compose` and `andThen` for composing new functions
- Generally, `f.compose(g).apply(x)` is the same as `f(g(x))`, and `f.andThen(g).apply(x)` is the same as `g(f(x))`.

```java
Function<Integer, Integer> adder = x -> x + 10;
Function<Integer, Integer> multiplier = x -> x * 5;

// compose: adder(multiplier(5))
System.out.println("result: " + adder.compose(multiplier).apply(5));
// 35

// andThen: multiplier(adder(5))
System.out.println("result: " + adder.andThen(multiplier).apply(5));
// 75
```

### Composing predicates

All functional interfaces representing predicates (`Predicate<T>`, `IntPredicate` and others) have three methods for composing new predicates: `and`, `or` and `negate`.

```java
IntPredicate isOdd = n -> n % 2 != 0;
IntPredicate lessThan11 = n -> n < 11;

IntPredicate isOddOrLessThan11 = isOdd.or(lessThan11);

System.out.println(isOddOrLessThan11.test(10)); // prints "true"
System.out.println(isOddOrLessThan11.test(11)); // prints "true"
System.out.println(isOddOrLessThan11.test(12)); // prints "false"
System.out.println(isOddOrLessThan11.test(13)); // prints "true"

IntPredicate isOddAndLessThan11 = isOdd.and(lessThan11);

System.out.println(isOddAndLessThan11.test(8));  // prints "false"
System.out.println(isOddAndLessThan11.test(9));  // prints "true"
System.out.println(isOddAndLessThan11.test(10)); // prints "false"
System.out.println(isOddAndLessThan11.test(11)); // prints "false"
```

### Composing consumers

- It is possible to combine consumer by using the method `andThen`
- It is used to output a value to different destinations, like a database or a logger

```java
Consumer<String> consumer = System.out::println;
Consumer<String> doubleConsumer = consumer.andThen(System.out::println);
doubleConsumer.accept("Hi!");

// Hi!
// Hi!
```