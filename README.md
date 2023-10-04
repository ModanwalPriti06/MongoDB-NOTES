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

