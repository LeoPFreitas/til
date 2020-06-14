# Promises + new features

## Promise

> A promise is a object that may produce a single value some time in the future. It can be a resolved or reject value. Possible states: fulfilled, rejected or pending

```jsx
// promise
const promise = new Promise((resolve, raejected) => {
  if (true) {
    resolve("Stuff worked");
  } else {
    rejected("Error, it broke");
  }
});

promise
  .then((results) => console.log(results))
  .catch(() => console.log("Error!"));

// pormise all
const promise2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 1000, "2");
});

const promise3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, "3");
});

const promise4 = new Promise((resolve, reject) => {
  setTimeout(resolve, 3000, "4");
});

Promise.all([promise2, promise3, promise4]).then((values) => {
  console.log(values);
});
```

## Async - Await

- Makes code easier to read
- Build on top of promises

```jsx
async function move() {
  const firstMove = await movePlayer(100, "left");

  await movePlayer(100, "left");
  await movePlayer(230, "top");
  await movePlayer(400, "right");
}
```

## Finally

- Allows us to do something after a promise has finished. It will be called regardless of whether '.then' works or not.

```jsx
const urls = ["https://jsonplaceholder.typicode.com/users"];

Promise.all(
  urls.map((url) => {
    return fetch(url).then((users) => users.json());
  })
)
  .then((array) => {
    // throw Error -> finally will run
    console.log(array[0]);
  })
  .catch((err) => console.log("error", err))
  .finally(() => console.log("extra"));
```

## For await of

- An array of promises is iterable and able to be looped by the for await of loop keywords

```jsx
const urls = [
  "https://jsonplaceholder.typicode.com/users",
  "https://jsonplaceholder.typicode.com/posts",
];

const getData = async function () {
  const arrayOfPromises = urls.map((url) => fetch(url));

  for await (let request of arrayOfPromises) {
    const data = await request.json();
    console.log(data);
  }
};
```
