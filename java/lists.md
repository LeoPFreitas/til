# Lists

- Ordered collections of elements → each element has a position in the list specified by an integer index in regular arrays

The `List<E>` interface represents a list as an abstract data type. It extends the `Collection<E>` interface
 acquiring its methods and adds some new methods:

- `E set(int index, E element)` replaces the element at the specified position in this list with the specified
 element and returns the element that was replaced;
- `E get(int index)` returns the element at the specified position in the list;
- `int indexOf(Object obj)` returns the index of the first occurrence of the element in the list or `1` if there is
 no such index;
- `int lastIndexOf(Object obj)` returns the index of the last occurrence of the element in the list or `1` if there
 is no such index;
- `List<E> subList(int fromIndex, int toIndex)` returns a sublist of this list from `fromIndex` included to`toIndex
` excluded.

### Important

- You cannot create an instance of the List interface, but you can create an instance of one of its implementations: ArrayList or LinkedList or an immutable list, and then use it through the common List interface.
- You will have access to all methods declared in both List<E> and Collection<E> interfaces.
- Working with lists through the List interface is considered good practice in programming since your code will not depend on the internal mechanisms of a specific implementation.

## Immutable lists

- It returns an immutable list containing either all the passed elements or an empty list. Using this method is convenient when creating list constants or testing some code.

```java
List<String> emptyList = List.of(); // 0 elements
List<String> names = List.of("Larry", "Kenny", "Sabrina"); // 3 elements
List<Integer> numbers = List.of(0, 1, 1, 2, 3, 5, 8, 13);  // 8 elements

List<String> daysOfWeek = List.of(
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
        "Sunday"
);

System.out.println(daysOfWeek.size()); // 7
System.out.println(daysOfWeek.get(1)); // Tuesday
System.out.println(daysOfWeek.indexOf("Sunday")); // 6

List<String> weekDays = daysOfWeek.subList(0, 5);
System.out.println(weekDays); // [Monday, Tuesday, Wednesday, Thursday, Friday]
```

## Mutable lists

```java
List<Integer> numbers = new ArrayList<>();

numbers.add(15);
numbers.add(10);
numbers.add(20);

System.out.println(numbers); // [15, 10, 20]

numbers.set(0, 30); // no exceptions here

System.out.println(numbers); // [30, 10, 20]

// Another mutable implementation of the List interface is the LinkedList class.
List<Integer> numbers = new LinkedList<>();
        
numbers.add(10);
numbers.add(20);
numbers.add(30);

System.out.println(numbers); // [10, 20, 30]
```

### List equality

- Two lists are equal when they contain the same elements in the same order.
- Equality does not depend on the types of the lists themselves.

```java
Objects.equals(List.of(1, 2, 3), List.of(1, 2, 3));    // true
Objects.equals(List.of(1, 2, 3), List.of(1, 3, 2));    // false
Objects.equals(List.of(1, 2, 3), List.of(1, 2, 3, 1)); // false

List<Integer> numbers = new ArrayList<>();
        
numbers.add(1);
numbers.add(2);
numbers.add(3);

Objects.equals(numbers, List.of(1, 2, 3)); // true
```