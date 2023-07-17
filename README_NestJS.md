## NestJS

### Table of Contents

| No. | Questions                                                                                                                                               |
|-----|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1   | [What are the possible ways to create objects in JavaScript](#what-are-the-possible-ways-to-create-objects-in-javascript)                               |
| 2   | [How to copy object](#how-to-copy-object)                                                                                                               |
| 3   | [What is prototype chain](#what-is-a-prototype-chain)                                                                                                   |
| 4   | [What is a callback function](#what-is-a-callback-function)                                                                                             |
| 5   | [What are the three states of promise](#what-are-the-three-states-of-promise)                                                                           |
| 6   | [What is a promise](#what-is-a-promise)                                                                                                                 |
| 7   | [What is memoization](#what-is-memoization)                                                                                                             |
| 8   | [What are the differences between cookie local storage and session storage](#what-are-the-differences-between-cookie-local-storage-and-session-storage) |
| 9   | [Explain event emitter](#explain-event-emitter)                                                                                                         |

1. ### What are the possible ways to create objects in JavaScript

   There are many ways to create objects in javascript as below

    1. **Object constructor:**

       The simplest way to create an empty object is using the Object constructor. Currently, this approach is not recommended.

       ```javascript
       const object = new Object();
       ```

    2. **Object's create method:**

       The create method of Object creates a new object by passing the prototype object as a parameter

       ```javascript
       var object = Object.create(null);
       // params pass in Object.create must be null or object cant be undefined
       ```

    3. **Object literal syntax:**

       The object literal syntax (or object initializer), is a comma-separated set of name-value pairs wrapped in curly braces.

       ```javascript
       const object = {
            name: "Mai",
            age: 16
       };
 
       // Object literal property values can be of any dat  a type, including array, function, and nested object.
       ```

       **Note:** This is an easiest way to create an object

    4. **Function constructor:**

       Create any function and apply the new operator to create object instances,

       ```javascript
       function Person(name) {
         this.name = name;
         this.age = 21;
       }
       const object = new Person("Mai");
       ```

    5. **Function constructor with prototype:**

       This is similar to function constructor but it uses prototype for their properties and methods,

       ```javascript
       function Person() {}
       Person.prototype.name = "Mai";
       const object = new Person();
       ```

       This is equivalent to an instance created with an object create method with a function prototype and then call that function with an instance and parameters as arguments.

       ```javascript
       function func() {};
 
       new func(x, y, z);
       ```

       **(OR)**

       ```javascript
       // Create a new instance using function prototype.
       const newInstance = Object.create(func.prototype)
 
       // Call the function
       let result = func.call(newInstance, x, y, z),
 
       // If the result is a non-null object then use it otherwise just use the new instance.
       console.log(result && typeof result === 'object' ? result : newInstance);
       ```

    6. **ES6 Class syntax:**

       ES6 introduces class feature to create the objects

       ```javascript
       class Person {
         constructor(name) {
           this.name = name;
         }
       }
 
       const object = new Person("Mai");
       ```

    7. **Singleton pattern:**

       A Singleton is an object which can only be instantiated one time. Repeated calls to its constructor return the same instance and this way one can ensure that they don't accidentally create multiple instances.

       ```javascript
       const object = new (function () {
         this.name = "Mai";
       })();
       ```

**[⬆ Back to Top](#table-of-contents)**


---

2. ### How to copy object
    
    There are 2 case will happen when you copy object.

   1. **Shallow copy**: is just copy the reference of the root object if you change property of new object it will affect root object and vice ver sar.
      ```javascript
      const objectA = {
        name: "Mai"
      };
      const objectB = objectA;
      // Shallow coppy with = (Only shallow copies object)
       ```
      
   2. **Deep copy**: is copy the value of the root object. 
      ```javascript
      const objectA = {
        name: "Mai"
      };
      const objectB = JSON.parse(JSON.stringify(objectA));
      // Deep cpies nested objects but dooesnt copy functions
       ```
       ```javascript
      const objectA = {
      name: "Mai"
      };
      const objectB = Object.assign({}, objectA);
      // Copes the imediate members of an object including function but doesnt deep copy nested object
      
      const objectC = {...objectA};
      // Simple syntax, the preferred way to coppy an object but doesnt deep copy nested object
       ```
      
       ```javascript
      const _ = require('lodash');
      const objectA = {
      name: "Mai"
      };
      const objectB = _.cloneDeep(objectA);
      // Most powerful copy clones nested object including functions but need add external dependency to use
       ```

**[⬆ Back to Top](#table-of-contents)**

---

3. ### What is a prototype chain

   **Prototype chaining** is used to build new types of objects based on existing ones. It is similar to inheritance in a class based language.

   The prototype on object instance is available through **Object.getPrototypeOf(object)** or **\_\_proto__** property whereas prototype on constructors function is available through **Object.prototype**.


   **[⬆ Back to Top](#table-of-contents)**

---

4. ### What is a callback function 

   **Callback function**: A callback function is a function passed into another function as an argument.
   ```javascript
        function callbackFunction(name) {
          console.log("Hello " + name);
        }

        function outerFunction(callback) {
          let name = prompt("Please enter your name.");
          callback(name);
        }

        outerFunction(callbackFunction);
   ```    

**[⬆ Back to Top](#table-of-contents)**

---

5. ### What are the three states of promise
   Promises have three states:

    1. **Pending:** This is an initial state of the Promise before an operation begins
    2. **Fulfilled:** This state indicates that the specified operation was completed.
    3. **Rejected:** This state indicates that the operation did not complete. In this case an error value will be thrown.

**[⬆ Back to Top](#table-of-contents)**

---

6. ### What is a promise
A promise is an object that may produce a single value some time in the future with either a resolved value or a reason that it’s not resolved(for example, network error). It will be in one of the 3 possible states: fulfilled, rejected, or pending.

The syntax of Promise creation looks like below,

  ```javascript
    const promise = new Promise(function (resolve, reject) {
      // promise description
    });
    ```

    The usage of a promise would be as below,

    ```javascript
    const promise = new Promise(
      (resolve) => {
        setTimeout(() => {
          resolve("I'm a Promise!");
        }, 5000);
      },
      (reject) => {}
    );

    promise.then((value) => console.log(value));
  ```

The action flow of a promise will be as below,

![Screenshot](public/image/promises.png)
**[⬆ Back to Top](#table-of-contents)**

---

7. ### What is memoization

   Memoization is a programming technique which attempts to increase a function’s performance by caching its previously computed results. Each time a memoized function is called, its parameters are used to index the cache. If the data is present, then it can be returned, without executing the entire function. Otherwise the function is executed and then the result is added to the cache.
   Let's take an example of adding function with memoization,

    ```javascript
    const memoizAddition = () => {
      let cache = {};
      return (value) => {
        if (value in cache) {
          console.log("Fetching from cache");
          return cache[value]; // Here, cache.value cannot be used as property name starts with the number which is not a valid JavaScript  identifier. Hence, can only be accessed using the square bracket notation.
        } else {
          console.log("Calculating result");
          let result = value + 20;
          cache[value] = result;
          return result;
        }
      };
    };
    // returned function from memoizAddition
    const addition = memoizAddition();
    console.log(addition(20)); //output: 40 calculated
    console.log(addition(20)); //output: 40 cached
    ```

**[⬆ Back to Top](#table-of-contents)**

---

8. ### What are the differences between cookie local storage and session storage
   Below are some of the differences between cookie, local storage and session storage,

   | Feature                           | Cookie                             | Local storage    | Session storage     |
   | --------------------------------- | ---------------------------------- | ---------------- | ------------------- |
   | Accessed on client or server side | Both server-side & client-side     | client-side only | client-side only    |
   | Lifetime                          | As configured using Expires option | until deleted    | until tab is closed |
   | SSL support                       | Supported                          | Not supported    | Not supported       |
   | Maximum data size                 | 4KB                                | 5 MB             | 5MB                 |

**[⬆ Back to Top](#table-of-contents)**

---

9. ### Explain event emitter

   **Event Emitter** If you worked with JavaScript in the browser, you know how much of the interaction of the user is handled through events: mouse clicks, keyboard button presses, reacting to mouse movements, and so on.

On the backend side, Node.js offers us the option to build a similar system using the events module.

This module, in particular, offers the EventEmitter class, which we'll use to handle our events.

   ```javascript
      const EventEmitter = require('events');

      const eventEmitter = new EventEmitter();

      eventEmitter.on('start', () => {
        console.log('started');
      });
        
      eventEmitter.emit('start');
   ```    


**[⬆ Back to Top](#table-of-contents)**

---