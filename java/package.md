# Package

## Grouping classes together

Advantages:

- Group related classes together, which makes it easier to figure out where a certain class is;
- Avoid the conflict of class names;
- Control access to classes and members together with access modifiers (you'll learn about this in another topic).

Classes declared inside a package have a special keyword package at the top of the file.

```java
package org.company.webapp.data;

public class User {
}
```

## Importing classes

If two classes are located in the same package using one class inside the other is no problem. If it is not the case and the classes are in different packages, you need to write an import statement to use one class inside the other.

> The package declaration and import statements are optional. If both of them are present, the package must come before all imports! Otherwise, we get compile-error.

```java
package org.hyperskill.java.packages.theory.p1;  // current package

import org.hyperskill.java.packages.theory.p2.B; // it's required to make the import

public class A {

    public static void method() {

        B b = new B();
    }
}
```

There is a way to use a class from another package without the import statement. In this case, you should write the full class name (including full packages path) instead of the name of the class itself (short name). This is how we would use the Scanner without explicitly importing it first:

```java
java.util.Scanner scanner = new java.util.Scanner(System.in);
java.util.Date now = new java.util.Date();
```
