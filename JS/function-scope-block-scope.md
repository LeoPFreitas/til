# Function Scope x Block Scope

## Introduction

- **Scope →** what variables we have access
- **Function scope →** every time we create a function, we create a new execution context which has its own variable environment

## Function Scope

We only create a new scope (new environment) when there is a function.

```jsx
// fucntion scope != block scope
if (1 > 2) {
  var name = "Leonardo";
}

name; // Leonardo

function a() {
  name1 = "Leonardo";
}

name1; // reference error
```

## JavaScript with block scope?

Thanks ES6. It's possible.

- Use **const** and **let**
