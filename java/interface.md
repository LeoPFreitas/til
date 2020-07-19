# Interface

An interface is a special kind of a class that can't be instantiated. Often (but not always) it contains only abstract methods that you can implement in the subclasses.

```java
public interface Interface {}
```

An interface can contain:

- public constants;
- abstract methods without an implementation (the keyword **`abstract`** is not required here);
- default methods with implementation since Java 8 (the keyword **`default`** is required);
- static methods with implementation (the keyword **`static`** is required)

> If the modifiers are not specified once the method is declared, its parameters will be public abstract by default.

### Important

- An interface can't contain fields (only constants), constructors and non-public abstract methods. Since Java 9 private default methods are allowed as well.
- Static and default methods should have an implementation in the interface!

```java
interface Interface {
        
    int INT_CONSTANT = 0; // static final constant
        
    void instanceMethod1(); // abstract method
        
    void instanceMethod2();
        
    static void staticMethod() {
        System.out.println("Interface: static method");
    }
        
    default void defaultMethod() {
        System.out.println("Interface: default method. It can be overridden");
    }
}
```

## Marker interfaces

- Called marker or tagged interfaces.
- Provide essential information to the JVM.
- ex: Serializable, Remote, Cloneable

## Implementing interface

- A class can inherit and interface using the keyword `implements` (even abstract)
- Non abstract class should provide implementation for all interface methods

```java
class Class implements Interface {
 
    @Override
    public void instanceMethod1() {
        System.out.println("Class: instance method1");
    }
 
    @Override
    public void instanceMethod2() {
        System.out.println("Class: instance method2");
    }
}
```

## Extending multiple interfaces

- Multiple inheritance is allowed
- An interface can extend another one

```java
interface A { }
    
interface B { }
    
interface C { }
    
class D implements A, B, C { }

interface E extends A, B, C { }
```

### Some use cases:

1. **public static <returnType> <methodName> (params...) {...}**

    Say you want an interface will have some functionality, and you would like to have 100 methods, but the interface
     allows only abstract methods so, we create a concrete class and implements all the 100 abstract methods, well
     , we created a utility class for that interface. To avoid doing it,Oracle provides the ability to implement these methods right inside of the interface 
     
2. **public default <returnType> <methodName> (params...) {...}**

    Say we have 2000 classes that implement our interface, and we would like to add a new method to our interface
    , all 2000 class now must implement our newly added method, we just "broke" our 2000 classes code!!! From Java 8 we can provide a method with initial implementation and all 2000 classes get it. We can override the method.