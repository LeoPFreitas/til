# Singleton

It is an especial design pattern that restrict the instantiation of a class to one object. Singleton ensures that
 there is only one instance of the class and provide global access to it for the outer world.

- Often control access to resources such as databases connections or sockets

## Basic Singleton

- A private constructor to defeat the creation of instances using the keyword `new`;
- A private static variable of the class that is the only instance of the class;
- A public static method to return the same instance of the class; this is a global access point to the instance.

```java
class Singleton {
 
    private static Singleton instance = new Singleton();
 
    private Singleton() { }
 
    public static Singleton getInstance() {
        return instance;
    }
}

Singleton s1 = Singleton.getInstance();
Singleton s2 = Singleton.getInstance();
Singleton s3 = Singleton.getInstance();
        
System.out.println(s1 == s2); // true because s1 and s2 refer the same object
System.out.println(s2 == s3); // true because s2 and s3 refer the same object
```

## Lazy initialization

- Loads the instance only if it is needed to a client → avoid expensive useless initialization
- Use it only in one-thread environments because it is prone to multithreading issues.

```java
class Singleton {
    
    private static Singleton instance;
    
    private Singleton () { }
 
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```