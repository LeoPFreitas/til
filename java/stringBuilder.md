# StringBuilder

- Strings in Java are immutable objects → once created string cannot be changed
- StringBuilder class is used to create mutable string objects

```java
StringBuilder sb = new StringBuilder("Hello!");
System.out.println(sb); // "Hello!"
```

## Methods

- `int length()` → returns the length (characters count) like for a regular string
- `char charAt(int index)` returns a character located at the specified index. The first character has the index 0. This method does not modify the object.
- `void **setCharAt**(int index, char ch)`sets a character located at the specified index to **ch**.
- `StringBuilder deleteCharAt(int index)` removes a character at the specified position.
- `StringBuilder append(String str)` concatenates the given string to the end of the invoking StringBuilder object. There are also several overloading to take primitive types and, even, arrays of characters.
- `StringBuilder insert(int offset, String str)` inserts the given string into the existing StringBuilder object at the given position, indicated by the offset. The method has a lot of overloadings for different types.
- `StringBuilder replace(int start, int end, String str)` replaces the substring from specified string index (inclusive) to the end index (exclusive) with a given string.
- `StringBuilder delete(int start, int end)` removes the substring from the start index (inclusive) to the end index (exclusive).
- `StringBuilder reverse()` causes this character sequence to be replaced by the reverse of the sequence.