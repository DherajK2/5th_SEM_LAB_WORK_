# Lab Cycle - Experiment 20

## Aim:

Write MongoDB aggregation queries on an `employees` collection to:

1. Group the employees by their department and calculate the total number of employees in each department.
2. Calculate the average salary of employees in each department.
3. Sort the aggregated results by the total number of employees in descending order.[^1][^2][^3]

***

***

## Example Data

```javascript
// Example data in the employees collection
db.employees.insertMany([
  { name: "Alice",   department: "HR",      salary: 45000 },
  { name: "Bob",     department: "HR",      salary: 47000 },
  { name: "Charlie", department: "IT",      salary: 60000 },
  { name: "David",   department: "IT",      salary: 65000 },
  { name: "Esha",    department: "IT",      salary: 62000 },
  { name: "Farhan",  department: "Finance", salary: 55000 }
]);
```


***

## 1) Group by Department and Count Employees

### Aggregation Query

```javascript
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      totalEmployees: { $sum: 1 }
    }
  }
]);
```


### Example Output

```text
{ _id: "IT",      totalEmployees: 3 }
{ _id: "HR",      totalEmployees: 2 }
{ _id: "Finance", totalEmployees: 1 }
```

This query uses `$group` with `_id: "$department"` to group employees by department and `$sum: 1` to count how many employees are in each group.[^4][^5][^1]

***

## 2) Average Salary in Each Department

### Aggregation Query

```javascript
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      avgSalary: { $avg: "$salary" }
    }
  }
]);
```


### Example Output

```text
{ _id: "IT",      avgSalary: 62333.33 }
{ _id: "HR",      avgSalary: 46000 }
{ _id: "Finance", avgSalary: 55000 }
```

This query again groups by `department` and uses the `$avg` accumulator to calculate the average salary in each department.[^2][^6][^7]

***

## 3) Group and Sort by Total Employees (Descending)

### Aggregation Query

```javascript
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      totalEmployees: { $sum: 1 }
    }
  },
  {
    $sort: { totalEmployees: -1 }
  }
]);
```


### Example Output

```text
{ _id: "IT",      totalEmployees: 3 }
{ _id: "HR",      totalEmployees: 2 }
{ _id: "Finance", totalEmployees: 1 }
```

Here `$sort: { totalEmployees: -1 }` orders the grouped results so that departments with more employees appear first.[^3][^8][^1]

***

## Explanation

- `$group` is used to aggregate documents by a specific field such as `department`, and accumulators like `$sum` and `$avg` compute counts and averages over each group.[^9][^1][^2]
- `$sort` with a value of `-1` sorts the aggregation result in descending order based on the specified field, here `totalEmployees`.[^8][^10][^3]

***

## Viva Questions

1. **What is the purpose of the `$group` stage in MongoDB aggregation?**

- It groups documents by a specified key and allows applying accumulator expressions like `$sum` and `$avg` on each group.[^11][^1]

2. **How does `$sum: 1` work inside a `$group` stage?**

- It increments the count by 1 for each document in the group, effectively giving the total number of documents per group.[^5][^12][^4]

3. **Which operator is used to calculate average values in aggregation?**

- The `$avg` operator is used to compute the average of a numeric expression over all documents in each group.[^6][^13][^2]

4. **How do you sort aggregation results in descending order?**

- By using a `$sort` stage with the key set to `-1`, for example `{ $sort: { totalEmployees: -1 } }`.[^3][^8]

5. **Can multiple stages like `$group` and `$sort` be combined in a single aggregation pipeline?**

- Yes, aggregation pipelines allow chaining multiple stages in order, so the output of `$group` can be passed to `$sort` or other stages for further processing.[^14][^9]

***

## Conclusion

This experiment demonstrates how to use MongoDB’s aggregation framework to group employees by department, calculate both the total number of employees and the average salary per department, and finally sort the aggregated results by the total number of employees in descending order.[^1][^2][^8][^14]

<div align="center">⁂</div>

[^1]: https://www.geeksforgeeks.org/mongodb/mongodb-aggregation-group-command/

[^2]: https://www.mongodbtutorial.org/mongodb-aggregation/mongodb-avg/

[^3]: https://mongoing.com/docs/reference/operator/aggregation/sort.html

[^4]: https://www.statology.org/mongodb-group-by-sum/

[^5]: https://www.singlestore.com/blog/complete-guide-to-the-mongodb-sum-operator/

[^6]: https://mongoing.com/docs/reference/operator/aggregation/avg.html

[^7]: https://www.singlestore.com/blog/how-to-calculate-an-average-in-mongodb/

[^8]: https://www.w3schools.com/mongodb/mongodb_aggregations_sort.php

[^9]: https://www.geeksforgeeks.org/mongodb/aggregation-in-mongodb/

[^10]: https://learn.mongodb.com/learn/course/mongodb-aggregation/lesson-3-using-sort-and-limit-stages-in-a-mongodb-aggregation-pipeline/learn?page=2

[^11]: https://www.appsyoda.com/blog/group-mongodb-aggregation-examples/

[^12]: https://stackoverflow.com/questions/70495023/mongodb-aggregation-sum-values-and-group-by-property

[^13]: https://www.mongodb.com/docs/manual/reference/operator/aggregation/avg/

[^14]: https://studio3t.com/knowledge-base/articles/mongodb-aggregation-framework/

