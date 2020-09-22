# Reflection basics

- It is the process of accessing and modifying the application at runtime (classes and its members such as constructors, fields and methods in runtime).

### Package java.lang.reflect

The four principal classes

- **`Field`**: you can use it to get and modify name, value, datatype and access modifier of a variable.
- **`Method`**: you can use it to get and modify name, return type, parameter types, access modifier, and exception type of a method.
- **`Constructor`**: you can use it to get and modify name, parameter types and access modifier of a constructor.
- **`Modifier`**: you can use it to get information about a particular access modifier.

### java.lang.Class

Reflection is achieved with the Reflect package. This package gives information about a field, method or constructor of a class. This is possible with `java.lang.Class` class and its static `forName()` method.

Here are some of java.lang.Class methods:

- `forName(String ClassName)`
- `getConstructors()`
- `getDeclaredConstructors()`
- `getFields()`
- `getDeclaredFields()`
- `getMethods()`
- `getDeclaredMethods()`

## Code example

```java
public class Student {
    public String firstName;
    public String lastName;
    public int age;
    protected String phoneNumber;
    private String accountNumber;
    
    Student(){
        System.out.println("This is default Constructor");
    }
    
    public Student(String firstName, String lastName){
        this.firstName= firstName;
        this.lastName= lastName;
        System.out.println("This is public Constructor");
    }
    
    private String sanitizeAccountNumber(String accountNumber){
        System.out.println("This is a private method to sanitize account number");
        //code to sanitize accountNumber goes here. 
        return accountNumber;
    }
    
    public void setAccountNumber(String accountNumber){
        accountNumber = sanitizeAccountNumber(accountNumber);
        this.accountNumber = accountNumber;
    }
}
```

### Reflection process

1. Get a java.lang.Class object of the class using the forName() method. In this case, the class we want to reflect is Student.

    ```java
    Class student = Class.forName("Student");
    ```

2. Get the class attributes as an array. In this case, we are interested in fields, constructors, and methods.

    ```java
    Constructor[] declaredConstructors = student.getDeclaredConstructors();
    Constructor[] constructors = student.getConstructors();
    Field[] declaredFields = student.getDeclaredFields();
    Field[] fields = student.getFields();
    Method[] declaredMethods = student.getDeclaredMethods();
    Method[] methods = student.getMethods();
    ```

3. Get the information about class attributes and use it. In this case, we are going to retrieve names of constructors, fields, and methods and print them.

    ```java
    for(Constructor dc : declaredConstructors) {
        System.out.println("Declared Constructor " + dc.getName());
    }
    for (Constructor c : constructors) {
        System.out.println("Constructor " + c.getName());
    }
    for (Field df : declaredFields) {
        System.out.println("Declared Field " + df.getName());
    }
    for (Field f : fields) {
        System.out.println("Field " + f.getName());
    }
    for (Method dm : declaredMethods) {
        System.out.println("Declared Method " + dm.getName());
    }
    for (Method m : methods) {
        System.out.println("Method " + m.getName());
    }
    ```

    ## Summary

    **Reflection** is a way to get information about or modify fields, methods, and constructors of a class. `java
    .lang.reflect` package and `java.lang.Class` class are essential in Java reflection.

    There are three steps in the Java reflection process:

    - Get the Class object of the class that you want to reflect on.
    - Get the attributes of the class you want to reflect on as a list or array using `java.lang.Class` methods.
    - Get information about the particular attribute you got in the second step using the `java.lang.reflect` package.