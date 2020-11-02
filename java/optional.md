# Optional

- The `Optional<T>` class represents the presence or absence of a value of the specified type `T`. An object of this class can be either **empty** or **non-empty**.

```java
Optional<String> absent = Optional.empty();
Optional<String> present = Optional.of("Hello");

System.out.println(absent.isPresent()); // false
System.out.println(present.isPresent()); // true
```

- Optional is like a box that contains either some value or nothing. It wraps a value or `null` keeping the possibility to check it by using special methods

```java
String message = getRandomMessage(); // it may be null

Optional<String> optMessage = Optional.ofNullable(message);

System.out.println(optMessage.isPresent()); // true or false
```

## Getting the value from an Optional

The most obvious thing to do with an Optional is to get its value. For now, we're going to discuss three methods with such purpose:

- `get` returns the value if it's present, otherwise throws an exception;
- `orElse` returns the value if it's present, otherwise returns `other`;
- `orElseGet` returns the value if it's present, otherwise invokes `other` and returns its result.

```java
Optional<String> optName = Optional.of("John");
String name = optName.get(); // "John"

Optional<String> optName = Optional.ofNullable(null);
String name = optName.get(); // throws NoSuchElementException

String nullableName = null;
String name = Optional.ofNullable(nullableName).orElse("unknown");   
System.out.println(name); // unknown

String name = Optional
        .ofNullable(nullableName)
        .orElseGet(SomeClass::getDefaultResult);
```

## Conditional actions

There are also convenient methods that take functions as arguments and perform some actions on values wrapped inside Optional:

- `ifPresent` performs the given action with the value, otherwise does nothing;
- `ifPresentOrElse` performs the given action with the value, otherwise performs the given empty-based action.

```java
Optional<String> companyName = Optional.of("Google");
companyName.ifPresent((name) -> System.out.println(name.length())); // 6

Optional<String> noName = Optional.empty();
noName.ifPresent((name) -> System.out.println(name.length())); // no print

String companyName = ...;
if (companyName != null) {
    System.out.println(companyName.length());
}

// safe alternative to if-else statetment
Optional<String> optName = Optional.ofNullable(/* some value goes here */);
optName.ifPresentOrElse(
        (name) -> System.out.println(name.length()), 
        () -> System.out.println(0)
);
```