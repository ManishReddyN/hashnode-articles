---
title: "Building Code Runner - Part #2 : Node.js Backend With Express Server and JDoodle API"
seoTitle: "Building an Express Server and using JDoodle API"
seoDescription: "In this part, we will learn about the JDoodle API and create an express server application, and get it running."
datePublished: Sun Jun 13 2021 18:05:51 GMT+0000 (Coordinated Universal Time)
cuid: ckpvi0kor0a4qzls12gwhg9ya
slug: code-runner-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1623595315265/YoyjKz1QT.png
tags: tutorial, express, nodejs, apis, mern

---

## Hello everyone 👋🏽

### Here is the third article in our series,  [CodeRunner](https://blog.nmreddy.me/series/code-runner). I  am pretty much excited to get us started. Let's dive in 🤩

### This article will speak about 2 things:
1. ### JDoodle API
2. ### Using Express and Node.js

---

# Introduction to the  [JDoodle API](https://www.jdoodle.com/compiler-api/) 
JDoodle is an online compiler and editor just like our CodeRunner, built and maintained by  [@thenutpan](https://twitter.com/thenutpan). They also provide an API as a service to run scripts, by spending credits.

The pricing is pretty much reasonable and the free plan should help you get started for a personal project like this. You will be provided with 200 credits per day, which means 200 API calls per day.
On signing up for the API, you will be provided with a client key and client secret which will be used for authenticating the API calls, so keep them handy.

The entire documentation for the API can be found  [here](https://docs.jdoodle.com/compiler-api/compiler-api). We will be using the  [execute API](https://docs.jdoodle.com/compiler-api/compiler-api#what-are-the-output-parameters-for-execute-api-call-when-the-execution-failed)  for now.

---

# Using Express and Node.js

Our application will be built on Node.js with express as our server. Do follow the steps in the previous part of the series before proceeding further.

1. Create the required files and folders in your server directory to match the below directory structure. 
 - The `index.js` will be the entry point to our server.
 - The `controllers` folder will contain all the functions that shall be executed on the server.
 - The `models` folder consists of the Mongoose models (will be discussed in the next part).
 - The `routes` folder consists of the server routes which will point to a function based on the path.
``` bash
└── server
    ├── controllers
    │   └── methods.js
    ├── index.js
    ├── models
    │   └── codes.js
    ├── node_modules 
    ├── package.json
    └── routes
        └── paths.js
``` 
2.  [Express](https://expressjs.com/en/starter/hello-world.html) is a framework which enables web server capabilities to the Node.js. To get started, we will import the `express` library in our `index.js` file and create an express app as follows.
```js
const express = require("express");
const app = express();
```
3. To test our app, let's have a dummy route at `/` which returns a simple message.
```js
app.get("/", (req, res) => {
  return res.status(200).json({ message: "Up & Running " });
});
```
Whenever a user reaches the `/` route of the app, they will be served with the message as response, showing that the server is active.
4. The app should be running and for that we need to provide a port, as follows.
```js
const port = process.env.PORT || 8000;
app.listen(port, () => {
  console.log(`App is running on PORT : ${port}`);
});
```
Here, process.env.PORT refers to the PORT environment variable which will be setup by the hosting providers. In the case of it's absence, the application will run on port **8000**. <br/><br/>
To enable the usage of environment variables, we will need to use the `dotenv` library as follows and it should be `line #1` of the program.
``` js
require("dotenv").config();
``` 
5. To enable JSON capabilities to our application, we will need the `body-parser` library, so import it and use it in the app as follows.
```js
const bodyParser = require("body-parser");
app.use(bodyParser.json());
```
This sets up the entry point for the application.

6. Moving on to routes, the `paths.js` file shall contain the routes of the application and map it them to the controllers. It is easy to debug large application, by having the routes on a different folder.
<br/>
The Express library provides the Router instance, that can be used to define the router paths.
To begin, import express and the express Router as follows.
```js
const express = require("express");
const router = express.Router();
```
7. Now, define the routes for the application based on the mind map and map them to the controller to execute and export them once ready. We need to import the controllers first and the code is as follows:
```js
const controller = require("../controllers/methods");
router.get("/getCode", controller.getCode);
router.post("/runCode", controller.runCode);
router.post("/saveCode", controller.saveCode);
module.exports = router;
```
With this, we have our routes ready.

---
## Code can be found here
%[https://github.com/nmreddy1911/CodeRunner-Tutorial]


### The controller and its methods along with the MongoDB functionality shall be discussed in the next part of the series.

## Do subscribe to the newsletter to not miss a new article. 📫

### Stay safe everyone ❤
### Until next time, <br/> Manish













