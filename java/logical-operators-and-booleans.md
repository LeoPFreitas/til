# Logical Operator and Booleans

## Logical operators

- **NOT** is a unary operator that reverses the boolean value. It is denoted as `!`.

```
boolean f = false; // f is false
boolean t = !f;    // t is true

```

- **AND** is a binary operator that returns `true` if both operands are `true`, otherwise, it is `false`. It is denoted as `&&`.

```
boolean b1 = false && false; // false
boolean b2 = false && true;  // false
boolean b3 = true && false;  // false
boolean b4 = true && true;   // true

```

- **OR** is a binary operator that returns `true` if at least one operand is `true`, otherwise, it returns `false`. It is denoted as `||`.

```
boolean b1 = false || false; // false
boolean b2 = false || true;  // true
boolean b3 = true || false;  // true
boolean b4 = true || true;   // true

```

- **XOR** (**exclusive OR**) is a binary operator that returns `true` if boolean operands have different values, otherwise, it is `false`.

```
boolean b1 = false ^ false; // false
boolean b2 = false ^ true;  // true
boolean b3 = true ^ false;  // true
boolean b4 = true ^ true;   // false

```

The **XOR** operator is used less often than others. Just remember that Java has it. If you really need it, you can use it.

## The precedence of logical operators

Below are the logical operations sorted in order of decreasing their priorities in expressions: ! (NOT), ^ (XOR), && (AND), || (OR).

```jsx
boolean b = true && !false; // true, because !false is evaluated first
```
