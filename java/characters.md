# Characters

## Initializing characters with codes

A character can be also created using its hexadecimal code in the Unicode table.

```java
char ch = '\u0040'; // it represents '@'
System.out.println(ch); // @
```

## Retrieving subsequent characters

```java
char ch = 'A';
ch += 10;
System.out.println(ch);   // 'K'
System.out.println(++ch); // 'L'
System.out.println(++ch); // 'M'
System.out.println(--ch); // 'L'
```

## Escape sequences

- `'\n'` is the newline character;
- `'\t'` is the tab character;
- `'\r'` is the carriage return character;
- `'\\'` is the backslash character itself;
- `'\''` is the single quote mark;
- `'\"'` is the double quote mark.
