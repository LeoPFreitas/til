# Spread Operator

1. Eliminate duplicated from an array

   ```jsx
   let num = [1, 2, 3, 3, 4, 2];

   let uniqueNum = [...new Set(num)];

   uniqueNum; // [1, 2, 3, 4]
   ```

2. Convert string to character

   ```jsx
   let name = ["leonardo freitas"];

   let chars = [...name];
   ```

3. Destructurig variable

   ```jsx
   let [person1, ...others] = ["leo", "julia", "pietro"];
   person1; // 'leo';

   others; // ['julia', 'pietro'];
   ```

4. Convert nodelist object to array

   ```jsx
   let nodeList = document.querySelectorAll(".class");

   var nodeArray = [...nodeList];
   ```

5. Passing as arguments

   ```jsx
   function sum(a, b) {
     return a + b;
   }

   let num = [1, 2];

   sum(...sum); // 3
   ```

6. Merging arrays

   ```jsx
   let mens = ["leo", "pedro"];
   let womens = ["julia", "carla"];

   let all = [...mens, ...womans];
   ```

7. Copying arrays (shallow)

   ```jsx
   let names = ["leo", "pedro", "pietra"];

   console.log(...copy); // ['leo', 'pedro', 'pietra']
   ```

8. Using spread operator in logging

   ```jsx
   let num = [1, 2, 3, 3, 4, 2];

   let uniqueNum = [...new Set(num)];

   uniqueNum; // [1, 2, 3, 4]
   ```

**Set**

- The Set object lets you store unique values of any type, whether primitive values or object references.
- Set objects are collections of values. You can iterate through the elements of a set in insertion order. A value in the Set may only occur once; it is unique in the Set's collection.
- If an iterable object is passed, all of its elements will be added to the new Set. If you don't specify this parameter, or its value is null, the new Set is empty.

```jsx
// new Set([iterable]);
var mySet = new Set();

mySet.add(1); // Set [ 1 ]
mySet.add(5); // Set [ 1, 5 ]
mySet.add(5); // Set [ 1, 5 ]
mySet.add("some text"); // Set [ 1, 5, 'some text' ]
mySet.has(1); // true
```
