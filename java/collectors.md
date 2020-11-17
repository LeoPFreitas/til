# Collectors

- The `collect` is a terminal reduction operation that can accept an object of the `Collector` type.
- The `Collections.toCollection` method accepts a function that generates a new collection of a specified type.

```java
LinkedList<Account> accounts = accountStream.collect(Collectors.toCollection(LinkedList::new));

Set<Account> accounts = accountStream.collect(Collectors.toSet());

List<Account> accounts = accountStream.collect(Collectors.toList());
```

### Producing values

Similarly to the `reduce` operation, `collect` is able to accumulate stream elements into a single value.

- `summingInt`, `summingLong`, `summingDouble`;
- `averagingInt`, `averagingLong`, `averagingDouble`;
- `maxBy`, `minBy`;
- `counting`.