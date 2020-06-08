# 4 ways of this

## New binding this

- Dynamically scoped — determined whenever it gets called
- Used with constructor functions
- Allow us to assign this keyword to the object that we instantiate

  ```jsx
  function Person(name, age) {
    this.name = name;
    this.age = age;
  }

  const me = new Person("leo", 22);
  ```

## Implicit binding

- Dynamically scoped — determined whenever it gets called
- That is how the language works
- The **this** keyword refer to the object person

  ```jsx
  const person = {
    name: "leo",
    age: 22,
    hi() {
      console.log("hi", this.name);
    },
  };

  person.hi();
  ```

## Explicit binding

- Dynamically scoped — determined whenever it gets called
- We dictate exactly what the this keyword should refer to
- Use bind, call or apply

  ```jsx
  const person = {
    name: "leo",
    age: 22,
    hi: function () {
      console.log("hi", this.setTimeout).bind(window);
    },
  };

  person.hi();
  ```

## Arrow function

- Lexical scope — determined whenever we write the function that's what this binds to
- without arrow function, this would be the window object

```jsx
const person = {
  name: "leo",
  age: 22,
  hi: function () {
    var inner = () => {
      console.log("hi", this.name);
    };

    return inner();
  },
};

person.hi();
```
