# Functional Data Processing

There are three stages of working with a stream:

1. Obtaining the stream from a source.
2. Performing intermediate operations with the stream to process data.
3. Performing a terminal operation to produce a result.

### Example

```java
// count numbers that are greater than 5
List<Integer> numbers = List.of(1, 4, 7, 6, 2, 9, 7, 8);

// conventional
long count = 0;
for (int number : numbers) {
    if (number > 5) {
        count++;
    }
}
System.out.println(count); // 5

// stream
long count = numbers.stream()
        .filter(number -> number > 5)
        .count(); // 5
```

## Create streams

1. Take it from a collection

    ```java
    List<Integer> famousNumbers = List.of(0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55);
    Stream<Integer> numbersStream = famousNumbers.stream();

    Set<String> usefulConcepts = Set.of("functions", "lazy", "immutability");
    Stream<String> conceptsStream = usefulConcepts.stream();
    ```

2. From an array

    ```java
    Stream<Double> doubleStream = Arrays.stream(new Double[]{ 1.01, 1d, 0.99, 1.02, 1d, 0.99 });
    ```

3. From some values

    ```java
    Stream<String> persons = Stream.of("John", "Demetra", "Cleopatra");
    ```

4. Concatenate other streams

    ```java
    Stream<String> stream1 = Stream.of(/* some values */);
    Stream<String> stream2 = Stream.of(/* some values */);
    Stream<String> resultStream = Stream.concat(stream1, stream2);
    ```

## Operations

All stream operations are divided into two groups: **intermediate** and **terminal** operations.

- **Intermediate operations** are not evaluated immediately when invoking. They simply return new streams to call
 next operations on them. Such operations are known as **lazy** because they do not actually do anything useful.
- **Terminal operations** begin all evaluations with the stream to produce a result or to make a side-effect. As we
 mentioned before, a stream always has only one terminal operation.

**Intermediate operations**

- `filter` returns a new stream that includes the elements that match a **predicate**;
- `limit` returns a new stream that consists of the first `n` elements of this stream;
- `skip` returns a new stream without the first `n` elements of this stream;
- `distinct` returns a new stream consisting of only unique elements according to results of `equals`;
- `sorted` returns a new stream that includes elements sorted according to the natural order or a given **comparator**;
- `peek` returns the same stream of elements but allows observing the current elements of the stream for debugging;
- `map` returns a new stream that consists of the elements that were obtained by applying a function (i.e
. transforming each element).

**Terminal operations**

- `count` returns the number of elements in the stream as a `long` value;
- `max` / `min` returns `Optional` maximum / minimum element of the stream according to the given comparator;
- `reduce` combines values from the stream into a single value (an aggregate value);
- `findFirst` / `findAny` returns the first / any element of the stream as an `Optional`;
- `anyMatch` returns `true` if at least one element matches a predicate (see also: `allMatch`, `noneMatch`);
- `forEach` takes a **consumer** and applies it to each element of the stream (for example, printing it);
- `collect` returns a collection of the values in the stream;
- `toArray` returns an array of the values in a stream.