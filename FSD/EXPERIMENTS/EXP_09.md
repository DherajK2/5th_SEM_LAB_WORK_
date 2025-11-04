# Lab Cycle - Experiment 9

## Aim:

Illustrate a React program implementing **error boundaries** to detect and handle:

1. Division by zero error.
2. Array index out of bound error.

***

## Source Code

### ErrorBoundary.js

```javascript
import React from "react";

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.log("Error caught by ErrorBoundary:", error, info);
  }

  render() {
    if (this.state.hasError) {
      return (
        <h3 style={{ color: "red" }}>Something went wrong!</h3>
      );
    }
    return this.props.children;
  }
}

export default ErrorBoundary;
```


***

### DivisionComponentError.js

```javascript
import React from "react";

function DivisionComponentError({ a, b }) {
  if (b === 0) {
    throw new Error("Division by zero is not allowed!");
  }

  const result = a / b;
  return (
    <div style={{ textAlign: "center" }}>
      <h3>Division Result: {result}</h3>
    </div>
  );
}

export default DivisionComponentError;
```


***

### ArrayComponentError.js

```javascript
import React from "react";

function ArrayComponentError() {
  const arr = [10, 20, 30];
  const index = 5; // intentionally out of bounds

  if (index >= arr.length) {
    throw new Error("Array Index Out of Bound!");
  }

  return (
    <div style={{ textAlign: "center" }}>
      <h3>Array Element: {arr[index]}</h3>
    </div>
  );
}

export default ArrayComponentError;
```


***

### App.js

```javascript
import DivisionComponentError from './DivisionComponentError';
import ErrorBoundary from './ErrorBoundary';
import ArrayComponentError from './ArrayComponentError';

function App() {
  return (
    <div style={{ textAlign: "center" }}>
      <h2>React Error Boundaries Example</h2>

      <ErrorBoundary>
        <h3>1. Division By Zero</h3>
        <DivisionComponentError a={10} b={0} /> {/* Trigger error */}
      </ErrorBoundary>

      <ErrorBoundary>
        <h3>2. Array Index Out of Bound</h3>
        <ArrayComponentError /> {/* Trigger error */}
      </ErrorBoundary>
    </div>
  );
}

export default App;
```


***

## Output

- On loading the page:
    - The **DivisionComponentError** throws a division-by-zero error.
    - The **ArrayComponentError** throws an array index out of bound error.
- Both errors are caught by the enclosing `<ErrorBoundary>`.
- Instead of the app crashing, the error boundary displays the message:

```
Something went wrong!
```

- Console logs the details of the errors captured by `componentDidCatch`.

***

## Explanation

### a) ErrorBoundary Class Component

- Implements `getDerivedStateFromError` to update state on error.
- Implements `componentDidCatch` to log error information.
- Displays fallback UI when an error occurs.


### b) DivisionComponentError

- Throws error if divisor `b` is zero to simulate division by zero.


### c) ArrayComponentError

- Throws error if accessing an invalid index in the array.


### d) Usage in App.js

- Wraps components likely to throw errors inside `<ErrorBoundary>`.
- Keeps UI stable by gracefully handling runtime errors in children.

***

## Viva Questions

1. **What are error boundaries in React?**
    - Components that catch JavaScript errors anywhere in their child component tree and display a fallback UI instead of crashing.
2. **Which lifecycle methods are used in Error Boundaries?**
    - `static getDerivedStateFromError()` and `componentDidCatch()`.
3. **Why is error handling important in React apps?**
    - Prevents app crashes and improves user experience by showing fallback UIs.
4. **Can functional components be error boundaries?**
    - No, currently error boundaries must be class components.
5. **What happens if an error is not caught by any error boundary?**
    - The error crashes the entire React component tree or page.

***

## Note:

- Always isolate error-prone components with error boundaries for robustness.
- `componentDidCatch` helps in logging and analytics for better debugging.

***

## Conclusion:

This experiment demonstrates implementing React error boundaries to catch runtime errors like division by zero and out-of-bound array access gracefully, ensuring the UI remains stable and user-friendly.

***
