# Lab Cycle – Experiment 26

## Aim:

Develop a Node.js program using the MongoDB native driver to:

1. Read a list of employee records from a file named `employees.json`.
2. Connect to a MongoDB database `CompanyDB` and insert the records into a collection called `employees`.
3. Update the record of the employee with `empId = 101` by changing the value of the `designation` field.
4. Retrieve all employee records and write them into a file named `updated_employees.json`.
5. Display a message confirming that the export process has been successfully completed.

***

***

## Input File – `employees.json`

```json
[
  {
    "empId": 101,
    "name": "Rahul",
    "designation": "Developer",
    "salary": 50000
  },
  {
    "empId": 102,
    "name": "Anita",
    "designation": "Tester",
    "salary": 45000
  },
  {
    "empId": 103,
    "name": "Vikas",
    "designation": "Manager",
    "salary": 70000
  }
]
```


***

## Source Code – `employeeOperations.js`

```javascript
const fs = require("fs");
const { MongoClient } = require("mongodb");

const employees = JSON.parse(fs.readFileSync("employees.json", "utf8"));
const url = "mongodb://127.0.0.1:27017";
const client = new MongoClient(url);
const dbName = "CompanyDB";

async function run() {
  try {
    // Connect to MongoDB
    await client.connect();
    const db = client.db(dbName);
    const collection = db.collection("employees");

    // Insert records into employees collection
    await collection.insertMany(employees);

    // Update employee with empId = 101
    await collection.updateOne(
      { empId: 101 },
      { $set: { designation: "Senior Developer" } }
    );

    // Retrieve all updated records
    const updatedRecords = await collection.find().toArray();

    // Write all records into updated_employees.json
    fs.writeFileSync(
      "updated_employees.json",
      JSON.stringify(updatedRecords, null, 2)
    );

    // Confirmation message
    console.log("Export completed successfully!");
  } catch (error) {
    console.error("Error occurred:", error);
  } finally {
    // Close connection
    await client.close();
  }
}

run();
```


***

## How to Run and Check Each Step

1. **Install MongoDB driver**
```bash
npm init -y
npm install mongodb
```

2. **Run the program**
```bash
node employeeOperations.js
```

3. **Check insertion and update in MongoDB**

Open `mongosh`:

```js
use CompanyDB
db.employees.find().pretty()
```

- You should see all employees from `employees.json`.
- For `empId: 101`, `designation` must be `Senior Developer`.

4. **Check exported file**

- Confirm `updated_employees.json` is created in the same folder.
- Open it and verify it contains all employee documents with the updated designation.

5. **Check confirmation message**

- Terminal must show:
`Export completed successfully!`

***

## Viva Questions

1. What is the role of `MongoClient` in this program?
2. Why is `find().toArray()` used before writing data to the JSON file?
3. How does the `$set` operator work in the `updateOne()` method?
4. What happens if `employees.json` is missing or has invalid JSON?
5. Why is `client.close()` called inside the `finally` block?
