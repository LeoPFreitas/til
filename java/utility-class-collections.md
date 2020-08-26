# The utility class Collections

- The Java Collections Framework includes the utility class Collections, that contains a number of static methods for creating and processing collections.
- [Docs](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/util/Collections.html)

### Create immutable collections

- Empty collections are often used as the return values from methods instead of `null` to avoid NPE
- Singleton collections are extremely optimized to work with a single value.
- Starting with Java 9, there is an alternative way to create immutable collections: `List.of()`, `List.of(1, 2)`, `Set.of("Hello")`. But it is still useful to know about the previous way of doing that since it is often present in existing code.

```java
// immutable
List<String> emptyList = Collections.emptyList();
Set<Integer> emptySet = Collections.emptySet();

List<Integer> singletonList = Collections.singletonList(100);
Set<String> singletonSet = Collections.singleton("Hello");

public static Collection<Integer> algorithm(Collection<Integer> numbers) {
    // lots lines of codes
    if (some_condition) {
        return Collections.emptyList(); // instead of null
    }
    // lots lines of codes
}

class SingletonList<E> extends .. implements ... {

    private final E element;  // storing a single elment

    SingletonList(E obj) {
        element = obj;
    }

    // some fields and methods
}
```

```java
class SingletonList<E> extends .. implements ... {

    private final E element;  // storing a single elment

    SingletonList(E obj) {
        element = obj;
    }

    // some fields and methods
}
```

### Processing lists

- The are also some methods for performing list-specific operations: sorting, reversing, rotating and shuffling lists.

```java
var numbers = new ArrayList<>(List.of(1, 2, 3, 2, 3, 4)); // getting a mutable list

Collections.sort(numbers);    // [1, 2, 2, 3, 3, 4]
Collections.reverse(numbers); // [4, 3, 3, 2, 2, 1]
Collections.shuffle(numbers); // randomly permutes the list

System.out.println(numbers);  // a result can be any: [4, 2, 3, 2, 3, 1]

// rotate method
List<Integer> numbers = new ArrayList<>(List.of(1, 2, 3, 2, 3, 4));

Collections.rotate(numbers, 1); // [4, 1, 2, 3, 2, 3]
Collections.rotate(numbers, 2); // [2, 3, 4, 1, 2, 3]
```

### Calculations

There are some methods that can be applied to any collections since the methods take the `Collection` interface as the
 argument.

- `frequency` counts the number of elements equal to the specified object;
- `min` and `max` according to the natural order of elements;
- `disjoint` checks the two collections do not contain common elements.

If the collection is empty, the methods finding min and max will throw `NoSuchElementException`. But the frequency will just return 0.

```java
List<Integer> numbers = List.of(1, 2, 3, 2, 3, 4);

System.out.println(Collections.frequency(numbers, 3)); // 2
System.out.println(Collections.min(numbers)); // 1
System.out.println(Collections.max(numbers)); // 4

System.out.println(Collections.disjoint(numbers, List.of(1, 2))); // false
System.out.println(Collections.disjoint(numbers, List.of(5, 6))); // true
```