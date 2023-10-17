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

1. npm i
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

  mongoose.connect();
  
  app.use(express.json());
  
  app.listen(1080,()=>{
      console.log('listening on 1080');
  })
```


```
brew services start mongodb-community

````

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
#### (Use the positional operator $)

Ques: {name: 'Tom', age: 28, marks: [50, 60, 70]} Update Tom's marks to 55 where marks are 50 (Use the positional operator $)
Ans: db.people.update({name: "Tom", marks: 50}, {"$set": {"marks.$": 55}})



