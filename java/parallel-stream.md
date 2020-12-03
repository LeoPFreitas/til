# Parallel Stream

### Create parallel Streams

- Invoke the `parallelStream()` method of a collection instead of `stream()`

```java
List<String> languages = List.of("java", "scala", "kotlin", "C#");

List<String> jvmLanguages = languages.parallelStream()
        .filter(lang -> !Objects.equals(lang, "C#"))
        .collect(Collectors.toList());

System.out.print(jvmLanguages); // [java, scala, kotlin]
```

- Transform an existing stream into a parallel stream using the `parallel()` method:

```java
long sum = LongStream
        .rangeClosed(1, 1_000_000)
        .parallel()
        .sum();

System.out.println(sum); // 500000500000
```

**Additional methods for working with parallel:**

- `isParallel()` returns `true` if the stream is parallel and `false` otherwise;
- `sequential()` returns an equivalent sequential stream.

### Performance

There are a number of factors which significantly affect the performance of a parallel stream.

- **Size of data.** The bigger size of data → the greater speedup.
- **Boxing/Unboxing.** Primitive values are processed faster than boxed values.
- **The number of cores are available at runtime.** The more available cores → the greater speedup.
- **Cost per element processing.** The longer each element is processed → the more efficient parallelization. But it
 is not recommended to use parallel stream for performing too long operations (for example, network connections). So it's a kind of a trade off.
- **The type of data source.** Usually initial data source is a collection. The easier it's split into parts → the
 greater speedup. For example, regular arrays, `ArrayList`, and `IntStream.range` are good sources for data splitting
  since they support random access. Others, such as `LinkedList`, `Stream.iterate` are bad sources for data splitting.
- **Type of operations: stateless or stateful**. Stateless operations (for example, `filter` and `map`) are better for
 parallel processing than stateful operations (for example, `distinct`, `sorted`, `limit`). Operations that are based
  on the order of elements are especially hard for parallelizing. But it's not always possible to avoid them.

### Reduce method and its initial value

Assume that we need to calculate the sum of numbers and add 100 to the result. When using a parallel stream, the second option will produce an strange result, because the dataset will be splited into some parts and the value 100 will be added to each of them.

```java
int result = numbers.stream().reduce(100, Integer::sum);

int result = numbers.stream().reduce(0, Integer::sum) + 100;
```

### The forEach method and the order of elements

Given a sorted list of numbers `1, 2, ..., 10` . We'd like to process and print each number from the list using streams.

```java
sortedNumbers.stream()
        .map(Function.identity()) // some processing
        .forEach(n -> System.out.print(n + " "));

// 1 2 3 4 5 6 7 8 9 10 -> sequential
// breaks the order -> parallel
```

```java
sortedNumbers.parallelStream()
        .map(Function.identity()) // some processing
        .forEachOrdered(n -> System.out.print(n + " "));

// code works now
```

### Empty lists and the order of elements

- Using `Collections.emptyList()` will not guarantee the order whem using `forEachOrdered`, because `Collections.emptyList()` doesn't report about its ordering and the stream cannot use the `forEachOrdered` method correctly.
- Using `List.of()` works fine

```java
// create a filled list of integers
List<Integer> numbers = List.of(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

// create an empty list
List<Integer> emptyList = List.of();

Stream.concat(numbers.stream(), emptyList.stream())
        .parallel()
        .filter(x -> x % 2 == 0)
        .limit(3)
        .forEachOrdered((n) -> System.out.print(n + " "));

// 2 4 6
```