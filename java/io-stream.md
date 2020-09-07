# IO streams

- Java provides an abstraction called stream that unifies work with disks, files, network locations and other resources

Streams can be further classified into two based on how they represent sequences of data:

- **byte streams** that are used to read and write data in bytes;
- **char streams** that are used to read and write data in characters according to the 16-bit Unicode format.

## Output Streams

- Character output streams allow writing text data: `char` or `String`.

### Character Streams

The class `java.io.Writer` contains a group of methods for writing. Some of them are listed here:

- `void write(char[] cbuf)` writes a char array
- `void write(char[] cbuf, int off, int len)` writes a portion of a char array
- `void write(int c)` writes a single character
- `void write(String str)` writes a string
- `void write(String str, int off, int len)` writes a portion of a string

> Try-with-resources construction is a better way to prevent resource leaks (alternative to `close()` )

```jsx
CharArrayWriter contactWriter = new CharArrayWriter();
FileWriter bc1 = new FileWriter("business_card_1.txt", true);
FileWriter bc2 = new FileWriter("business_card_2.txt", true);

contactWriter.write("Phone: 111-222-333; Address: Java Avenue, 7");
contactWriter.writeTo(bc1);
contactWriter.writeTo(bc2);

char[] array = contactWriter.toCharArray(); // writer content as char[]

bc1.close();
bc2.close();
contactWriter.close();
```

### Byte streams

Byte output stream classes from the standard library extend `java.io.OutputStream` abstract class. The class contains
 three methods for writing:

- `void write(byte[] b)` writes a byte array
- `void write(byte[] b, int off, int len)` writes a portion of a byte array
- `abstract void write(int b)` writes a single byte

```java
byte[] data = new byte[] {'s', 't', 'r', 'e', 'a', 'm'};
OutputStream outputStream = new FileOutputStream("sample.txt", false);
outputStream.write(data);
outputStream.close();
```

### Buffered streams

- Intermediate output stream
- Take an output stream as an input and do buffering before delegating to another stream
- Buffering minimizes a number of interactions with source or destination

Output streams have 2 classes from the standard library which do buffering.

`BufferedOutputStream` is based on the buffering principle. It has only two constructors:

- `BufferedOutputStream(OutputStream out)`
- `BufferedOutputStream(OutputStream out, int size)`

Same works for `BufferedWriter`:

- `BufferedWriter(Writer out)`
- `BufferedWriter(Writer out, int size)`

## Input streams

- The class name indicates what type of source it uses as input and usually ends with Reader, since all such classes extend `java.io.Reader` class.

Each class provides a set of useful methods while they also have common methods for reading data:

- `int read()` reads a single character. If end of stream is reached, the method returns `1` value. Otherwise, it
 returns the numerical representation of character according to encoding;
- `int read(char[] cbuf)` reads a sequence of characters into passed array up to its capacity and returns a number of
 characters that were actually read. It can also return `1` in case of no data was read;
- `int read(char[] cbuf, int off, int len)` reads characters into a portion of array.

```java
Reader reader = new FileReader("file.txt");

char first = (char) reader.read(); // i
char second = (char) reader.read(); // n

char[] others = new char[12];
int number = reader.read(others); // 10
```

```java
// When -1 is returned, it means the end of stream was reached, 
// that is there's nothing left to read.
FileReader reader = new FileReader("file.txt");

int charAsNumber = reader.read();
while(charAsNumber != -1) {
    char character = (char) charAsNumber;
    System.out.print(character);
    charAsNumber = reader.read();
}
reader.close();
```

### Byte stream

All byte stream classes have methods for reading similar to character input streams:

- `abstract int read()` reads a single byte
- `int read(byte[] b)` reads some number of bytes and stores them in byte array
- `byte[] readAllBytes()` reads all bytes

Suppose we have `file.txt` that contains text: input stream.

```java
FileInputStream inputStream = new FileInputStream("myfile.txt");

byte[] bytes = new byte[5];
int numberOfBytes = inputStream.read(bytes);
System.out.println(numberOfBytes); // 5
inputStream.close();

// Now bytes contains ['i', 'n', 'p', 'u', 't']
```