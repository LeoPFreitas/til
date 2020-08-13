# NPE

- NPE when invoking a method

    ```java
    String someString = null; // a reference type can be null

    int size = someString.length(); // NullPointerException (NPE)

    int size = str != null ? str.length() : 0; // if the string is empty, the size is 0
    ```

- Comparing strings

    ```java
    String str = null;
    String s1 = null;
    String s2 = null;

    if (str.equals("abc")) { // it throws NPE
        System.out.println("The same");
    }

    if ("abc".equals(str)) { // no NPE here
        System.out.println("The same");
    }

    if (Objects.equals(s1, s2)) { // no NPE here
        System.out.println("Strings are the same");
    }
    ```

### Rules for avoiding NPE

- for reference types, use a condition statement to check whether the given variable is `null` before using it;
- try to avoid assigning `null` to variables whenever possible;
- use NPE-safe features from the standard library.