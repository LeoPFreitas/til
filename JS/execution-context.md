## Introduction

In order to become a great JavaScript developer, we need to understand how it works internally. That is not mandatory for becoming a developer, but that kind of knowledge is the one that makes programming so exciting and beautiful. It will also help us understand what Hoisting, Scope and Closures are.

### Global Execution Context - creation phase

Keep in mind that initially our JS engine will create a global execution context. It's underneath the hood, so we can't see this.

The global execution context will have two objects: 'Global Object' and 'this'. They are equal to one another. We can easily add variables, functions and many things to the global object.

```jsx
windown === this;
// true

var a = "test";
windown;
// you can see the added variable a.
```

If you are using Node.js, the global object is called 'global' instead of 'window'.

### Execution Context - execution phase

After that step, when the JS Engine sees the instruction '**devDay()'** it create an execution context and add it onto the stack. Then it tries to run this function and sees that this function is calling another function (findDev), so it will create another execution context to "**findDev"** and add it onto the stack.

As we can see, it will create 3 execution context and 3 elements will be pushed to the call stack.

```jsx
// global context -- this is created behid the scenes

function dev() { // execution context
	return 'eat, sleep, code, repeat';
}

function findDev() { // execution context
	return return dev();
}

function devDay() { // execution context
	return findDev();
}

devDay();
```
