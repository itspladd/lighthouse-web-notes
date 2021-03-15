# Promises

## Agenda
* Async flow recap (with callbacks)
* Exception handling
* Error handling with callbacks
* Callback Hell
* Promises!

## Asynchronous Control Flow Recap
* Asynchronous functions get shunted to the side, and do not execute until the execution stack is done running the synchronous code
* The asynchronous function moves to the *callback queue*, awaiting its turn.
* Due to how all this works, using `return` statements in asynchronous code is generally not advisable!

### Using comments to manage
* Example: Since the asynchronous code will always run after the synchronous code, the following steps can help get a handle on what's going on:
  1. Comment out asynchronous code
  2. Run the program and see the output
  3. Uncomment the async code
  4. Run the program and compare the output

### Errors in Asynch Code
* If your `try/catch` block is synchronous, but an error occurs in your *asynchronous* code, then the `try/catch` block will not catch the error!
* You could put a `try/catch` block inside your async code, but that's not usually the best way!
* Let's try a different approach.

### Error Parameters in Callback Functions
* By adding an `error` (or `err`) parameter to our callback functions, we can pass errors around and process them where necessary
* By convention, the `err` parameter will be the *first* parameter in the callback.
* Within the callback function, we can add an `if/else` statement to check for the existence of a defined error parameter, and handle the error there.

## Callback Hell
Callbacks still have a problem: when we need to do several callbacks in a row, we're in a place called **`CALLBACK HELL`**.

The takeaway: **If you have more than two callbacks, you're in callback hell!**

## Promises
**Promises** give us a better syntax with which to handle callbacks, especially when we have multiple asynchronous calls that take an unknown time to execute

A **promise** is an Object that represents an assurance that some data will exist in the future.

### Promise states
A promise can be in one of 3 states (imagine an order receipt at a restaurant):
* **Pending**: You've been given a receipt for your order. Wait.
* **Fulfilled**: Your order is ready! You can present the receipt and get your food.
* **Rejected**: There was a problem with your order. You have to do something else besides get the food you wanted!

A **pending** promise will eventually turn into a **fulfilled** promise *or* a **rejected** promise.

### Using a Promise
1. Create an **`executor function`** to create a promise.
2. **`Consume`** the promise (i.e. use it).

NOTE: We will be consuming promises far more than we will be creating executor functions! But here's an example:

```JS
const ExecutorFunc = (resolveFct, rejectFct) => {
  //Explicit error variable to trigger success/fail
  const error = true;
  //Some async code we want to run, with a 3-sec timeout
  setTimeout(() => {
    if (error) {
      //error case
      rejectFct("Failure!")
    } else {
      //success case
      resolveFct("Success!");
    }
  }, 3000);
};

//1. Create the promise
const promiseObj = new Promise(ExecutorFunc);

//2. Consume the promise with .then and .catch
promiseObj
  .then((result) => console.log(result))
  .catch((err) => console.log(err));
```

### Promise.all
For multiple promises, you can chain them, OR you can use `Promise.all`

```JS
Promise
  .all([promiseFnc1(), promiseFnc2(), promiseFnc3()])
  .then(result => {
    //result is an array! If everything worked, the array contains the results of each resolved promise!
    console.log(result[0], result[1], result[2]);
  }
  .catch(err => console.log(err));
  })
```