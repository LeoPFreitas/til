# Object class

The Java Standard Library has a class named Object that is the parent of all standard classes and your custom classes by default.

```java
Object anObject = new Object();
```

### Method provided by the Object class

- *threads synchronization*: `wait`, `notify`, `notifyAll`;
- *object identity*: `hashCode`, `equals`;
- *object management*: `finalize`, `clone`, `getClass`;
- *human-readable representation*: `toString`;

**More detailed**

- The first group of methods (`wait`, `notify`, `notifyAll`) are for working in multithreaded applications.
- The method `hashCode` returns a hash code value for the object.
- The method `equals` indicates whether some other object is **"equal to"** this particular one.
- The method `finalize` is called by the garbage collector (GC) on an object when the GC wants to clean it up. (**Note
:** this method has been deprecated as of JDK 9).
- The method `clone` creates and returns a copy of the object.
- The method `getClass` returns an instance of `Class`, which has information about the runtime class.
- The method `toString` returns a string representation of the object.