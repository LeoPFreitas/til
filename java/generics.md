# Generics

- A generic type is a generic class (or an interface) that is parameterized over types.
- To declare a generic class, we should declare a class with the type parameter section delimited by angle brackets following the class name.

```java
class GenericType<T> { 

    /**
     * A field of "some type"
     */
    private T t;

    /**
     * Takes a value of "some type" and set it to the field
     */
    public GenericType(T t) {
        this.t = t;
    }

    /**
     * Returns a value of "some type"
     */
    public T get() {
        return t;
    }

    /**
     * Takes a value of "some type", assigns it to a field and then returns it
     */
    public T set(T t) {
        this.t = t;
        return this.t;   
    }
}
```

## Naming and conventions

- There is a naming convention that restricts type parameter name choices to single uppercase letters.

The most commonly used type parameter names are:

- `T` – Type
- `S`, `U`, `V` etc. – 2nd, 3rd, 4th types
- `E` – Element (used extensively by different collections)
- `K` – Key
- `V` – Value
- `N` – Number

## Creating objects of generic classes

- It is important, that a type argument must be a reference type. It is impossible to use a primitive type like int or double as a type argument.

```java
GenericType<Integer> obj1 = new GenericType<Integer>(10);

GenericType<String> obj2 = new GenericType<String>("abc");

var obj3 = new GenericType<>("abc");
```

### Generic array

```java
public class ImmutableArray<T> {

    private T[] items;

    public ImmutableArray(T[] items) {
        this.items = items;
    }

    public T get(int index) {
        return items[index];
    }

    public int length() {
        return items.length;
    }
}
```

## Generic static methods

Static methods cannot use type parameters of their class! Type parameters of the class these methods belong to can only be used in instance methods. If you want to use type parameters in a static method, declare this method’s own type parameters.

- Static generic methods are often used to write generic algorithms that do not depend on the type they operate on.
- Generic static methods are widely used in different operations with arrays and collections, for example, sorting an array, searching a value in a collection, reversing an array and so on.

```java
// The following static method is declared as generic.
public static <T> T doSomething(T t) {
    return t;
}

// The type parameter T can be used to declare the return type and the type of method's arguments.
public static <E> int length(E[] array) {
    return array.length;
}

Integer[] array = { 1, 2, 3, 4 };
int len = length(array);

public static <T, U> void method(T t, U u) {
    // do something
}
```

## Generic instance methods

- Instance methods can have their own type parameters as well as static methods.
- Note, generic instance methods declared outside a generic class is a rare case.
- Normally, you will write and find generic static methods or instance methods that belong to a generic class.

```java
// Note, that in this example we cannot use T as the type of class's field, because it belongs to the method rather than the class itself.
class SimpleClass {
 
    public <T> T getParameterizedObject(T t) {
        return t;
    }
}

class SimpleClass<T> {
 
    public <U> T getParameterizedObject(T t, U u) {
        return t;
    }
}
```