## Basic Questions

1. **What is JavaScript?**
- JavaScript is a high-level, interpreted programming language that conforms to the ECMAScript specification. It is widely used for creating dynamic and interactive web pages.

2. **What are the data types supported by JavaScript?**
   - Number
   - String
   - Boolean
   - Undefined
   - Null
   - Object
   - Symbol (introduced in ES6)
   - BigInt (introduced in ES11)

3. **What are the different ways to declare a variable in JavaScript?**
   - `var`
   - `let`
   - `const`

4. **Explain the difference between `var`, `let`, and `const`.**
   - `var`: Function-scoped, can be re-declared and updated.
   - `let`: Block-scoped, can be updated but not re-declared within the same scope.
   - `const`: Block-scoped, cannot be updated or re-declared.

5. **What are the different types of loops in JavaScript?**
   - `for`
   - `while`
   - `do...while`
   - `for...in`
   - `for...of`

6. **Explain how `forEach` works.**
   The `forEach` method executes a provided function once for each array element.
   ```javascript
   const array = [1, 2, 3];
   array.forEach(element => console.log(element));
   ```

7. **How does the `map` function work?**
  - The `map` method creates a new array populated with the results of calling a provided function on every element in the calling array.
 ```javascript
   const array = [1, 2, 3];
   const newArray = array.map(element => element * 2);
   console.log(newArray); // [2, 4, 6]
 ```

8. **What is the difference between `==` and `===`?**
   - `==`: Abstract equality comparison (checks for value equality, performs type coercion if necessary).
   - `===`: Strict equality comparison (checks for both value and type equality).

9. **What is a closure in JavaScript?**
   - A closure is a function that retains access to its outer scope, even after the outer function has returned.
```javascript
   function outer() {
     let counter = 0;
     return function() {
       counter++;
       return counter;
     };
   }
   const increment = outer();
   console.log(increment()); // 1
   console.log(increment()); // 2
```

10. **Explain the concept of hoisting.**
    - Hoisting is JavaScript's default behavior of moving declarations to the top of the current scope (function or global scope). Only declarations (not initializations) are hoisted.
```javascript
    console.log(x); // undefined
    var x = 5;
```

11. **What is the difference between `null` and `undefined`?**
    - `null`: Explicitly represents the absence of any object value.
    - `undefined`: Indicates a variable that has been declared but not yet assigned a value.

12. **What are template literals?**
    - Template literals are string literals that allow embedded expressions, multi-line strings, and string interpolation.
```javascript
    const name = 'John';
    console.log(`Hello, ${name}!`); // Hello, John!
```

13. **What is an arrow function, and how is it different from a regular function?**
    - Arrow functions are a shorthand for writing function expressions. They do not have their own `this`, `arguments`, `super`, or `new.target` bindings.
```javascript
    const add = (a, b) => a + b;
```

14. **Explain the use of the `this` keyword.**
    - The `this` keyword refers to the object it belongs to. Its value depends on how the function is called.
```javascript
    const obj = {
      value: 42,
      getValue() {
        return this.value;
      }
    };
    console.log(obj.getValue()); // 42
```

15. **What is the difference between function declaration and function expression?**
    - Function Declaration:
      ```javascript
      function greet() {
        console.log('Hello');
      }
      ```
    - Function Expression:
      ```javascript
      const greet = function() {
        console.log('Hello');
      };
      ```

16. **What is an Immediately Invoked Function Expression (IIFE)?**
   -  An IIFE is a function that is executed immediately after it is defined.
   ```javascript
    (function() {
      console.log('IIFE');
    })();
   ```

17. **Explain the concept of event delegation.**
   - Event delegation involves using a single event listener to manage events for multiple elements by taking advantage of event bubbling.
   ```javascript
    document.getElementById('parent').addEventListener('click', function(event) {
      if (event.target && event.target.matches('button.classname')) {
        console.log('Button clicked');
      }
    });
   ```

18. **How do you handle errors in JavaScript?**
   - Errors in JavaScript can be handled using `try...catch` blocks.
   ```javascript
    try {
      // Code that may throw an error
    } catch (error) {
      console.log(error.message);
    }
   ```

19. **What is the purpose of the `try...catch` block?**
   - The `try...catch` block is used to handle exceptions. Code within the `try` block is executed, and if an error occurs, it is caught in the `catch` block.

20. **Explain the concept of promises in JavaScript.**
   - A promise is an object representing the eventual completion or failure of an asynchronous operation.
   ```javascript
    const promise = new Promise((resolve, reject) => {
      setTimeout(() => resolve('Success'), 1000);
    });
    promise.then(result => console.log(result));
   ```

## Intermediate Questions

21. **What are async/await, and how do they relate to promises?**
   - `async/await` is syntactic sugar for working with promises. `async` functions return promises, and `await` is used to wait for the promise to resolve.
   ```javascript
    async function fetchData() {
      const response = await fetch('url');
      const data = await response.json();
      return data;
    }
   ```

22. **What is a callback function?**
   - A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some action.
   ```javascript
    function greet(name, callback) {
      console.log('Hello ' + name);
      callback();
    }
    greet('John', function() {
      console.log('Callback executed');
    });
   ```

23. **Explain the concept of callback hell and how to avoid it.**
   - Callback hell refers to the situation where callbacks are nested within other callbacks, making the code difficult to read and maintain. It can be avoided using promises or async/await.
   ```javascript
    // Callback hell
    doSomething(function(result) {
      doSomethingElse(result, function(newResult) {
        doAnotherThing(newResult, function(finalResult) {
          console.log(finalResult);
        });
      });
    });

    // Using promises
    doSomething()
      .then(result => doSomethingElse(result))
      .then(newResult => doAnotherThing(newResult))
      .then(finalResult => console.log(finalResult))
      .catch(error => console.error(error));

    // Using async/await
    async function process() {
      try {
        const result = await doSomething();
        const newResult = await doSomethingElse(result);
        const finalResult = await doAnotherThing(newResult);
        console.log(finalResult);
      } catch (error) {
        console.error(error);
      }
    }
    process();
   ```

24. **What are JavaScript modules?**
   - JavaScript modules allow you to break down your code into smaller, reusable pieces, making it easier to manage and maintain. Modules can export and import functionalities between each other.

25. **How do you export and import modules in JavaScript?**
    - Exporting:
    ```javascript
      // module.js
      export const value = 42;
      export function greet() {
        console.log('Hello');
      }
    ```
    - Importing:
    ```javascript
      // main.js
      import { value, greet } from './module.js';
      console.log(value); // 42
      greet(); // Hello
    ```

26. **What is the purpose of the `spread` operator?**
   - The `spread` operator (`...`) allows an iterable to be expanded in places where zero or more arguments or elements are expected.
   ```javascript
    const arr1 = [1, 2, 3];
    const arr2 = [...arr1, 4, 5, 6];
    console.log(arr2); // [1, 2, 3, 4, 5, 6]
   ```

27. **How does the `rest` operator work?**
    - The `rest` operator (`...`) allows us to represent an indefinite number of arguments as an array.
   ```javascript
    function sum(...numbers) {
      return numbers.reduce((acc, curr) => acc + curr, 0);
    }
    console.log(sum(1, 2, 3)); // 6
   ```

28. **What is destructuring assignment?**
   - Destructuring assignment allows you to unpack values from arrays or properties from objects into distinct variables.
   ```javascript
    const [a, b] = [1, 2];
    console.log(a, b); // 1 2

    const {name, age} = {name: 'John', age: 30};
    console.log(name, age); // John 30
   ```

29. **What is the event loop in JavaScript?**
   - The event loop is responsible for executing the code, collecting and processing events, and executing queued sub-tasks in JavaScript's runtime.

30. **Explain the concept of single-threaded in JavaScript.**
   - JavaScript is single-threaded, meaning it has one call stack and executes one command at a time.

31. **What are higher-order functions?**
   - Higher-order functions are functions that take other functions as arguments or return functions as their result.
   ```javascript
    function greet() {
      return function(name) {
        console.log('Hello ' + name);
      };
    }
    const sayHello = greet();
    sayHello('John'); // Hello John
   ```

32. **How do you create a class in JavaScript?**
   ```javascript
    class Person {
      constructor(name, age) {
        this.name = name;
        this.age = age;
      }
      greet() {
        console.log(`Hello, my name is ${this.name}`);
      }
    }
    const john = new Person('John', 30);
    john.greet(); // Hello, my name is John
   ```

33. **What are getters and setters in JavaScript classes?**
   - Getters and setters allow you to define object accessors (computed properties).
   ```javascript
    class Person {
      constructor(name) {
        this._name = name;
      }
      get name() {
        return this._name;
      }
      set name(value) {
        this._name = value;
      }
    }
    const john = new Person('John');
    console.log(john.name); // John
    john.name = 'Doe';
    console.log(john.name); // Doe
   ```

34. **What is prototype inheritance?**
   - Prototype inheritance is a feature in JavaScript where objects inherit properties and methods from other objects.
```javascript
    function Person(name) {
      this.name = name;
    }
    Person.prototype.greet = function() {
      console.log(`Hello, my name is ${this.name}`);
    };
    const john = new Person('John');
    john.greet(); // Hello, my name is John
   ```

35. **How does the `prototype` chain work?**
   - The prototype chain is a series of links between objects, where each object has a link to another object, known as its prototype. This chain ends when an object has a `null` prototype.

36. **What is the difference between classical inheritance and prototypal inheritance?**
    - Classical inheritance: Involves creating a class hierarchy where classes inherit from other classes.
    - Prototypal inheritance: Involves creating objects that inherit directly from other objects.

37. **What are pure functions?**
   - Pure functions are functions that always produce the same output for the same input and have no side effects.
```javascript
    function add(a, b) {
      return a + b;
    }
```

38. **What is the concept of immutability in JavaScript?**
   - Immutability means that an object cannot be modified after it is created. Instead of modifying an object, a new object is created with the desired changes.
```javascript
    const obj = { a: 1 };
    const newObj = { ...obj, b: 2 };
    console.log(newObj); // { a: 1, b: 2 }
```

39. **Explain the concept of `strict mode`.**
   - `Strict mode` is a way to opt into a restricted variant of JavaScript, which helps catch common coding mistakes and "unsafe" actions.
   ```javascript
    'use strict';
    x = 3.14; // This will cause an error because x is not declared
   ```

40. **What are the differences between `call`, `apply`, and `bind`?**
    - `call`: Invokes a function with a given `this` value and arguments provided individually.
    ```javascript
      function greet() {
        console.log(`Hello, ${this.name}`);
      }
      const obj = { name: 'John' };
      greet.call(obj); // Hello, John
    ```
    - `apply`: Invokes a function with a given `this` value and arguments provided as an array.
    ```javascript
      function greet(greeting) {
        console.log(`${greeting}, ${this.name}`);
      }
      const obj = { name: 'John' };
      greet.apply(obj, ['Hello']); // Hello, John
    ```
    - `bind`: Returns a new function with a given `this` value and optionally some arguments pre-filled.
    ```javascript
      function greet(greeting) {
        console.log(`${greeting}, ${this.name}`);
      }
      const obj = { name: 'John' };
      const boundGreet = greet.bind(obj);
      boundGreet('Hello'); // Hello, John
    ```

## Advanced Questions

41. **What is an async function?**
   - An `async` function is a function declared with the `async` keyword, which allows the use of `await` within it to pause execution until the awaited promise is resolved.
   ```javascript
    async function fetchData() {
      const response = await fetch('url');
      const data = await response.json();
      return data;
    }
   ```

42. **How do you handle asynchronous operations in JavaScript?**
   - Asynchronous operations can be handled using callbacks, promises, or `async/await`.
  ```javascript
    // Using callbacks
    function fetchData(callback) {
      setTimeout(() => callback('Data'), 1000);
    }
    fetchData(data => console.log(data)); // Data

    // Using promises
    const promise = new Promise((resolve, reject) => {
      setTimeout(() => resolve('Data'), 1000);
    });
    promise.then(data => console.log(data)); // Data

    // Using async/await
    async function fetchData() {
      const data = await new Promise((resolve) => {
        setTimeout(() => resolve('Data'), 1000);
      });
      console.log(data); // Data
    }
    fetchData();
  ```

43. **What is the `fetch` API?**
    - The `fetch` API is a modern interface that allows you to make network requests similar to `XMLHttpRequest`. It returns a promise.
   ```javascript
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => console.log(data))
      .catch(error => console.error('Error:', error));
   ```

44. **How do you make an HTTP request in JavaScript?**
   - You can make an HTTP request using the `fetch` API, `XMLHttpRequest`, or third-party libraries like Axios.
 ```javascript
    // Using fetch
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => console.log(data));

    // Using XMLHttpRequest
    const xhr = new XMLHttpRequest();
    xhr.open('GET', 'https://api.example.com/data', true);
    xhr.onload = function() {
      if (xhr.status === 200) {
        console.log(JSON.parse(xhr.responseText));
      }
    };
    xhr.send();
 ```

45. **What are service workers?**
    - Service workers are scripts that run in the background, separate from the web page, enabling features such as background sync, push notifications, and offline caching.
```javascript
    if ('serviceWorker' in navigator) {
      navigator.serviceWorker.register('/service-worker.js')
        .then(registration => {
          console.log('Service Worker registered with scope:', registration.scope);
        })
        .catch(error => {
          console.error('Service Worker registration failed:', error);
        });
    }
```

46. **How do you implement caching in JavaScript?**
    Caching can be implemented using service workers and the Cache API.
```javascript
    // In service-worker.js
    self.addEventListener('install', event => {
      event.waitUntil(
        caches.open('v1').then(cache => {
          return cache.addAll([
            '/',
            '/index.html',
            '/styles.css',
            '/script.js',
          ]);
        })
      );
    });

    self.addEventListener('fetch', event => {
      event.respondWith(
        caches.match(event.request).then(response => {
          return response || fetch(event.request);
        })
      );
    });
```

47. **What is the purpose of the `Symbol` type?**
    - `Symbol` is a unique and immutable primitive value that can be used as the key of an object property, ensuring that property keys do not collide.
```javascript
    const sym1 = Symbol('description');
    const sym2 = Symbol('description');
    console.log(sym1 === sym2); // false
```

48. **What are weak maps and weak sets?**
    - WeakMap: A collection of key-value pairs where the keys are weakly referenced, meaning they do not prevent garbage collection if there are no other references to the object.
    - WeakSet: A collection of objects, where the objects are weakly referenced.

49. **How do you create and use generators in JavaScript?**
    - Generators are functions that can be paused and resumed, using the `function*` syntax and `yield` keyword.
```javascript
    function* generatorFunction() {
      yield 'First';
      yield 'Second';
      return 'Third';
    }
    const generator = generatorFunction();
    console.log(generator.next().value); // First
    console.log(generator.next().value); // Second
    console.log(generator.next().value); // Third
```

50. **What is the purpose of the `yield` keyword?**
    - The `yield` keyword is used in generator functions to pause the function execution and return a value to the caller. The function can be resumed later.
```javascript
    function* generatorFunction() {
      yield 'First';
      yield 'Second';
    }
    const generator = generatorFunction();
    console.log(generator.next().value); // First
    console.log(generator.next().value); // Second
```

51. **What are iterators and iterable objects?**
    - Iterators: Objects that define a sequence and potentially a return value upon its termination.
    - Iterable objects: Objects that implement the `[Symbol.iterator]` method and return an iterator.

52. **What is the concept of dynamic typing?**
     - Dynamic typing means that the type of a variable is determined at runtime and can change during the execution of a program.
```javascript
    let variable = 42;
    variable = 'Hello';
```

53. **How does type coercion work in JavaScript?**
    - Type coercion is the automatic or implicit conversion of values from one data type to another.
```javascript
    console.log(5 + '5'); // '55' (number to string)
    console.log('5' - 3); // 2 (string to number)
```

54. **What are the new features introduced in ECMAScript 6 (ES6)?**
    - ES6 introduced several new features such as arrow functions, classes, template literals, destructuring assignment, `let` and `const`, default parameters, rest and spread operators, promises, and more.

55. **What are promises, and how do they work?**
   - Promises are objects representing the eventual completion or failure of an asynchronous operation. They have three states: pending, fulfilled, and rejected.
```javascript
    const promise = new Promise((resolve, reject) => {
      setTimeout(() => resolve('Data'), 1000);
    });
    promise.then(data => console.log(data)); // Data
```

56. **How do you handle multiple promises in JavaScript?**
    - Multiple promises can be handled using `Promise.all` or `Promise.race`.
```javascript
    const promise1 = Promise.resolve('First');
    const promise2 = Promise.resolve('Second');

    Promise.all([promise1, promise2]).then(values => {
      console.log(values); // ['First', 'Second']
    });
```

57. **What is the `Promise.all` method?**
    - `Promise.all` takes an iterable of promises and returns a single promise that resolves when all the promises in the iterable have resolved.
```javascript
    Promise.all([promise1, promise2])
      .then(values => console.log(values))
      .catch(error => console.error(error));
```

58. **What is the `Promise.race` method?**
    - `Promise.race` takes an iterable of promises and returns a single promise that resolves or rejects as soon as one of the promises in the iterable resolves or rejects.
```javascript
    Promise.race([promise1, promise2])
      .then(value => console.log(value))
      .catch(error => console.error(error));
```

59. **How do you create a custom promise?**
```javascript
    const customPromise = new Promise((resolve, reject) => {
      setTimeout(() => {
        const success = true;
        if (success) {
          resolve('Operation succeeded');
        } else {
          reject('Operation failed');
        }
      }, 1000);
    });

    customPromise.then(
      result => console.log(result),
      error => console.log(error)
    );
```

60. **What is the purpose of the `Proxy` object?**
  - A `Proxy` object allows you to create an object that can redefine fundamental operations like property lookup, assignment, enumeration, function invocation, etc.
```javascript
    const target = {};
    const handler = {
      get: function(obj, prop) {
        return prop in obj ? obj[prop] : 'default';
      }
    };
    const proxy = new Proxy(target, handler);
    console.log(proxy.nonExistentProperty); // 'default'
```

61. **How do you create a proxy in JavaScript?**
```javascript
    const target = {};
    const handler = {
      get: function(obj, prop) {
        return prop in obj ? obj[prop] : 'default';
      }
    };
    const proxy = new Proxy(target, handler);
```

62. **What is the `Reflect` API?**
   - The `Reflect` API provides a set of static methods to perform operations that are usually handled by the internal methods of an object.
```javascript
    const obj = { x: 1, y: 2 };
    console.log(Reflect.get(obj, 'x')); // 1
    Reflect.set(obj, 'x', 42);
    console.log(obj.x); // 42
```

63. **How does the `Reflect` API differ from normal object operations?**
   - The `Reflect` API methods provide the same functionality as proxy traps and can be used to modify the default behavior of these traps.

64. **What is the difference between synchronous and asynchronous code?**
   - Synchronous code is executed sequentially, one statement at a time. Asynchronous code is executed in parallel, allowing other operations to continue before the previous one completes.

65. **How do you debug JavaScript code?**
   - JavaScript code can be debugged using tools like browser developer tools (e.g., Chrome DevTools), adding `debugger` statements, using console logging, and utilizing debugging tools like Visual Studio Code.

66. **What are the different ways to handle asynchronous operations?**
   - Asynchronous operations can be handled using callbacks, promises, and `async/await`.

67. **How do you prevent default behavior in an event?**
   - The `preventDefault` method prevents the default action of an event from being executed.
```javascript
    document.querySelector('form').addEventListener('submit', function(event) {
      event.preventDefault();
      console.log('Form submission prevented');
    });
```

68. **What is event bubbling and event capturing?**
    - Event bubbling: Events propagate from the target element up to the root.
    - Event capturing: Events propagate from the root down to the target element.

69. **How do you stop event propagation?**
    - The `stopPropagation` method stops the event from propagating further.
```javascript
    document.querySelector('button').addEventListener('click', function(event) {
      event.stopPropagation();
      console.log('Event propagation stopped');
    });
```

70. **What are custom events in JavaScript?**
   - Custom events are user-defined events that can be dispatched and listened to.
```javascript
    const event = new CustomEvent('myEvent', { detail: { someData: 'data' } });
    document.addEventListener('myEvent', function(e) {
      console.log(e.detail.someData);
    });
    document.dispatchEvent(event); // data
```

## Expert Questions

71. **What are WebSockets?**
   - WebSockets provide a way to open a persistent connection between a client and server for real-time communication.
```javascript
    const socket = new WebSocket('ws://example.com/socket');
    socket.onopen = function(event) {
      socket.send('Hello Server!');
    };
    socket.onmessage = function(event) {
      console.log('Message from server:', event.data);
    };
```

72. **How do you implement real-time communication in JavaScript?**
   - Real-time communication can be implemented using WebSockets, Server-Sent Events (SSE), or third-party libraries like Socket.io.
```javascript
    // Using WebSockets
    const socket = new WebSocket('ws://example.com/socket');
    socket.onmessage = function(event) {
      console.log('Message from server:', event.data);
    };

    // Using Socket.io
    const io = require('socket.io-client');
    const socket = io('http://example.com');
    socket.on('message', function(data) {
      console.log('Message from server:', data);
    });
```

73. **What is the difference between local storage and session storage?**
    - Local storage: Stores data with no expiration date, accessible only within the same origin.
    - Session storage: Stores data for the duration of the page session, accessible only within the same origin.

74. **How do you store data in the browser?**
    - Data can be stored in the browser using cookies, local storage, and session storage.
```javascript
    // Local storage
    localStorage.setItem('key', 'value');
    console.log(localStorage.getItem('key')); // value

    // Session storage
    sessionStorage.setItem('key', 'value');
    console.log(sessionStorage.getItem('key')); // value
```

75. **What are the security concerns with storing data in cookies?**
    - Cookies can be intercepted during transmission.
    - Sensitive information stored in cookies can be accessed by malicious scripts if not secured properly.

76. **How do you create a regular expression in JavaScript?**
```javascript
    const regex = /pattern/;
    const regexWithFlags = /pattern/g;
```

77. **How do you use regular expressions for pattern matching?**
    - Regular expressions can be used with methods like `test`, `exec`, `match`, `replace`, `search`, and `split`.
```javascript
    const regex = /hello/;
    console.log(regex.test('hello world')); // true
    console.log('hello world'.match(regex)); // ['hello']
```

78. **What is the purpose of the `exec` method in regular expressions?**
    - The `exec` method executes a search for a match in a specified string and returns an array of matched results or `null` if no match is found.
```javascript
    const regex = /hello/;
    const result = regex.exec('hello world');
    console.log(result); // ['hello']
```

79. **What is the `RegExp` constructor?**
    - The `RegExp` constructor creates a regular expression object for matching text with a pattern.
```javascript
    const regex = new RegExp('pattern', 'flags');
```

80. **What is the difference between `let` and `var` in terms of scope?**
    - `let`: Block-scoped, not hoisted to the top of their block.
    - `var`: Function-scoped, hoisted to the top of their function.

81. **How does the `const` keyword work in JavaScript?**
    - `const` declares block-scoped constants. The value of a `const` variable cannot be changed through reassignment, but the variable itself is not immutable.
```javascript
    const obj = { key: 'value' };
    obj.key = 'new value'; // This is allowed
    obj = {}; // This will cause an error
```

82. **What is destructuring assignment?**
   - Destructuring assignment is a syntax that allows unpacking values from arrays or properties from objects into distinct variables.
```javascript
    const [a, b] = [1, 2];
    const { x, y } = { x: 10, y: 20 };
```

83. **What are template literals?**
    - Template literals are string literals allowing embedded expressions and multi-line strings, using backticks (``) instead of single or double quotes.
```javascript
    const name = 'John';
    const greeting = `Hello, ${name}!`;
```

84. **What is the rest operator, and how is it used?**
    - The rest operator (`...`) allows you to represent an indefinite number of arguments as an array.
```javascript
    function sum(...numbers) {
      return numbers.reduce((acc, num) => acc + num, 0);
    }
    console.log(sum(1, 2, 3)); // 6
```

85. **What is the spread operator, and how is it used?**
    - The spread operator (`...`) allows an iterable to expand in places where 0+ arguments are expected.
```javascript
    const arr1 = [1, 2, 3];
    const arr2 = [...arr1, 4, 5];
    console.log(arr2); // [1, 2, 3, 4, 5]
```

86. **What is a `class` in JavaScript?**
   - A `class` is a blueprint for creating objects with predefined properties and methods.
```javascript
    class Person {
      constructor(name, age) {
        this.name = name;
        this.age = age;
      }
      greet() {
        console.log(`Hello, my name is ${this.name}`);
      }
    }
```

87. **How do you create and use classes in JavaScript?**
```javascript
    class Person {
      constructor(name, age) {
        this.name = name;
        this.age = age;
      }
      greet() {
        console.log(`Hello, my name is ${this.name}`);
      }
    }
    const person = new Person('John', 30);
    person.greet(); // Hello, my name is John
```

88. **What are class inheritance and the `extends` keyword?**
   - Class inheritance allows one class to inherit properties and methods from another class using the `extends` keyword.
```javascript
    class Animal {
      constructor(name) {
        this.name = name;
      }
      speak() {
        console.log(`${this.name} makes a sound`);
      }
    }
    class Dog extends Animal {
      speak() {
        console.log(`${this.name} barks`);
      }
    }
    const dog = new Dog('Rex');
    dog.speak(); // Rex barks
```

89. **What are getters and setters in JavaScript classes?**
   - Getters and setters are special methods that get or set the value of a property.
```javascript
    class Person {
      constructor(name) {
        this._name = name;
      }
      get name() {
        return this._name;
      }
      set name(value) {
        this._name = value;
      }
    }
    const person = new Person('John');
    console.log(person.name); // John
    person.name = 'Doe';
    console.log(person.name); // Doe
```

90. **What are static methods in JavaScript classes?**
   - Static methods are defined on the class itself, not on instances of the class.
```javascript
    class MathUtils {
      static add(a, b) {
        return a + b;
      }
    }
    console.log(MathUtils.add(1, 2)); // 3
```

91. **How do you create a module in JavaScript?**
    - Modules are created by exporting variables, functions, or classes from a file and importing them into another file.
```javascript
    // math.js
    export function add(a, b) {
      return a + b;
    }

    // main.js
    import { add } from './math.js';
    console.log(add(2, 3)); // 5
```

92. **What is the purpose of `export` and `import` statements?**
   - The `export` statement is used to export functions, objects, or primitives from a module, while the `import` statement is used to import them into other modules.
```javascript
    // module.js
    export const name = 'John';

    // main.js
    import { name } from './module.js';
    console.log(name); // John
```

93. **What is the default export, and how is it used?**
    - The default export is used to export a single value from a module. It can be imported without curly braces.
```javascript
    // module.js
    export default function greet() {
      console.log('Hello');
    }

    // main.js
    import greet from './module.js';
    greet(); // Hello
```

94. **What is the difference between named exports and default exports?**
    - Named exports: Export multiple values, must be imported using the same name.
    - Default exports: Export a single value, can be imported with any name.
```javascript
    // named exports
    export const name = 'John';
    export function greet() {
      console.log('Hello');
    }

    // default export
    export default function greet() {
      console.log('Hello');
    }
```

95. **How do you handle exceptions in JavaScript?**
   - Exceptions can be handled using `try`, `catch`, `finally`, and `throw` statements.
```javascript
    try {
      throw new Error('Something went wrong');
    } catch (error) {
      console.log(error.message);
    } finally {
      console.log('This will always execute');
    }
```

96. **What is the purpose of the `finally` block?**
   - The `finally` block contains code that will be executed regardless of whether an exception is thrown or not.
```javascript
    try {
      console.log('Try block');
    } catch (error) {
      console.log('Catch block');
    } finally {
      console.log('Finally block');
    }
```

97. **How do you throw custom errors in JavaScript?**
    - Custom errors can be thrown using the `throw` statement with an instance of the `Error` class or a custom error class.
   ```javascript
    class CustomError extends Error {
      constructor(message) {
        super(message);
        this.name = 'CustomError';
      }
    }
    throw new CustomError('This is a custom error');
   ```

98. **What are async functions, and how do they work?**
    Async functions are functions that return a promise. They can be paused using the `await` keyword.
```javascript
    async function fetchData() {
      const response = await fetch('https://api.example.com/data');
      const data = await response.json();
      console.log(data);
    }
```

99. **How do you use the `await` keyword?**
    - The `await` keyword is used to wait for a promise to resolve or reject within an async function.
   ```javascript
    async function getData() {
      const response = await fetch('https://api.example.com/data');
      const data = await response.json();
      return data;
    }
    getData().then(data => console.log(data));
   ```

100. **What are the differences between classical inheritance and prototypal inheritance?**
   - **Classical inheritance**: Objects inherit from classes, typically seen in languages like Java.
   - **Prototypal inheritance**: Objects inherit directly from other objects, seen in JavaScript.

