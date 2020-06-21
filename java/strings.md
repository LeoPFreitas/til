# Strings

## Introduction

- **immutable type**: it's impossible to change a character in a string;
- it has methods for getting individual characters and extracting substrings;
- individual characters can be accessed by indexes, the first character has the index **0**, the last one – **the length of the string** – **1**;
- non-primitive type.

### Create a String

```jsx
// a simple string
String simpleString = "It is a simple string";

// it creates an object and assigns it to the variable
String str = new String("my-string");
```

### Get the length and characters of a string

- `length()` returns the number of characters in the string;
- `charAt(int index)` returns a character by its index;

### Useful methods of Strings

- `isEmpty()` returns `true` if the string is empty, otherwise – `false`;
- `toUpperCase()` returns a new string in uppercase;
- `toLowerCase()` returns a new string in lowercase;
- `startsWith(prefix)` returns `true` if the string starts with the given string prefix, otherwise, `false`;
- `endsWith(suffix)` returns `true` if the string ends with the given string suffix, otherwise, `false`.
- `contains(...)` returns `true` if the string contains the given string or character;
- `substring(beginIndex, endIndex)` returns a substring of the string in the range: `beginIndex`, `endIndex - 1`;
- `replace(old, new)` returns a new string obtained by replacing all occurrences of `old` with `new` that can be chars or strings.
- `trim()` returns a copy of the string obtained by omitting the leading and trailing whitespace. Note that whitespace includes not only space character, but mostly everything that looks empty: tab, carriage return, newline character, etc.

### Exceptions when processing strings

1. NullPointerException. If a string is null and you call a method of the string, it throws NullPointerException.

```jsx
String s = null;
int length = s.length(); // it throws NullPointerException
```

2. StringIndexOutOfBoundsException. If you try to access a non-existing character by an index then this exception occurs.

```jsx
String s = "ab";
char c = s.charAt(2); // it throws StringIndexOutOfBoundsException because indexing starts with 0
```

### Concatenating Strings

- When we concatenate two strings a new string is created (strings are immutable).

```jsx
String firstName = "John";
String lastName = "Smith";

// concatenation using the "+" operator
String fullName1 = firstName + " " + lastName; // "John Smith"

// concatenation using the concat method
String fullName2 = firstName.concat(" ").concat(lastName); // "John Smith"
```

### Appending

It's possible to add values of different types to a string. The value will be automatically converted to a string. See an example below.

```jsx
String str = "str" + 10 + false; // the result is "str10false"
```

- The order of operations is important.

```jsx
String shortString = "str";
long number = 100;

String result1 = shortString + number + 50; // str10050
String result2 = number + 50 + shortString; // 150str
```

### compare strings

Since String is a reference type you shouldn't compare strings using == or != operators. In this case, only addresses will be compared, but not actual values.

String has two convenient methods for comparing the equivalence of the actual content of one string with the content of another string: equals(other) and equalsIgnoreCase(other).

```jsx
String first = "first";
String second = "second";

String anotherFirst = "first";
String secondInUpperCase = "SECOND";

System.out.println(first.equals(second)); // false, the strings have different values
System.out.println(first.equals(anotherFirst)); // true, the strings have the same value

System.out.println(second.equals(secondInUpperCase)); // false, the strings have different cases
System.out.println(second.equalsIgnoreCase(secondInUpperCase)); // true, it ignores cases
```
