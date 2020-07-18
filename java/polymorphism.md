# Polymorphism

Java provides two types of polymorphism: static (compile-time) and dynamic (run-time) polymorphism. The first one is achieved by method overloading, the second one is based on inheritance and method overriding.

- **Ad-hoc polymorphism** refers to polymorphic functions that can be applied to arguments of different types, but behave differently depending on the type of the argument to which they are applied. Java supports it as **method overloading**.
- **Subtype polymorphism** (also known as subtyping) is a possibility to use an instance of a subclass when an instance of the base class is permitted.
- **Parametric polymorphism** is when the code is written without mention of any specific type and thus can be used transparently with any number of new types. Java supports it as **generics** or **generic programming**.

## Runtime polymorphic behavior

- Method overriding is when a subclass redefines a method of the superclass with the same name

### The run-time polymorphism relies on two principles:

- a reference variable of the superclass can refer to any subtype object;
- a superclass method can be overridden in a subclass.

Run-time polymorphism works when an overridden method is called through the reference variable of a superclass. Java determines at runtime which version of the method (superclass/subclasses) is to be executed based on the type of the object being referred, not the type of reference. It uses a mechanism known as dynamic method dispatching.

Subtype polymorphism allows a class to specify methods that will be common to all of its subclasses while allowing subclasses to define the specific implementations of some or all of those methods.

```java
class MythicalAnimal {    
 
    public void hello() {
        System.out.println("Hello, I'm an unknown animal");
    }
}
 
class Chimera extends MythicalAnimal {
 
    public void hello() {
        System.out.println("Hello! Hello!");
    }
}
 
class Dragon extends MythicalAnimal {
 
    public void hello() {
        System.out.println("Rrrr...");
    }
}

MythicalAnimal chimera = new Chimera();
MythicalAnimal dragon = new Dragon();
MythicalAnimal animal = new MythicalAnimal();

chimera.hello(); // Hello! Hello!
dragon.hello(); // Rrrr...
animal.hello(); // Hello, i'm an unknown animal
```

> The result of a method call depends on the actual type of instance, not the reference type. It's a polymorphic feature in Java. The JVM calls the appropriate method for the object that is referred to in each variable.

## Polymorphism within a class hierarchy

```java
class File {
 
    protected String fullName;
 
    // constructor with a single parameter
 
    // getters and setters
 
    public void printFileInfo() {
        String info = this.getFileInfo(); // here is polymorphic behavior!!!
        System.out.println(info);
    }
 
    protected String getFileInfo() {
        return "File: " + fullName;
    }
}
 
class ImageFile extends File {
 
    protected int width;
    protected int height;
    protected byte[] content;
 
    // constructor
 
    // getters and setters
 
    @Override
    protected String getFileInfo() {
        return String.format("Image: %s, width: %d, height: %d", fullName, width, height); 
    }
}
```