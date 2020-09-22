# Managing files

- `java.io.file` represent an abstract path to a file or a directory that may not even exist.
- We are able to manage files and directories by creating, deleting and renaming them.

### Creating files

To create a file in the file system, we'll have to do the following:

1. Create an instance of `java.io.File` with the specified abstract path.
2. Invoke the `createNewFile` method of this instance → returns true id the file was successfully created and false if
 it already exists

```java
File file = new File("/home/username/Documents/file.txt");
try {
    boolean createdNew = file.createNewFile();
    if (createdNew) {
        System.out.println("The file was successfully created.");
    } else {
        System.out.println("The file already exists.");
    }
} catch (IOException e) {
    System.out.println("Cannot create the file: " + file.getPath());
}
```

### Creating directories

To create a directory we also need to start by creating an instance of `java.io.File`. After that, we should call one
 of the two methods of this instance:

- `boolean **mkdir**` creates the directory; it returns `true` only if the directory was created, otherwise, it returns 
`false`.
- `boolean **mkdirs**` creates the directory including all necessary non-existing parent directories; it returns `true
` only if the directory was created along with all of 
the specified parent directories.

```java
File file = new File("/home/art/Documents/dir");

boolean createdNewDirectory = file.mkdir();
if (createdNewDirectory) {
    System.out.println("It was successfully created.");
} else {
    System.out.println("It was not created.");
}
```

### Removing files and dirs

- Method `delete` → used to remove a file or a directory. Return `true` if and only if the file or directory is successfully deleted, otherwise, returns `false`
- It is important to remember that it also returns false if the directory contains subdirectories or files.

```java
File file = new File("/home/art/Documents/dir/dir/dir");
        
if (file.delete()) {
    System.out.println("It was successfully removed.");
} else {
    System.out.println("It was not removed.");
}

// assumes that dir exists, otherwise -> NPE
public void deleteDirRecursively(File dir) {
    File[] children = dir.listFiles();
    for (File child : children) {
        if (child.isDirectory()) {
            deleteDirRecursively(child);
        } else {
            child.delete();
        }
    }

    dir.delete();
}
```

### Renaming and moving files and dirs

- `renameTo` → changes the name of the file by editing in the abstract path. Returns `true` if and only if the renaming succeeded.

```java
File file = new File("/home/art/Documents/dir/filename.txt");
boolean renamed = file.renameTo(new File("/home/art/Documents/dir/newname.txt"));

File file = new File("/home/art/Documents/dir/file.txt");
boolean renamed = file.renameTo(new File("/home/art/Documents/another/file.txt"));
```

```java
// Throws NPE in case when a destination file is null
File file = new File("/home/art/Documents/dir/filename.txt");
File renamedFile = new File("/home/art/Documents/dir/newname.txt");

boolean renamed = file.renameTo(renamedFile);
if (renamed) {
    System.out.println("It was successfully renamed.");
} else {
    System.out.println("It was not renamed.");
}
```