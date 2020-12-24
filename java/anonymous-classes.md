# Anonymous classes

- Enable the developer to declare and instantiate a class at the same time
- An anonymous class always implements an interface or extends another class (concrete or abstract).
- An anonymous class must override all abstract methods of the superclass. That is, all interface methods must be overridden except default methods. If an anonymous class extends a class that has no abstract methods, it doesn't have to override anything.

```java
interface SpeakingEntity {

    void sayHello();

    void sayBye();
}

SpeakingEntity englishSpeakingPerson = new SpeakingEntity() {
            
    @Override
    public void sayHello() {
        System.out.println("Hello!");
    }

    @Override
    public void sayBye() {
        System.out.println("Bye!");
    }
};
```

### Accessing context variables

In the body of an anonymous class, it is possible to capture variables from a context where it is defined:

- an anonymous class can capture members of its enclosing class (the outer class);
- an anonymous class can capture local variables that are declared as **`final`** or are **effectively final** (i.e. the
 variable is not changed but it doesn't have the **`final`** keyword).

```java
public class AnonymousClassExample {

    private static String BYE_STRING = "Auf Wiedersehen!"; // static constant

    public static void main(String[] args) {

        final String hello = "Guten Tag!"; // final local variable

        SpeakingEntity germanSpeakingPerson = new SpeakingEntity() {

            @Override
            public void sayHello() {
                System.out.println(hello); // it captures the local variable
            }

            @Override
            public void sayBye() {
                System.out.println(BYE_STRING); // it captures the constant field
            }
        };

        germanSpeakingPerson.sayHello();

        germanSpeakingPerson.sayBye();
    }
}
```

### Restrictions

Anonymous classes have some restrictions:

- they cannot have static initializers or interface declarations;
- they cannot have static members, except the constant variables (final static fields);
- they cannot have constructors.

```java
final String robotName = "Bug";
final int robotAssemblyYear = 2112;

SpeakingEntity robot = new SpeakingEntity() {

    static final int MAGIC_CONSTANT = 10;

    private String name;
    private int assemblyYear;

    { /* instance initialization block for setting fields */
        name = robotName;
        assemblyYear = robotAssemblyYear;
    }

    @Override
    public void sayHello() {
        System.out.println("1010001" + MAGIC_CONSTANT);
    }

    @Override
    public void sayBye() {
        System.out.println("0101110" + MAGIC_CONSTANT);
    }
};
```

### When to use?

Generally, you should consider using an anonymous class when:

- only one instance of the class is needed;
- the class has a very short body;
- the class is used right after it's defined.

For instance, anonymous classes are actively used when writing user interfaces with the standard Java library called Swing. The same with developing a web user interface using Google Web Toolkit (GWT). It is very common to have a lot of listeners that are used just once for one button, so using anonymous classes allows us to avoid writing a lot of classes and having useless files in the development of the code.

Some widespread libraries for working through the HTTP protocol also use anonymous classes.

## Callbacks

- Often, after creating an instance of an anonymous class we pass it to some method as an argument.
- A callback is a piece of executable code that is passed to another code which executes it (performs a call back) at a convenient time.

```java
interface Callback {

    /**
     * Takes a result and processes it
     */
    void calculated(int result);

    /**
     * Takes an error message
     */
    void failed(String errorMsg);
}

class Divider {

    /**
     * Divide a by b. It executes the specified callback to process results
     */
    public static void divide(int a, int b, Callback callback) {

        if (b == 0) {
            callback.failed("Division by zero!");
            return;
        }

        callback.calculated(a / b);
    }
}

public class CallbacksExample {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int a = scanner.nextInt();
        int b = scanner.nextInt();

        Divider.divide(a, b, new Callback() { // passing callback as an argument

            @Override
            public void calculated(int result) {
                String textToPrint = String.format("%d / %d is %d", a, b, result);
                print(textToPrint);
            }

            @Override
            public void failed(String errorMsg) {
                print(errorMsg);
            }
        });
    }

    public static void print(String text) {
        System.out.println(text);
    }
}
```