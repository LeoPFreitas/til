# Type Bounds

- Simple generics can easily accept any type parameter and make it possible to reuse code once written
- Useful when we need to restrict the types of objects

## Usage

- Note that "extends" can mean not only an extension of a certain class but also an implementation of an interface. Generally speaking, this word is used as a replacement for an extension of usual classes because generic classes do not extend this way: you cannot write Storage<Brochures> extends Storage<Books>, because it will lead to an error.

```java
public class Books { }
public class Brochures extends Books { }
public class Computers { }

class Storage<T extends Books> {
    private T nameOfElements;
    //other methods
}

Storage<Books> storage1 = new Storage<>(); //no problem
Storage<Brochures> storage2 = new Storage<>(); //no problem
Storage<Computers> storage3 = new Storage<>(); //a compile-time error
```

### Multiple bounds

- The bound may have the form of a single type variable or have multiple bounds
- Here "A" is a class or an interface; "B", "C", ... are necessarily interfaces.
- If `T` has a bound with a class, this class must be specified first! Otherwise, it results in a compile-time error:

```java
<T extends A>
<T extends A & B & C & ...>
```
