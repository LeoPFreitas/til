# Files

## Create a file

```java
File fileOnUnix = new File("./images/picture.jpg");
```

## Basic methods

An instance of `File` would have a list of methods. Take a look at some of them:

- `String **getPath()**` returns the string path to this file or directory;
- `String **getName()**` returns the name of this file or directory (just the last name of the path)
- `boolean **isDirectory()**` returns `true` if it is a directory and exists, otherwise, `false`;
- `boolean **isFile()**` returns `true` if it is a file that exists (not a directory), otherwise, `false`;
- `boolean **exists()**` returns `true` if this file or directory actually exists in your file system, otherwise, `false`;
- `String **getParent()**` returns the string path to the parent directory that contains this file or directory.

There is also a group of methods canRead(), canWrite(), canExecute() to test whether the application can read/modify/execute the file denoted by the path. 

## Reading using Scanner

- After using a scanner, we should close the object to avoid leaks.
- A convenient way to close scanners and handle exceptions is to use the try-with-resources statement

```java
File file = new File(pathToFile);
 
try (Scanner scanner = new Scanner(file)) {
    while (scanner.hasNext()) {
        System.out.print(scanner.nextLine() + " ");
    }
} catch (FileNotFoundException e) {
    System.out.println("No file found: " + pathToFile);
}
```

### Single string

- Only for small text files (size is smaller than JVM available RAM)

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Paths;
 
public class ReadingFileDemo {
    public static String readFileAsString(String fileName) throws IOException {
        return new String(Files.readAllBytes(Paths.get(fileName)));
    }
 
    public static void main(String[] args) {
        String pathToHelloWorldJava = "path/HelloWorld.java";
        try {
            System.out.println(readFileAsString(pathToHelloWorldJava));
        } catch (IOException e) {
            System.out.println("Cannot read file: " + e.getMessage());
        }
    }
}
```

## FileWriter class

The class `FileWriter` has a set of constructors to write characters and string to a specified file:

- `FileWriter(String fileName)`;
- `FileWriter(String fileName, boolean append)`;
- `FileWriter(File file)`;
- `FileWriter(File file, boolean append)`;

All these constructors can throw an `IOException` for several reasons:

- if the named file exists, but it is a directory;
- if a file does not exist and cannot be created;
- if a file exists but cannot be opened.

```java
// If the specified file does not exist, it will be created after executing this code. 
// If the file already exists, this code overwrites the data.
File file = new File("/home/username/path/to/your/file.txt");
FileWriter writer = new FileWriter(file); // overwrites the file
 
writer.write("Hello");
writer.write("Java");
 
writer.close();

// append some new data
File file = new File("/home/username/path/to/your/file.txt");
FileWriter writer = new FileWriter(file, true); // appends text to the file
 
writer.write("Hello, World\n");
writer.close();
```

### Closing a FileWriter

- It is important to close a FileWriter after using to avoid the resource leak

```java
writer.close();
```

It will close the writer automatically.

```java
File file = new File("/home/username/path/to/your/file.txt");
 
try (FileWriter writer = new FileWriter(file)) {
    writer.write("Hello, World");
} catch (IOException e) {
    System.out.printf("An exception occurs %s", e.getMessage());
}
```

### PrintWriter

- Write formatted data to a file.
- It can output strings, primitive types and even an array of characters. The class provides several overloaded methods: print, println and printf.

```java
File file = new File("/home/art/Documents/file.txt");
try (PrintWriter printWriter = new PrintWriter(file)) {
    printWriter.print("Hello"); // prints a string
    printWriter.println("Java"); // prints a string and then terminates the line
    printWriter.println(123); // prints a number
    printWriter.printf("You have %d %s", 400, "gold coins"); // prints a formatted string
} catch (IOException e) {
    System.out.printf("An exception occurs %s", e.getMessage());
}
```

The class has several constructors. Some of them are similar to FileWriter's constructors:

- `PrintWriter(String fileName)`;
- `PrintWriter(File file)`;

Others allow passing `FileWriter` as a class that extends `Writer` abstract class:

- `PrintWriter(Writer writer)`;