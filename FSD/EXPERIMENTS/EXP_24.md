# Lab Cycle – Experiment 24

## Aim:

Develop an Express.js API for Teacher Records that:

1. Provides CRUD routes to create, fetch all, fetch by ID, update, and delete teacher details.
2. Parses JSON data using middleware and returns error messages for invalid requests.
3. Uses fields: `name`, `department`, `experience`, and `email`.
4. Returns meaningful success messages for each action.

***

***

## Source Code – `index.js`

```javascript
const express = require("express");
const app = express();

app.use(express.json()); // JSON middleware

let teachers = [];
let id = 1;

// CREATE teacher
app.post("/teachers", (req, res) => {
  const { name, department, experience, email } = req.body;

  if (!name || !department || !experience || !email)
    return res.status(400).json({ error: "All fields are required" });

  const teacher = { id: id++, name, department, experience, email };
  teachers.push(teacher);

  res.json({ message: "Teacher added successfully", data: teacher });
});

// FETCH all teachers
app.get("/teachers", (req, res) => {
  res.json(teachers);
});

// FETCH teacher by ID
app.get("/teachers/:id", (req, res) => {
  const teacher = teachers.find(t => t.id == req.params.id);
  if (!teacher)
    return res.status(404).json({ error: "Teacher not found" });

  res.json(teacher);
});

// UPDATE teacher
app.put("/teachers/:id", (req, res) => {
  const teacher = teachers.find(t => t.id == req.params.id);
  if (!teacher)
    return res.status(404).json({ error: "Teacher not found" });

  Object.assign(teacher, req.body);
  res.json({ message: "Teacher updated successfully", data: teacher });
});

// DELETE teacher
app.delete("/teachers/:id", (req, res) => {
  const index = teachers.findIndex(t => t.id == req.params.id);
  if (index === -1)
    return res.status(404).json({ error: "Teacher not found" });

  teachers.splice(index, 1);
  res.json({ message: "Teacher deleted successfully" });
});

// Start server
app.listen(3000, () => console.log("Server running on port 3000"));
```


***

## How to Run

```bash
npm init -y
npm install express
node index.js
```

The server runs on `http://localhost:3000`.

***

## Testing (Postman / Thunder Client)

All routes can be tested using **Postman or Thunder Client**.

1. **Create Teacher (POST)**
    - Method: `POST`
    - URL: `http://localhost:3000/teachers`
    - Body → JSON:

```json
{
  "name": "Anita",
  "department": "CS",
  "experience": 5,
  "email": "anita@gmail.com"
}
```

    - Expected:

```json
{
  "message": "Teacher added successfully",
  "data": { ...teacher object... }
}
```

2. **Fetch All Teachers (GET)**
    - Method: `GET`
    - URL: `http://localhost:3000/teachers`
    - Expected: Array of all teacher objects.
3. **Fetch Teacher by ID (GET)**
    - Method: `GET`
    - URL: `http://localhost:3000/teachers/1`
    - If found, returns the teacher object; otherwise:

```json
{ "error": "Teacher not found" }
```

4. **Update Teacher (PUT)**
    - Method: `PUT`
    - URL: `http://localhost:3000/teachers/1`
    - Body → JSON (example):

```json
{
  "experience": 6
}
```

    - Expected:

```json
{
  "message": "Teacher updated successfully",
  "data": { ...updated teacher... }
}
```

5. **Delete Teacher (DELETE)**
    - Method: `DELETE`
    - URL: `http://localhost:3000/teachers/1`
    - Expected:

```json
{ "message": "Teacher deleted successfully" }
```
