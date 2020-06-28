# Instance methods

Instance methods represent a common behavior for a whole set of objects belonging to the same class.

- The method is called an instance method because it doesn't have the keyword static in its declaration. Instance methods correspond to a particular object of a class and can access its fields.
- The keyword this represents a particular instance of the class MyClass. This keyword is optional, but very useful when it comes to managing objects of the class.
- Instance methods is that they can take arguments and return values of any type including the same type as the defined class.

```java
class MyClass {

    int field;

    public void print() {
        System.out.println(this.field);
    }
}
```

## Calling instance methods

```java
public static void main(String[] args) {

   MyClass object = new MyClass();
   object.field = 10;

   object.print(); // prints "10"
}
```
