# Closures

## Introduction

We have the closures because functions are first class citizens and lexical scope exists (JavaScript engine knows, based on where our code, what variables each function has access to)

- Closures are simply a combination of function and lexical environment which it was declared
- Allows a function access variables from an enclosing scope or environment even after it leaves the scope in which it was declared

```jsx
function a() {
  let grandpa = "grandpa";

  return function () {
    let father = "father";

    return function c() {
      let son = "son";

      return `${grandpa} > ${father} > ${son}`;
    };
  };
}

a(); // [function b]
a()(); // [function c]
a()()(); // 'grandpa > father > son'
```

## Example

- It works because of closures → even without hoisting (const).

```jsx
function name() {
  setTimeout(function () {
    console.log(me);
  }, 3000);

  const me = "leonardo";
}

name(); // leonardo
```

```jsx
// we can't use let

const arr = [1, 2, 3, 4];
for (var i = 0; i < arr.length; i++) {
  (function (closureI) {
    setTimeout(function () {
      console.log("I am at index " + closureI);
    }, 3000);
  })(i);
}
```

## Benefits

- Memory efficient
- Encapsulation

We only create the array one time. The closure keeps the array in memory because someone is referencing it.

```jsx
function havyDuty() {
  const arr = new Array(7000).fill(0);
  console.log("created");
  return function (index) {
    return arr[index];
  };
}

const getArr = havyDuty();

getArr(434);
getArr(230);
getArr(800);

// created
// 0
```
