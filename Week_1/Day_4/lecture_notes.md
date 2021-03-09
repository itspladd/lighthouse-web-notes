# Day 4 Lecture Notes

## Q and A
* Question 1: what are good ways to loop through objects?
  *   Example:
      ```JS
      const object = {
        one: {name: 'Milk', qty: 2, price: 4},
        two: {name: 'Chips', qty: 1, price: 2},
        three: {name: 'Eggs', qty: 1, price: 3.45},
      }

      //To add values together:
      //Method 1
      let sum = 0;
      for (let key in object) {
        sum += object[key].price * object[key].qty;
      }
      //Method 2
      const keysArr = Object.keys(object);
      let sum = 0;
      for (let key of keysArr) {
        sum += object[key].price * object[key].qty;
      }
      //Method 3, slightly less code in the for loop
      const values = Object.values(object);
      for (let item of values) {
        sum += item.qty * item.price;
      }
      ```
* NOTE: DON'T GOLF YOUR CODE! It makes it hard for you and others to maintain later!

## Review of Functions
* What are functions?
  * A function is a reusable chunk of code with a name and optional parameters
  * A function can return values, or have side effects, or both!
  * Without a return statement, the function returns `undefined`
* What are they for?
  * Keeping code clean, saving time
* Parameters
  * You don't have to pass every parameter that a function has! It will only cause a problem if you try to use a parameter that isn't defined!
  * What about another function as a parameter? Oh no.

## Functions as Parameters
* If you have a function defined into a variable name, you can pass that function into another function! YOWZA
* This is called a CALLBACK
* A *callback* is a function passed into another function

## Callbacks
* A callback can be a named function or an anonymous function! You can define the function right in the argument list!
  ```JS
  const test = function (arg1, arg2) {
    console.log(arg1);
    console.log(arg2());
  }

  test("Hello", function () {
    console.log("Goodbye");
  })
  ```
* A function that takes another function as a parameter is called a **HIGH ORDER FUNCTION**
* A function that is a parameter of another function is a **CALLBACK**

## Okay, but..like..WHY
* Check out the printOnly example:
  ```JS
    // write a function that takes an array as an argument.
    // then it prints out ONLY numbers from this array.
    // 1,3,5,7,9
    const arr = [1,'two', 3, 'four', 5, 'six', 7, 'eight', 9, 'ten'];

    const printOnlyNumbers = function(arr) {
      // we have an array
      // we loop through array
      for (let item of arr) {
        // we check if the item we loop through is a number
        if (typeof item === 'number') {
          // if it is a number ---> print
          console.log(item);
        }
      }
    }

    console.log(printOnlyNumbers(arr));

    // write a function that takes an array as an argument.
    // then it prints out ONLY strings from this array.
    // two, four, six, eight, ten

    // const printOnlyStrings = function() { .... }
    const printOnlyStrings = (arr) => {
      for (let item of arr) {
        if (typeof item === 'string') {
          console.log(item);
        }
      }
    }
  ```
* Two functions to do the same basic thing, but with different datatypes? Bleh! Callbacks can make it better!
* Check this out:
  ```JS
  const arr = [1,'two', 3, 'four', 5, 'six', 7, 'eight', 9, 'ten'];

  const printOnly = function(arr, callback) {
    for (let item of arr) {
      console.log(callback(item));
    }
  }

  const onlyNumCheck = function(arg) {
    if(typeof item === "number") {
      return item;
    }
  const onlyStrCheck = function(arg) {
    if(typeof item === "string") {
      return item;
    }
  }

  printOnly(arr, onlyNumCheck);
  printOnly(arr, onlyStringCheck);
  ```
* Now we can use them all independently of each other, and we're note repeating the for loop!

## MORE EXAMPLES
* First off: ES5 notation vs ES6 notation for function expressions
* ES5: ```const myFunc = function () {};```
* ES6: ```const myFunc = () => {};```
* In ES6, if it's a one-line function, it automatically returns the result of the right-hand side

### Demo 4
* Make a function that executes a callback function on each value of an input array
  ```JS
  const array = [1,2,3,4,5,6,7,8,9,10];

  const arrLOop = (arr, callback) => {
    for (let item of arr) {
      callback(item);
    }
  }

  let sum = 0;
  arrLoop(array, (val) => {
    sum += val;
  });

  console.log(sum); //Prints the sum of all the items

  arrLoop(array, (val) => {
    if (val % 2 === 0) {
      console.log(val);
    }
  });

  console.log
  ```
* Many libraries and functions already use callbacks!
* `array.forEach(callback)` is an array function that executes a callback function for each element of the array!
* `array.map(callback)` returns a NEW array, where each element is the result of using a callback function on the element of the original array!
* `array.filter(callback)` returns a new array where each element from the original array is ONLY added if the callback function returns TRUE for that element!