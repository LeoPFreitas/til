# Increment and decrement

## Introduction

- **prefix** (`++n` or `--n`) increases/decreases the value of a variable before it is used;
- **postfix** (`n++` or `n--`) increases/decreases the value of a variable after it is used.

### Prefix increment

```java
int a = 4;
int b = ++a;

System.out.println(a); // 5
System.out.println(b); // 5
```

### Postfix increment

```java
int a = 4;
int b = a++;

System.out.println(a); // 5
System.out.println(b); // 4

int a = 4;
System.out.println(a++ + a); // this is 9
```
