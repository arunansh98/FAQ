# What is React ?

React is a JavaScript library used for building user interfaces, particularly for web applications. It helps developers create interactive and dynamic UIs by breaking down the interface into smaller, reusable components. These components encapsulate their own state and behavior, making it easier to manage and update different parts of the UI independently.

In simple terms, React allows developers to build web applications in a more organized and efficient manner by breaking down the UI into smaller, manageable pieces called components, which can be reused and updated easily. This makes it easier to build complex user interfaces while maintaining code readability and scalability.

# What is Virtual DOM in React and how does it work with an example ?

React uses a Virtual DOM, which is a lightweight representation of the actual DOM (Document Object Model) present in web browsers. When there are changes to a React component's state or props, React constructs a new Virtual DOM tree and compares it with the previous one to determine what has changed. React then efficiently updates only the parts of the actual DOM that need to be changed, minimizing the number of manipulations on the real DOM, which can be computationally expensive.

Here's a simplified example to illustrate how the Virtual DOM works in React:

Suppose you have a React component called Counter that displays a counter and increments its value when a button is clicked.

```
import React, { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default Counter;
```

Now, when the button is clicked, the increment function updates the count state variable using setCount. Here's how React utilizes the Virtual DOM:

Initial Rendering:

React renders the Counter component and creates a Virtual DOM representation of the UI.
This Virtual DOM is a lightweight copy of the actual DOM structure.
State Update:

When the button is clicked, the increment function updates the count state variable.
React constructs a new Virtual DOM tree, reflecting the updated state.
Diffing and Reconciliation:

React compares the new Virtual DOM tree with the previous one (generated before the state update).
It identifies the differences (or "diffs") between the two trees efficiently.
Update DOM:

React applies only the necessary changes to the actual DOM.
In our example, it updates the text displaying the count without re-rendering the entire component or refreshing the entire page.
By using the Virtual DOM, React minimizes the number of manipulations on the actual DOM, leading to better performance and a smoother user experience, especially in complex applications with frequent updates.

# How does React work ?

React works by providing developers with a declarative and component-based approach to building user interfaces. Here's a high-level overview of how React operates:

Component-Based Architecture: React applications are built using reusable components. Each component encapsulates a piece of UI, including its own logic and state, and can be composed together to form complex interfaces.

Declarative Syntax: React uses a declarative syntax to describe how the UI should look at any given point in time. Instead of directly manipulating the DOM, developers define the desired UI state, and React takes care of updating the DOM efficiently to match that state.

Virtual DOM: React maintains a lightweight representation of the actual DOM in memory, known as the Virtual DOM. When there are changes to a component's state or props, React constructs a new Virtual DOM tree and compares it with the previous one to determine what has changed. This diffing process allows React to minimize the number of manipulations on the real DOM, leading to better performance.

Reconciliation: After identifying the differences between the old and new Virtual DOM trees, React performs reconciliation to update the actual DOM with the minimal set of changes needed to reflect the new UI state.

State Management: React components can manage their own state using the useState hook (for functional components) or by extending the React.Component class (for class components). By keeping track of state changes, React triggers re-renders of components as needed to reflect the updated state.

Lifecycle Methods (for Class Components): Class components in React have lifecycle methods that allow developers to hook into different stages of a component's life, such as when it is first mounted, updated, or unmounted. These methods provide opportunities to perform actions like fetching data, subscribing to events, or cleaning up resources.

Efficient Updates: React employs various optimization techniques, such as batching updates and using key prop to help identify and track changes in lists, to ensure that UI updates are performed efficiently and without unnecessary re-renders.

Overall, React's core principles of componentization, declarative syntax, and efficient rendering make it a powerful and popular choice for building modern web applications.

# What is the difference between a Presentational component and a Container component?

Presentational components and container components are two patterns often used in React applications to organize code and separate concerns. Here's the difference between them:

Presentational Components:

Also known as "dumb" components or UI components.
Concerned only with how things look and present UI elements to the user.
Typically receive data and callbacks via props and use them to render UI elements.
Do not manage state or handle business logic; they are primarily concerned with rendering.
Reusable and easily composed together to create complex UIs.
Examples include buttons, input fields, cards, and other UI elements.
Container Components:

Also known as "smart" components or stateful components.
Concerned with how things work and handle application logic, data fetching, and state management.
Often responsible for fetching data from APIs, managing state, and passing data down to presentational components via props.
Typically do not contain much UI markup themselves but may render presentational components and pass them data and behavior via props.
May use React's state or context API to manage state and maintain the overall application logic.
Tend to be less reusable as they are more closely tied to specific application logic.
Examples include pages, forms, and other components that orchestrate the behavior of multiple presentational components.
In summary, presentational components focus on UI presentation and receive data and callbacks from their parent containers, while container components manage application logic, state, and data fetching, and pass data down to presentational components. This separation of concerns helps improve code maintainability, reusability, and testability in React applications.

# what are controlled components in react ?

In React, a controlled component is a component whose value is controlled by React's state. This means that the component's value is derived from the state and any changes to the component's value are handled by updating the state. Controlled components are commonly used for form elements like input fields, checkboxes, and radio buttons.

```
import React, { useState } from 'react';

const MyForm = () => {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (event) => {
    setInputValue(event.target.value);
  };

  return (
    <div>
      <input
        type="text"
        value={inputValue}
        onChange={handleChange}
      />
      <p>Value: {inputValue}</p>
    </div>
  );
};

export default MyForm;

```

# What are refs used for in React ?

In React, refs provide a way to access and interact with DOM elements or React components directly.

```
import React, { useRef } from 'react';

const MyComponent = () => {
  const inputRef = useRef(null);

  const handleClick = () => {
    // Focus the input field when the button is clicked
    inputRef.current.focus();
  };

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={handleClick}>Focus Input</button>
    </div>
  );
};

export default MyComponent;
```

In this example, inputRef is a ref created using the useRef hook. When the button is clicked, the handleClick function is called, which focuses the input field by calling inputRef.current.focus(). This demonstrates how refs can be used to interact with DOM elements imperatively in React components.

# What is a higher order component in React ?

A Higher Order Component (HOC) in React is a pattern used for reusing component logic. It's a function that takes a component and returns a new component with additional functionality or props.

```
import React from 'react';

// Higher Order Component that adds a "theme" prop to the wrapped component
const withTheme = (WrappedComponent) => {
  return class WithTheme extends React.Component {
    render() {
      return <WrappedComponent {...this.props} theme="dark" />;
    }
  };
};

// Component that receives the "theme" prop from the HOC
const ThemedComponent = ({ theme }) => {
  return <div>Theme: {theme}</div>;
};

// Enhance ThemedComponent with the withTheme HOC
const EnhancedThemedComponent = withTheme(ThemedComponent);

export default EnhancedThemedComponent;
```

In this example, withTheme is a Higher Order Component that adds a theme prop to the wrapped component. The ThemedComponent receives the theme prop and renders it. The EnhancedThemedComponent is created by wrapping ThemedComponent with withTheme, thus adding the theme prop to it.

# What is JSX ?

JSX stands for JavaScript XML. It's an extension to JavaScript syntax that allows developers to write HTML-like code directly within JavaScript. JSX makes it easier to create and manipulate the structure of UI components in React applications.

Here are some key points about JSX:

1. Embedding HTML in JavaScript: JSX allows developers to write HTML-like code directly within JavaScript. This helps in creating component-based UI structures in a more intuitive and readable way.

`// JSX example
const element = <h1>Hello, world!</h1>;`

2. Expressiveness: JSX supports embedding JavaScript expressions within curly braces {}. This allows dynamic content to be included within JSX elements.

```
// JSX with JavaScript expressions
const name = 'John';
const element = <h1>Hello, {name}!</h1>;
```

3. Components: In React, JSX is used to define components. Components can be written as functions or classes, and JSX is used to define the UI structure within those components.

```
// Functional component written with JSX
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

4. Compile-time Transformation: JSX code is not directly understood by browsers. It needs to be compiled or transformed into regular JavaScript code before it can be executed. Tools like Babel are commonly used to perform this transformation.

5. React.createElement(): JSX gets transpiled into calls to React.createElement(). The transpiler converts JSX tags into calls to React.createElement() with the appropriate arguments.

```
// JSX transpiles to React.createElement()
const element = <h1>Hello, world!</h1>;
// Transpiles to:
const element = React.createElement('h1', null, 'Hello, world!');
```

# What is React.createElement ?

React.createElement() is a fundamental method in React used to create React elements. React elements represent
UI components and are the building blocks of React applications.

While developers typically use JSX to define React elements due to its readability and expressiveness, React.createElement() provides a low-level API for creating React elements programmatically. It's used internally by React to create and manage the virtual DOM representation of components.

In JSX syntax, React.createElement() is implicitly called to create React elements. JSX tags get transpiled into calls to React.createElement() during the build process.

```
const element = <div className="container">Hello, world!</div>;
// Transpiles to:
const element = React.createElement('div', { className: 'container' }, 'Hello, world!');
```

# What is redux in React ?

Redux is a predictable state container for JavaScript applications, primarily used with React for managing application state. It provides a centralized store to hold the entire state of your application, which can be accessed and modified using pure functions called reducers.

Here's an overview of Redux and its key concepts:

Store: The store is a centralized container that holds the entire state tree of your application. It represents a single source of truth for the state and provides methods to access and update the state.

State: The state is a plain JavaScript object that represents the current data of your application. In Redux, the state is immutable, meaning it cannot be changed directly. Instead, you update the state by dispatching actions.

Actions: Actions are payloads of information that describe changes to the state of your application. They are plain JavaScript objects with a type property that indicates the type of action being performed. Actions can optionally include additional data (payload) that is necessary to perform the action.

Reducers: Reducers are pure functions that specify how the state of your application changes in response to actions. Each reducer takes the current state and an action as arguments, and returns the next state of the application. Reducers are responsible for updating specific parts of the state based on the type of action dispatched.

Dispatch: Dispatch is a method provided by the Redux store to send actions to the store. When you dispatch an action, Redux invokes the corresponding reducer function, which updates the state accordingly.

Selectors: Selectors are functions used to extract specific pieces of data from the Redux store. They provide a way to query the store state in a consistent and reusable manner.

Redux is commonly used with React to manage the state of complex applications. It helps in maintaining a predictable state management flow, making it easier to understand and debug application behavior. Additionally, Redux provides features like middleware and DevTools integration for advanced state management and debugging capabilities.

# Write a custom hook to copy text to clipboard.

Here's a simple custom React hook to copy text to the clipboard:

```
import { useState } from 'react';

const useClipboard = () => {
  const [copied, setCopied] = useState(false);

  const copyToClipboard = (text) => {
    if (!navigator.clipboard) {
      // Clipboard API not available, fallback to older method
      const textarea = document.createElement('textarea');
      textarea.value = text;
      document.body.appendChild(textarea);
      textarea.select();
      document.execCommand('copy');
      document.body.removeChild(textarea);
      setCopied(true);
    } else {
      navigator.clipboard.writeText(text)
        .then(() => setCopied(true))
        .catch((error) => {
          console.error('Failed to copy text to clipboard:', error);
        });
    }
  };

  const resetCopied = () => {
    setCopied(false);
  };

  return { copied, copyToClipboard, resetCopied };
};

export default useClipboard;
```

You can use this hook in your React components like this:

```
import React, { useState } from 'react';
import useClipboard from './useClipboard';

const MyComponent = () => {
  const [textToCopy, setTextToCopy] = useState('');
  const { copied, copyToClipboard, resetCopied } = useClipboard();

  const handleCopy = () => {
    copyToClipboard(textToCopy);
  };

  return (
    <div>
      <input
        type="text"
        value={textToCopy}
        onChange={(e) => setTextToCopy(e.target.value)}
      />
      <button onClick={handleCopy}>Copy Text</button>
      {copied && <span>Text copied to clipboard!</span>}
      <button onClick={resetCopied}>Reset</button>
    </div>
  );
};

export default MyComponent;
```

In this example, useClipboard hook handles the logic for copying text to the clipboard, while the MyComponent component demonstrates its usage. When the "Copy Text" button is clicked, the text entered in the input field will be copied to the clipboard, and a message will be displayed indicating that the text has been copied. The resetCopied function can be used to reset the copied state if needed.

# How to validate Props in React?

- We can use 'prop-types' package

- Earlier, till React v15.5 this was there as part of React iteslf

```
import PropTypes from "prop-types";

function MyComponent({ name }) {
  return <div>Hello, {name}</div>;
}

MyComponent.propTypes = {
  name: PropTypes.string,
};

export default MyComponent;
```

# What is prop drilling in React ?

When state is shared/passed as an input to multiple nested child components one by one, it is known as prop drilling.
One way to avoid drop drilling in React is to use context provider in which by default all child components wrapped under a context provider will have access to all the props without passing the props again and again from one child to another nested child and so on.
