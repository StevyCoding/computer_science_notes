In JavaScript, a promise is an object that represents the eventual completion or failure of an asynchronous operation. It allows you to handle asynchronous operations such as fetching data from a server or reading a file without blocking the execution of your code. Promises provide a cleaner and more maintainable way to work with asynchronous code compared to using callbacks.

A promises has tree state: 

1. **Pending:** The initial state of the promise before it is fulfilled or rejected.
2. **Fulfilled:** The state of the promise representing a successful operation.
3. **Rejected:** The state of the promise representing a failed operation.

```js
const myPromise = new Promise((resolve, reject) => {
  // Asynchronous operation
  if (/* operation successful */) {
    resolve('Operation was successful');
  } else {
    reject('Operation failed');
  }
});

myPromise.then((successMessage) => {
  // Handle successful operation
  console.log(successMessage);
}).catch((errorMessage) => {
  // Handle failed operation
  console.error(errorMessage);
});
```

1. Create a new promise using the `new Promise` syntax. Inside the promise constructor, you define an asynchronous operation.
2. If the operation is successful, you call the `resolve` function, passing the result as an argument. If it fails, you call the `reject` function, passing an error message as an argument.
3. Use the `then` method to handle the successful result of the promise. You can access the result passed to the `resolve` function inside the `then` block.
4. Use the `catch` method to handle any errors that occur during the asynchronous operation. You can access the error message passed to the `reject` function inside the `catch` block.

Promises can be chained together using the `then` method, allowing you to perform a series of asynchronous operations one after the other. Additionally, you can use the `Promise.all` and `Promise.race` methods to handle multiple promises concurrently.

Overall, promises provide a way to write more maintainable and readable asynchronous code in JavaScript, making it easier to handle complex asynchronous operations.