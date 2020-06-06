# Hoisting

## Introduction

Hoisting is the behavior of moving the variables or function declarations to the top of their respective environments during compilation phase. Keep in mind that variables are partially hoisted and function declarations are hoisted.

```jsx
console.log(name); // undefined

myName(); // 'Leonardo'

console.log(myName()); // 'Leonardo'

function myName() {
  var name = "Leonardo";
}
```

That behavior above is because the hoisting. The JavaScript engine allocates memory for the variables and function that it sees in our code during the creation phase before it executes it.

Underneath the hood, during the creation phase, the JavaScript engine is going to look through the code and as soon as it sees the "var" keyword or the "function" keyword it is going to allocate memory.

## Partial hoisted x Full hoisted

The variables are partially hoisted because the variable it self is hoisted, but note the actual value of it (just assign undefined).

Function are fully hoisted because during the creation phase, the compiler assign a location in memory.

## Examples

```jsx
console.log(myName());

(function myName() {
  var name = "Leonardo";
});

// ReferenceError
```

That error is occurs because now the first word is no longer 'function', so the compiler will not hoist that function

```jsx
console.log(name);

let name = "Leonardo";

// Uncaught Reference: name is not defined
// no hoisting
```

Keep in mind that hoisting occurs with vars and functions.

## Function Expression x Function Declaration

```jsx
// function expression
var name = function myName() {
  console.log("Leonardo");
};

// function declaration
function myName2() {
  console.log("Leonardo");
}
```

During the creation phase of the function expression, the variable is going to be hoisted and it's going to be assigned undefined. The function is going to be run just after its definition.

````jsx
console.log(name()); // TypeError```jsx
console.log(name); // undefined

var name = function myName() {
  console.log("Leonardo");
};

console.log(name()); // 'Leonardo';
````

## Exercice

```jsx
a();

function a() {
  console.log("hi");
}

a();

function a() {
  console.log("hi");
}

a();

// we will get 'bye' 3 times!
// During the creation phase, the function will be fully hoisted
// and because the function declaration is duplicated, the last one
// will be the one that is save in the memory.
// Doesn't matter where you call function a, its value is already hoisted.
```

```jsx
function bigBrother() {
  function littleBrother() {
    return "it is me!";
  }
  return littleBrother();
  function littleBrother() {
    return "no me!";
  }
}

bigBrother(); // 'no me'

// wee always need to think that the function will be hoisted
```
