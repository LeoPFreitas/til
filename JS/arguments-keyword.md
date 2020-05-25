# Arguments Keyword

## Introduction

With that we can create an array from whatever we pass as arguments. Now we can use array methods on this arguments. On each execution context we create a new argument object.

```jsx
function concat(a, b) {
  console.log(arguments);
  console.log(Array.from(arguments));
  // console.log(this);
}

function c() {
  console.log(arguments);
}

concat("leo", "freitas");
c();

// [Arguments] { '0': 'leo', '1': 'freitas' }
// [ 'leo', 'freitas' ]
// {}
```
