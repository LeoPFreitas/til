# Dynamic Scope x Lexical Scope + this part 2

## Example 1

> In JavaScript our lexical scope (available data + variables where the function was defined) determines our available variables. Not where the function is called (dynamic scope)

- This keyword is one exception → dynamically scoped

```jsx
const a = function () {
  console.log("a", this);

  const b = function () {
    console.log("b", this);
    const c = {
      hi: function () {
        console.log("c", this);
      },
    };
    c.hi();
  };
  b();
};

a();

// a -> Window {parent: Window, opener: null, top: Window, length: 4, frames: Window, …}
// b -> Window {parent: Window, opener: null, top: Window, length: 4, frames: Window, …}
// c -> {hi: ƒ}

// we have windown.a(b())
```

## Example 2

Why b returns window? Because it is not lexically scoped. It means that doesn't matter where it is written, it matters how the function was called.

Notice that the function "anotherFunction" wasn't called by the object "obj". The age function did! In JavaScript, the this keyword defaults to the window object.

```jsx
const obj = {
  name: "Leonardo",
  age() {
    console.log("a", this);
    var anotherFunction = function () {
      console.log("b", this);
    };
    anotherFunction();
  },
};

obj.age();

// a -> {name: "Leonardo", age: ƒ}
// b -> Window {parent: Window, opener: null, top: Window, length: 4, frames: Window, …}
```

## Solution?

- Arrow functions → lexical this behavior unlike normal function (lexically bind "this")

```jsx
const obj = {
  name: "Leonardo",
  age() {
    console.log("a", this);
    var anotherFunction = () => {
      console.log("b", this);
    };
    anotherFunction();
  },
};

obj.age();

// a -> {name: "Leonardo", age: ƒ}
// b -> {name: "Leonardo", age: ƒ}
```

- Before ES6, use bind

```jsx
const obj = {
  name: "Leonardo",
  age() {
    console.log("a", this);
    var anotherFunction = function () {
      console.log("b", this);
    };
    return anotherFunction.bind(this);
  },
};

obj.age();
// a -> {name: "Leonardo", age: ƒ}
// b ->  ƒ () { console.log('b', this) }

obj.age()();
// a -> {name: "Leonardo", age: ƒ}
// b -> {name: "Leonardo", age: ƒ}
```
