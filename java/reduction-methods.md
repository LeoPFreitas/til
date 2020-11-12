# Reduction methods

- The `reduce` is a method of a `Stream` class that combines elements of a stream into a single value
- `Reduce` is a terminal operation, which means that it begins all evaluations with the stream and produces a final result

### Example

Simple case → reduce method accepts a two-arguments accumulator function.

- Reduce operation that accepts the accumulator function returns Optional type.

```java
List<Integer> transactions = List.of(20, 40, -60, 5);

transactions.stream().reduce((sum, transaction) -> sum + transaction);
```

 Reduce implementation has one additional parameter: identity value or seed

- The identity value represents the initial value for the reduction operation.
- If the stream is empty, reduce operation will return identity value.

```java
transactions.stream().reduce(0, (sum, transaction) -> sum + transaction);
```