
# Java Full Stack Interview Questions for Cognizant
## First Round Assessment

### Coding Questions
1. **Question 1:React** 
2. **Question 2:Spring Boot** 
### 4 Multiple Choice Questions


## Technical Round 1

1. **Self-Introduction**
   - Introduce yourself briefly.

2. **About Your Project**
   - Describe your recent project, your role, and the technologies used.

3. **GCP Experience**
   - Have you worked on GCP and deployed any project in GCP?

4. **React Project Experience**
   - How many React projects have you worked on?

5. **Props in React**
   - Props are used to pass data from parent to child components.

6. **Passing Data from Child to Parent in React**
   - Use callback functions passed as props to send data from child to parent.

7. **Validating Props in React**
   - Use `PropTypes` to validate props.

8. **Reusable Components in React**
   - Components that can be reused across the application, e.g., buttons, input fields.

9. **Lazy Loading in React**
   - Load components only when they are needed using `React.lazy`.

10. **React.lazy**
    - A function to lazily load a component dynamically.

11. **React Fragments**
    - A way to group a list of children without adding extra nodes to the DOM.

12. **Difference Between Fragment and Div Tag**
    - Fragment does not add extra nodes to the DOM, while div does.

13. **Memory Usage of Div vs. Fragment**
    - Using div instead of Fragment can add extra memory usage due to additional DOM nodes.

14. **React Hooks Used**
    - `useState`, `useEffect`, `useContext`, `useReducer`, `useCallback`, `useMemo`.

15. **useCallback Hook**
    - Returns a memoized callback to prevent unnecessary re-renders.

16. **useEffect Hook**
    - Side effects in function components.

17. **Dependency Array in useEffect**
    - List of dependencies that determine when the effect should re-run.

18. **Calling APIs in React**
    - Use `fetch` or libraries like `axios` inside `useEffect`.

19. **API Intersection Observer for Lazy Loading**
    - An API to observe changes in the intersection of a target element.

20. **State Management in React**
    - Use Context API, Redux, or libraries like MobX.

21. **Context API**
    - A way to pass data through the component tree without prop drilling.

22. **Redux**
    - A state management library for JavaScript applications.

23. **Memorization in React**
    - Use `useMemo` and `useCallback` to optimize performance.

24. **JavaScript Map Method**
    ```javascript
    const numbers = [1, 2, 3];
    const doubled = numbers.map(num => num * 2);
    console.log(doubled);
    ```

25. **Return Type of Map and forEach in JavaScript**
    - `map` returns a new array, `forEach` returns undefined.

26. **Callback Function in JavaScript**
    ```javascript
    function greeting(name) {
      alert('Hello ' + name);
    }
    function processUserInput(callback) {
      const name = prompt('Please enter your name.');
      callback(name);
    }
    processUserInput(greeting);
    ```

27. **Promise Example in JavaScript**
    ```javascript
    const promise = new Promise((resolve, reject) => {
      const success = true;
      if (success) {
        resolve('Success!');
      } else {
        reject('Failure.');
      }
    });
    ```

28. **Async and Await in JavaScript**
    - Yes, async and await are used to handle promises more comfortably.

29. **Callback Hell in React**
    - Multiple nested callbacks, which can be avoided using Promises or async/await.

30. **Handling Errors in ReactJS**
    - Use `try...catch` blocks or error boundaries.

31. **Handling Null Employee Data in React**
    - Use conditional rendering or optional chaining (`?.`).

32. **Nullish Coalescing Operator (??) in React**
    - Used to handle null or undefined values, e.g., `employeeName ?? 'Unknown'`.

## Backend Java

33. **Java Version**
    - Java 8

34. **Java 8 Features**
    - Lambdas, Streams, Optional, Date and Time API.

35. **Displaying Dates in Java 8**
    ```java
    LocalDate today = LocalDate.now();
    LocalDate oneMonthBefore = today.minusMonths(1);
    System.out.println(today);
    System.out.println(oneMonthBefore);
    ```

36. **Age Difference Using Period Class**
    ```java
    LocalDate birthDate = LocalDate.of(1990, Month.JULY, 15);
    LocalDate currentDate = LocalDate.now();
    Period age = Period.between(birthDate, currentDate);
    System.out.println(age.getYears());
    ```

37. **Functional Interface in Java**
    - An interface with a single abstract method, e.g., `Runnable`.

38. **Custom Functional Interface**
    ```java
    @FunctionalInterface
    interface MyFunction {
      void execute();
    }
    ```

39. **Sum Method vs. Apply Method in Java**
    - Sum method is used for summing values, while apply is used in functional interfaces.

40. **Custom Functional Interface Example**
    ```java
    @FunctionalInterface
    interface Calculator {
      int calculate(int a, int b);
    }
    ```

41. **Streams in Java**
    - Streams are sequences of data that allow functional-style operations.

42. **Stream Functions**
    - `filter`, `map`, `reduce`, `collect`.

43. **First Non-Repeated Character Using Streams**
    ```java
    String input = "swiss";
    Optional<Character> result = input.chars()
                                      .mapToObj(c -> (char) c)
                                      .collect(Collectors.groupingBy(c -> c, LinkedHashMap::new, Collectors.counting()))
                                      .entrySet()
                                      .stream()
                                      .filter(entry -> entry.getValue() == 1)
                                      .map(Map.Entry::getKey)
                                      .findFirst();
    result.ifPresent(System.out::println);
    ```

44. **Merge Two Arrays**
    ```java
    int[] arr1 = {4, 2, 3, 4, 6};
    int[] arr2 = {6, 8, 2};
    int[] merged = IntStream.concat(Arrays.stream(arr1), Arrays.stream(arr2)).distinct().sorted().toArray();
    System.out.println(Arrays.toString(merged));
    ```

45. **Spring Boot Overview**
    - A framework for creating standalone Spring applications.

46. **Basic Annotations in Spring Boot**
    - `@SpringBootApplication`, `@RestController`, `@Autowired`.

47. **Spring Security**
    - A framework for securing Java applications.

48. **Method-Level Security**
    - Security annotations like `@Secured` and `@PreAuthorize`.

49. **@Component vs. @Bean**
    - `@Component` is a class-level annotation, `@Bean` is a method-level annotation.

50. **@Primary vs. @Qualifier**
    - `@Primary` gives a higher preference, `@Qualifier` specifies which bean to use.

51. **@Controller vs. @RestController**
    - `@Controller` returns views, `@RestController` returns JSON/XML responses.

52. **Entity Class in Spring Boot Using JPA Annotations**
    ```java
    @Entity
    public class Employee {
        @Id
        private Long empId;
        private String empName;
        private String email;

        @ManyToOne
        private Department department;
    }

    @Entity
    public class Department {
        @Id
        private Long deptId;
        private String deptName;

        @OneToMany
        private List<Project> projects;
    }

    @Entity
    public class Project {
        @Id
        private Long projectId;
        private String projectName;
    }
    ```
```
