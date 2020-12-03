# Infinite streams

- Creating an infinite stream is an intermediate operation, so it actually does note create elements until a 
  terminal operation is executed.

## Generate a stream of objects

- `generate` → Takes a supplier function that produces an object that will be a part of the stream

```java
Stream<T> generate(Supplier<T> supplier)

        Stream<Double> randomNumbers=Stream.generate(Math::random);

        Stream.generate(Math::random)
        .limit(5) // don't miss it
        .forEach(System.out::println);

        double randomNumber=Stream.generate(Math::random).findAny().get();
```

## Iterations

- `iterate` → takes a starting value (seed), and an operator function to generate the next value based on the previous
  one

```java
Stream<T> iterate(T seed,UnaryOperator<T> next)

        Stream<Integer> oddNumbersStream=Stream.iterate(1,x->x+2); // 1, 3, 5, ...

        Stream.iterate(1,x->x+2)
        .limit(5)
        .forEach(System.out::println); // 1 3 5 7 9
```

- An overloaded version that generates a finite stream. It takes a predicate to determine whether the stream has the next
  element

```java
Stream<T> iterate(T seed,Predicate<T> hasNext,UnaryOperator<T> next)

        Stream.iterate(1,x->x< 10,x->x+2)
        .forEach(System.out::println); // 1 3 5 7 9
```