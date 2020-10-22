# Standard functional interfaces

All functional interfaces that are presented in the `java.util.function` package can be divided into five groups:

- **functions** that accept arguments and produce results;
- **operators** that produce results of the same type as their arguments (a special case of function);
- **predicates** that accept arguments and return boolean values (boolean-valued function);
- **suppliers** that accept nothing and return values;
- **consumers** that accept arguments and return no result.

### Examples

1. **Functions**

    ```java
    // String to Integer function
    Function<String, Integer> converter = Integer::parseInt;
    converter.apply("1000"); // the result is 1000 (Integer)

    // String to int function
    ToIntFunction<String> anotherConverter = Integer::parseInt;
    anotherConverter.applyAsInt("2000"); // the result is 2000 (int)

    // (Integer, Integer) to Integer function
    BiFunction<Integer, Integer, Integer> sumFunction = (a, b) -> a + b;
    sumFunction.apply(2, 3); // it returns 5 (Integer)
    ```

2. **Operators**

    ```java
    // Long to Long multiplier
    UnaryOperator<Long> longMultiplier = val -> 100_000 * val;
    longMultiplier.apply(2L); // the result is 200_000L (Long)

    // int to int operator
    IntUnaryOperator intMultiplier = val -> 100 * val;
    intMultiplier.applyAsInt(10); // the result is 1000 (int)

    // (String, String) to String operator
    BinaryOperator<String> appender = (str1, str2) -> str1 + str2;
    appender.apply("str1", "str2"); // the result is "str1str2"
    ```

3. **Predicates**

    ```java
    // Character to boolean predicate
    Predicate<Character> isDigit = Character::isDigit;
    isDigit.test('h'); // the result is false (boolean)

    // int to boolean predicate
    IntPredicate isEven = val -> val % 2 == 0;
    isEven.test(10); // the result is true (boolean)
    ```

4. **Suppliers**

    ```java
    Supplier<String> stringSupplier = () -> "Hello";
    stringSupplier.get(); // the result is "Hello" (String)

    BooleanSupplier booleanSupplier = () -> true;
    booleanSupplier.getAsBoolean(); // the result is true (boolean)

    IntSupplier intSupplier = () -> 33;
    intSupplier.getAsInt(); // the result is 33 (int)
    ```

5. **Consumers**

    ```java
    // it prints a given string
    Consumer<String> printer = System.out::println;
    printer.accept("!!!"); // It prints "!!!"
    ```