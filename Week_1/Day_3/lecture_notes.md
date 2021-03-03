# Day 3: Objects and Arrays

## Arrays
  * Arrays can have any number of elements, and any type of data per element.
  * Arrays are mutable, even if declared as a constant (you just can't reassign a constant array to a different array)
  * Data is accessed with array[index]
  * However, since arrays have a specific order, using multiple arrays to store the same kind of information can get annoying, since every array HAS to have the same kind of data in the same order
  * Human brains don't work that way! Maybe I want to list my middle name in my information array, and someone else doesn't, or maybe we put the information out of order
  * Also, accessing that information out of the order of the array gets annoying - you have to specify the index each time, and the index might be different depending on how the data was entered!
  * Enter: OBJECTS

## Objects
  * Similar to arrays, objects are collections of any kind of data, but they are unordered!
  * Instead, they have key:value pairs, so their information can be accessed by *name* instead of by index
  * But remember: there is NO INDEX in an object. The concept of an "index" doesn't work at all on an object!
  * Objects are contained in {} instead of in []
  * Objects are defined as {key: value, key2: value2}
  * Data is accessed with object.key
  * If the order doesn't matter, use an object!
  * When defining an object, you can use a string literal {"key":value}
  * At compile, all keys are transformed into strings by the compiler!
  * QUESTION FOR LATER: Is there a functional difference between an object in JS and the idea of a "hash table"? It seems really similar!

### Square bracket notation
  * Object values are usually accessed with dot notation: object.key
  * You can also access values with square bracket notation, similar to arrays, BUT: the value in the bracket must be a string, or a value that contains a string!
  * Example: object["key"] will work, object[key] will not!
  * Why do we have these different possibilities?! This is confusing!
  * Consider the following:
  ```JS
  const xyz = 'keyName';
  console.log(object.xyz); //This will print "undefined", because xyz!
  console.log(object[xyz]); //This will work!
  ```R
### Complexity
  * Objects can get REAL big and REAL complex, REAL fast!
  * Use sequential dot notation to access deep into nested objects!
  * For instance: `object.type.name.firstName`

### Find Data Question
  * Create a function to find a specific user with a random-looking key
  ```JS
  const users = {
    jfsjfkas: 'firstName lastName
  }

  const findUserById = function(users, id) {
    return users[id];
  }
  ```
### Find Key Question
  * Create a function to find the KEY given a specific VALUE

    ```JS
    const users = {
    jfsjfkas: 'firstName lastName',
    asdsdsss: 'Bob Trumpleton',
    }

    const findIdByUser = function (users, username) {
      //How do I loop through an object? for in loop?
      for (let key in users) {
        if (users[key] === username) {
          return key;
        }
      }
    }
    ```

    * That's one way, but you could also create an array of the keys:

    ```JS
    const userKeys = Object.keys(users); //Returns an array of all the keys!
    for (let key of userKeys) {
      if (users[key] === userName) {
        return key
      }
    }
    ```
    * This will give us a list of all the keys in an array!
    * One last method: convert the whole thing to an array of arrays:
    ```JS
    const userEntries = Object.entries(users); //Returns [[key, value], [key2, value2]]
    ```
    * There are other ways too! No Rules Just Right™ OUTBACK STEAKHOUSE BABY