# Lab Cycle - Experiment 18

## Aim:

Demonstrate basic MongoDB operations using `mongosh` to:

1. Create a database `CollegeDB` and a collection `students`.
2. Insert three documents into `students` using `insert()`.
3. Insert multiple documents into a `courses` collection using `insertMany()`.
4. Retrieve all documents from `students`.
5. Retrieve students where `age > 18`.
6. Retrieve students with `grade = "A"`.
7. Retrieve courses with `credits >= 3`.[^1][^2][^3][^4]

***
***

## Source Code

```javascript
// 1. Select/Create the database
use CollegeDB;

// 2. Create the 'students' collection
db.createCollection("students");

// 3. Insert three documents into 'students' using insert()
db.students.insert({
  name: "Rahul",
  age: 19,
  sem: 3,
  usn: "1AB20CS001",
  grade: "A"
});

db.students.insert({
  name: "Sneha",
  age: 17,
  sem: 2,
  usn: "1AB20CS002",
  grade: "B"
});

db.students.insert({
  name: "Amit",
  age: 21,
  sem: 5,
  usn: "1AB20CS003",
  grade: "A"
});

// 4. Create 'courses' collection and insert multiple documents using insertMany()
db.createCollection("courses");

db.courses.insertMany([
  {
    courseName: "Data Structures",
    courseCode: "CS201",
    credits: 4
  },
  {
    courseName: "Operating Systems",
    courseCode: "CS301",
    credits: 3
  },
  {
    courseName: "Computer Networks",
    courseCode: "CS401",
    credits: 2
  }
]);

// 5. Retrieve all documents from 'students'
db.students.find();
// or
db.students.find().pretty();

// 6. Retrieve all students where age > 18
db.students.find({ age: { $gt: 18 } });

// 7. Find all students with grade "A"
db.students.find({ grade: "A" });

// 8. Find all courses with credits >= 3
db.courses.find({ credits: { $gte: 3 } });

```


***

## Output

- **Students collection (sample)**
- All three inserted student documents are listed when running `db.students.find()` or `db.students.find().pretty()`.[^5][^6]
- **Courses collection (sample)**
- All three inserted course documents are listed when running `db.courses.find()`.[^7]
- **Filtered queries**
- `db.students.find({ age: { $gt: 18 } })` returns students with age strictly greater than 18.[^3][^8]
- `db.students.find({ grade: "A" })` returns only the students having grade "A".
- `db.courses.find({ credits: { $gte: 3 } })` returns only those courses whose credits are 3 or more.[^4]

***

## Explanation

### a) Creating database and collections

- The `use CollegeDB;` command switches to the `CollegeDB` database and creates it implicitly when a collection is added.[^1]
- `db.createCollection("students")` and `db.createCollection("courses")` explicitly create the collections inside `CollegeDB`.[^6][^5]


### b) Inserting documents

- `db.students.insert({...})` inserts a single document into the `students` collection each time it is called.[^2][^9]
- `db.courses.insertMany([...])` inserts multiple course documents in one operation, which is efficient for batch inserts.[^10][^2][^7]


### c) Querying with find(), \$gt, and \$gte

- `db.students.find()` returns all documents in the `students` collection; `pretty()` formats them for readability.[^11][^5]
- The `$gt` operator selects documents where a field value is greater than a specified value, used here for `age > 18`.[^12][^13][^3]
- The `$gte` operator selects documents where a field value is greater than or equal to a specified value, used here for `credits >= 3`.[^8][^4]

***

## Viva Questions

1. **How do you create and select a database in MongoDB?**

- By using the `use dbName;` command, which switches to that database and creates it when collections are added.[^1]

2. **What is the purpose of `db.createCollection()`?**

- It explicitly creates a collection with the given name in the current database, although MongoDB can also create collections implicitly on first insert.[^5][^6]

3. **What is the difference between `insert()` and `insertMany()`?**

- `insert()` (or `insertOne()`) adds a single document, whereas `insertMany()` inserts an array of documents in a single call, which is more efficient for bulk inserts.[^9][^2][^10]

4. **What does the `$gt` operator do in a MongoDB query?**

- It filters documents where the specified field value is strictly greater than the given value, such as `age > 18`.[^13][^3][^12]

5. **When would you use the `$gte` operator instead of `$gt`?**

- When documents with field values equal to the threshold should also be included, such as courses with `credits >= 3`.[^4][^8]

***

## Note

- Collections can be created automatically when the first document is inserted, but using `db.createCollection()` provides explicit control and options.[^14][^15][^1]
- Using query operators like `$gt` and `$gte` allows flexible filtering of documents based on numeric or comparable field values.[^3][^12][^13]
- Structured naming for fields like `courseName`, `courseCode`, and `credits` helps maintain clarity in academic databases such as `CollegeDB`.

***

## Conclusion

This experiment demonstrates creating a MongoDB database and collections, inserting single and multiple documents, and querying data using `find()`, `$gt`, and `$gte` operators to meet typical academic record management requirements in `CollegeDB`.[^2][^3][^4][^1]
<span style="display:none">[^16][^17][^18][^19][^20]</span>

<div align="center">⁂</div>

[^1]: https://www.geeksforgeeks.org/mongodb/how-to-create-database-collection-in-mongodb/

[^2]: https://sparkbyexamples.com/mongodb/mongodb-insertone-insertmany-documents/

[^3]: https://www.geeksforgeeks.org/mongodb/mongodb-greater-than-operator-gt/

[^4]: https://www.geeksforgeeks.org/mongodb/mongodb-greater-than-equals-to-operator-gte/

[^5]: https://www.w3schools.com/mongodb/mongodb_mongosh_create_collection.php

[^6]: https://www.tutorialspoint.com/mongodb/mongodb_create_collection.htm

[^7]: https://www.mongodbtutorial.org/mongodb-crud/mongodb-insertmany/

[^8]: https://www.statology.org/mongodb-greater-than-less-than/

[^9]: https://stackoverflow.com/questions/36792649/whats-the-difference-between-insert-insertone-and-insertmany-method

[^10]: https://www.geeksforgeeks.org/mongodb/mongodb-insertmany-method-db-collection-insertmany/

[^11]: https://www.mycompiler.io/view/KJWxHhwctOt

[^12]: https://www.scaler.com/topics/gt-in-mongodb/

[^13]: https://www.bmc.com/blogs/mongodb-operators/

[^14]: https://www.studytonight.com/mongodb/collection-create-and-drop-mongodb

[^15]: https://www.simplilearn.com/tutorials/mongodb-tutorial/create-collection-in-mongodb

[^16]: https://studio3t.com/knowledge-base/articles/mongodb-collections-a-complete-guide-and-tutorial/

[^17]: https://www.w3schools.com/nodejs/nodejs_mongodb_createcollection.asp

[^18]: https://www.geeksforgeeks.org/python/difference-between-insert-insertone-and-insertmany-in-pymongo/

[^19]: https://www.mongodb.com/docs/v3.2/reference/method/db.createCollection/

[^20]: https://www.w3resource.com/mongodb/shell-methods/database/db-createCollection.php

