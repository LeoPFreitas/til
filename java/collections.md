# Collections

- Collections are more sophisticated and flexible than arrays
- Resizable
- Provide a rich set of methods that are already implemented for you.

## features of collections

There are several specific features of collections in Java:

1. They are represented by different classes from the Java Standard Library.
2. All modern collections are **generic types** while old collections are **non-generic**. We will only focus on new
 collections. As regular generics, they can store any reference types including classes defined by you (like `Person
 ` or something else).
3. Collections can be **mutable** (possible to add and remove elements) and **immutable** (impossible to do that).

### Example

**ArrayList** → It works in a similar way to a regular array, but you do not have to manually resize it to add and remove elements.

```java
ArrayList<String> list = new ArrayList<>();

list.add("first");
list.add("second");
list.add("third");

System.out.println(list); // [first, second, third]

System.out.println(list.get(0)); // first
System.out.println(list.get(1)); // second
System.out.println(list.get(2)); // third

list.remove("first");

System.out.println(list); // [second, third]

System.out.println(list.size()); // 2
```