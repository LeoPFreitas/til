# Overloading

- Overloading allows us to change the method’s signature: the number of parameters, their type or both.

-  If methods have the same name, but a different number or type of parameters, they are overloaded. It means we can invoke different methods by the same name by passing different arguments.

> Important that it's impossible to declare more than one method with the same name and parameters (number and types), even with different return types. The return type is not considered for overloading because it's not a part of the signature.

- Note, that changing the order of the same parameters is a valid case of overloading.

```java
public static void print(String stringToPrint) {
    System.out.println(stringToPrint);
}
 
public static void print(String stringToPrint, int times) {
    for (int i = 0; i < times; i++) {
        System.out.println(stringToPrint);
    }
}
 
public static void print(int times, String stringToPrint) {
    for (int i = 0; i < times; i++) {
        System.out.println(stringToPrint);
    }
}
 
public static void print(int val) {
    System.out.println(val);
}

print("some string");
print("another string", 2);
print(2, "another string again");
print(5);

// some string
// another string
// another string
// another string again
// another string again
// 5
```

## Overloading and casting

In the case, where the type of a method parameter is not exactly the same as the type of the passed argument, the compiler chooses the method that has the closest type of the argument in order of the **implicit casting**.

```java
public class OverloadingExample {
 
    public static void print(short a) {
        System.out.println("short arg: " + a);
    }
 
    public static void print(int a) {
        System.out.println("int arg: " + a);
    }
 
    public static void print(long a) {
        System.out.println("long arg: " + a);
    }
 
    public static void print(double a) {
        System.out.println("double arg: " + a);
    }
 
    public static void main(String[] args) {
        print(100);
    }
  
  	print(100); // int arg: 100
  
  	// comment the method public static void print(int a)
  	print(100); // long arg: 100
  
  	// comment the method public static void print(long a) too
  	print(100); // double arg: 100.0
  
  	// comment the public static void print(double a) too
  	print(100); // the program can't be compiled
}
```
