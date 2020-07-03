# Array as parameters

## Passing arrays to methods

- A method can have parameters of any types including arrays, strings, primitive types and so on.

> When you pass a value of a primitive type to a method, a copy of the value is created. When you pass an array to a method, a copy of the reference is created but the value is the same. It means if you change the actual value (elements of an array) in the body of a method, you will see these changes outside the method.

## Varargs

It's possible to pass an arbitrary number of the same type arguments to a method using the special syntax named varargs (variable-length arguments).

```java
public static void printNumberOfArguments(int... numbers) {
    System.out.println(numbers.length);
}

printNumberOfArguments(1, 2, 3);
printNumberOfArguments(new int[] { }); // no arguments here
printNumberOfArguments(new int[] { 1, 2 });

// 1
// 2
// 3
// 0
// 2
```

** If a method has more than one parameter, a vararg parameter must be the last parameter in the declaration of the method. **

```java
public static void method(int a, double... varargs) { /* do something */ }
```
