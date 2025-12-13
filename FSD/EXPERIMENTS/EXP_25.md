# Lab Cycle – Experiment 25

## Aim:

Create a Course Management REST API using Node.js, Express, and MongoDB (Mongoose) to:

- Add routes to create, view, update, and delete course details.
- Store for each course: `courseName`, `faculty`, `credits`, and `studentsEnrolled`.
- Implement a `/courses/totalStudents` route to calculate total enrollment across all courses.
- Use Mongoose validation (`required: true`) for all fields.

***

***

## Source Code – `index.js`

```javascript
const express = require("express");
const mongoose = require("mongoose");

const app = express();
app.use(express.json());

// MongoDB connection
mongoose.connect("mongodb://127.0.0.1:27017/courseDB");

// Schema
const Course = mongoose.model("Course", {
  courseName: { type: String, required: true },
  faculty: { type: String, required: true },
  credits: { type: Number, required: true },
  studentsEnrolled: { type: Number, required: true }
});

// Add course
app.post("/courses", async (req, res) => {
  const course = await Course.create(req.body);
  res.send(course);
});

// View all courses
app.get("/courses", async (req, res) => {
  res.send(await Course.find());
});

// Update course
app.put("/courses/:id", async (req, res) => {
  const course = await Course.findByIdAndUpdate(
    req.params.id,
    req.body,
    { new: true }
  );
  res.send(course);
});

// Delete course
app.delete("/courses/:id", async (req, res) => {
  await Course.findByIdAndDelete(req.params.id);
  res.send("Course deleted");
});

// Total students
app.get("/courses/totalStudents", async (req, res) => {
  const courses = await Course.find();
  let total = 0;
  courses.forEach(c => total += c.studentsEnrolled);
  res.send({ totalStudents: total });
});

app.listen(3000, () => console.log("Server started"));
```


***

## How to Run

```bash
npm init -y
npm install express mongoose
node index.js
```

Ensure MongoDB is running locally on `mongodb://127.0.0.1:27017`.

***

## Testing (Thunder Client / Postman)

All routes are tested using **Thunder Client or Postman**.

1. **Add Course (CREATE)**
    - Method: `POST`
    - URL: `http://localhost:3000/courses`
    - Body → JSON:

```json
{
  "courseName": "DBMS",
  "faculty": "Dr. Rao",
  "credits": 4,
  "studentsEnrolled": 60
}
```

2. **View All Courses (READ)**
    - Method: `GET`
    - URL: `http://localhost:3000/courses`
3. **Update Course (UPDATE)**
    - Method: `PUT`
    - URL: `http://localhost:3000/courses/<id>`
    - Body → JSON (example):

```json
{
  "courseName": "Advanced DBMS",
  "faculty": "Dr. Rao",
  "credits": 4,
  "studentsEnrolled": 70
}
```

4. **Delete Course (DELETE)**
    - Method: `DELETE`
    - URL: `http://localhost:3000/courses/<id>`
5. **Total Students Across All Courses**
    - Method: `GET`
    - URL: `http://localhost:3000/courses/totalStudents`

***

## Viva Questions and Answers

1. **What is the purpose of `mongoose.model("Course", {...})`?**
It defines a Mongoose model named `Course` with a schema describing the fields and their types; this model is then used to interact with the `courses` collection in MongoDB.
2. **How is validation implemented in this API?**
Validation is provided by Mongoose using `required: true` on each field in the schema, so creating a course without a required field will throw a validation error.
3. **Which HTTP methods are used to implement CRUD operations?**
    - `POST /courses` → Create a new course.
    - `GET /courses` → Read all courses.
    - `PUT /courses/:id` → Update an existing course.
    - `DELETE /courses/:id` → Delete a course.
4. **How does the `/courses/totalStudents` route calculate total enrollment?**
It fetches all course documents, iterates over them, sums the `studentsEnrolled` value for each course into `total`, and returns `{ totalStudents: total }`.
5. **Why do we use `app.use(express.json())` in this program?**
It parses incoming JSON request bodies so that `req.body` automatically contains the JavaScript object sent from Thunder Client or Postman.
