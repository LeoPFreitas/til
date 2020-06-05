# Functions

## Introduction

When we invoke a function we get two parameters automatically (this and arguments).

## Functions are Objects

- We can add properties to function and underneath the hood JavaScript creates an special type of object (callable).

```jsx
function name() {
  console.log("leonardo");
}

name.age = 24;
```

- The special object for function has:
  - some code that we can invoke
  - name property → we can have anonymous functions
  - properties → call, apply, bind

![functions](assets/function.png)

## Functions are First Class Citizens in JS

- Can be assigned to variables and properties of objects

  ```jsx
  var x = function () {};
  ```

- Functions as arguments → can pass a function as parameter to another function

  ```jsx
  function a(fn) {
    fn();
  }

  a(function () {
    console.log("hi");
  });
  ```

- Return functions as values from other functions

  ```jsx
  function a() {
  	return fucntion c(){ console.log('hi')}
  }
  ```

## High Order Functions

> It is a function that can take a function as an argument or a function that returns another function

```jsx
const multiplyBy = function (num1) {
  return function (num2) {
    return num1 * num2;
  };
};

const multiplyByTwo = multiplyBy(2);
const multiplyByFive = multiplyBy(5);

multiplyByTwo(4); // 8
multiplyByFive(10); // 50
multiplyBy(4)(5); // 20
```
