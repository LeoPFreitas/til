# Map

## Introduction

- A map is a collection of key-value pairs. Keys are always unique while values can repeat.
- To start using a map, you need to instantiate one of its implementations: `HashMap`, `TreeMap`, and `LinkedHashMap`.
- They use different rules for ordering elements and have some additional methods.
- There are also immutable maps whose names are not important for programmers.

**Maps have some similarities with sets and arrays;**

- **keys** of a map form a **set**, but each key has an associated value;
- **keys** of a map are similar to **indexes of an array**, but the keys can have any type including integer numbers
, strings and so on.

### Map Interface

- The Collections Framework provides the `Map<K,V>` interface to represent a map as an abstract data type.
- The `Map` interface is not a subtype of the `Collection` interface, but maps are often considered as collections since they are part of the framework.

**1) Collection-like methods:**

- `int size()` returns the number of elements in the map;
- `boolean isEmpty()` returns `true` if the map does not contain elements and `false` otherwise;
- `void clear()` removes all elements from the map.

We hope, these methods do not need any comments.

**2) Keys and values processing:**

- `V put(K key, V value)` associates the specified `value` with the specified `key` and returns the previously
 associated value with this `key` or `null`;
- `V get(Object key)` returns the value associated with the key, or `null` otherwise;
- `V remove(Object key`) removes the mapping for a `key` from the map;
- `boolean containsKey(Object key)` returns `true` if the map contains the specified `key`;
- `boolean containsValue(Object value)` returns `true` if the map contains the specified `value`.

These methods are similar to the methods of collections, except they process key-value pairs.

**3) Advanced methods:**

- `V putIfAbsent(K key, V value)` puts a pair if the specified key is not already associated with a value (or is
 mapped to `null`) and return `null`, otherwise, returns the current value;
- `V getOrDefault(Object key, V defaultValue)` returns the value to which the specified key is mapped, or 
`defaultValue` if this map contains no mapping for the key.

These methods together with some others are often used in real projects.

**4) Methods which return other collections:**

- `Set<K> keySet()` Returns a `Set` view of the keys contained in this map;
- `Collection<V> values()` returns a `Collection` view of the values contained in this map;
- `Set<Map.Entry<K, V>> entrySet()` returns a `Set` view of the entries (associations) contained in this map.

## Immutable maps

The simplest way to create a map is to invoke the of method of the `Map` interface.

- It is also possible to check whether a map contains a particular key or value by using `containsKey` and `containsValue` methods.
- Since it is immutable, only methods that do not change the elements of this map will work.
- Others will throw an exception `UnsupportedOperationException`. If you'd like to put or to remove elements, use one of `HashMap`, `TreeMap` or `LinkedHashMap`.

```java
Map<String, String> emptyMap = Map.of();

Map<String, String> friendPhones = Map.of(
        "Leonardo", "98383-9933",
        "Pedro", "98383-7677",
				"Joao", "96565-8787"
);

System.out.println(emptyMap.size());     // 0
System.out.println(friendPhones.size()); // 3

String leonardoPhone = friendPhones.get("Leonardo"); // 98383-9933
String alicePhone = friendPhones.get("Alice"); // null
String phone = friendPhones.getOrDefault("Alex", "Unknown phone"); // Unknown phone

System.out.println(friendPhones.keySet()); // [Leonardo, Pedro, Joao]
System.out.println(friendPhones.values()); // [98383-9933, 98383-7677, 96565-8787]
```

## HashMap

- Represents a map backed by a hash table.
- This implementation provides constant-time performance for `get` and `put` methods assuming the hash function disperses the elements properly among the buckets.
- This implementation is often used in practice since it is highly-optimized for putting and getting pairs.

```java
Map<Integer, String> products = new HashMap<>();

products.put(1000, "Notebook");
products.put(2000, "Phone");
products.put(3000, "Keyboard");

System.out.println(products); // {2000=Phone, 1000=Notebook, 3000=Keyboard}

System.out.println(products.get(1000)); // Notebook

products.remove(1000);

System.out.println(products.get(1000)); // null

products.putIfAbsent(3000, "Mouse"); // it does not change the current element

System.out.println(products.get(3000)); // Keyboard
```

## LinkedHashMap

- The `LinkedHashMap` stores the order in which elements were inserted.
- In this code, the order of pairs is always the same and matches the order in which they are inserted into the map.

```java
Map<Integer, String> products = new LinkedHashMap<>(); // ordered map of products

products.put(1000, "Notebook");
products.put(2000, "Phone");
products.put(3000, "Keyboard");

System.out.println(products); // it's always ordered {1000=Notebook, 2000=Phone, 3000=Keyboard}
```

## TreeMap

- Represents a map that gives us guarantees on the order of the elements.
- It is corresponding to the sorting order of the keys determined either by their natural order (if they implement the `Comparable` interface) or by specific `Comparator` implementation.
- Use `TreeMap` only when you really need the sorting order of elements since this implementation is less effective than `HashMap`.

This class implements the `SortedMap` interface which extends the base `Map` interface. It provides some new methods
, related to comparisons of keys:

- `Comparator<? super K> comparator()` returns the comparator used to order elements in the map or `null` if the map
 uses the natural ordering of its keys;
- `E firstKey()` returns the first (lowest) key in the map;
- `E lastKey()` returns the last (highest) key in the map;
- `SortedMap<K, V> headMap(K toKey)` returns a submap containing elements whose keys are strictly less than `toKey`;
- `SortedMap<K, V> tailMap(K fromKey)` returns a submap containing elements whose keys are greater than or equal to 
`fromKey`;
- `SortedMap<K, V> subMap(K fromKey, E toKey)` returns a submap containing elements whose keys are in range `fromKey
` (inclusive) `toKey` (exclusive);

```java
SortedMap<LocalDate, String> events = new TreeMap<>();

events.put(LocalDate.of(2017, 6, 6), "The Java Conference");
events.put(LocalDate.of(2017, 6, 7), "Another Java Conference");
events.put(LocalDate.of(2017, 6, 8), "Discussion: career or education?");
events.put(LocalDate.of(2017, 6, 9), "The modern art");
events.put(LocalDate.of(2017, 6, 10), "Coffee master class");

LocalDate fromInclusive = LocalDate.of(2017, 6, 8);
LocalDate toExclusive = LocalDate.of(2017, 6, 10);

System.out.println(events.subMap(fromInclusive, toExclusive));

// {2017-06-08=Discussion: career or education?, 2017-06-09=The modern art}
```

## Iterating

- It is impossible to directly iterate over a map since it does not implement the `Iterable` interface
- Some methods return other collections which are iterable

```java
Map<String, String> friendPhones = Map.of(
        "Bob", "+1-202-555-0118",
        "James", "+1-202-555-0220",
        "Katy", "+1-202-555-0175"
);

// printing names
for (String name : friendPhones.keySet()) {
    System.out.println(name);
}

// printing phones
for (String phone : friendPhones.values()) {
    System.out.println(phone);
}

for (var entry : friendPhones.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}

friendPhones.forEach((name, phone) -> System.out.println(name + ": " + phone));
```

## Collections of Collections

```java
Map<String, Set<String>> synonyms = new HashMap<>();

synonyms.put("Do", Set.of("Execute"));
synonyms.put("Make", Set.of("Set", "Attach", "Assign"));
synonyms.put("Keep", Set.of("Hold", "Retain"));

// {Keep=[Hold, Retain], Make=[Attach, Assign, Set], Do=[Execute]}
System.out.println(synonyms);
```

## Equality

- Two maps are considered equal if they contain the same keys and values.
- Types of maps are not important.

```java
Map<String, Integer> namesToAges1 = Map.of("John", 30, "Alice", 28);
Map<String, Integer> namesToAges2 = new HashMap<>();

namesToAges2.put("Alice", 28);
namesToAges2.put("John", 30);

System.out.println(Objects.equals(namesToAges1, namesToAges2)); // true
```