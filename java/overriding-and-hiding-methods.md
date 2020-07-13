# Hiding and overriding

Java provides an opportunity to declare a method in a subclass with the same name as a method in the superclass. It's known as **method overriding**. The benefit of overriding is that a subclass can give its own specific implementation of a superclass method.

**Overriding methods** in subclasses allows a class to inherit from a superclass whose behavior is **"close enough"** and then to change this behavior as the subclass needs.

Instance methods can be overridden if they are inherited by the subclass. The overriding method must have the same name, parameters (number and type of parameters), and the return type (or a subclass of the type) as the overridden method.

```java
class Mammal {
 
    public String sayHello() {
        return "lalala";
    }
}
 
class Cat extends Mammal {
 
    @Override
    public String sayHello() {
        return "meow";
    }
}
 
class Human extends Mammal {
 
    @Override
    public String sayHello() {
        return "hello";
    }
}

Cat cat = new Cat();
System.out.println(cat.sayHello()); // it prints "meow"
 
Human human = new Human();
System.out.println(human.sayHello()); // it prints "hello"
```

## Rules

- the method must have the same name as in the superclass;
- the arguments should be exactly the same as in the superclass method;
- the return type should be the same type or a subtype of the return type declared in the method of the superclass;
- the access level must be the same or more open than the overridden method's access level;
- a private method cannot be overridden because it's not inherited by subclasses;
- if the superclass and its subclass are in the same package, then package-private methods can be overridden;
- static methods cannot be overridden.

## Forbidding overriding

- Use final methods
- Trying to override this method in a subclass will generate a compile-time error

```java
public final void noOverriding() { /* code */ }
```

## Hiding static methods

- Static methods cannot be overridden.
- Overriding is different from overloading → If a subclass has a static method with the same signature as an instance method in the superclass or vice versa. But if the methods have the same name but different parameters there should be no problems.