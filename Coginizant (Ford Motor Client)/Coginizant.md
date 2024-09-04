
# Java Full Stack Interview Questions for Cognizant
## First Round Assessment

### Coding Questions
1. **Question 1: Implement a React component that filters a list of transactions based on an input date and sorts the list based on the amount when the amount header is clicked**
   
3. **Question 2:Implement a Spring Boot application with POST, GET, and DELETE APIs. Include proper response statuses and separate the controller, service, and repository layers** 
### 4 Multiple Choice Questions


## Technical Round 1 - Cognizant Interview

### 1. Self Introduction
**Answer:** [Provide a brief introduction about yourself, your experience, and your technical expertise.]

### 2. About your project
**Answer:** [Explain your project, its objectives, the technologies used, and your role in it.]

### 3. Have you worked on GCP and deployed any project in GCP?
**Answer:** [Yes/No. If yes, explain the project and deployment process.]

### 4. How many React projects have you worked on?
**Answer:** [State the number of projects and briefly describe each.]

### 5. Explain props in React.
**Answer:** Props are short for properties and are used to pass data from one component to another in React.

### 6. How to pass data from child to parent in React.
**Answer:** By passing a function as a prop to the child component and then calling that function in the child component with the data you want to pass.

### 7. How to validate props in React.
**Answer:** By using PropTypes, a library for type-checking props.

#### 8. Have you used reusable components in React? Give an example.
**Answer:** Yes, for example, a Button component that can be used across different parts of an application.

### 9. Explain lazy loading in React.
**Answer:** Lazy loading in React is a technique for delaying the loading of non-critical resources during the initial loading phase.

### 10. What is React.lazy?
**Answer:** `React.lazy` is a function that lets you render a dynamic import as a regular component.

### 11. What are React fragments?
**Answer:** React fragments allow you to group a list of children without adding extra nodes to the DOM.

### 12. Difference between fragment and div tag in React.
**Answer:** A fragment does not add an extra node to the DOM, whereas a div does.

### 13. Does using div instead of fragment take extra memory?
**Answer:** Yes, using div adds an extra node to the DOM, which can consume more memory.

### 14. Which hooks have you used in React?
**Answer:** `useState`, `useEffect`, `useContext`, `useReducer`, `useCallback`, `useMemo`, `useRef`, etc.

### 15. Explain useCallback hook.
**Answer:** `useCallback` returns a memoized callback function that only changes if one of its dependencies changes.

### 16. Explain useEffect.
**Answer:** `useEffect` is a hook that runs side effects in function components. It can be used for data fetching, direct DOM updates, and more.

### 17. What is a dependency array in useEffect?
**Answer:** The dependency array in `useEffect` specifies when the effect should be re-run based on the changes in the array items.

### 18. How do you call APIs in React?
**Answer:** By using `fetch`, `axios`, or other HTTP client libraries within a `useEffect` hook or event handler.

### 19. Explain the API intersection observer for lazy loading.
**Answer:** The Intersection Observer API is used to asynchronously observe changes in the intersection of a target element with an ancestor element or the top-level document’s viewport.

### 20. What do you use for state management in React?
**Answer:** `useState`, `useReducer`, Context API, Redux, etc.

### 21. What is Context API in React?
**Answer:** The Context API provides a way to pass data through the component tree without having to pass props down manually at every level.

### 22. Do you know Redux?
**Answer:** Yes, Redux is a state management library for JavaScript applications, used to manage the application state in a predictable way.

### 23. How do you memorize in React?
**Answer:** By using `useMemo` and `useCallback` hooks to memoize values and functions.

### 24. Using map, write any code in JavaScript.
**Answer:**
```javascript
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8]
```

### 25. What is the return type of map and forEach in JavaScript?
**Answer:** `map` returns a new array, `forEach` returns `undefined`.

### 26. Write and explain a callback function in JavaScript.
**Answer:**
```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback('Data received');
  }, 1000);
}

fetchData(data => {
  console.log(data); // Data received
});
```
A callback function is a function passed into another function as an argument, which is then invoked inside the outer function.

### 27. Write a code for a promise example.
**Answer:**
```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Promise resolved');
  }, 1000);
});

promise.then(data => {
  console.log(data); // Promise resolved
});
```

### 28. Have you used async and await in JavaScript?
**Answer:** Yes, `async` and `await` are used to handle asynchronous operations in a more readable way.

### 29. What is callback hell in React?
**Answer:** Callback hell refers to the situation where callbacks are nested within other callbacks, leading to difficult-to-read and maintain code.

### 30. How do you handle errors in ReactJS?
**Answer:** By using `try-catch` blocks, error boundaries, and error handling in promises.

### 31. If we are displaying some employee data and the employee is null, how can you handle it in React code?
**Answer:** By using conditional rendering to check if the employee data is null before attempting to display it.

### 32. Have you used the ?? operator in React?
**Answer:** Yes, the `??` (nullish coalescing) operator is used to provide a fallback value if the left-hand operand is null or undefined.

### 33. Which Java version are you using?
**Answer:** [Specify the Java version you are using.]

### 34. What are the new features in Java 8?
**Answer:** Lambda expressions, functional interfaces, Stream API, new Date and Time API, Optional class, and more.

### 35. Write a code to display today’s date and the date one month before using Java 8 features.
**Answer:**
```java
import java.time.LocalDate;

public class DateExample {
  public static void main(String[] args) {
    LocalDate today = LocalDate.now();
    LocalDate oneMonthBefore = today.minusMonths(1);
    System.out.println("Today: " + today);
    System.out.println("One Month Before: " + oneMonthBefore);
  }
}
```

### 36. Write code to display age difference using the Period class.
**Answer:**
```java
import java.time.LocalDate;
import java.time.Period;

public class AgeDifference {
  public static void main(String[] args) {
    LocalDate birthDate = LocalDate.of(1990, 1, 1);
    LocalDate today = LocalDate.now();
    Period age = Period.between(birthDate, today);
    System.out.println("Age: " + age.getYears() + " years, " + age.getMonths() + " months, " + age.getDays() + " days.");
  }
}
```

### 37. What is a functional interface in Java?
**Answer:** A functional interface is an interface with exactly one abstract method, which can be used as a target for lambda expressions and method references.

### 38. Write a custom functional interface.
**Answer:**
```java
@FunctionalInterface
public interface MyFunctionalInterface {
    int sum(int a, int b);
}

// Example usage
public class FunctionalInterfaceExample {
    public static void main(String[] args) {
        // Implementing the sum method using a lambda expression
        MyFunctionalInterface addition = (a, b) -> a + b;

        // Executing the sum method
        int result = addition.sum(5, 3);
        System.out.println("Sum: " + result); // Sum: 8
    }
}

```

### 39. Why use the sum method instead of the apply method in Java?
**Answer:**

In the context of the custom functional interface, the `sum` method is specifically named and defined to perform a summation operation on two integers. Here's why using the `sum` method instead of a more generic method name like `apply` can be advantageous:

1. **Clarity and Intent**: Naming the method `sum` clearly indicates its purpose is to add two numbers. This makes the code more readable and the intent of the method obvious to anyone who reads it.
   
2. **Domain-Specific Naming**: In this case, the interface is designed for summing two integers. Using a domain-specific name like `sum` rather than a generic name like `apply` aligns with the single-responsibility principle and makes the code easier to understand and maintain.

3. **Consistency with Functional Interfaces**: While the standard functional interfaces like `Function` use generic names like `apply` to support a wide range of operations, custom functional interfaces can benefit from specific names that denote the exact operation they perform.

Example with `apply`:
```java
@FunctionalInterface
public interface MyFunctionalInterface {
    int apply(int a, int b);
}

// Usage
public class FunctionalInterfaceExample {
    public static void main(String[] args) {
        MyFunctionalInterface addition = (a, b) -> a + b;
        int result = addition.apply(5, 3);
        System.out.println("Result: " + result); // Result: 8
    }
}
```

Example with `sum`:
```java
@FunctionalInterface
public interface MyFunctionalInterface {
    int sum(int a, int b);
}

// Usage
public class FunctionalInterfaceExample {
    public static void main(String[] args) {
        MyFunctionalInterface addition = (a, b) -> a + b;
        int result = addition.sum(5, 3);
        System.out.println("Sum: " + result); // Sum: 8
    }
}
```

Using `sum` in the custom functional interface makes the purpose of the method clear and specific, enhancing code readability and maintainability.

### 40. Why do you need a custom functional interface? Give an example.
**Answer:** Custom functional interfaces are needed when you want to define a specific contract that doesn't match existing functional interfaces.
```java
@FunctionalInterface
public interface StringConcatenator {
  String concatenate(String a, String b);
}
```

### 41. What are streams in Java?
**Answer:** Streams represent a sequence of elements supporting sequential and parallel aggregate operations.

### 42. Explain stream functions.
**Answer:** Stream functions include operations like `filter`, `map`, `reduce`, `collect`, `forEach`, `sorted`, etc., used to process collections of objects.

### 43. Find the first non-repeated character using streams (code).
**Answer:**
```java
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.function.Function;
import java.util.stream.Collectors;

public class FirstNonRepeated {
  public static void main(String[] args) {
    String input = "swiss";
    Character result = input.chars()
        .mapToObj(c -> (char) c)
        .collect(Collectors.groupingBy(Function.identity(), LinkedHashMap::new, Collectors.counting()))
        .entrySet()
        .stream()
        .filter(entry -> entry.getValue() == 1)
        .map(Map.Entry::getKey)
        .findFirst()
        .orElse(null);

    System.out.println("First non-repeated character: " + result);
  }
}
```

### 44 Given two arrays, arr1 = [4,2,3,4,6] and arr2 = [6,8,2], the output should be distinct array [2,3,4,6,8].
**Answer:**
```java
import java.util.Arrays;
import java.util.Set;
import java.util.TreeSet;

public class MergeArrays {
  public static void main(String[] args) {
    Integer[] arr1 = {4, 2, 3, 4, 6};
    Integer[] arr2 = {6, 8, 2};
    Set<Integer> resultSet = new TreeSet<>(Arrays.asList(arr1));
    resultSet.addAll(Arrays.asList(arr2));
    System.out.println(resultSet); // [2, 3, 4, 6, 8]
  }
}
```

### 45. What is Spring Boot?
**Answer:** Spring Boot is a framework for building production-ready Spring applications quickly with convention over configuration.

### 46. What are the basic annotations in Spring Boot?
**Answer:** `@SpringBootApplication`, `@RestController`, `@RequestMapping`, `@Autowired`, etc.

### 47. What is Spring Security?
**Answer:** Spring Security is a framework that focuses on providing authentication and authorization to Spring applications.

### 48. What is method-level security?
**Answer:** Method-level security allows you to apply security rules directly on methods using annotations like `@PreAuthorize` and `@Secured`.

### 49. What is the difference between @Component and @Bean?
**Answer:** `@Component` is used to denote a class as a Spring component, while `@Bean` is used to declare a bean inside a configuration class.

### 50. What is the difference between @Primary and @Qualifier?
**Answer:** `@Primary` is used to give a higher preference to a bean when multiple beans of the same type exist, while `@Qualifier` is used to specify which bean to use when multiple options are available.

### 51. What is the difference between @Controller and @RestController?
**Answer:** `@Controller` is used for traditional MVC controllers, returning views. `@RestController` combines `@Controller` and `@ResponseBody`, returning JSON/XML responses directly.

### 52. Given the following structure, create an entity class in Spring Boot using JPA annotations.
```json
{
  "empId": "",
  "empName": "",
  "email": "",
  "department": {
    "deptId": "",
    "deptName": "",
    "projects": [
      {
        "projectId": "",
        "projectName": ""
      },
      {
        "projectId": "",
        "projectName": ""
      }
    ]
  }
}
```
**Answer:**
```java
import javax.persistence.*;
import java.util.List;

@Entity
public class Employee {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long empId;
  private String empName;
  private String email;

  @ManyToOne
  @JoinColumn(name = "deptId")
  private Department department;

  // Getters and Setters
}

@Entity
public class Department {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long deptId;
  private String deptName;

  @OneToMany(mappedBy = "department", cascade = CascadeType.ALL)
  private List<Project> projects;

  // Getters and Setters
}

@Entity
public class Project {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long projectId;
  private String projectName;

  @ManyToOne
  @JoinColumn(name = "deptId")
  private Department department;

  // Getters and Setters
}
```

## Final Round  - Cognizant Interview

### 1. Explain your experience in React projects and the components you have worked on.
**Answer:** I have worked on several React projects, including a bank application where I primarily focused on the user registration page and transaction data handling. I have worked with various components such as forms, modals, tables, and custom reusable components.

### 2. What is the purpose of Context API?
**Answer:** The Context API is used to share data across the component tree without passing props down manually at every level. It helps manage state globally, making it easier to handle shared data like user authentication, themes, and settings.

### 3. Have you passed data through the backend using authentication via headers or body?
**Answer:** Yes, I have passed data through the backend using authentication via headers. Typically, I use JWT tokens in the headers for secure communication between the client and server.

### 4. How do you validate your data and which components have you used in your project?
**Answer:** I validate data using Formik along with Yup for schema validation. Formik handles form state management and validation, while Yup is used for defining validation schemas.

### 5. Are you using Formik in your project globally or in every component?
**Answer:** I use Formik in every component where form handling is required. This ensures each form has its own state and validation logic.

### 6. How do you validate passwords in your ReactJS application?
**Answer:** I validate passwords using Formik and Yup. Yup allows me to define complex validation rules, such as minimum length, inclusion of special characters, and matching confirmation passwords.

### 7. Have you created any reusable components in your project?
**Answer:** Yes, I have created several reusable components, such as input fields, buttons, modals, and form validation schemas. These components help maintain consistency and reduce code duplication.

### 8. For security purposes, are you passing JWT tokens from client-side to server-side?
**Answer:** Yes, I pass JWT tokens from the client-side to the server-side through HTTP headers to ensure secure communication and authentication.

### 9. How is JWT working, and are you validating it on the server-side or client-side?
**Answer:** JWT tokens are generated upon user authentication and sent to the client. They are then included in the HTTP headers for subsequent requests. Validation is done on the server-side to ensure the token's authenticity and to grant access to protected routes.

### 10. How do you test your React components?
**Answer:** I test my React components using tools like Jest and React Testing Library. These tools allow me to write unit tests and integration tests to ensure component functionality and behavior.

### 11. How do you improve performance in your components?
**Answer:** I improve performance by using techniques such as memoization with `React.memo`, optimizing re-renders with `useCallback` and `useMemo`, lazy loading components with `React.lazy`, and ensuring efficient state management.

### 12. Have you used refs in your project?
**Answer:** Yes, I have used refs for accessing DOM elements directly, managing focus, and integrating with third-party libraries where direct DOM manipulation is required.

### 13 What are the key features introduced in ES6?

**Answer:**
1. **Arrow Functions:** Provides a shorter syntax for writing functions.
    ```javascript
    const add = (a, b) => a + b;
    ```

2. **Classes:** Simplifies the creation of objects and inheritance.
    ```javascript
    class Person {
        constructor(name) {
            this.name = name;
        }

        greet() {
            console.log(`Hello, my name is ${this.name}`);
        }
    }

    const john = new Person('John');
    john.greet();
    ```

3. **Template Literals:** Allows string interpolation and multi-line strings.
    ```javascript
    const name = 'John';
    const message = `Hello, ${name}!`;
    console.log(message);
    ```

4. **Default Parameters:** Enables function parameters to have default values.
    ```javascript
    function greet(name = 'Guest') {
        console.log(`Hello, ${name}`);
    }

    greet(); // Hello, Guest
    ```

5. **Destructuring Assignment:** Extracts values from arrays or objects into distinct variables.
    ```javascript
    const person = { name: 'John', age: 30 };
    const { name, age } = person;
    console.log(name, age); // John 30

    const [first, second] = [10, 20];
    console.log(first, second); // 10 20
    ```

6. **Rest and Spread Operators:** Used with arrays and objects.
    ```javascript
    function sum(...numbers) {
        return numbers.reduce((acc, curr) => acc + curr, 0);
    }

    console.log(sum(1, 2, 3)); // 6

    const arr1 = [1, 2, 3];
    const arr2 = [...arr1, 4, 5, 6];
    console.log(arr2); // [1, 2, 3, 4, 5, 6]

    const obj1 = { a: 1, b: 2 };
    const obj2 = { ...obj1, c: 3 };
    console.log(obj2); // { a: 1, b: 2, c: 3 }
    ```

7. **Promises:** For asynchronous programming.
    ```javascript
    const promise = new Promise((resolve, reject) => {
        setTimeout(() => resolve('Success!'), 1000);
    });

    promise.then(result => console.log(result)); // Success!
    ```

8. **Modules:** Enables import and export of modules.
    ```javascript
    // module.js
    export const name = 'John';

    // main.js
    import { name } from './module.js';
    console.log(name); // John
    ```

9. **Enhanced Object Literals:** Makes object creation easier.
    ```javascript
    const name = 'John';
    const person = {
        name,
        greet() {
            console.log(`Hello, my name is ${this.name}`);
        }
    };

    person.greet(); // Hello, my name is John
    ```

10. **Let and Const:** Introduces block-scoped variables and constants.
    ```javascript
    let variable = 'I can be reassigned';
    const constant = 'I cannot be reassigned';

    variable = 'New value';
    console.log(variable); // New value

    // constant = 'New value'; // Error: Assignment to constant variable
    ```

---

### 14. What is the difference between a React functional component and an arrow component?

**Answer:**
- **React Functional Component:**
  A React functional component is a JavaScript function that returns a React element. It can be written using the `function` keyword.
  ```javascript
  function MyComponent() {
      return <div>Hello, World!</div>;
  }
  ```

- **Arrow Component:**
  An arrow component is a functional component defined using the ES6 arrow function syntax. It also returns a React element.
  ```javascript
  const MyComponent = () => {
      return <div>Hello, World!</div>;
  }
  ```

**Key Differences:**
1. **Syntax:** Functional components use the `function` keyword, while arrow components use the arrow function `=>` syntax.
2. **`this` Binding:** Arrow functions do not have their own `this` context, inheriting it from the parent scope. Functional components with the `function` keyword have their own `this` context, which can be useful in class components but less so in functional components.
3. **Conciseness:** Arrow functions are often more concise and can be written in a single line if the function body is simple.

---

### 15 Why would you use an arrow function in a React component?

**Answer:**
1. **Lexical `this` Binding:** Arrow functions do not have their own `this` context and inherit `this` from the parent scope. This prevents common mistakes with `this` binding in class components.
    ```javascript
    class MyComponent extends React.Component {
        handleClick = () => {
            console.log(this); // `this` refers to the component instance
        }

        render() {
            return <button onClick={this.handleClick}>Click me</button>;
        }
    }
    ```

2. **Simplified Syntax:** Arrow functions provide a more concise and readable syntax, especially for simple functions.
    ```javascript
    const MyComponent = () => <div>Hello, World!</div>;
    ```

3. **No Need for Binding:** In class components, methods defined with arrow functions do not need to be explicitly bound in the constructor, reducing boilerplate code.
    ```javascript
    class MyComponent extends React.Component {
        constructor(props) {
            super(props);
            this.handleClick = this.handleClick.bind(this); // Not needed with arrow functions
        }

        handleClick() {
            console.log(this); // `this` is undefined without binding
        }

        render() {
            return <button onClick={this.handleClick}>Click me</button>;
        }
    }
    ```

4. **Consistency:** Using arrow functions throughout your codebase can provide consistency, especially when working with functional components and hooks.


......etc (General Questions && Project-Oriented Questions)

## HR Round - Cognizant Interview
- salary & project etc....
## Ford Motor Client Interview
- soon
