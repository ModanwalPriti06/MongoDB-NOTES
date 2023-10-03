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

## Get, Post, Put and Delete
1. *GET* : This method is used to request data from a web server. When you type a URL into your web browser and press Enter, your browser sends a GET request to the server, asking for a specific web page. It's like asking for information or reading data. GET requests should not change the server's state and are generally considered safe and idempotent, meaning multiple identical requests should have the same effect as a single request.
