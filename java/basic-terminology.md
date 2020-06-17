# Java basic terminology

## The basic terminology

- **Program** – a sequence of instructions (called statements), which are executed one after another in a predictable manner. Sequential flow is the most common and straightforward sequence of statements, in which statements are executed in the order that they are written – from top to bottom in a sequential manner;

- **Statement** – a single action (like print a text) terminated by semi-colon (`;`);
- **Block** – a group of zero, one or more statements enclosed by a pair of braces `{...}`; There are two such blocks in the program above.
- **Method** – a sequence of statements that represents a high-level operation (also known as subprogram or procedure).
- **Syntax** – a set of rules that define how a program needs to be written in order to be valid; Java has its own specific syntax that we will learn;
- **Keyword** – a word that has a special meaning in the programming language (`public`, `class`, and many others). These words cannot be used as variable names for your own program;
- **Identifier or name** – a word that refers to something in a program (such as a variable or a function name);
- **Comment** – a textual explanation of what the code does. Java comments start with `//`.
- **Whitespace** – \*\*\*\*all characters that are not visible (space, tab, newline, etc.).

## Hello World

1. **The public class** → It is the basic unit of a program. Every Java program must have at least one class

   ```java
   public class Main {
   	// ...
   }
   ```

2. **The main method →** To make a program runnable, we put a method named main inside a class. It is the entry point for a Java program.

   - The element **String[] args** represents a sequence of arguments passed to the program from the outside world.
   - The name of this method (main) is predefined and should always be the same.

   ```java
   public static void main(String[] args) {
       // statements go here
   }
   ```
