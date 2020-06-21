# Inputs

## Introduction

The standard input is a stream of data going into a program. It is supported by the operating system.

## Reading data with a scanner

The simplest way to obtain data from the standard input is to use the standard class Scanner. It allows a program to read values of different types (string, numbers, etc) from the standard input.

In order to use the Scanner class, we need to import it. After that, create an object of Scanner class that enables us to use its methods.

```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);
```

### next()

There are two ways to read strings with a Scanner class. If the input is an integer number or a single word, we can read the data using next() method.

- next() method reads one word only and doesn't include any whitespace

```java
String name = scanner.next();

System.out.println("Hello, " + name +"!");
```

### nextLine()

- nextLine() method includes all space characters it encounters.
- The more correct term to refer to what we’ve called “word” is token: it is a piece of text surrounded by whitespace.

> next() method finds and returns the next token, while nextLine() reads all data till the end of the current line.

## Reading multiline input

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String word1 = scanner.next(); // "This"
        String line1 = scanner.nextLine(); // " is a simple"
        String word2 = scanner.next(); // "multiline"
        String word3 = scanner.next(); // "input,"
        String line2 = scanner.nextLine(); // ""

    }
}
```
