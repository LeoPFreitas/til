# Variable Environment

## Introduction

In JS we can have many execution context. What about variables that are created inside this individual execution context (inside of function...). Each execution context has it's own variable environment

On top of the execution context, we have a space called variable environment. They all live in our JS engine memory, but they must know how they relate to one another. Some function have access to certain variables and some don't .

```jsx
function two() {
  var isValid;
}

function one() {
  isValid = true;
}

var isValid = false;
one();

// two() -- undefined
// one() -- true
// global() -- false
```

At the example, we can observe that in each execution context the variable has one value. When the function two finish the execution, it will be popped off the stack and the memory space for the variable is gone.
