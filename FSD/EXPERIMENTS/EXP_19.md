# Lab Cycle - Experiment 19

## Aim:

Demonstrate MongoDB operations using Mongo shell and database tools to:

1. Switch to the `WorkDB` database.
2. Create a `teachers` collection.
3. Insert documents with fields `name`, `subject`, and `experience`.
4. Export the `teachers` collection to a JSON file.
5. Import the JSON file into a new collection `teachersBackup`.[^1][^2][^3][^4][^5][^6]

***
***

## Source Code

```javascript
// 1. Switch to the WorkDB database
use WorkDB;

// 2. Create the 'teachers' collection
db.createCollection("teachers");

// 3. Insert documents into 'teachers' (name, subject, experience)
db.teachers.insert({
  name: "Anita",
  subject: "Mathematics",
  experience: 8
});

db.teachers.insert({
  name: "Ramesh",
  subject: "Physics",
  experience: 5
});

db.teachers.insert({
  name: "Kavya",
  subject: "Computer Science",
  experience: 10
});

// 4. EXPORT students collection to JSON (run in terminal / CMD, not in mongosh)
// Command:
 // mongoexport --db=WorkDB --collection=students --out=teachers.json

// 5. IMPORT JSON file into new collection 'studentsBackup' (terminal / CMD)
// Command:
 // mongoimport --db=WorkDB --collection=teachersBackup --file=teachers.json
```


***

## Output

- **Mongo shell operations**
- `use WorkDB;` switches the context to the `WorkDB` database or creates it when collections are added.[^4]
- `db.createCollection("teachers")` creates an empty `teachers` collection, and subsequent `insert()` calls add three teacher documents.[^3][^7]
- **Export operation (`mongoexport`)**
- `mongoexport --db=WorkDB --collection=students --out=students.json` creates a `students.json` file containing all documents from the `students` collection in JSON format.[^2][^8][^5][^9][^1]
- **Import operation (`mongoimport`)**
- `mongoimport --db=WorkDB --collection=studentsBackup --file=students.json` reads the JSON file and inserts the data into a new collection `studentsBackup` in the same `WorkDB` database.[^10][^11][^6][^12]

***

## Explanation

### a) Database and collection creation

- The `use WorkDB;` command selects the `WorkDB` database, and MongoDB creates it on disk when a collection or document is first added.[^4]
- `db.createCollection("teachers")` explicitly creates the `teachers` collection instead of relying on implicit creation during the first insert.[^13][^7][^3]


### b) Inserting teacher documents

- Each `db.teachers.insert({...})` call inserts a single document with `name`, `subject`, and `experience` fields into the `teachers` collection.[^4]
- The inserted documents form a simple dataset of teachers that can be queried later based on subject or years of experience.


### c) Exporting and importing with mongoexport/mongoimport

- `mongoexport` is a standalone database tool used from the system terminal to export collection data to JSON or CSV files; typical syntax includes `--db`, `--collection`, and `--out` options.[^8][^5][^9][^1][^2]
- `mongoimport` is used from the terminal to import JSON or CSV data into a MongoDB collection, and it can create the database or collection if they do not already exist.[^11][^6][^12][^10]

***

## Viva Questions

1. **What is the effect of the `use WorkDB;` command in Mongo shell?**

- It switches the current context to the `WorkDB` database and prepares it for collection and document operations.[^4]

2. **Why is `db.createCollection("teachers")` used if MongoDB can create collections automatically?**

- It provides explicit control over collection creation and can be used to specify options such as caps and limits if needed.[^7][^3][^13]

3. **What is the purpose of the `mongoexport` command?**

- It exports data from a specific MongoDB collection to an external JSON or CSV file for backup, migration, or analysis.[^5][^9][^1][^2][^8]

4. **How does `mongoimport` handle the target collection if it does not exist?**

- It can automatically create the target collection (and database) while importing the data from the specified file.[^6][^12][^10]

5. **Why are `mongoexport` and `mongoimport` not run inside `mongosh`?**

- They are separate command-line tools that interact with MongoDB from the operating system shell, not JavaScript methods inside the Mongo shell.[^14][^15][^1][^10]

***

## Note

- Always run `mongoexport` and `mongoimport` from a terminal or command prompt with correct connection parameters if MongoDB is not on the default host or port.[^1][^14][^2][^5]
- Keeping a backup collection like `studentsBackup` is a good practice to safeguard original data before performing bulk updates or deletes.[^9]

***

## Conclusion

This experiment shows how to manage data in MongoDB by creating collections, inserting teacher records, and using `mongoexport` and `mongoimport` tools to back up and restore the `students` collection between JSON files and database collections in `WorkDB`.[^2][^5][^6][^1][^4]
<span style="display:none">[^16][^17][^18][^19][^20]</span>

<div align="center">⁂</div>

[^1]: https://www.mongodb.com/docs/database-tools/mongoexport/mongoexport-examples/

[^2]: https://hevodata.com/learn/mongoexport-export-mongodb-collections/

[^3]: https://www.w3schools.com/mongodb/mongodb_mongosh_create_collection.php

[^4]: https://www.geeksforgeeks.org/mongodb/how-to-create-database-collection-in-mongodb/

[^5]: https://www.mongodbtutorial.org/mongodb-tools/mongoexport/

[^6]: https://www.geeksforgeeks.org/mongodb/import-data-to-mongodb/

[^7]: https://www.tutorialspoint.com/mongodb/mongodb_create_collection.htm

[^8]: https://www.geeksforgeeks.org/mongodb/export-data-from-mongodb/

[^9]: https://www.scaler.com/topics/mongodb/export_and_import_a_db_and_a_collection/

[^10]: https://hevodata.com/learn/mongoimport/

[^11]: https://sparkbyexamples.com/mongodb/import-json-file-using-the-mongoimport-command/

[^12]: https://www.mongodb.com/docs/database-tools/mongoimport/mongoimport-examples/

[^13]: https://www.w3resource.com/mongodb/shell-methods/database/db-createCollection.php

[^14]: https://www.mongodb.com/docs/database-tools/mongoexport/

[^15]: https://docs.aws.amazon.com/documentdb/latest/developerguide/backup_restore-dump_restore_import_export_data.html

[^16]: https://stackoverflow.com/questions/11255630/how-to-export-all-collections-in-mongodb

[^17]: https://www.nielit.gov.in/gorakhpur/sites/default/files/Gorakhpur/ALEVEL_1_DBTECH_08_June_2020_IL.pdf

[^18]: https://www.w3schools.com/nodejs/nodejs_mongodb_createcollection.asp

[^19]: https://www.youtube.com/watch?v=dwLi8L2HTbc

[^20]: https://docs.digitalocean.com/products/databases/mongodb/how-to/import-collections/

