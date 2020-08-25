# Sets

- When you need only unique elements within a collection, rid of duplicates in a sequence or intent to perform some mathematical operations, you may use a set.
- A set is a collection of unique elements like a mathematical set. A set is significantly different from an array or a list since it's impossible to get an element by its index.

## Set interface

***The Collections Framework*** provides the `Set<E>` interface to represent a **set** as an abstract data type. It
 inherits all the methods from the `Collection<E>` interface, but doesn't add any new ones. The most used its methods
  are the following:

- `contains(Object o)` returns `true` only if this collection contains the specified element;
- `add(E element)` adds a new element to the set;
- `addAll(Collection<E> coll)` adds all of the elements from other collection to this set;
- `retainAll(Collection<E> coll)` retains only the elements in this set that are contained in the specified collection;
- `remove(Object obj)` removes the specified element from this set;
- `removeAll(Collection<E> coll)` removes from this set all elements that are contained in the specified collection;
- `size()` returns the number of elements in this set;
- `isEmpty()` returns `true` only if this collection contains no elements;
- `clear()` removes all elements from this collection

To start using a set, you need to instantiate one of its implementations: `HashSet`, `TreeSet`, and `LinkedHashSet`.

## Immutable sets

```java
Set<String> emptySet = Set.of();
Set<String> persons = Set.of("Larry", "Kenny", "Sabrina");
Set<Integer> numbers = Set.of(100, 200, 300, 400);

System.out.println(emptySet); // []
System.out.println(persons);  // [Kenny, Larry, Sabrina] or another order
System.out.println(numbers);  // [400, 200, 300, 100] or another order
```

### Important

For immutable sets, it's only possible to invoke `contains`, `size`, and `isEmpty` methods. All others will throw `UnsupportedOperationException` since they try to change the set. If you'd like to `add` / `remove` elements, use one of `HashSet`, `TreeSet` or `LinkedHashSet`.

### HashSet

- Represents a set backend by a hash table
- Uses hash codes of elements to effectively store them
- It makes no guarantees as to the iteration order of the set
- he `HashSet` class offers constant time `O(1)` performance for the basic operations (`add`, `remove`, and `contains`), assuming the hash function disperses the elements properly among the buckets.
- In practice, sets are often used to check whether some elements belong to them. The `HashSet` class is especially recommended for such cases since its `contains` operation is highly optimized.

```java
Set<String> countries = new HashSet<>();

countries.add("India");
countries.add("Japan");
countries.add("Switzerland");
countries.add("Japan");
countries.add("Brazil");

System.out.println(countries); // [Japan, Brazil, Switzerland, India]
System.out.println(countries.contains("Switzerland")); // true
```

### TreeSet

- Represents a set that gives us guarantees on the order of the elements.
- It corresponds to the sorting order of the elements determined either by their natural order (if they implement the `Comparable` interface) or by specific `Comparator` implementation.

The `TreeSet` class implements the `SortedSet` interface which extends the base `Set` interface. The `SortedSet
` interface provides some new methods related to comparisons of elements:

- `Comparator<? super E> comparator()` returns the **comparator** used to order elements in the set or `null` if the set
 uses the natural ordering of its elements;
- `E first()` returns the first (lowest) element in the set;
- `E last()` returns the last (highest) element in the set;
- `SortedSet<E> headSet(E toElement)` returns a subset containing elements that are strictly less than `toElement`;
- `SortedSet<E> tailSet(E fromElement)` returns a subset containing elements that are greater than or equal to 
`fromElement`;
- `SortedSet<E> subSet(E fromElement, E toElement)` returns a subset containing elements in the range `fromElement
` (inclusive) `toElement` (exclusive).

```java
SortedSet<Integer> sortedSet = new TreeSet<>();

sortedSet.add(10);
sortedSet.add(15);
sortedSet.add(13);
sortedSet.add(21);
sortedSet.add(17);

System.out.println(sortedSet); // [10, 13, 15, 17, 21]
System.out.println(sortedSet.headSet(15)); // [10, 13]

System.out.println(sortedSet.first()); // minimum is 10
System.out.println(sortedSet.last());  // maximum is 21
```

### LinkedHashSet

- Represents a set with linked elements.
- It differs from `HashSet` by guaranteeing that the order of the elements is the same as the order they were inserted to the set.
- Reinserting an element that is already in the `LinkedHashSet` does not change this order.
- In some sense, `LinkedHashSet` is something intermediate between `HashSet` and `TreeSet`. Implemented as a hash table with a linked list running through it, this set provides insertion-ordered iteration and runs nearly as fast as `HashSet`.

```java
Set<Character> characters = new LinkedHashSet<>();

for (char c = 'a'; c <= 'k'; c++) {
    characters.add(c);
}
        
System.out.println(characters); // [a, b, c, d, e, f, g, h, i, j, k]
```

## Operations

- In math and other programming languages, the demonstrated set operations are known as union (`addAll`), intersection (`retainAll`) and difference (`removeAll`).

```java
// getting a mutable set from an immutable one
Set<String> countries = new HashSet<>(List.of("India", "Japan", "Switzerland"));

countries.addAll(List.of("India", "Germany", "Algeria"));
System.out.println(countries ); // [Japan, Algeria, Switzerland, Germany, India]

countries.retainAll(List.of("Italy", "Japan", "India", "Germany"));
System.out.println(countries ); // [Japan, Germany, India]

countries.removeAll(List.of("Japan", "Germany", "USA"));
System.out.println(countries ); // [India]
```

## Equality

- Two sets are equal when they contain the same elements.
- Equality does not depend on the types of sets themselves.

```java
Objects.equals(Set.of(1, 2, 3), Set.of(1, 3));    // false
Objects.equals(Set.of(1, 2, 3), Set.of(1, 2, 3)); // true
Objects.equals(Set.of(1, 2, 3), Set.of(1, 3, 2)); // true

Set<Integer> numbers = new HashSet<>();

numbers.add(1);
numbers.add(2);
numbers.add(3);

Objects.equals(numbers, Set.of(1, 2, 3)); // true
```