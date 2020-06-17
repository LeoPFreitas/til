# Types and variables

## Introduction

A variable is a placeholder for storing a value of a particular type: a string, a number, or something else. Every variable has a name (identifier) to distinguish it from others.

```java
DataType variableName = initialization;
```

Variables can be changed. You don't need to declare a variable again to change its value. You can only assign a value of the same type as the type of the initial variable.\

```java
int number = 10;
number = 11; // ok
number = "twelve"; // it does not work!
```

## Type inference

Since Java 11, you can write var instead of a specific type to force automatic type inference based on the type of assigned value:

```java
var variableName = initialization;
```

```java
var language = "Java"; // String
var version = 11; // int
```

## Theory: Sizes and ranges

### Integer numbers

- `byte`: size 8 bits (1 byte)
- `short`: size 16 bits (2 bytes)
- `int`: size 32 bits (4 bytes)
- `long`: size 64 bits (8 bytes)

### Floating-point types

- Represent numbers with fractional parts.
- These types can store only a limited number of significant decimal digits (~6-7 for float and ~14-16 for double).

### Characters

- Java has a type named char to represent letters (uppercase and lowercase), digits, and other symbols.
- Each character is just a single letter enclosed in single quotes.
- This type has the same size as the short type (2 bytes = 16 bits).

### Booleans

- Java provides a type called boolean, which can store only two values: true and false
