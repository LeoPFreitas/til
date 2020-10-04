# Thread synchronization

- **Critical section →** It is a region of code that accesses shared resources and should not be executed by more than one thread at the same time.
- **Monitor →** It is a special mechanism to control concurrent access to an object.
    - Each object and class has an associated implicit monitor. A thread can acquire a monitor at the same time. They will wait until the owner release it.
    - A thread can be locked by the monitor of an object and wait for its release.

### The synchronized keyword

The "classic" and simplest way to protect code from being accessed by multiple threads concurrently is using the keyword synchronized.

It is used in two different forms:

- synchronized method (a static or an instance method)
- synchronized blocks or statements (inside a static or an instance method)

### Static synchronized methods

- When we synchronize static methods using the synchronized keyword the monitor is the class itself.
- Only one thread can execute the body of a synchronized static method at the same time. This can be summarized as "one thread per class".
- The monitor is `SomeClass`
- The method can be invoked only from one thread at the same time

```java
class SomeClass {

    public static synchronized void doSomething() {
        
        String threadName = Thread.currentThread().getName();
        System.out.println(String.format("%s entered the method", threadName));
        System.out.println(String.format("%s leaves the method", threadName));
    }
}

/* call the method from two threads concurrently */
// Thread-0 entered the method
// Thread-0 leaves the method
// Thread-1 entered the method
// Thread-1 leaves the method
```

### Instance synchronized methods

- Instance methods are synchronized on the instance (object).
- The monitor is the current object (this) that owns the method.
- If we have two instances of a class, each instance has a monitor for synchronizing.

Only one thread can execute code in a synchronized instance method of a particular instance. But different threads can execute methods of different objects at the same time. This can be summarized as "one thread per instance".

```java
class SomeClass {

    private String name;

    public SomeClass(String name) {
        this.name = name;
    }

    public synchronized void doSomething() {

        String threadName = Thread.currentThread().getName();
        System.out.println(String.format("%s entered the method of %s", threadName, name));
        System.out.println(String.format("%s leaves the method of %s", threadName, name));
    }
}

SomeClass instance1 = new SomeClass("instance-1");
SomeClass instance2 = new SomeClass("instance-2");

MyThread first = new MyThread(instance1);
MyThread second = new MyThread(instance1);
MyThread third = new MyThread(instance2);

first.start();
second.start();
third.start();

// Thread-0 entered the method of instance-1
// Thread-2 entered the method of instance-2
// Thread-0 leaves the method of instance-1
// Thread-1 entered the method of instance-1
// Thread-2 leaves the method of instance-2
// Thread-1 leaves the method of instance-1
```

### Synchronized blocks (statements)

- It is possible to synchronize only a part of a method by using synchronized blocks. They must specify an object for locking threads
- The block inside `staticMethod` is synchronized on the class that means only one thread can execute code in this block
- The block inside `instanceMethod` is synchronized on this instance that means only one thread can execute the block of the instance.

```java
class SomeClass {

    public static void staticMethod() {

        // unsynchronized code
                
        synchronized (SomeClass.class) { // synchronization on the class
            // synchronized code
        }
    }

    public void instanceMethod() {

        // unsynchronized code

        synchronized (this) { // synchronization on this instance
            // synchronized code
        }
    }
}
```

## Synchronization and visibility of changes

- The Java Language Specification guarantees that changes performed by a thread are visible to other threads if they are synchronized on the same monitor.

### Example: synchronized counter

- When multiple threads invoke `increment` on the same instance, no problem arises because the synchronized keyword protects the shared field.
- The method `getValue` doesn't modify the field. It only reads the current value. The method is synchronized so that the reading thread always reads the actual value

```java
class SynchronizedCounter {
    
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public synchronized int getValue() {
        return count;
    }
}
```

### OBS

Sometimes, however, there's no need to synchronize methods that only read shared data (including getters):

- If we have a guarantee that the reading thread successfully returns from `join` on all writing threads when it reads
 a field. That's true about the code above and we can remove the synchronized keyword from the declaration of
  `getValue`.
- If a shared field is declared with the **volatile** keyword. ****In that case, we will always see the actual value of
 this field.

### One monitor

- An object or class that has only one monitor and only one thread can execute synchronized code on the same monitor. If a class has several synchronized instances methods a thread invokes one of them, other threads cannot execute either of these methods on the same instance until the first thread releases the monitor of the instance.

```java
class SomeClass {

    public synchronized void method1() {
        // do something useful
    }

    public synchronized void method2() {
        // do something useful
    }
    
    public void method3() {
        synchronized (this) {
            // do something useful
        }
    }
}
```

If a thread invokes `method1` and executes statements inside the method, no other can execute statements inside `method2` or in the synchronized block in `method3` because this monitor is already acquired

### Reentrant synchronization

A thread cannot acquire a lock owned by another thread. But a thread can acquire a lock that it already owns. This behavior is called reentrant synchronization.

```java
class SomeClass {

    public static synchronized void method1() {
        method2(); // legal invocation because a thread has acquired monitor of SomeClass
    }

    public static synchronized void method2() {
        // do something useful
    }
}
```

## Fine-grained synchronization

- To improve the concurrency rate it's possible to use an idiom with additional objects as monitors.

```java
class SomeClass {

    private int numberOfCallingMethod1 = 0;
    private int numberOfCallingMethod2 = 0;

    final Object lock1 = new Object(); // an object for locking
    final Object lock2 = new Object(); // another object for locking

    public void method1() {
        System.out.println("method1...");

        synchronized (lock1) {
            numberOfCallingMethod1++;
        }
    }

    public void method2() {
        System.out.println("method2...");
        
        synchronized (lock2) {
            numberOfCallingMethod2++;
        }
    }
}
```