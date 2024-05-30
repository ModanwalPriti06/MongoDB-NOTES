:smile: 
:rocket:
:cry:
✍️
```
Emphasis and Lists:
Use *italic* or **bold** to add emphasis.
Create bulleted or numbered lists.

Headers:
Use #, ##, ###, etc., for different levels of headings.

Links:
Create hyperlinks using [link text](URL).

Images:
Embed images with ![alt text](image URL).

Code Blocks:
Present code using triple backticks (`) to create code blocks. You can specify the programming language for syntax highlighting after the first triple backtick, like ```python.

Tables:
Design tables using the | symbol to separate columns.

Horizontal Lines:
Add horizontal lines with three hyphens (---) or asterisks (***).

Blockquotes:
Use > to create blockquotes for important information or quotes.

Inline Code:
Highlight inline code with backticks, like inline code.

Footnotes:
Include footnotes using [^1] and define them at the bottom of your document.

Math Formulas:
If your project involves mathematical expressions, you can use LaTeX-style math notation enclosed in $$ for block-level math, or $ for inline math.

Checkboxes:
Create checkboxes by using - [ ] for an unchecked box and - [x] for a checked box.

Task Lists:
Use - [ ] to create task lists, which can be used for tracking to-dos or milestones.

GitHub Flavored Markdown (GFM):
GitHub supports some additional features such as @mentions, issue and pull request linking, and automatic linking of URLs.

Emoji:
You can use emoji in your README to add some personality and context. For example, :smile: or :rocket:.

```

# MERN-NOTES
##Install Mongodb and compass

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
![Alt Text](https://dotnettrickscloud.blob.core.windows.net/img/react/meanst-crud2.png)

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

### Frontend CRUD OPeration TODO:
- Add:
- Read:
- Update:
- Delete: 


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

#CRUD
## Create
```
db.mydb.insert({name: 'priti'})
db.mydb.insertOne({name: 'priti'});
db.mydb.insertMany([{name: 'priti', age: 20}, {name: 'Kriti', id: 02, age: 18, address: 'varanshi' }]);

OR

db.mydb.save({name: 'priti'});
db.mydb.save([{name: 'priti', age: 20}, {name: 'Kriti', id: 02, age: 18, address: 'varanshi' }]);
```
## Read
```
db.mydb.find()
db.mydb.find({})
db.people.find().pretty()
db.mydb.findOne({name:'priti'})
db.people.find({name: 'Tom'}, {_id: 0, age: 1})
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
db.people.deleteMany({name: 'Tom'})

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
### (Use the positional operator $)

Ques: {name: 'Tom', age: 28, marks: [50, 60, 70]} Update Tom's marks to 55 where marks are 50 (Use the positional operator $)           

Ans: db.people.update({name: "Tom", marks: 50}, {"$set": {"marks.$": 55}})

## limit, skip, sort and count the results of the find() method
- db.test.find({}).skip(3)
- db.test.find({}).sort({ "name" : -1}) //descending order sort
- db.test.find({}).count()
- db.test.find({}).sort({ "name" : -1}).skip(1).limit(2)

## Query Document - Using AND, OR and IN Conditions
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

# Aggregration
Aggregations operations process data records and return computed results. Aggregation operations group values from multiple documents together, and can perform a variety of operations on the grouped data to return a single result. MongoDB provides three ways to perform aggregation: the aggregation pipeline, the map-reduce function, and single purpose aggregation methods.
Aggregation is used to perform complex data search operations in the mongo query which can't be done in normal "find" query.

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






