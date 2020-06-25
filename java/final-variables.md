# Introduction

Java provides a special keyword called final to declare a constant variable. The only difference between a regular variable and a final variable is that we cannot modify the value of a final variable once assigned

## Final variables

```java
final double PI = 3.1415;
final String HELLO_MSG = "Hello";

System.out.println(PI); // 3.1415
System.out.println(HELLO_MSG); // Hello
```

> A good practice is to represent a final variable in all caps using an underscore to separate words. It allows you to distinguish them from regular variables. But sometimes you will also see final variables, written in lowercase: this is also admissible for local final variables

Notice that the value of a final variable can be reassigned to a regular variable without any restrictions:

```java
final int count = 10;
int cnt = count;
cnt = 20; // no errors here, cnt is not final
```

## Final reference variables

The final keyword can be legally used with reference variables. In this case, the final keyword means that it is not possible to reassign a reference to the variable.

```java
final StringBuilder builder = new StringBuilder();
builder = new StringBuilder(); // error line
```

> Important, that it is always possible to change the internal state of an object point by a final reference object, i.e. the constant is only the variable itself (the reference), not the object to which it refers.

```java
final StringBuilder builder = new StringBuilder(); // ""
builder.append("Hello!"); // it works
System.out.println(builder.toString()); // Hello!
```

## When to use final variables

Some programmers mark all variables that they do not want to modify as final. In this case, the program will contain a lot of such variables.

This approach allows you to write programs with the minimum number of mutable variables which usually leads to fewer errors. In addition, the Java compiler can optimize code with final variables effectively and your program can be a little faster.
