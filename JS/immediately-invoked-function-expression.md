# Immediately Invoked Function Expression

- Place all library code inside of local scope to avoid any namespace collisions.
- No global property is created
- Enables us to attach private data to a function and it creates a fresh variable environment.

```jsx
(function () {
  // functions
})();
```

- Create one global variable that can be an object that contains many properties that we might want to use.

```jsx
// script 1
var script1 = (function () {
  function a() {
    return 5;
  }
  return {
    a: a,
  };
})();
```
