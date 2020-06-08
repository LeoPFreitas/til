# OOP - JS - Intro

## Introduction

JavaScript leverages its prototype nature to welcome OOP developers to its ecosystem. It also provides easy ways to creating prototypes and organize related data.

> A prototype-based language has the notion of a prototypical object, an object used as a template from which to get the initial properties for a new object.

## Object.create()

- Creates prototype chain — log the object newPerson.**proto**

```jsx
const person = {
  work() {
    return "I work at " + this.company;
  },
};

function createPerson(name, company) {
  newPerson = Object.create(person);

  newPerson.name = name;
  newPerson.company = company;

  return newPerson;
}

const leo = createPerson("leo", "fishtag");
console.log(leo.work());
```

## Constructor Function

1. It creates a new object. The type of this object is simply *object*.
2. It sets this new object's internal, inaccessible,  *\[[prototype]]*  (i.e. **\_\_proto\_\_**) property to be the constructor function's external, accessible, *prototype* object (every function object automatically has a *prototype* property).
3. **It makes the `this` variable point to the newly created object.**
4. It executes the constructor function, using the newly created object whenever `this` is mentioned.
5. It returns the newly created object, unless the constructor function returns a non-`null` object reference. In this case, that object reference is returned instead.

```jsx
function Person(name, company) {
  this.name = name;
  this.company = company;
}

const leo = new Person("leo", "fishtag");

// using Function contructor
const Person2 = new Function(
  "name",
  "company",
  `this.name = name;
	this.company = company;`
);

const pedro = new Person2("pedro", "google");
pedro; // {name: "pedro", company: "google"}
```

- The prototype property is very useful with constructor functions

```jsx
function Person(name, company) {
  this.name = name;
  this.company = company;
}

Person.prototype.work = function () {
  return "I work at " + this.company;
};

const leo = new Person("leo", "fishtag");
leo.work(); // I work at fishtag
```

### More Constructor

- The only way to add properties to object is to use this keyword

  ```jsx
  function Me(name) {
    this.name = name;
    var age = 22;

    console.log("this", this);
  }

  const leo1 = new Me("leonardo");
  // this Me {name: "leonardo"}
  ```

### Tip

- Arrow functions are lexicaly scoped —> the keyword this is defined based on where it's written (global object in this case)
- Regular functions are dynamically scoped —> the important is who calls it

```jsx
function Person(name, company) {
  this.name = name;
  this.company = company;
}

Person.prototype.work = () => {
  return "I work at " + this.company;
};

const leo = new Person("leo", "fishtag");
leo.work(); // I work at undefined
```

## ES6 and Classes

> JavaScript classes, introduced in ECMAScript 2015, are primarily syntactical sugar over JavaScript’s existing prototype-based inheritance. The class syntax is not introducing a new object-oriented inheritance model to JavaScript. JavaScript classes provide a much simpler and clearer syntax to create objects and deal with inheritance.

- Syntactic sugar —> we still use prototype inheritance underneath the hood

```jsx
class Person {
  constructor(name, company) {
    this.name = name;
    this.company = company;
  }

  work() {
    return "I work at " + this.company;
  }
}

// instanciate a class
const leo = new Person("leonardo", "fishtag");
```

## Inheritance

- Instead of copying, it creates an efficient link using prototype inheritance

```jsx
class Person {
  constructor(name, company) {
    this.name = name;
    this.company = company;
  }

  work() {
    return "I work at " + this.company;
  }
}

class Programmer extends Person {
  constructor(name, company, tech) {
    super(name, company);
    this.tech = tech;
  }

  // create a method = extend the prototype
  code() {
    return "I am writting some " + this.tech + " code";
  }
}

const leo = new Programmer("leo", "fishtag", "js");
leo.code(); // "I am writting some js code"
```

## The 4 pilars

1. Encapsulation
   1. Organize things into units/objects that model real world applications
   2. Objects can interact with each other using the methods and properties
2. Abstraction
   1. Hide the complexity
3. Inheritance
   1. Avoid having to rewrite the same code
   2. Save memory space by having shared methods
4. Polymorphism
   1. Call the same method on different objects and each object responding in different way
   2. Ability of an object to take on many forms.
