# Memoization

> It is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again.

A memoized function "remembers" the results corresponding to some set of specific inputs. Subsequent calls with remembered inputs return the remembered result rather than recalculating it, thus eliminating the primary cost of a call with given parameters from all but the first call made to the function with those parameters.

```jsx
// use closure to not pollute the global environment
function memoizedAddTo10(n) {
  let cache = {};

  return function () {
    if (n in cache) {
      return cache[n];
    } else {
      console.log("expensive task");
      cache[n] = n + 10;
      return cache[n];
    }
  };
}

const memoized = memoizedAddTo10();

console.log("1", memoized(2));
console.log("2", memoized(2));
console.log("3", memoized(3));
```
