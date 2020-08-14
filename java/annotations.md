# Annotations

- Kind of metadata that provide information about a program.
- Mark classes, methods, fields, variables and others

Annotations can be used for different purposes:

- to provide information for the compiler;
- to provide information for development tools to generate code, XML files and so forth;
- to provide information for frameworks and libraries at runtime.

### Build-in annotations

- `@Deprecated` indicates that the marked element (class, method, field and so on) is deprecated and should no longer
 be used. This annotation causes a compile warning if the element is used.
- `@SuppressWarnings` instructs the compiler to disable the compile-time warnings specified in the annotation
 parameters. This annotation can be applied to classes, methods, fields, local variables and other elements.
- `@Override` marks a method that overrides a superclass method. This annotation can only be applied to methods. We
 will consider it in a separated topic about overriding methods

```java
@Deprecated
class MyClass {
    // fields and methods
}

@SuppressWarnings(value = "unused")
public static void method() {
    int a = 0;
}
```

## Example

The `@NotNull` annotation indicates that:

- a method should not return `null`;
- a variable cannot be `null`.

The `@Range` annotation indicates that:

- a method returns an integer number that belongs to the specified range;
- a variable always belongs to the specified range.

```java
class GameCharacter {

    @NotNull
    private String login;

    @Range(min = 1, max = 100)
    private int level = 1;

    public GameCharacter(
            @NotNull String login,
            @Range(min = 1, max = 100) int level) {

        this.login = login;
        this.level = level;
    }

    @NotNull
    public String getLogin() {
        return login;
    }

    @Range(min = 1, max = 100)
    public int getLevel() {
        return level;
    }
}
```