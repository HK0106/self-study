## Javascript

### Table of Contents

| No. | Questions                                                                                                                 |
|-----|---------------------------------------------------------------------------------------------------------------------------|
| 1   | [What are the possible ways to create objects in JavaScript](#what-are-the-possible-ways-to-create-objects-in-javascript) |
| 2   | [How to copy object](#how-to-copy-object)                                                                                 |
| 3   | [What is prototype chain](#what-is-a-prototype-chain)                                                                     |

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