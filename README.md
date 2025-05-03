# MERN-NOTES
# MongoDB Topic
1. MongoDB’s design philosophy and architecture
2. MongoDB Model
3. API Method
4. CRUD operations
5. Data modeling
6. Indexing and performance
7. Aggregation
8. Replication
9. Sharding

```
Ctrl + l = Clear terminal
```

---
# MongoDB 

- MongoDB is NoSQL, schemaless database that have collection and inside document which store JSON format. less relation and data is store together.
- MongoDB Shell: A command-line interface to interact with MongoDB databases. Running queries (find(), insertOne(), etc.)
- MongoDB Compass: A GUI (Graphical User Interface) tool provided by MongoDB.
- MongoDB Atlas UI (Cloud): Hosting and managing cloud databases. Monitoring, backups, performance tracking.
- MongoDB Drivers (for Node.js, Python, Java, etc.):  Libraries that allow applications to interact with MongoDB. Used in: Backend apps using languages like: Node, JAVA , etc.

## BSON? 
- Binary structure encoded type and length information, which allow it to be traversed much more quickly compared to JSON.

## Feature of MongoDB
<img  width="1000" height="600"  alt="Screenshot 2025-04-13 at 4 49 21 PM" src="https://github.com/user-attachments/assets/6967672d-bd0c-4181-8eb0-b476b7683b47" />

## Difference between mongoDB and SQL
| **Feature** | **MongoDB (NoSQL)** | **SQL (MySQL, PostgreSQL,** | 
| ------------ | ---------------| ------------ |
| Data Structure| 	Document-based (JSON-like BSON)| 	Table-based (rows & columns)| 
| Schema| Schema-less (flexible)| 	Fixed schema (defined in advance)| 
| Query Language	| MongoDB Query Language (MQL)| 	Structured Query Language (SQL)| 
| Joins| 	Limited support via $lookup | Strong support for joins (foreign keys)| 
| Scalability| 	Horizontally scalable (easy sharding)| 	Vertically scalable (harder to scale out)| 
| Transactions| 	Supported (since v4.0), but less robust than SQL| 	Strong, ACID-compliant transactions| 
| Use Case| 	Best for unstructured or semi-structured data	| Best for structured data with relationships| 
| Speed	| Faster for large unstructured data sets | 	Slower when handling large, unrelated datasets| 
| Examples	| MongoDB, CouchDB |	MySQL, PostgreSQL, OracleDB| 

## MongoDb CLI (Command line interface)
<img width="843" alt="Run Manually mongodb" src="https://github.com/user-attachments/assets/e60eea80-d009-4b81-a7db-08e6a6b3417f" />
<img width="566" alt="Screenshot 2025-05-03 at 4 12 16 PM" src="https://github.com/user-attachments/assets/44c078c2-d415-4455-9d28-4196562d65e4" />

Schema Validation through CLI
<img width="930" alt="Screenshot 2025-05-03 at 5 17 16 PM" src="https://github.com/user-attachments/assets/292d1deb-d763-44b7-8de9-d828650bf813" />

Modify Schema Validation
<img width="618" alt="Screenshot 2025-05-03 at 5 20 41 PM" src="https://github.com/user-attachments/assets/6ef69d6e-5e58-42d8-8093-7d9df882605c" />

```
Create DB- use db_name 
Create collection: db.createCollection('students')
Show all collections: show collections
Drop db: db.dropDatabase
drop Collection: db.collection_name.drop()

```

## Embedded Documents
- Inside one document we can create another document but limitation is 16mb only
```
{
  name: 'Ram',
  nickName: { isthere : true , address: {'Varanshi', 'banglore'} }
}
```
```
 db.students.find({'nickName.isthere' : true})
```
## Some Alternative NOSQL databases to MongoDB?
- Apache Hbase
- Cassandra
- Redis
- neo4j
- Amazon DynamoDB

<img width="800" height="600" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/1aa132db-2db2-42ef-8d0e-0aa1c43ed41e" />

<img width="800" height="600" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/708ae847-d8e5-4130-b52e-e57f2a86b9df" />

## How does mongoDB stored data?
- MongoDB stores data records as documents (Specially in BSON document) which is gathered together in collections.
- MongoDB Data Storage Structure
1. **Database**
- MongoDB has multiple databases (like in SQL). Each database contains:
2. **Collections**
- Collections are like tables in SQL, but more flexible. Each collection contains:
3. **Documents**
- Documents are the basic units of data in MongoDB. They are stored in a format called BSON (Binary JSON). Each document is like a JSON object.

## MongoDB is a Schema-less database. If Yes how do you create Schema in MongoDB?
- The schema of a database describes the structure of the data to be stored.
   <img width="800" height="400" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/f2599091-601d-4fc0-bc5c-d12d543a0d75" />

## Data Model
   <img width="800" height="400" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/e330745a-9bfc-4033-a11a-e6b5f9630488" />

## Indexing
- An index in MongoDB is similar to an index in a book — it helps MongoDB locate and access data faster without scanning every document in a collection.
- By default, MongoDB creates an index on the _id field in every collection. You can also create custom indexes on any other field(s).
<img width="924" height="500" alt="indexing" src="https://github.com/user-attachments/assets/87ce6c0f-a345-408e-b1a6-8bcdd78cf7ed" />

### How Indexing Works:
1. Without an index:
- MongoDB performs a collection scan — it goes through every document to find matches.
- This is slow for large datasets.
2. With an index:
- MongoDB uses a B-tree data structure to jump directly to relevant documents.
- This makes queries much faster.

## Start Mongodb And connection frontend to backend

1. npm i / npm init -y
2. npm i express mongoose cors nodemon
3. goto package.json and add "start": "nodemon index.js" in script
4. start sever using npm start
5. make one file index.js and import express, mongoose and cors
```
  const express =require('express');
  const mongoose = require('mongoose');
  const cors = require('cors');
  
  const app= express();
  
  app.use(cors());

  mongoose.connect('mongodb://localhost:27017');
  
  app.use(express.json());
  
  app.listen(1080,()=>{
      console.log('listening on 1080');
  })
```


```
brew services start mongodb-community

````
# Setup and Installation
## Front-end dependencies
- npm install
- react-router-dom
- npm install react-bootstrap
- npm install axios
  
# Setup of Backend
## Back-end dependencies
- npm install mongoose express body-parser cors

## Backend File Structure
![mongodb structure](https://dotnettrickscloud.blob.core.windows.net/img/react/meanst-crud2.png)

## Setting up a server environment
---
We are going to create the server application with the help of nodejs and express framework and will set up basic configuration such as database connection with Mongo server, route configuration, express configuration and other required setup.

```
 // Imported required packages
 const express = require('express'),
 path = require('path'),
 bodyParser = require('body-parser'),
 cors = require('cors'),
 mongoose = require('mongoose');
 
 // MongoDB Databse url
 var mongoDatabase = 'mongodb://localhost:27017/employeeDetails';
 
 // Created express server
 const app = express();
 mongoose.Promise = global.Promise;
 
 // Connect Mongodb Database
 mongoose.connect(mongoDatabase, { useNewUrlParser: true }).then(
 () => { console.log('Database is connected') },
 err => { console.log('There is problem while connecting database ' + err) }
 );
 
 // All the express routes
 const employeeRoutes = require('../Routes/Employee.route');
 
 // Conver incoming data to JSON format
 app.use(bodyParser.json());
 
 // Enabled CORS
 app.use(cors());
 
 // Setup for the server port number
 const port = process.env.PORT || 4000;
 
 // Routes Configuration
 app.use('/employees', employeeRoutes);
 
 // Staring our express server
 const server = app.listen(port, function () {
 console.log('Server Lisening On Port : ' + port);
 });
```
   
## MongoDB Model
```
const mongoose = require('mongoose');
 const Schema = mongoose.Schema;
 
 // List of columns for Employee schema
 let Employee = new Schema({
 firstName: {
 type: String
 },
 lastName: {
 type: String
 },
 email: {
 type: String
 },
 phone: {
 type: Number
 }
 },{
 collection: 'employees'
 });
 
 module.exports = mongoose.model('Employee', Employee);
```

## API METHODS: Get, Post, Put and Delete
1. *GET* : This method is used to request data from a web server. When you type a URL into your web browser and press Enter, your browser sends a GET request to the server, asking for a specific web page. It's like asking for information or reading data. GET requests should not change the server's state.

2. *POST*: POST is used to submit data to be processed by a specific resource on the server. It's often used when you want to send data to the server to create a new resource. For example, when you submit a form on a website, the data you enter is typically sent to the server using a POST request. POST requests can change the server's state and are not idempotent, meaning multiple identical requests may have different effects.

3. *PUT*: PUT is used to update or replace an existing resource on the server with the data provided. PUT requests are typically idempotent, meaning making the same request multiple times should have the same effect as making it once.

4. *DELETE*: DELETE is used to request the removal of a specific resource on the server. It's like asking the server to get rid of something. DELETE requests are also typically idempotent, meaning multiple identical requests should have the same effect as a single request.

## Difference betweeen PUT and POST

```Purpose``` The PUT method is used to request that the server updates a resource or creates it if it doesn't exist at the specified URL.

```Idempotent``` PUT requests are idempotent, which means that making the same request multiple times should have the same effect as making it once.

```Usage``` Typically, PUT is used when you have complete knowledge of the resource's URL, and you want to replace or update the resource entirely with the data provided in the request body.

```Purpose``` The POST method is used to submit data to be processed by a resource

```Idempotent``` It is often used to create a new resource on the server.

```Usage``` POST requests are not idempotent, which means that making the same request multiple times may result in different actions or resource creations.

---
### Pitfall Backend CRUD Operation:
- Create: POST-> UserModal.create(req.body)
- Read: GET->  UserModal.find({})
- Update: PUT-> UserModal.findByIdAndUpdate({{_id:id},{name: req.body.name}}) //here _id it's by default field but name,age etc and other key is that same name which is in model.
- Delete: DELETE -> UserModal.findByIdAndDelete({_id:req.params.id})

### CRUD Operation TODO:
- Create: insertOne, insertMany
- Read: find, findMany
- Update: updateOne, updateMany, replaceOne
- Delete: deleteOne, deletemany

#CRUD
## Create
```
db.mydb.insert({name: 'priti'})  // become old
db.mydb.insertOne({name: 'priti'});
db.mydb.insertMany([{name: 'priti', age: 20}, {name: 'Kriti', id: 02, age: 18, address: 'varanshi' }]);

OR

db.mydb.save({name: 'priti'});
db.mydb.save([{name: 'priti', age: 20}, {name: 'Kriti', id: 02, age: 18, address: 'varanshi' }]);
```
<img width="1305" alt="Screenshot 2025-05-03 at 5 09 41 PM" src="https://github.com/user-attachments/assets/1215a72c-f8dd-4d5a-b6c2-fc599d38c55d" />

## Read
```
db.mydb.find() - Return curser/pointer with the help of this can iterate over the array
db.mydb.find({}) - limit(), count(), toArray()
db.people.find().pretty()
db.mydb.findOne({name:'priti'}) - return object single object
db.people.find({name: 'Tom'}, {_id: 0, age: 1})

** Enginnering_Digest> db.students.find({}).forEach((item)=>{printjson(item)}) 
```
## Update
```
db.people.update({name: 'Tom'}, {age: 29, name: 'Tom'})
db.people.updateOne({name: 'Tom'},{age: 29, name: 'Tom'})
db.people.updateMany({name: 'Tom'},{age: 29, name: 'Tom'})
db.people.update({name: 'Tom'}, {$set: {age: 29}})
db.people.updateOne({name: 'Tom'},{$set:{age: 30}) //Will update only first matching document.
db.people.updateMany({name: 'Tom'},{$set:{age: 30}}) //Will update all matching documents.
db.people.updateMany({name: 'Tom'},{$set:{age: 30, salary:50000}})
```
## Delete
```
// New Version
db.people.deleteOne({name: 'Tom'})
db.people.deleteMany({})

// All versions
db.people.remove({name: 'Tom'})
db.people.remove({name: 'Tom'}, true)
```
MongoDB's remove() method. If you execute this command without any argument or without empty argument it will remove all documents from the collection.
```
db.people.remove();
        or
db.people.remove({});
```
# CRUD OPERATION CODE
### POST-1
```
 const handleSubmit = async (e) => {
    e.preventDefault();

    try {
      const result = await axios.post('/submit', formData);  //formData is object inside all data which is add into backend
      setResponse(result.data);
    } catch (error) {
      console.error(error);
      setResponse('Error');
    }
  };
```
```
app.post('/submit', (req, res) => {
  const { name, age } = req.body;
  console.log(`Received data: Name: ${name}, Age: ${age}`);
  res.send('Data received successfully!');
});
```
### POST-2
```
app.post('/api/tasks', async (req, res) => {
  try {
    const { title, description } = req.body;
    const task = new Task({ title, description });
    await task.save();
    res.json(task);
  } catch (error) {
    console.error(error);
    res.status(500).json({ error: 'Internal Server Error' });
  }
});
```
# Projection in MongoDB
```
db.mydb.find({},{name: 1})
db.mydb.find({},{name: 1, _id: 0})

```

# (Use the positional operator $)
Ques: {name: 'Tom', age: 28, marks: [50, 60, 70]} Update Tom's marks to 55 where marks are 50 (Use the positional operator $)           
Ans: db.people.update({name: "Tom", marks: 50}, {"$set": {"marks.$": 55}})

# limit, skip, sort and count the results of the find() method
- db.test.find({}).skip(3)
- db.test.find({}).sort({ "name" : -1}) //descending order sort
- db.test.find({}).count()
- db.test.find({}).sort({ "name" : -1}).skip(1).limit(2)

# Query Document - Using AND, OR and IN Conditions
- AND Queries
```
db.students.find({
    "firstName": "Prosen",
    "age": {
"$gte": 23 }
});
```
- Or Queries
```
db.students.find({
     "$or": [{
         "firstName": "Prosen"
     }, {
         "age": {
             "$gte": 23
} }]
});
```
- And OR Queries
```
db.students.find({
firstName : "Prosen",
$or : [
{age : 23},
{age : 25} ]
}]
```
- IN Queries 
```db.students.find(lastName:{$in:["Ghosh", "Amin"]})```


# Data Type 
1. Null
2. Boolean
3. Number
4. String
5. Date
6. Regular expression
7. Array
8. Embedded document
9. Object ID
10. Binary Data
11. ISO Date
12. Timestamp
    
<img width="1447" alt="Screenshot 2025-05-03 at 5 01 05 PM" src="https://github.com/user-attachments/assets/38063f58-063b-4060-b2d2-6729d755bf69" />
<img width="1152" alt="Screenshot 2025-05-03 at 5 02 44 PM" src="https://github.com/user-attachments/assets/c75dd39c-6087-4e5d-90b5-1ae6c857d1e1" />


# Aggregration
- Aggregations operations process data records and return computed results. Aggregation operations group values from multiple documents together, and can perform a variety of operations on the grouped data to return a single result. MongoDB provides three ways to perform aggregation: the aggregation pipeline, the map-reduce function, and single purpose aggregation methods.
- Aggregation is used to perform complex data search operations in the mongo query which can't be done in normal "find" query.
- The MongoDB Aggregation Pipeline serves as a framework for data processing and transformation within MongoDB. It involves a series of sequential stages, facilitating operations like filtering, projection, grouping, and sorting on documents. Each stage in the pipeline processes the data and forwards the results to the subsequent stage, culminating in the generation of the final output.

- count: $count
- sum: $sum
- average: $avg
- group: $group

## Aggregate query examples useful for work and learning:
1. Match: Used to match documents
  ```
  db.employees.aggregate([{$match:{dept:"Admin"}}]);
  ```
   
2. Project: Used to populate specific field's value(s)
   ```
   db.employees.aggregate([{$match:{dept:"Admin"}}, {$project:{"name":1, "dept":1}}]);
   ```
3. Group: $group is used to group documents by specific field, here documents are grouped by "dept" field's value. Another useful feature is that you can group by null, it means all documents will be aggregated into one.
```
db.employees.aggregate([{$group:{"_id":"$dept"}}]);
```
4. Sum: $sum is used to count or sum the values inside a group.
```
db.employees.aggregate([{$group:{"_id":"$dept", "noOfDept":{$sum:1}}}]);
```
5. Average: Calculates average of specific field's value per group.
```
db.employees.aggregate([{$group:{"_id":"$dept", "noOfEmployee":{$sum:1},"avgExp":{$avg:"$totalExp"}}}]);
```
6. Minimum: Finds minimum value of a field in each group.
```
db.employees.aggregate([{$group:{"_id":"$dept", "noOfEmployee":{$sum:1},"minExp":{$min:"$totalExp"}}}]);
```
7. Maximum: Finds maximum value of a field in each group.
```
db.employees.aggregate([{$group:{"_id":"$dept", "noOfEmployee":{$sum:1},"maxExp":{$max:"$totalExp"}}}]);
```
8. Push and addToSet: Push adds a field's value form each document in group to an array used to project data in array format, addToSet is simlar to push but it omits duplicate values.
```
db.employees.aggregate([{$group:{"_id":"dept", "arrPush":{$push:"$age"}, "arrSet":{$addToSet:"$age"}}}])
```
9. Unwind: Used to create multiple in-memory documents for each value in the specified array type field, then we
can do further aggregation based on those values.
```
db.employees.aggregate([{$match:{"name":"Adma"}}, {$unwind:"$languages"}]);
```
10. Sorting
```
db.employees.aggregate([{$match:{dept:"Admin"}}, {$project:{"name":1, "dept":1}}, {$sort: {name:1}}]);
```
11. Skip
```
db.employees.aggregate([{$match:{dept:"Admin"}}, {$project:{"name":1, "dept":1}}, {$sort: {name:-1}}, {$skip:1}]);
```
12. Limit
```
db.employees.aggregate([{$match:{dept:"Admin"}}, {$project:{"name":1, "dept":1}}, {$sort: {name:-1}}, {$limit:1}]);
```
13. Comparison operator in projection
```
db.employees.aggregate([{$match:{dept:"Admin"}}, {$project:{"name":1, "dept":1, age: {$gt: ["$age", 30]}}}]);
```
14. Comparison operator in match
```
db.employees.aggregate([{$match:{dept:"Admin", age: {$gt:30}}}, {$project:{"name":1, "dept":1}}]);
```
## Get sample data

To get random data from certain collection refer to $sample aggregation.
```db.emplyees.aggregate({ $sample: { size:1 } })```
where size stands for number of items to select.

## Left Outer Join with aggregation ( $Lookup)
```
let col_1 = db.collection('col_1'); let col_2 = db.collection('col_2'); col_1 .aggregate([
    { $match: { "_id": 1 } },
    {
        $lookup: {
            from: "col_2",
            localField: "id",
            foreignField: "id",
            as: "new_document"
        }
}
],function (err, result){
    res.send(result);
});
```

## upsert
#### Insert if not found
If you would like to insert the document if it is not found, you can use the upsert option.

```
db.posts.updateOne( 
  { title: "Post Title 5" }, 
  {
    $set: 
      {
        title: "Post Title 5",
        body: "Body of post.",
        category: "Event",
        likes: 5,
        tags: ["news", "events"],
        date: Date()
      }
  }, 
  { upsert: true }
)
```
# pitfall
- whenever send data from frontend to backend then make only object we can send so make obj and push data into object then send and get req.body.XX
- 661 Upload File


# MongoDB Query Operators
## Comparison
The following operators can be used in queries to compare values:

- $eq: Values are equal
- $ne: Values are not equal
- $gt: Value is greater than another value
- $gte: Value is greater than or equal to another value
- $lt: Value is less than another value
- $lte: Value is less than or equal to another value
- $in: Value is matched within an array

## Logical
The following operators can logically compare multiple queries.

- $and: Returns documents where both queries match
- $or: Returns documents where either query matches
- $nor: Returns documents where both queries fail to match
- $not: Returns documents where the query does not match

## Evaluation
The following operators assist in evaluating documents.

- $regex: Allows the use of regular expressions when evaluating field values
- $text: Performs a text search
- $where: Uses a JavaScript expression to match documents

## Element Query Operator
1. $exist: Matches the document that have the specific field.
```
  db.users.find({ email: { $exists: true } })
```
2. $type: Checks if the field is of a specific BSON data type.
```
db.products.find({ price: { $type: "double" } })
or
db.products.find({ price: { $type: 1 } }) // 1 = double
```
---

## Next level Query Operator
1. $expr: Allows to use aggregation expressions inside the find() query, enabling you to compare fields within the same document, or use logical/math expressions in a standard query.
```
//compare two fields
db.orders.find({
  $expr: { $gt: ["$amountPaid", "$totalCost"] }
})

//match both are equal or not
db.transactions.find({
  $expr: { $eq: ["$debit", "$credit"] }
})
```
2. 

## what is MongoDB Replication and sharding
<img width="1069" height="500" alt="Screenshot 2025-04-13 at 3 49 37 PM" src="https://github.com/user-attachments/assets/46352552-d2dd-44a4-9486-a08ae1180fc9" />

<img width="1069" height="500" alt="Screenshot 2025-04-13 at 3 52 06 PM" src="https://github.com/user-attachments/assets/1d444b99-ede4-4cc1-97c8-ad735e27f4e8" />

## Explain Horizontal and Vertical Scalling
<img width="1069" height="500" alt="Screenshot 2025-04-13 at 3 53 43 PM" src="https://github.com/user-attachments/assets/00471fed-cfdd-460a-a348-189e42ec3a4e" />

<img width="800" height="500" alt="Screenshot 2025-04-13 at 4 09 36 PM" src="https://github.com/user-attachments/assets/eb3c8f88-3db0-4525-b762-d9d6b03caf64" />

## What is replica sets? 
- A replica set is a group of MongoDB servers that maintain the same data. It’s MongoDB’s way of providing data replication, fault tolerance, and automatic failover.
- ✅ Think of it like a team of MongoDB servers where one is the leader (Primary) and others are backups (Secondaries).

### Key Components:
1. Primary
- Only node that receives write operations.
- Automatically elected during replica set setup or failover.
2. Secondary(s)
- Read-only by default (can be used for read queries with readPreference).
- Continuously sync data from Primary.
3. Arbiter (optional)
- Doesn’t store data.
- Only helps in election of a new Primary when needed (used to break tie votes).

### Replica sets Diagram
```
               [Secondary]
                   |
                   v
[Client] --> [Primary] --> [Secondary]
                   ^
                   |
               [Arbiter]

```
## What is the use os capped collection
- A capped collection is a fixed-size collection in MongoDB that automatically overwrites the oldest documents when it reaches its size limit.
- You can't delete individual documents — MongoDB handles it automatically, and You cannot update documents if it increases their size.
- Documents are stored and returned in insertion order.
<img width="1097" height="500" alt="Screenshot 2025-04-13 at 4 15 04 PM" src="https://github.com/user-attachments/assets/2b0dd373-1b10-44e5-aad0-4e2cef1713bd" />

### Use Cases
- Application logs
- Chat messages (latest N messages)
- Sensor data (e.g., temperature, motion)
- Notification/event streams

  ** Example**
 ```
  db.createCollection("logs", {
  capped: true,
  size: 10485760,  // 10 MB
  max: 1000        // optional: max number of documents
  })

db.logs.isCapped()

 ```
- Capped collections are perfect when you need fast writes, fixed storage, and don't care about keeping old data forever.

## Handle large file image and all
  <img width="1020" height="500" alt="Screenshot 2025-04-13 at 4 20 40 PM" src="https://github.com/user-attachments/assets/91fcc339-ef86-4377-8ccb-dc24211202f3" />

## Aggregation
<img width="1020" height="500" alt="aggregation" src="https://github.com/user-attachments/assets/9a6f1fe1-369a-433b-8387-a7d621fc7556" />

## What the meant by _id
<img width="1020" height="500" alt="id" src="https://github.com/user-attachments/assets/82abae70-e4ab-4aeb-8a47-3af4f866ad79" />

## What is the some utilities for Backup nd restoring in MongoDB?
<img width="1020" height="500" alt="backup" src="https://github.com/user-attachments/assets/288962e6-8739-48be-83c9-c17a29fff0b0" />

## What is map reduce process in MongoDB?
- Map-reeduce s a data processing paradigms for condensing large volume of data into useful aggregation results.
- Map-Reduce is a programming model for processing and transforming large amounts of data using two functions:
1. Map → processes each document and emits key-value pairs.
2. Reduce → takes the emitted values with the same key and combines them.
- It’s useful for grouping, filtering, summing, or transforming large datasets.

  ## What is role of profiler in mongoDB?
  - DB profiler use to collect information regarding the queries which are executed on an individual database instance.
  - Its allow to us collect performance data about operation curring on a MongoDB instance.
  - The MongoDB Profiler is a built-in tool that logs detailed information about database operations such as:
   - Slow queries
   - Writes
   - Reads
   - Index usage
   - Aggregation performance

## What is regular Expression? ($regex operator)
- A regular expression (RegEx or regex) is a sequence of characters that defines a search pattern. It’s used to match, search, or replace text based on specific patterns.
- Provide pattern and sequence of character for matching text and define search pattern.
- Query db to find smaller subset of data within a collection.

## What is Shard Key
<img  width="1020" height="500"  alt="Screenshot 2025-04-13 at 4 46 13 PM" src="https://github.com/user-attachments/assets/e1e7ead3-8f00-4803-8d2e-0c0a007f5808" />

## $lookup operation is equivalent of JOIN in MongoDB.

## Some Application in mongoDB?
- IOT
- Content Management
- Mobile application
- Real time Analysis
- Catalog Managements



# Transaction in MongoDB
- A Transaction is a set of operation that is executed as a single atomic unit.
- Example - there is three operation and that is transaction when all will be completed means transaction if any one is fail then it is cancel, means not traansaction.
- Example2 - A have 500Rs. and b have 0Rs. Now A want to send 100 rs to B so when transaction is completed means A- 100 and B+ 100. If happen then see updation in both side.
- Transaction provide data consistency by ensuring that either all the operation within the transaction are commited to the database, or none of them are.
- Transaction are designed to provide ACID properties.

## ACID Properties
1. Atomicity - Achieve Document Level (either fail either complete)
2. Consistency
3. Isolation
4. Durability
<img width="860" alt="1" src="https://github.com/user-attachments/assets/0995dde4-a821-4a45-98fc-d74affc9f22e" />
<img width="860" height="580" alt="2" src="https://github.com/user-attachments/assets/f7448613-ebe0-4bed-9524-a53604566144" />




 








