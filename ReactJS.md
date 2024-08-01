## Basic Questions

1. **What is React?**
    - React is a JavaScript library for building user interfaces, developed by Facebook. It allows you to build single-page applications with a component-based architecture.

2. **What are the main features of React?**
   - Component-based architecture
   - Virtual DOM
   - One-way data binding
   - JSX syntax
   - Hooks for managing state and side effects
   - Context API for global state management

3. **What are the advantages of using React?**
   - Efficient update and rendering with Virtual DOM
   - Component reusability
   - Unidirectional data flow
   - Rich ecosystem and community support
   - Strong tooling and developer experience

4. **What is JSX?**
 - JSX (JavaScript XML) is a syntax extension for JavaScript that allows you to write HTML-like code within JavaScript. It gets compiled into JavaScript code.

   ```jsx
   const element = <h1>Hello, world!</h1>;
   ```

5. **How does JSX transform into JavaScript?**
   - JSX is transformed into `React.createElement` calls by Babel. For example:

   ```jsx
   const element = <h1>Hello, world!</h1>;
   ```

   Transforms to:

   ```javascript
   const element = React.createElement('h1', null, 'Hello, world!');
   ```

6. **What are components in React?**
  - Components are the building blocks of a React application. They can be either class-based or functional and manage their own state and lifecycle.

7. **Explain the difference between functional and class components.**
   - **Class Components**: Have lifecycle methods, `this` context, and can manage state directly.
   - **Functional Components**: Are simpler and can use hooks for state and side effects. They don’t have lifecycle methods but can use `useEffect` to achieve similar behavior.

   ```jsx
   // Class Component
   class MyComponent extends React.Component {
     render() {
       return <h1>Hello, world!</h1>;
     }
   }

   // Functional Component
   function MyComponent() {
     return <h1>Hello, world!</h1>;
   }
   ```

8. **What is the virtual DOM, and how does it work?**
  - The Virtual DOM is an in-memory representation of the actual DOM. React uses it to optimize rendering by updating only the changed parts of the real DOM, which improves performance.

9. **How do you create a React application?**
  - Use the `create-react-app` command to bootstrap a new React project:

   ```bash
   npx create-react-app my-app
   ```

10. **What are props in React?**
    - Props (short for properties) are read-only attributes passed to components to configure or customize them.

    ```jsx
    function Greeting(props) {
      return <h1>Hello, {props.name}!</h1>;
    }

    // Usage
    <Greeting name="Alice" />
    ```

11. **How do you pass data between components?**
    - Pass data through props from a parent component to a child component.

    ```jsx
    function Parent() {
      return <Child message="Hello from Parent" />;
    }

    function Child(props) {
      return <h1>{props.message}</h1>;
    }
    ```

12. **What is state in React?**
    - State is an object that holds data that may change over time and affects how the component renders.

    ```jsx
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        this.state = { count: 0 };
      }

      render() {
        return <h1>{this.state.count}</h1>;
      }
    }
    ```

13. **How do you manage state in a React component?**
    - Use the `useState` hook for functional components or `this.state` and `this.setState` in class components.

    ```jsx
    // Functional Component with useState
    function Counter() {
      const [count, setCount] = useState(0);
      return <button onClick={() => setCount(count + 1)}>{count}</button>;
    }
    ```

14. **Explain the lifecycle methods in React.**
    - Lifecycle methods are hooks in class components that allow you to run code at different stages of a component's life:

    - `componentDidMount()`
    - `componentDidUpdate()`
    - `componentWillUnmount()`

    ```jsx
    class MyComponent extends React.Component {
      componentDidMount() {
        console.log('Component mounted');
      }

      componentWillUnmount() {
        console.log('Component will unmount');
      }

      render() {
        return <h1>Hello</h1>;
      }
    }
    ```

15. **What are hooks in React?**
    - Hooks are functions that let you use state and other React features in functional components. Examples include `useState`, `useEffect`, and `useContext`.

16. **Explain the useState hook.**
    - The `useState` hook allows you to add state to functional components.

    ```jsx
    function Counter() {
      const [count, setCount] = useState(0);
      return <button onClick={() => setCount(count + 1)}>{count}</button>;
    }
    ```

17. **Explain the useEffect hook.**
    - The `useEffect` hook allows you to perform side effects in functional components, such as data fetching or subscriptions.

    ```jsx
    useEffect(() => {
      // Code to run on component mount
      console.log('Component mounted');
      return () => {
        // Cleanup code
        console.log('Component unmounted');
      };
    }, []);
    ```

18. **What is the Context API?**
    - The Context API is a feature in React that allows you to pass data through the component tree without having to pass props manually at every level.

    ```jsx
    const MyContext = React.createContext();

    function MyProvider({ children }) {
      const value = "some value";
      return <MyContext.Provider value={value}>{children}</MyContext.Provider>;
    }

    function MyComponent() {
      const value = useContext(MyContext);
      return <h1>{value}</h1>;
    }
    ```

19. **How do you use the Context API to manage state?**
    - Create a context, provide a value in a provider component, and consume the context in child components.

    ```jsx
    const ThemeContext = React.createContext('light');

    function App() {
      return (
        <ThemeContext.Provider value="dark">
          <Toolbar />
        </ThemeContext.Provider>
      );
    }

    function Toolbar() {
      return <ThemedButton />;
    }

    function ThemedButton() {
      const theme = useContext(ThemeContext);
      return <button>{theme}</button>;
    }
    ```

20. **What are refs in React?**
    - Refs provide a way to access DOM nodes or React elements directly.

    ```jsx
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        this.myRef = React.createRef();
      }

      componentDidMount() {
        this.myRef.current.focus();
      }

      render() {
        return <input ref={this.myRef} />;
      }
    }
    ```

21. **How do you create and use refs?**
    - Use `React.createRef()` in class components or `useRef()` in functional components.

    ```jsx
    // Functional Component
    function MyComponent() {
      const myRef = useRef(null);

      useEffect(() => {
        myRef.current.focus();
      }, []);

      return <input ref={myRef} />;
    }
    ```

22. **What is React Router?**
    - React Router is a library for handling routing in React applications, allowing you to create single-page applications with navigation.

23. **How do you perform navigation in a React application?**
    - Use the `react-router-dom` library to set up routes and navigation.

    ```jsx
    import { BrowserRouter as Router, Route, Switch, Link } from 'react-router-dom';

    function App() {
      return (
        <Router>
          <nav>
            <Link to="/">Home</Link>
            <Link to="/about">About</Link>
          </nav>
          <Switch>
            <Route path="/" exact component={Home} />
            <Route path="/about" component={About} />
          </Switch>
        </Router>
      );
    }
    ```

24. **What is the difference between controlled and uncontrolled components?**
    - **Controlled Components**: Form data is handled by the state within the component.
    - **Uncontrolled Components**: Form data is handled by the DOM.

    ```jsx
    // Controlled Component
    function ControlledForm() {
      const [value, setValue] = useState('');
      return <input value={value} onChange={e => setValue(e.target.value)} />;
    }

    // Uncontrolled Component
    function UncontrolledForm() {
      const inputRef = useRef(null);
      return <input ref={inputRef} />;
    }
    ```

25. **How do you handle forms in React?**
    - Use controlled components to handle form inputs, or use uncontrolled components with refs.

    ```jsx
    function Form() {
      const [inputValue, setInputValue] = useState('');

      const handleSubmit = (e) => {
        e.preventDefault();
        alert('Form submitted with: ' + inputValue);
      };

      return (
        <form onSubmit={handleSubmit}>
          <input
            type="text"
            value={inputValue}
            onChange={(e) => setInputValue(e.target.value)}
          />
          <button type="submit">Submit</button>
        </form>
      );
    }
    ```

26. **How do you handle events in React?**
    - Handle events by passing event handler functions as props.

    ```jsx
    function MyButton() {
      const handleClick = () => {
        alert('Button clicked!');
      };

      return <button onClick={handleClick}>Click me</button>;
    }
    ```

27. **What is a higher-order component (HOC)?**
    - A higher-order component is a function that takes a component and returns a new component with additional props or behavior.

    ```jsx
    function withExtraProps(WrappedComponent) {
      return function EnhancedComponent(props) {
        return <WrappedComponent extraProp="extra" {...props} />;
      };
    }
    ```

28. **What is the purpose of keys in React?**
    - Keys help React identify which items have changed, are added, or are removed, improving performance in lists.

29. **What is the significance of the key prop?**
    - The `key` prop is used to give elements a stable identity, which helps React efficiently update the UI.

    ```jsx
    function List({ items }) {
      return (
        <ul>
          {items.map(item => (
            <li key={item.id}>{item.name}</li>
          ))}
        </ul>
      );
    }
    ```

30. **How do you optimize performance in a React application?**
    - Use `React.memo` to memoize functional components
    - Use `shouldComponentUpdate` in class components
    - Implement lazy loading and code splitting
    - Avoid unnecessary re-renders

31. **What are React fragments?**
    - React fragments allow you to group multiple elements without adding extra nodes to the DOM.

    ```jsx
    function List() {
      return (
        <>
          <h1>Title</h1>
          <p>Content</p>
        </>
      );
    }
    ```

32. **How do you use React fragments?**
    - Use `<React.Fragment>` or the shorthand `<>` to wrap multiple elements.

    ```jsx
    function List() {
      return (
        <React.Fragment>
          <h1>Title</h1>
          <p>Content</p>
        </React.Fragment>
      );
    }
    ```

33. **What is the difference between React.Fragment and a regular HTML element?**
    - React.Fragment does not create an additional DOM node, while a regular HTML element does.

34. **What are error boundaries in React?**
    - Error boundaries are components that catch JavaScript errors in their child components, log those errors, and display a fallback UI.

    ```jsx
    class ErrorBoundary extends React.Component {
      constructor(props) {
        super(props);
        this.state = { hasError: false };
      }

      static getDerivedStateFromError() {
        return { hasError: true };
      }

      componentDidCatch(error, info) {
        console.log(error, info);
      }

      render() {
        if (this.state.hasError) {
          return <h1>Something went wrong.</h1>;
        }
        return this.props.children;
      }
    }
    ```

35. **How do you implement an error boundary in React?**
    - Wrap your components with the error boundary component.

    ```jsx
    function App() {
      return (
        <ErrorBoundary>
          <MyComponent />
        </ErrorBoundary>
      );
    }
    ```

36. **What is PropTypes in React?**
    - PropTypes is a type-checking library for React props. It helps in validating the types of props passed to components.

    ```jsx
    import PropTypes from 'prop-types';

    function MyComponent({ name }) {
      return <h1>Hello, {name}</h1>;
    }

    MyComponent.propTypes = {
      name: PropTypes.string.isRequired,
    };
    ```

37. **How do you validate props using PropTypes?**
    - Define `propTypes` on the component to specify the expected types of props.

    ```jsx
    MyComponent.propTypes = {
      name: PropTypes.string.isRequired,
      age: PropTypes.number,
    };
    ```

38. **What is the difference between Props and State?**
    - **Props**: Passed from parent to child components, immutable.
    - **State**: Managed within a component, mutable and can change over time.

39. **How do you use default props in React?**
    - Define `defaultProps` on the component to set default values for props.

    ```jsx
    function MyComponent({ name }) {
      return <h1>Hello, {name}</h1>;
    }

    MyComponent.defaultProps = {
      name: 'Guest',
    };
    ```

40. **What are React Portals?**
    - Portals provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

    ```jsx
    import ReactDOM from 'react-dom';

    function Modal({ children }) {
      return ReactDOM.createPortal(
        children,
        document.getElementById('modal-root')
      );
    }
    ```

41. **How do you create a portal in React?**
    - Use `ReactDOM.createPortal` to render children into a different part of the DOM.

    ```jsx
    function Modal({ children }) {
      return ReactDOM.createPortal(
        <div className="modal">{children}</div>,
        document.getElementById('modal-root')
      );
    }
    ```

42. **What is server-side rendering (SSR)?**
    - SSR is the process of rendering a React application on the server and sending the HTML to the client. It improves performance and SEO.

43. **How does SSR differ from client-side rendering?**
    - **SSR**: Renders content on the server before sending it to the client.
    - **CSR**: Renders content on the client side using JavaScript.

44. **What is the purpose of Redux in React?**
    - Redux is a state management library that helps manage and centralize application state in a predictable way.

45. **Explain the basic concepts of Redux.**
    - **Store**: Holds the state of the application.
    - **Actions**: Payloads of information that send data from the application to the Redux store.
    - **Reducers**: Functions that specify how the application's state changes in response to actions.
    - **Dispatch**: A method to send actions to the store.
    - **Selectors**: Functions to retrieve data from the store.

46. **How do you connect Redux with a React application?**
    - Use the `react-redux` library's `Provider` and `connect` functions.

    ```jsx
    import { Provider, connect } from 'react-redux';
    import { createStore } from 'redux';

    const store = createStore(reducer);

    function App() {
      return (
        <Provider store={store}>
          <MyComponent />
        </Provider>
      );
    }

    function mapStateToProps(state) {
      return { data: state.data };
    }

    const MyComponent = connect(mapStateToProps)(function ({ data }) {
      return <div>{data}</div>;
    });
    ```

47. **What is the difference between Redux and Context API?**
    - **Redux**: More complex, provides a predictable state container, supports middleware, and is more suited for large-scale applications.
    - **Context API**: Simpler, built into React, suitable for small to medium-sized applications or specific use cases.

48. **What is React.memo?**
    - `React.memo` is a higher-order component that memoizes functional components to prevent unnecessary re-renders.

    ```jsx
    const MyComponent = React.memo(function ({ value }) {
      return <div>{value}</div>;
    });
    ```

49. **How do you use React.memo to optimize performance?**
    - Wrap a functional component with `React.memo` to avoid re-rendering when props haven’t changed.

    ```jsx
    const MyComponent = React.memo(function ({ value }) {
      return <div>{value}</div>;
    });
    ```

50. **Explain the useCallback hook.**
    - `useCallback` returns a memoized callback function that only changes if one of the dependencies has changed.

    ```jsx
    function MyComponent() {
      const [count, setCount] = useState(0);

      const handleClick = useCallback(() => {
        setCount(count + 1);
      }, [count]);

      return <button onClick={handleClick}>{count}</button>;
    }
    ```

## Intermediate Questions

51. **What is React.lazy?**
    - `React.lazy` is a function that allows you to dynamically import a component, enabling code splitting.

    ```jsx
    const LazyComponent = React.lazy(() => import('./LazyComponent'));

    function App() {
      return (
        <React.Suspense fallback={<div>Loading...</div>}>
          <LazyComponent />
        </React.Suspense>
      );
    }
    ```

52. **How do you implement lazy loading in React?**
    - Use `React.lazy` with `React.Suspense` to load components only when they are needed.

    ```jsx
    const LazyComponent = React.lazy(() => import('./LazyComponent'));

    function App() {
      return (
        <React.Suspense fallback={<div>Loading...</div>}>
          <LazyComponent />
        </React.Suspense>
      );
    }
    ```

53. **What is the Suspense component?**
    - `Suspense` is a component that lets you define a loading state while waiting for lazy-loaded components to be ready.

    ```jsx
    function App() {
      return (
        <React.Suspense fallback={<div>Loading...</div>}>
          <LazyComponent />
        </React.Suspense>
      );
    }
    ```

54. **How do you use the Suspense component with React.lazy?**
    - Wrap `React.lazy` components with `Suspense` to provide a loading fallback.

    ```jsx
    const LazyComponent = React.lazy(() => import('./LazyComponent'));

    function App() {
      return (
        <React.Suspense fallback={<div>Loading...</div>}>
          <LazyComponent />
        </React.Suspense>
      );
    }
    ```

55. **What is the difference between React.lazy and dynamic imports?**
    - **React.lazy**: A function to dynamically import components with support for code splitting and lazy loading.
    - **Dynamic imports**: A JavaScript feature to load modules asynchronously.

56. **How do you handle side effects in a React application?**
    - Use the `useEffect` hook to handle side effects like data fetching, subscriptions, and manual DOM manipulations.

    ```jsx
    useEffect(() => {
      // Side effect code here
      fetchData();
    }, []);
    ```

57. **What is the useReducer hook?**
    - `useReducer` is a hook for managing complex state logic with actions and reducers, similar to Redux.

    ```jsx
    const initialState = { count: 0 };

    function reducer(state, action) {
      switch (action.type) {
        case 'increment':
          return { count: state.count + 1 };
        default:
          throw new Error();
      }
    }

    function Counter() {
      const [state, dispatch] = useReducer(reducer, initialState);

      return (
        <>
          <p>{state.count}</p>
          <button onClick={() => dispatch({ type: 'increment' })}>
            Increment
          </button>
        </>
      );
    }
    ```

58. **How does useReducer differ from useState?**
    - `useReducer` is more suited for complex state logic involving multiple sub-values or when the next state depends on the previous one. `useState` is simpler and better for managing basic state.

59. **How do you use custom hooks in React?**
    - Create a custom hook by encapsulating reusable logic in a function prefixed with `use`.

    ```jsx
    function useCustomHook() {
      const [value, setValue] = useState(0);

      const increment = () => setValue(value + 1);

      return [value, increment];
    }

    function MyComponent() {
      const [value, increment] = useCustomHook();

      return (
        <div>
          <p>{value}</p>
          <button onClick={increment}>Increment</button>
        </div>
      );
    }
    ```

60. **How do you create a custom hook?**
    - Define a function that uses React hooks and returns values or functions for use in other components.

    ```jsx
    function useFetch(url) {
      const [data, setData] = useState(null);
      const [loading, setLoading] = useState(true);

      useEffect(() => {
        fetch(url)
          .then(response => response.json())
          .then(data => {
            setData(data);
            setLoading(false);
          });
      }, [url]);

      return { data, loading };
    }
    ```

61. **What are compound components?**
    - Compound components are a pattern where multiple components work together to form a unified UI component.

    ```jsx
    function Tabs({ children }) {
      const [activeTab, setActiveTab] = useState(0);

      return (
        <div>
          <div>
            {React.Children.map(children, (child, index) =>
              React.cloneElement(child, {
                isActive: index === activeTab,
                onClick: () => setActiveTab(index),
              })
            )}
          </div>
          <div>
            {React.Children.toArray(children)[activeTab].props.children}
          </div>
        </div>
      );
    }

    function Tab({ isActive, onClick, children }) {
      return (
        <button
          style={{ fontWeight: isActive ? 'bold' : 'normal' }}
          onClick={onClick}
        >
          {children}
        </button>
      );
    }
    ```

62. **How do you implement compound components?**
    - Use a parent component to manage state and pass it down to child components to control their behavior.

    ```jsx
    function Tabs({ children }) {
      // Implementation
    }

    function Tab({ isActive, onClick, children }) {
      // Implementation
    }

    // Usage
    function App() {
      return (
        <Tabs>
          <Tab>Tab 1</Tab>
          <Tab>Tab 2</Tab>
        </Tabs>
      );
    }
    ```

63. **What is the difference between class-based and function-based components in terms of lifecycle?**
    - **Class-based components**: Have lifecycle methods like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.
    - **Function-based components**: Use hooks like `useEffect` to handle lifecycle events.

64. **How do you handle authentication in a React application?**
    - Use context or state management libraries to manage authentication status and protect routes.

    ```jsx
    function AuthProvider({ children }) {
      const [isAuthenticated, setIsAuthenticated] = useState(false);

      // Implement authentication logic

      return (
        <AuthContext.Provider value={{ isAuthenticated, setIsAuthenticated }}>
          {children}
        </AuthContext.Provider>
      );
    }
    ```

65. **What are render props?**
    - Render props are a pattern where a component uses a function prop to know what to render.

    ```jsx
    function DataProvider({ render }) {
      const [data, setData] = useState(null);

      useEffect(() => {
        // Fetch data
        setData(fetchedData);
      }, []);

      return render(data);
    }

    function App() {
      return (
        <DataProvider
          render={data => <div>{data ? data : 'Loading...'}</div>}
        />
      );
    }
    ```

66. **How do you use render props in React?**
    - Pass a function as a prop to a component and use it to render different content based on state or props.

    ```jsx
    function DataProvider({ render }) {
      // Implementation
    }

    function App() {
      return (
        <DataProvider
          render={data => <div>{data ? data : 'Loading...'}</div>}
        />
      );
    }
    ```

67. **What is the Context API, and how does it replace Redux in certain scenarios?**
    - The Context API provides a way to pass data through the component tree without having to pass props down manually at every level. It can replace Redux for simpler state management needs.

68. **How do you handle file uploads in React?**
    - Use the `input` element of type `file` to select files and handle them with an `onChange` event.

    ```jsx
    function FileUpload() {
      const handleFileChange = (event) => {
        const file = event.target.files[0];
        // Process file
      };

      return <input type="file" onChange={handleFileChange} />;
    }
    ```

69. **What are code splitting and lazy loading in React?**
    - Code splitting is a technique to split code into smaller bundles, which can be loaded on demand. Lazy loading is a way to defer the loading of components until they are needed.

70. **How do you implement code splitting?**
    - Use `React.lazy` and `React.Suspense` to load components only when needed.

    ```jsx
    const LazyComponent = React.lazy(() => import('./LazyComponent'));

    function App() {
      return (
        <React.Suspense fallback={<div>Loading...</div>}>
          <LazyComponent />
        </React.Suspense>
      );
    }
    ```

71. **How do you test React components?**
    - Use testing libraries like `React Testing Library` and `Jest` to write unit tests and integration tests.

    ```jsx
    import { render, screen } from '@testing-library/react';
    import MyComponent from './MyComponent';

    test('renders component', () => {
      render(<MyComponent />);
      expect(screen.getByText(/hello/i)).toBeInTheDocument();
    });
    ```

72. **What are the different ways to test React components?**
    - **Unit tests**: Test individual components in isolation.
    - **Integration tests**: Test how components work together.
    - **End-to-end tests**: Test the entire application flow.

73. **What is the purpose of the React Developer Tools?**
    - React Developer Tools helps inspect the React component tree, view props and state, and debug performance issues.

74. **How do you use the React Developer Tools?**
    - Install the React Developer Tools extension for your browser and use it to inspect React components and their state.

75. **How do you handle errors in a React application?**
    - Use error boundaries to catch and handle errors in the component tree.

    ```jsx
    function App() {
      return (
        <ErrorBoundary>
          <MyComponent />
        </ErrorBoundary>
      );
    }
    ```

76. **How do you use the ErrorBoundary component?**
    - Wrap your components with an `ErrorBoundary` to catch and handle errors.

    ```jsx
    class ErrorBoundary extends React.Component {
      constructor(props) {
        super(props);
        this.state = { hasError: false };
      }

      static getDerivedStateFromError() {
        return { hasError: true };
      }

      componentDidCatch(error, errorInfo) {
        // Log error
      }

      render() {
        if (this.state.hasError) {
          return <h1>Something went wrong.</h1>;
        }

        return this.props.children;
      }
    }
    ```

77. **What are controlled and uncontrolled components in React?**
    - **Controlled components**: Manage form data using React state.
    - **Uncontrolled components**: Manage form data using the DOM directly.

78. **How do you handle forms in React?**
    - Use controlled components to manage form inputs with React state.

    ```jsx
    function MyForm() {
      const [value, setValue] = useState('');

      const handleChange = (event) => {
        setValue(event.target.value);
      };

      const handleSubmit = (event) => {
        event.preventDefault();
        // Handle submit
      };

      return (
        <form onSubmit={handleSubmit}>
          <input type="text" value={value} onChange={handleChange} />
          <button type="submit">Submit</button>
        </form>
      );
    }
    ```

79. **What are pure components in React?**
    - Pure components only re-render when their props or state change, optimizing performance by avoiding unnecessary renders.

80. **How do you implement a pure component in React?**
    - Use `React.PureComponent` or `React.memo` for function components.

    ```jsx
    class MyPureComponent extends React.PureComponent {
      // Implementation
    }

    const MyComponent = React.memo(function MyComponent(props) {
      // Implementation
    });
    ```

81. **What is the use of the useRef hook?**
    - `useRef` returns a mutable object whose `.current` property is initialized with the passed argument and persists for the full lifetime of the component.

    ```jsx
    const inputRef = useRef(null);

    function focusInput() {
      inputRef.current.focus();
    }

    return <input ref={inputRef} />;
    ```

82. **How do you use the useImperativeHandle hook?**
    - Customize the instance value exposed when using `ref` with `forwardRef`.

    ```jsx
    const FancyInput = React.forwardRef((props, ref) => {
      const inputRef = useRef();

      useImperativeHandle(ref, () => ({
        focus: () => inputRef.current.focus()
      }));

      return <input ref={inputRef} />;
    });
    ```

83. **How do you optimize performance in React applications?**
    - Use techniques like memoization (`React.memo`, `useMemo`), lazy loading, code splitting, and optimizing rendering with `shouldComponentUpdate` or `React.PureComponent`.

84. **How do you use memoization in React?**
    - Use `React.memo` for components and `useMemo` for values to prevent unnecessary re-renders.

    ```jsx
    const MemoizedComponent = React.memo(function Component(props) {
      // Implementation
    });

    const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
    ```

85. **What are the performance optimization techniques in React?**
    - **Memoization**: Use `React.memo` and `useMemo`.
    - **Lazy loading**: Use `React.lazy` and `Suspense`.
    - **Avoid inline functions**: Define functions outside render methods.
    - **Code splitting**: Split code into smaller bundles.

86. **How do you use `useMemo` and `useCallback` hooks?**
    - **`useMemo`**: Memoizes the result of a computation.
    - **`useCallback`**: Memoizes the function itself.

    ```jsx
    const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
    const memoizedCallback = useCallback(() => { /* callback code */ }, [dependencies]);
    ```

87. **How do you handle state updates in functional components?**
    - Use the `useState` hook to manage and update state.

    ```jsx
    const [state, setState] = useState(initialState);

    const updateState = (newState) => {
      setState(newState);
    };
    ```

88. **What is the difference between useEffect and useLayoutEffect?**
    - **`useEffect`**: Runs after the paint, suitable for side effects.
    - **`useLayoutEffect`**: Runs synchronously after all DOM mutations, useful for layout calculations.

89. **How do you use `useEffect` for cleanup?**
    - Return a cleanup function from `useEffect` to handle resource cleanup.

    ```jsx
    useEffect(() => {
      const timer = setTimeout(() => {
        // Side effect code
      }, 1000);

      return () => clearTimeout(timer);
    }, []);
    ```

90. **How do you handle asynchronous operations in useEffect?**
    - Use an asynchronous function inside `useEffect` or handle promises with `then`/`catch`.

    ```jsx
    useEffect(() => {
      async function fetchData() {
        const response = await fetch(url);
        const data = await response.json();
        setData(data);
      }

      fetchData();
    }, [url]);
    ```

91. **What is the purpose of the useContext hook?**
    - `useContext` provides a way to access the context value directly without needing to use a Consumer component.

    ```jsx
    const value = useContext(MyContext);
    ```

92. **How do you use useContext with a Context Provider?**
    - Wrap components with a `Context.Provider` and use `useContext` to access the context value.

    ```jsx
    const MyContext = React.createContext();

    function App() {
      return (
        <MyContext.Provider value={/* context value */}>
          <MyComponent />
        </MyContext.Provider>
      );
    }

    function MyComponent() {
      const value = useContext(MyContext);
      // Use context value
    }
    ```

93. **What is the purpose of the `useImperativeHandle` hook?**
    - `useImperativeHandle` customizes the instance value exposed to parent components when using `ref`.

    ```jsx
    useImperativeHandle(ref, () => ({
      focus: () => { /* custom focus method */ }
    }));
    ```

94. **How do you implement server-side rendering with React?**
    - Use frameworks like Next.js or libraries like `react-dom/server` to render React components to HTML on the server.

    ```jsx
    import React from 'react';
    import ReactDOMServer from 'react-dom/server';
    import App from './App';

    const html = ReactDOMServer.renderToString(<App />);
    ```

95. **What is Next.js and how does it enhance React applications?**
    - Next.js is a React framework for server-side rendering, static site generation, and routing. It simplifies building production-ready React applications with optimized performance and SEO.

96. **How do you set up a Next.js project?**
    - Use the `create-next-app` command to initialize a Next.js project.

    ```bash
    npx create-next-app my-next-app
    ```

97. **How do you create dynamic routes in Next.js?**
    - Use file-based routing with dynamic segments in the `pages` directory.

    ```jsx
    // pages/[id].js
    export default function Page({ id }) {
      return <div>Page ID: {id}</div>;
    }

    export async function getServerSideProps(context) {
      const { id } = context.params;
      return { props: { id } };
    }
    ```

98. **What is static site generation (SSG) and how do you implement it in Next.js?**
    - SSG generates HTML at build time. Use `getStaticProps` to fetch data and generate static pages.

    ```jsx
    export async function getStaticProps() {
      const data = await fetchData();
      return { props: { data } };
    }
    ```

99. **What is server-side rendering (SSR) and how do you implement it in Next.js?**
    - SSR generates HTML on each request. Use `getServerSideProps` to fetch data on each request.

    ```jsx
    export async function getServerSideProps(context) {
      const data = await fetchData();
      return { props: { data } };
    }
    ```

100. **How do you handle API routes in Next.js?**
    - Define API routes in the `pages/api` directory.

```jsx
    // pages/api/hello.js
    export default function handler(req, res) {
      res.status(200).json({ message: 'Hello' });
    }
```

101. **What is the use of the `getStaticPaths` function in Next.js?**
    - `getStaticPaths` defines which dynamic routes to pre-render at build time.

```jsx
    export async function getStaticPaths() {
      const paths = await fetchPaths();
      return { paths, fallback: false };
    }
```

102. **How do you handle environment variables in Next.js?**
    - Define environment variables in `.env.local` and access them using `process.env`.

```jsx
    const apiUrl = process.env.NEXT_PUBLIC_API_URL;
```

103. **What are API routes in Next.js and how do you use them?**
    - API routes allow serverless functions to handle backend logic within the Next.js application. Define them in the `pages/api` directory.
```jsx
    // pages/api/hello.js
    export default function handler(req, res) {
      res.status(200).json({ message: 'Hello' });
    }
```

104. **How do you use TypeScript with Next.js?**
    - Add TypeScript by installing the necessary packages and creating a `tsconfig.json` file.
```bash
    npm install --save-dev typescript @types/react @types/node
```
