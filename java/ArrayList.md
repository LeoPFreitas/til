# ArrayList

- Represents a resizable array of objects of a specified type
- Can dynamically grow after the addition and shrink after the removal of its elements.
- Cannot store primitive types

## Create an instance

1) The simplest way is to use a no-argument constructor:

```java
ArrayList<String> list = new ArrayList<>();
```

The created list is empty, but its initial capacity is 10 (by default).

2) We can also specify the initial capacity of it:

```java
ArrayList<String> list = new ArrayList<>(50);
```

This list is empty, but its initial capacity is set to 50.

3) Or you can construct an `ArrayList` that consists of elements of another list:

```java
ArrayList<String> list = new ArrayList<>(anotherList);
```

## Basic methods

The collection has a set of convenient methods that emulate and extend the functionality of standard arrays.

- `int size()` return the number of elements of the list;
- `Object get(int index)` returns the object of the list which is present at the specified index;
- `add(Object o)` adds a passed element to the last position of the collection;
- `add(int index, Object o)` adds a passed element to the specified position of the collection;
- `set(int index, Object o)` replaces the element present at the specified index with the object;
- `remove(Object o)` removes the object from the array;
- `remove(int index)` removes element from a given index;
- `clear()` removes all elements from the collection.

```java
/* an ArrayList of Integers, not ints */
ArrayList<Integer> numbers = new ArrayList<>();

numbers.add(1);
numbers.add(2);
numbers.add(3);
numbers.add(1);

System.out.println(numbers.contains(2)); // true
System.out.println(numbers.contains(4)); // false
System.out.println(numbers.indexOf(1)); // 0
System.out.println(numbers.lastIndexOf(1)); // 3
System.out.println(numbers.lastIndexOf(4)); // -1
```