# Objects

A typical object-oriented program consists of a set of interacting objects. Each object has its own state separated from others. Each object is an instance of a particular class (type) that defines common properties and possible behavior for its objects.

All classes from the standard library (String, Date) and classes defined by programmers are reference types which means that variables of these types store addresses where the actual objects are located.

## Immutability of objects

- Immutability means that an object always stores the same values. If we need to modify these values, we should create a new object.
- The class Patient is not immutable because it is possible to change any field of an object.

```java
class Patient {
    String name;
    int age;
}

Patient patient = new Patient();

patient.name = "Mary";
patient.name = "Alice";
```

The common example is the standard String class. Strings are immutable objects so all string operations produce a new string. Immutable types allow you to write programs with fewer errors.
