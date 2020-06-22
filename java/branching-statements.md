# Branching statements

## Introduction

Branching statements are used to alter the standard behavior of loops; they can terminate a loop or skip some iterations.

### The break statement

- it terminates the current loop of any type (**for**, **while**, **do-while**);
- it terminates a case in the **switch** statement;
- The break statement terminates only the loop in which it is currently located. If this loop is performed inside another loop, the outer loop won't be stopped.

```jsx
int i = 10;
while (true) { // the condition to continue the loop
    if (i == 0) { // the condition to perform break that stops this loop
        break;
    }
    i--;
}
```

To stop the outer loop we'd like to declare a Boolean variable stopped and use it as a special Boolean flag.

```jsx
boolean stopped = false;
for (int i = 0; (i < 10) && !stopped; i++) {
    for (int j = 0; j < 10; j++) {
        System.out.print(j + " ");
        if (i == j) {
            stopped = true;
            break;
        }
     }
    System.out.println();
}
```

### The continue statement

It causes a loop to skip the current iteration and go to the next one.

- inside the **for-loop**, the continue causes control to immediately move to the increment/decrement statement;
- inside the **while** or **do-while loop**, control immediately moves to the condition.

```jsx
int n = 10;
for (int i = 0; i < n; i++) {
    if (i % 2 != 0) {
        continue;
    }
    System.out.print(i + " ");
}

// 0 2 4 6 8
```
