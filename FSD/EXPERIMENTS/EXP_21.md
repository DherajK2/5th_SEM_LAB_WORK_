# Lab Cycle – Experiment 21

## Aim:

Build a React application using React Router with:

- A **Dashboard** page that shows a list of tasks.
- A **Task Details** page using a dynamic route `/task/:taskId`.
- A **Settings** page containing user preferences.
- A navigation menu and a **“Page Not Found”** screen for invalid routes.

***

***

## Folder Structure

```text
src/
 ├── App.js
 ├── Dashboard.js
 ├── TaskDetails.js
 ├── Settings.js
 └── NotFound.js
```


***

## Source Code

### src/App.js

```javascript
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import Dashboard from "./Dashboard";
import TaskDetails from "./TaskDetails";
import Settings from "./Settings";
import NotFound from "./NotFound";

export default function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Dashboard</Link> |{" "}
        <Link to="/settings">Settings</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Dashboard />} />
        <Route path="/task/:taskId" element={<TaskDetails />} />
        <Route path="/settings" element={<Settings />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}
```


### src/Dashboard.js

```javascript
import { Link } from "react-router-dom";

export default function Dashboard() {
  const tasks = [
    { id: 1, name: "Task One" },
    { id: 2, name: "Task Two" }
  ];

  return (
    <div>
      <h2>Dashboard</h2>
      <ul>
        {tasks.map((t) => (
          <li key={t.id}>
            <Link to={`/task/${t.id}`}>{t.name}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
}
```


### src/TaskDetails.js

```javascript
import { useParams } from "react-router-dom";

export default function TaskDetails() {
  const { taskId } = useParams();

  return (
    <div>
      <h2>Task Details</h2>
      <p>Task ID: {taskId}</p>
    </div>
  );
}
```


### src/Settings.js

```javascript
export default function Settings() {
  return (
    <div>
      <h2>Settings</h2>
      <p>User preferences page</p>
    </div>
  );
}
```


### src/NotFound.js

```javascript
export default function NotFound() {
  return <h2>404 - Page Not Found</h2>;
}
```


***

## How to Run

```bash
npm install react-router-dom
npm start
```

