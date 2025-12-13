# 21. Build a React application using React Router with the following pages: • Dashboard – shows a list of tasks.

• Task Details – dynamic route showing task info using /task/:taskId.
• Settings – contains user preferences.
Add a navigation menu and show a “Page Not Found” screen for invalid routes

✅ Folder Structure (NO subfolders)
src/
├── App.js
├── Dashboard.js
├── TaskDetails.js
├── Settings.js
└── NotFound.js

✅ src/App.js
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

✅ src/Dashboard.js
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
{tasks.map(t => (
<li key={t.id}>
<Link to={`/task/${t.id}`}>{t.name}</Link>
</li>
))}
</ul>
</div>
);
}

✅ src/TaskDetails.js
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

✅ src/Settings.js
export default function Settings() {
return (
<div>
<h2>Settings</h2>
<p>User preferences page</p>
</div>
);
}

✅ src/NotFound.js
export default function NotFound() {

```
return <h2>404 - Page Not Found</h2>;
```

}

✅ Run
npm install react-router-dom
npm start

Here is the clean, final **.md file content** for **Experiment 21** using your React Router code.

***

# Lab Cycle – Experiment 21

## Aim:

Build a React application using React Router with:

- A **Dashboard** page that shows a list of tasks.
- A **Task Details** page using a dynamic route `/task/:taskId`.
- A **Settings** page containing user preferences.
- A navigation menu and a **“Page Not Found”** screen for invalid routes.[^1][^2][^3][^4]

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
        {tasks.map(t => (
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

`BrowserRouter` provides client-side routing, `Routes` and `Route` map URL paths to components, `Link` creates navigation links, and `useParams` reads the `taskId` parameter from the dynamic `/task/:taskId` route; the `path="*"` route renders the **NotFound** component for any invalid URL.[^5][^6][^4][^7]
<span style="display:none">[^10][^11][^12][^13][^14][^15][^16][^17][^18][^19][^20][^21][^8][^9]</span>

<div align="center">⁂</div>

[^1]: https://blog.logrocket.com/react-router-v6-guide/

[^2]: https://www.freecodecamp.org/news/how-to-use-react-router-version-6/

[^3]: https://www.sitepoint.com/react-router-complete-guide/

[^4]: https://www.w3schools.com/react/react_router.asp

[^5]: https://reactrouter.com/api/hooks/useParams

[^6]: https://www.geeksforgeeks.org/reactjs/how-to-setup-404-page-in-react-routing/

[^7]: https://www.geekster.in/articles/browserrouter-routes-route-in-react-router-dom/

[^8]: https://trio.dev/guide-to-react-router-v6/

[^9]: https://www.geeksforgeeks.org/reactjs/create-a-basic-navbar-using-react-router-v6/

[^10]: https://stackoverflow.com/questions/32128978/react-router-no-not-found-route

[^11]: https://reactrouter.com/6.30.2/start/tutorial

[^12]: https://refine.dev/blog/react-router-useparams/

[^13]: https://www.telerik.com/blogs/react-basics-how-to-use-react-router-v6

[^14]: https://www.freecodecamp.org/news/use-dynamic-segments-in-react-router/

[^15]: https://github.com/remix-run/react-router/discussions/10640

[^16]: https://reactrouter.com

[^17]: https://api.reactrouter.com/v7/functions/react_router.useParams.html

[^18]: https://www.dhiwise.com/post/a-comprehensive-guide-to-fixing-react-router-refresh-404

[^19]: https://www.youtube.com/watch?v=5bLFrkJMteU

[^20]: https://stackoverflow.com/questions/67050966/how-to-build-a-404-page-with-react-router-dom-v6

[^21]: https://www.youtube.com/watch?v=Ul3y1LXxzdU

