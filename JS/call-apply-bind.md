# Call, Apply and Bind

## Call and Apply

- All function when created has the property "call" that allows us to call the function.
- Useful to borrow methods of other properties (keep code dry)

```jsx
function a() {
  console.log("hello");
}

a.call(); // hi
a(); // hi

// -------------------

function a() {
  console.log("hi");
}

a.apply(); // hi
```

## Differences?

The difference is that apply lets you invoke the function with arguments as an array; call requires the parameters be listed explicitly. A useful mnemonic is "A for array and C for comma."

```jsx
theFunction.apply(valueForThis, arrayOfArgs)

theFunction.call(valueForThis, arg1, arg2, ...)
```

**Example — [stackoverflow link](https://stackoverflow.com/questions/1986896/what-is-the-difference-between-call-and-apply)**

```jsx
function theFunction(name, profession) {
  console.log("My name is " + name + " and I am a " + profession + ".");
}
theFunction("John", "fireman");
theFunction.apply(undefined, ["Susan", "school teacher"]);
theFunction.call(undefined, "Claude", "mathematician");
theFunction.call(undefined, ...["Matthew", "physicist"]);

// My name is John and I am a fireman.
// My name is Susan and I am a school teacher.
// My name is Claude and I am a mathematician.
// My name is Matthew and I am a physicist.
```

## Bind

- Unlike call and apply that immediately runs a function, bind returns a new function with a certain context and parameters.
- Usually used when we want a function to be called later on with a certain type of context or a certain type of this keyword

```jsx
let user = {
  firstName: "John",
};

function func() {
  alert(this.firstName);
}

let funcUser = func.bind(user);
funcUser(); // John
```

**Tip**

```jsx
function multiply(a, b) {
  return a * b;
}

let multiplyByTwo = multiply.bind(this, 2);

console.log(multiplyByTwo(4)); // 8
```
