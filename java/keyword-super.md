# Keyword super

Sometimes when we define a new subclass we need to access members or constructors of its superclass. Java provides a special keyword `super` to do this. This keyword can be used in several cases:

- to access instance fields of the parent class;
- to invoke methods of the parent class;
- to invoke constructors of the parent class (no-arg or parameterized).

## Accessing superclass fields and methods

The keyword super is optional if members of a subclass have different names from members of the superclass. Otherwise, using super is the right way to access hidden (with the same name) members of the base class.

```java
class SuperClass {
    
    protected int field;
 
    protected int getField() {
        return field;
    }
    
    protected void printBaseValue() {
        System.out.println(field);
    }
}
 
class SubClass extends SuperClass {
    
    protected int field;
 
    public SubClass() {
        this.field = 30;  // It initializes the field of SubClass
        field = 30;       // It also initializes the field of SubClass
        super.field = 20; // It initializes the field of SuperClass
    }
 
    /**     
     * It prints the value of SuperClass and then the value of SubClass
     */
    public void printSubValue() {
        super.printBaseValue(); // It invokes the method of SuperClass, super is optional here
        System.out.println(field);
    }
}
```

## Invoking superclass constructor

Constructors are not inherited by subclasses, but a superclass constructor can be invoked from a subclass using the keyword super with parentheses. We can also pass some arguments to the superclass constructor.

### Two important points:

- invoking `super(...)` must be the first statement in a subclass constructor, otherwise, the code cannot be compiled;
- the default constructor of a subclass automatically calls the no-argument constructor of the superclass.

```java
class Person {
 
    protected String name;
    protected int yearOfBirth;
    protected String address;
 
    public Person(String name, int yearOfBirth, String address) {
        this.name = name;
        this.yearOfBirth = yearOfBirth;
        this.address = address;
    }
 
    // getters and setters
}
 
class Employee extends Person {
 
    protected Date startDate;
    protected Long salary;
 
    public Employee(String name, int yearOfBirth, String address, Date startDate, Long salary) {
        super(name, yearOfBirth, address); // invoking a constructor of the superclass
        
        this.startDate = startDate;
        this.salary = salary;
    }
 
    // getters and setters
}
```