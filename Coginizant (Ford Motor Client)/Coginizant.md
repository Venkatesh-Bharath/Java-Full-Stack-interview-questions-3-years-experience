
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

1. **Can you provide a brief self-introduction and explain your current project?**

   - **Answer:** This question typically requires a personalized response where you introduce yourself, your background, skills, and experience. Followed by a brief description of your current project, including its goals, technologies used, and your role in the project.

2. **Given the string `String st = "Win Win!!! You have got a lottery";`, write a Java program using stream that:**
   - **Processes this string to determine if it should be classified as "Spam" or "Not Spam".**
   - **Counts the occurrences of the words "win" and "lottery".**
   - **If the count is 2.5 or less, classify the string as "Not Spam"; otherwise, classify it as "Spam".**

   ```java
   import java.util.Arrays;

   public class SpamChecker {
       public static void main(String[] args) {
           String st = "Win Win!!! You have got a lottery";

           long ans = Arrays.stream(st.toLowerCase().split("\\s+"))
                            .map(word -> word.replaceAll("[^a-zA-Z]", ""))
                            .filter(e -> e.equals("win") || e.equals("lottery"))
                            .count();

           String result = ans <= 2.5 ? "Not Spam" : "Spam";
           System.out.println(result);
       }
   }
   ```

3. **Is `count` a terminal operator or an intermediate operator in Java Streams?**

   - **Answer:** `count` is a terminal operator in Java Streams. It triggers the processing of the stream and produces a result.

4. **What is upcasting and downcasting in Java?**

   - **Answer:** 
     - **Upcasting:** Converting a subclass reference to a superclass reference. It is implicit and safe, e.g., `Dog dog = new Dog(); Animal animal = dog;`
     - **Downcasting:** Converting a superclass reference back to a subclass reference. It is explicit and requires a cast, e.g., `Animal animal = new Dog(); Dog dog = (Dog) animal;` It can cause a `ClassCastException` if the object is not actually an instance of the subclass.

5. **For a music player where you want to add and remove songs in middle, which collection is suitable and why?**

   - **Answer**:For a music player where you need to frequently add and remove songs in the middle of the collection, a **`LinkedList`** is more suitable compared to an `ArrayList`. Here's why:

   - **Efficient Insertions/Deletions**: `LinkedList` provides constant time complexity (O(1)) for inserting and deleting elements if you have a reference to the node where the operation needs to occur. This is because it involves only changing pointers between nodes, which is efficient.

    - **No Resizing Overhead**: Unlike `ArrayList`, which requires resizing and copying elements to a new array when it grows, `LinkedList` does not require resizing. This makes it more efficient for frequent insertions and deletions.
**Sequential Access**: While `LinkedList` has a higher overhead for accessing elements by index (O(n) time complexity), it excels in scenarios where you are performing many insertions and deletions rather than random access.


6. **What is the difference between `map` and `flatMap` in Java Streams?**

   - **Answer:**
     - **`map`:** Transforms each element in the stream into another object. It applies a function to each element and returns a stream of the results.
     - **`flatMap`:** Transforms each element into a stream of objects and then flattens these streams into a single stream. It is used when the transformation results in multiple elements for each input element.

7. **What are fail-fast and fail-safe iterators, and how can you overcome issues related to them?**

   - **Answer:**
     - **Fail-fast iterators:** Throw a `ConcurrentModificationException` if the collection is modified while iterating. To avoid issues, use synchronized collections or concurrent collections like `CopyOnWriteArrayList`.
     - **Fail-safe iterators:** Do not throw exceptions if the collection is modified. They work on a clone of the collection, e.g., `ConcurrentHashMap` provides fail-safe iterators.

8. **Which databases have you worked with?**

   - **Answer:** This answer should be specific to your experience. Common databases include MySQL, PostgreSQL, Oracle, SQL Server, MongoDB, etc.

9. **How would you design table structures for a scenario where a customer can place multiple orders, and each order can contain multiple products?**

   - **Answer:**
     ```sql
     CREATE TABLE Customer (
         customer_id INT PRIMARY KEY,
         customer_name VARCHAR(100)
     );

     CREATE TABLE Product (
         product_id INT PRIMARY KEY,
         product_name VARCHAR(100),
         price DECIMAL
     );

     CREATE TABLE `Order` (
         order_id INT PRIMARY KEY,
         customer_id INT,
         order_date DATE,
         FOREIGN KEY (customer_id) REFERENCES Customer(customer_id)
     );

     CREATE TABLE OrderProduct (
         order_id INT,
         product_id INT,
         quantity INT,
         PRIMARY KEY (order_id, product_id),
         FOREIGN KEY (order_id) REFERENCES `Order`(order_id),
         FOREIGN KEY (product_id) REFERENCES Product(product_id)
     );
     ```

10. **Write a query to get the customer name and total order price for customers named "Bharath" where the order is placed today.**

    - **Answer:**
      ```sql
      SELECT c.customer_name, SUM(p.price * op.quantity) AS total_order_price
      FROM Customer c
      JOIN `Order` o ON c.customer_id = o.customer_id
      JOIN OrderProduct op ON o.order_id = op.order_id
      JOIN Product p ON op.product_id = p.product_id
      WHERE c.customer_name = 'Bharath'
      AND o.order_date = CURDATE()
      GROUP BY c.customer_name;
      ```

11. **Given the following Spring Boot code, will it work?**
    ```java
    @Component
    public class Controller {
        @Autowired
        private Filter filter;
    }
    
    public interface Filter {
    }
    
    @Component
    public class Abc implements Filter {
    }
    
    @Component
    public class Abc1 implements Filter {
    }
    ```

    - **Answer:** No, it will not work as intended. Spring will not be able to resolve the `Filter` bean because there are multiple implementations (`Abc` and `Abc1`). You need to use `@Qualifier` to specify which implementation should be injected.

12. **How would you fix the issue in the Spring Boot code provided above?**

    - **Answer:** Use `@Qualifier` to specify which bean to inject:
      ```java
      @Component
      public class Controller {
          @Autowired
          @Qualifier("abc")
          private Filter filter;
      }
      
      @Component("abc")
      public class Abc implements Filter {
      }
      
      @Component("abc1")
      public class Abc1 implements Filter {
      }
      ```

13. **What is the difference between `@Primary` and `@Qualifier` in Spring?**

    - **Answer:**
      - **`@Primary`:** Indicates the preferred bean when multiple candidates are available for autowiring. It is used at the bean definition level.
      - **`@Qualifier`:** Used to specify which bean to inject when multiple beans of the same type are available. It is used at the injection point.

14. **How can you ensure that an API request processes data and responds while sending a notification to another API simultaneously in Spring Boot?**

    - **Answer:** Use asynchronous processing with `@Async` or `CompletableFuture` to handle the notification separately from the main request processing. Here’s an example:
      ```java
      @Service
      public class MyService {
          @Async
          public CompletableFuture<Void> sendNotification() {
              // Code to send notification
              return CompletableFuture.completedFuture(null);
          }
          
          public void processRequest() {
              // Process request
              sendNotification(); // Non-blocking call
          }
      }
      ```

15. **How do you communicate between one API and another API?**

    - **Answer:** You can use HTTP clients such as `RestTemplate`, `WebClient` (for reactive applications), or external libraries to make API calls. For example, using `RestTemplate`:
      ```java
      @Autowired
      private RestTemplate restTemplate;

      public String callAnotherApi() {
          String url = "http://example.com/api";
          return restTemplate.getForObject(url, String.class);
      }
      ```

16. **What is `Mono` and `Flux` in WebClient?**

    - **Answer:**
      - **`Mono`:** Represents a single asynchronous value or an empty value.
      - **`Flux`:** Represents a stream of 0 to N asynchronous values.

17. **What is a Kafka server?**

    - **Answer:** Apache Kafka is a distributed event streaming platform used for building real-time data pipelines and streaming applications. It is designed for high-throughput, fault tolerance, and scalability.

18. **Given a controller with a GET API that takes a number as a `@PathVariable`, and returns a 404 Not Found for invalid values, how would you implement a JUnit test case for this controller?**

    - **Answer:**
      ```java
      @SpringBootTest
      @AutoConfigureMockMvc
      public class MyControllerTest {

          @Autowired
          private MockMvc mockMvc;

          @Test
          public void testGetApiNotFound() throws Exception {
              mockMvc.perform(get("/api/{number}", 999)) // assuming 999 is invalid
                     .andExpect(status().isNotFound());
          }
      }
      ```

19. **How do you configure and connect a Spring Boot application to a database, and how does it work?**

    - **Answer:** Configure the `application.properties` or `application.yml` with database connection details:
      ```properties
      spring.datasource.url=jdbc:mysql://localhost:3306/mydb
      spring.datasource.username=root
      spring.datasource.password=password
      spring.jpa.hibernate.dd

l-auto=update
      ```
      Spring Boot uses these properties to configure the `DataSource`, `EntityManagerFactory`, and `TransactionManager` beans automatically.

20. **How can you determine if the application is connected to MySQL or Oracle?**

    - **Answer:** Check the `application.properties` or `application.yml` for the JDBC URL. The URL usually contains the database type, e.g., `jdbc:mysql://` for MySQL or `jdbc:oracle:thin:@` for Oracle.

21. **What is the `@Transactional` annotation in Spring?**

    - **Answer:** The `@Transactional` annotation is used to define the scope of a single database transaction. It ensures that all operations within the annotated method are completed successfully before committing the transaction, and rolls back the transaction in case of errors.

22. **Are you familiar with entity graphs in JPA?**

    - **Answer:** Yes, entity graphs in JPA allow you to specify fetch strategies for entities dynamically. They help in optimizing queries by specifying which related entities should be fetched eagerly.

23. **Have you used `join` and `joinFetch` in JPA?**

    - **Answer:** Yes, `join` is used in JPQL queries to perform joins between entities, while `joinFetch` is used to fetch related entities eagerly in a single query to avoid the N+1 select problem.

24. **What are closures in JavaScript, and can you provide an example?**

    - **Answer:** Closures are functions that have access to variables from their outer scope, even after the outer function has finished executing. Example:
      ```javascript
      function outerFunction() {
          let outerVariable = 'I am from outer function';
          return function innerFunction() {
              console.log(outerVariable);
          }
      }
      let closureFunction = outerFunction();
      closureFunction(); // Outputs: 'I am from outer function'
      ```

25. **What is debouncing in JavaScript?**

    - **Answer:** Debouncing is a technique used to limit the rate at which a function is executed. It ensures that a function is not called repeatedly in quick succession, which helps in optimizing performance. Example:
      ```javascript
      function debounce(func, wait) {
          let timeout;
          return function(...args) {
              clearTimeout(timeout);
              timeout = setTimeout(() => func.apply(this, args), wait);
          }
      }
      ```

26. **What is `useEffect` in React?**

    - **Answer:** `useEffect` is a React hook that allows you to perform side effects in functional components. It is used to handle operations like data fetching, subscriptions, or manually changing the DOM.

27. **What is the difference between `state` and `props` in React?**

    - **Answer:**
      - **`state`:** Represents data that changes over time within a component. It is mutable and managed within the component using `useState` or `this.setState`.
      - **`props`:** Short for properties, they are read-only data passed from parent to child components. Props are immutable and used to pass data and event handlers between components.
