# Static members

All objects of the class has the same fields and methods, but all the values of the fields of objects are usually different. A class may also have fields and methods which are common for all objects. Such fields and methods are known as **static members**. Use the keyword static to declare them.

## Class variables

A class variable (static field) is a field declared with the keyword static. It can have any primitive or reference type, just like a regular instance field. A static field has the same value for all instances of the class. It belongs to the class, rather than to an instance of the class.

If we want all instances of a class to share a common value, for example, a global variable, then it's better to declare it as static. This can save memory because a single copy of a static variable is shared by all created objects.

```java
public class SomeClass {

    public static Date lastCreated;

    public SomeClass() {
        lastCreated = new Date();
    }
}
```

## Class Constants

Static fields with the keyword final are class constants.

According to the naming convention, constant fields should always be written in the upper case with the underscore (\_) to separate parts of the name.

```java
public static final long SPEED_OF_LIGHT = 299_792_458;
```

## Class methods

A class may have static methods as well as static fields. Such methods are also known as class methods. A static method can be accessed by the class name and doesn't need an object of the class.

- a static method can access only static fields, it cannot access non-static fields;
- a static method can invoke another static method, but it cannot invoke an instance method;
- a static method cannot refer to `this` keyword because there is no instance in the static context.

```java
ClassName.staticMethodName(args);
```

> Static methods are often used as utility methods that are common for the whole project. As an example, you can create a class with only static methods for performing typical math operations.

```java
public class SomeClass {

    public SomeClass() {
        invokeAnInstanceMethod(); // this is possible here
        invokeAStaticMethod();    // this is possible here too
    }

    public static void invokeAStaticMethod() {
        // it's impossible to invoke invokeAnInstanceMethod() here
    }

    public void invokeAnInstanceMethod() {
        invokeAStaticMethod();  // this is possible too
    }
}
```
