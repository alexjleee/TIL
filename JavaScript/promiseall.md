# Promise.all()

- Syntax: `Promise.all(arrayOfPromises)`

- `Promise.all()` returns a promise itself, which is resolved when the promises inside the array (that has been passed in as an argument) are all resolved.

- It is useful when you have to wait for more than one promise to be resolved.

- It rejects immediately when any of the input promises rejects.
  - On the other hand, `Promise.allSettled()` waits for all input promises to complete.

- If the array passed in as an argument is empty or contains no promises, it will return an already resolved promise. In any other cases, it will return a pending promise.

- `Promise.all()` maintain the order of the array passed in as an argument, which means the first promise in the array will be resolved to the first element of the output array.

Example
```javascript
const timeout = (delay) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Completed: took ${delay}ms`);
    }, delay)
  })
}

Promise.all([timeout(2000), timeout(1000)])
  .then(result => console.log(result));
// ["Completed: took 2000ms", "Completed: took 1000ms"]
```