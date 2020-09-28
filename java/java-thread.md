# Introduction to Java Thread

- Each thread is represented by an object that is an instance of the `java.lang.Thread` class (or its subclass).
- This class has a static method named `currentThread` to obtain a reference to the currently executing thread object

```java
public class MainThreadDemo {
    public static void main(String[] args) {
        Thread t = Thread.currentThread(); // main thread

        System.out.println("Name: " + t.getName());
        System.out.println("ID: " + t.getId());
        System.out.println("Alive: " + t.isAlive());
        System.out.println("Priority: " + t.getPriority());
        System.out.println("Daemon: " + t.isDaemon());

        t.setName("my-thread");
        System.out.println("New name: " + t.getName());
    }
}
```

## Custom Threads

Java primarily has two ways to create a new thread

- Extending the `Thread` class and overriding its `run` method

    ```java
    class HelloThread extends Thread {

        @Override
        public void run() {
            String helloMsg = String.format("Hello, i'm %s", getName());
            System.out.println(helloMsg);
        }
    }
    ```

- Implementing the `Runnable` interface and passing the implementation to the `constructor` of the Thread class

    ```java
    class HelloRunnable implements Runnable {

        @Override
        public void run() {
            String threadName = Thread.currentThread().getName();
            String helloMsg = String.format("Hello, i'm %s", threadName);
            System.out.println(helloMsg);
        }
    }
    ```

    ```java
    Thread t1 = new HelloThread(); // a subclass of Thread
    Thread t2 = new Thread(new HelloRunnable()); // passing runnable

    // specify a name
    Thread myThread = new Thread(new HelloRunnable(), "my-thread");

    // lambda
    Thread t3 = new Thread(() -> {
        System.out.println(String.format("Hello, i'm %s", Thread.currentThread().getName()));
    });

    ```

### Starting threads

- The class `Thread` has a method called `start()` that is used to start a thread. The method `run` will be invoked automatically.
- By default, a new thread is running in non-daemon mode.
- JVM will not terminate the running program while there're still non-daemon threads left. The daemon threads won't prevent JVM from terminating.
- If you invoke run directly, the code will be executed in the same thread.

```java
public class StartingMultipleThreads {

    public static void main(String[] args) {
        Thread t1 = new HelloThread();
        Thread t2 = new HelloThread();

        t1.start();
        t2.start();

        System.out.println("Finished");
    }
}
```

## Sleeping

- The static method `Thread.sleep()` causes the currently executing thread to suspend execution for the specified number of milliseconds.

Another way to make the current thread sleep is to use the special class `TimeUnit` from the package `java.util
.concurrent:`

- `TimeUnit.MILLISECONDS.sleep(2000)` performs `Thread.sleep` for 2000 milliseconds;
- `TimeUnit.SECONDS.sleep(2)` performs `Thread.sleep` for 2 seconds;

```java
System.out.println("Started");

Thread.sleep(2000L); // suspend current thread for 2000 millis
         
System.out.println("Finished");
```

## Joining

- The `join` method forces the current thread to wait for the completion of another thread on which the method was called.

```java
Thread thread = ...
thread.start(); // start thread

System.out.println("Do something useful");

thread.join();  // waiting for thread to die

System.out.println("Do something else");
```