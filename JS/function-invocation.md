# Function Invocation

## Introduction

- function invocation/call/execution is the same thing
- function invocation → create a new execution environment on top of global execution context ( here we have access to "this" and "arguments")

```jsx
function concat(a, b) {
  console.log(arguments);
  console.log(this);
}

concat("leo", "freitas");

// returns
// Arguments(2) ["leo", "freitas", callee: ƒ, Symbol(Symbol.iterator): ƒ]
// {parent: Window, opener: null, top: Window, length: 4, frames: Window, …}
```

## Function Declaration

- Starts with the function keyword
- Defined at parse time → when the compiler initially looks at the code and start hoisting and allocating memory.

```jsx
function myName() {
  console.log("Leonardo");
}
```

## Function Expression

- Defined at runtime → when we actually run the function.

```jsx
var name = function myName() {
  console.log("Leonardo");
};
```
