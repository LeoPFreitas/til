# Referencing subclass objects

There are two ways to refer to a subclass object:

1. **using the subclass reference.** A subclass reference can be used to refer to its object;
2. **using the superclass reference.** A reference variable of the superclass can be used to refer to any subclass object derived from that superclass because a subclass is a special case of the superclass.

```java
class Person {
 
    protected String name;
    protected int yearOfBirth;
    protected String address;
 
    // public getters and setters for all fields
}
 
class Client extends Person {
 
    protected String contractNumber;
    protected boolean gold;
 
    // public getters and setters for all fields
}
 
class Employee extends Person {
 
    protected Date startDate;
    protected Long salary;
 
    // public getters and setters for all fields
}

// subclass reference
Person person = new Person(); // the reference is Person, the object is Person
Client client = new Client(); // the reference is Client, the object is Client
Employee employee = new Employee(); // the reference is Employee, the object is Employee

// superclass reference
Person client = new Client(); // the reference is Person, the object is Client
Person employee = new Employee(); // the reference is Person, the object is Employee
```

## Accessing fields and methods through a superclass reference

We can use a superclass reference for any subclass object derived from it. However, we cannot access specific members of the subclass through the base class reference. **We have access only to those members of the object defined by the type of reference**

```java
Person employee = new Employee();
 
employee.setName("Ginger R. Lee"); // Ok
employee.setYearOfBirth(1980); // Ok
employee.setSalary(30000); // Compile-time error
```

## Casting between superclass and subclass

- It is possible to cast an object of a subclass to its superclass
- It is possible to cast an object from a superclass type to a subclass, but only if the object really is an instance of this subclass, otherwise ClassCastException will be thrown.

```java
Person person = new Client();
 
Client clientAgain = (Client) person; // it's ok
Employee employee = (Employee) person; // ClassCastException
```

## When to use the superclass reference?

- Processing an array (or another collection) of objects which have different types from the same hierarchy;
- A method that accepts an object of the base class, but can also work with objects of its subclasses.

```java
public static void printNames(Person[] persons) {
    for (Person person : persons) {
        System.out.println(person.getName());
    }
}

Person person = new Employee();
person.setName("Leonardo");
 
Client client = new Client();
client.setName("Pedro");
 
Employee employee = new Employee();
employee.setName("Maria");
 
Person[] persons = {person, client, employee};
 
printNames(persons);

// Leonardo
// Pedro
// Maria
```