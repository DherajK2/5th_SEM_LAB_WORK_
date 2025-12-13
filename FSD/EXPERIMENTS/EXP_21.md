# Lab Cycle – Experiment 21

## Aim:

Build a React application using React Router with:

- A **Dashboard** page that shows a list of tasks.
- A **Task Details** page using dynamic route `/task/:taskId`.
- A **Settings** page with user preferences.
- A navigation bar and a **“Page Not Found”** screen for invalid routes.

***

***

## Folder Structure

```text
src/
 ├── App.js
 ├── index.js
 ├── components/
 │     └── Navbar.js
 └── pages/
       ├── Dashboard.js
       ├── TaskDetails.js
       ├── Settings.js
       └── NotFound.js
```


***

## Install React Router

```bash
npm install react-router-dom
```


***

## Source Code

### src/App.js

```javascript
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Navbar from "./components/Navbar";
import Dashboard from "./pages/Dashboard";
import TaskDetails from "./pages/TaskDetails";
import Settings from "./pages/Settings";
import NotFound from "./pages/NotFound";

export default function App() {
  return (
    <Router>
      <Navbar />

      <Routes>
        <Route path="/" element={<Dashboard />} />
        <Route path="/task/:taskId" element={<TaskDetails />} />
        <Route path="/settings" element={<Settings />} />
        {/* Invalid route */}
        <Route path="*" element={<NotFound />} />
      </Routes>
    </Router>
  );
}
```


### src/index.js

```javascript
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```


### src/components/Navbar.js

```javascript
import { Link } from "react-router-dom";

export default function Navbar() {
  return (
    <nav style={{ padding: 10, background: "#eee" }}>
      <Link to="/" style={{ marginRight: 10 }}>Dashboard</Link>
      <Link to="/settings">Settings</Link>
    </nav>
  );
}
```


### src/pages/Dashboard.js

```javascript
import { Link } from "react-router-dom";

export default function Dashboard() {
  const tasks = [
    { id: 1, name: "Buy Groceries" },
    { id: 2, name: "Study React" },
    { id: 3, name: "Go for a Walk" },
  ];

  return (
    <div>
      <h2>Dashboard</h2>
      <ul>
        {tasks.map((task) => (
          <li key={task.id}>
            <Link to={`/task/${task.id}`}>{task.name}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
}
```


### src/pages/TaskDetails.js

```javascript
import { useParams } from "react-router-dom";

export default function TaskDetails() {
  const { taskId } = useParams();

  return (
    <div>
      <h2>Task Details</h2>
      <p>You are viewing task ID: {taskId}</p>
    </div>
  );
}
```


### src/pages/Settings.js

```javascript
export default function Settings() {
  return (
    <div>
      <h2>Settings</h2>
      <p>User preferences will appear here.</p>
    </div>
  );
}
```


### src/pages/NotFound.js

```javascript
export default function NotFound() {
  return (
    <div>
      <h2>404 - Page Not Found</h2>
      <p>The page you are looking for does not exist.</p>
    </div>
  );
}
```



***

## How to Run

```bash
npm install react-router-dom
npm start
```

