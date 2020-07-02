# Processing Strings

Strings are similar to arrays: in some sense, a string looks like an array of characters. Sometimes you may need to process the string and convert it to an array.

## Strings and Arrays

- It's possible to convert between strings and characters arrays using special method like valueOf() or toCharArray()

```java
char[] chars = { 'A', 'B', 'C', 'D', 'E', 'F' };

String stringFromChars = String.valueOf(chars); // "ABCDEF"

char[] charsFromString = stringFromChars.toCharArray(); // { 'A', 'B', 'C', 'D', 'E', 'F' }

String theSameString = new String(charsFromString); // "ABCDEF"
```

## Splitting the string

- A string can be separated by delimiters to an array of strings.

```java
String text = "Hello";
String[] parts = text.split(""); // {"H", "e", "l", "l", "o"}
```

## Iterating over a string

- It's possible to iterate over characters of a string using a loop (while, do-while, for-loop).

```java
String scientistName = "Isaac Newton";

for (int i = 0; i < scientistName.length(); i++) {
    System.out.print(scientistName.charAt(i) + " "); // print the current character
}

// I s a a c   N e w t o n
```
