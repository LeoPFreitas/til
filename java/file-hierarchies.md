# File hierarchies

It is possible to iterate through a file hierarchy in Java programs by using the `java.io.File` class.

- `File **getParentFile()**` returns an instance of `java.io.File` representing the parent directory of this file, or 
`null` if this file does not have the parent (it means it is the root);
- `String **getParent()**` returns a string representation of the parent directory of this file, or `null` if this file
 does not have a parent;
- `File[] **listFiles()**` returns an array of files that are located in this directory, or `null` if this instance is
 not a directory;
- `String[] **list()**` returns an array of strings naming the files and directories in the directory denoted by this
 abstract pathname.