# Covariant return types

- Method overriding is a mechanism for providing new behavior for the superclass method in a subclass method
- When you override a superclass method, the name and parameters of a subclass method have to be exactly the same as that of the superclass method
- **Return types are different -> ** the subclass method can return the same type as the superclass method or a subtype
 of this return type (**covariant return type**).
- Covariant return types works only for non-primitive return types

### How it works

- Covariant return type allows you to narrow the return type of the overridden method (make it more specific)

```java
class SuperType { }

class SubType extends SuperType { }

class A {
    
    public SuperType getType() {
        return new SuperType();
    }
}

class B extends A {
    
    @Override
    public SubType getType() {
        return new SubType();
    }
}
```