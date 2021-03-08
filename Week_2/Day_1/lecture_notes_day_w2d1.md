# Automated Testing

## Why Automated Tests? What is the benefit?
* To make sure your code output matches the expected output
* To make sure changes to your code don't break previous functionality
* To collect all the tests into one place to run them at once
* Writing tests makes us think about potential bugs up-front
* Automated tests can be integrated into a build workflow
* Main takeaway: **automated testing improves overall code quality!**

## What is Test-Driven Development?
* Write the tests FIRST, then write code to solve your tests:
  1. Write a failing test to indicate needed functionality and behavior
  2. Write the minimal amount of code to make the test pass.
  3. Refactor the code to make it more readab

## Example 1
```JS
const numberOfVowels = function (str) {

};

console.assert(numberOfVowels("tomato") === 3, 'it should have 3 vowels');
```

  1. Start with the minimum code that solves that test
  2. Write another test that breaks it
  3. Write more code that solves that test as well!
  4. Continue until your function passes every test you can think of

## Non-Optimal Assert Options
* `console.assert()` is usable, but it only logs to the console if the assertion fails
* Node has a built-in assertion library with advanced assertions, such as `true`, `false`, `equal`, `deepEqual` (for objects or arrays), etc.
* The problem here is that Node's assertions throw errors when they fail, which stops subsequent tests from executing
* This means that each Node assertion must be wrapped in a try/catch statement to handle the error without breaking things

### Try/Catch
* Two blocks: try {} and catch {}
```JS
try {
  // What we want to do normally
} catch (error) {
  // What we will do if an error is thrown
}
```
* When an error happens, JS dumps all the information about the error into an `Error` object, which is then accessible through `catch`

## Mocha and Chai
* Mocha and Chai were created to keep us from having to use try/catch all over the place
* **Mocha** gives us a better framework for writing the test overall, with `describe` and `it`, graceful error handling, pending tests, and pretty console logging for both successful and failed tests
* **Chai** is a BDD/TDD assertion library that helps us use more natural language and user stories to describe the *behavior* of the system from the user's point of view
* It gives us flexible options for how to state our tests: `should`. `expect`, and `assert`! They all have the same capabilities for testing, but they read differently.
  * These three are all the same:
  * `expect(result).to.deep.equal([1,2])`
  * `assert.deepEqual(result, [1, 2])`
  * `result.should.deep.equal([1, 2])`

## OBJECT SHORTHAND
If you want to create an object key/value pair where a variable name is the name of the key, and the variable value is the value of the key, you can use a shorthand:
  ```JS
  const firstName = "Paul";
  const lastName = "Ladd";
  const nickName = "Pladd";

  const pladdObj = {firstName, lastName, nickName};
  //Resulting pladdObj is:
  /*
    {
      firstName: "Paul",
      lastName: "Ladd",
      nickName: "Pladd"
    }
  */
  ```