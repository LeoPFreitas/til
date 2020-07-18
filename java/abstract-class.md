# Abstract class

An **abstract class** is a class declared with the keyword **`abstract`**. It represents an abstract concept that is used as a base class for subclasses.

Abstract classes have some special features:

- it's impossible to create an instance of an abstract class;
- an abstract class can contain abstract methods that must be implemented in non-abstract subclasses;
- it can contain fields and non-abstract methods (including static);
- an abstract class can extend another class, including abstract;
- it can contain a constructor.

> Abstract class has two main differences from regular (concrete) classes: no instances and abstract methods.

**Abstract methods** are declared by adding the keyword abstract. They have a declaration (modifiers, a return type, and a signature) but don't have an implementation. Each concrete (non-abstract) subclass must implement these methods.

```java
public abstract class Pet {
 
    protected String name;
    protected int age;
 
    protected Pet(String name, int age) {
        this.name = name;
        this.age = age;
    }
 
    public abstract void say(); // an abstract method
}

class Cat extends Pet {
 
    // It can have additional fields as well
 
    public Cat(String name, int age) {
        super(name, age);
    }
 
    @Override
    public void say() {
        System.out.println("Meow!");
    }
}

Dog dog = new Dog("Boss", 5); // it prints "Woof!"
Pet pet = new Pet("Unnamed", 5); // this throws a compile time error
```

### Important

- Static methods can't be abstract!
- class can extend only one abstract class.