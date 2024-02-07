---
title: "Building Code Runner - Part #1 : Creating An Overview And  MERN Project Setup With PNPM and Vite"
seoTitle: "Creating An Overview And Project Setup Using PNPM and Vite"
seoDescription: "In this part, we will learn about creating mind maps and setting up our project with required dependencies."
datePublished: Sun Jun 06 2021 18:20:46 GMT+0000 (Coordinated Universal Time)
cuid: ckpligsoj0n0xw9s1gwj75fdg
slug: code-runner-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1622971892231/FxWp-7M6A.png
tags: tutorial, nodejs, projects, reactjs, mern

---

## Hello people 👋🏽
### Hoping you all are safe. Firstly, sorry for not being able to bring up this article last week. It was a packed one with exams and other work.
### I think this article will make up for the delay 🤞🏽


### This article will be focusing on two aspects:
- **Understanding the project and building a mind map for all future reference.**
- **Setting up the project folders and installing the required dependencies.**
---
### Building the Mind Map

The most critical part of building any application, for that matter solving any problem is analysing the functionalities and requirements of that problem.

A mind map is one of the many ways to put those points in a visual way. For smaller applications like these, the mind maps should be sufficient, but bigger applications need proper documentation.

The use cases and requirements of our Code Runner can be defined as follows:
1. User should be able to type code in an editor with syntax highlighting, language specific suggestions and other features.
2. User should be able to provide custom input.
3. User should be able to run this program with or without the custom input.
4. User should be able to save these codes, upon request.
5. User should be able to retrieve codes or share them using a simple URL (UID in the slug).


I use a tool called  [Miro](https://miro.com/) to build these mind maps and store them for further reference. Below is a mind map for our project. It should explain for itself, and it is just an overview of the application. The implementation of it shall be looked into in detail during the development process.

We clearly define the required needs of our application on both the front-end and the back-end.

![Code Runner Map.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1622999557831/3fAXYEiwL.jpeg)

---

### Project Setup

We will setup our project in an unconventional yet fast way which helps keep the development overhead processes like installations and builds less time consuming.

The default package manager we will be using is  [PNPM](https://pnpm.io/). It is a cache-enabled package manager which allows using shared node modules using hard links. It helps to reduce the space occupied on the disk and skips redownloading the modules each time you build a new project.

**To install PNPM: **
```bash
npm i -g pnpm
``` 

### Server Folder Structure

Now that you have PNPM installed and ready, we can start creating the project folders and install dependencies.
Create a folder called `CodeRunner` with a subfolder called `server`. (Naming can be done according to your preference) and open the main folder in an IDE or terminal.
- Move into the server directory: 
``` bash
cd server
```
- Initialize it as a node directory (I am using the default options here):
```bash
pnpm init -y
```
- We will need express, mongoose, axios and other libraries to perform the operations. The use of each of the library will be discussed in the coming article.
```bash
pnpm install axios body-parser dotenv express mongoose nanoid nodemon
```
- Create a file called `index.js` which will serve as the entry point of our application.
- Add the start script to the `package.json` as follows:
```js
"scripts" : {
        "start" : "nodemon index.js"
}
```
**nodemon** will watch for file changes and restart the server if any changes are found.
- Add the following code to your index.js file:

``` js
require("dotenv").config();
const express = require("express");
const bodyParser = require("body-parser");
const cors = require("cors");
const app = express();
const mongoose = require("mongoose");

const mongoSRV = process.env.MONGO_SRV;
const port = process.env.PORT || 8000;

// Establising connection with MongoDB
mongoose.connect(mongoSRV, {
    "useNewUrlParser": true,
    "useUnifiedTopology": true,
    "useCreateIndex": true
})
.then(() => console.log("DB Connected"))
.catch((err) => console.log("Error connecting DB", err))

//To enable cross-origin-resources in our application
const corsOptions = {
    origin: "*",
    optionsSuccessStatus: 200
}
app.use(cors(corsOptions));

//To parse JSON body
app.use(bodyParser.json());

//Serving the application on Port
app.listen(port, () => {
    console.log(`App is running on PORT: ${port}`);
})
```
- Create a MongoDB  [Atlas](http://atlas.mongodb.com/)  instance and save the SRV value in a file called `.env` in the server folder with key as `MONGO_SRV`.
- Create sub-folders called `routes`, `controllers` and `models` in the `server` folder.

### Client Folder Structure
-  [Create react app](https://create-react-app.dev/)  is the default way used to generate react applications but it is time consuming and uses NPM under the hood instead of PNPM.
- We shall use  [Vite](https://vitejs.dev/)  to generate our react application and PNPM to install the dependencies.
- To generate the client application open the CodeRunner(project root) folder and run the following command:
```bash
npm init @vitejs/app client --template react
```
This will generate a folder called `client` inside the CodeRunner folder with the required files.
You can refer to the documentation of Vite if you encounter any errors with respect to the versions of PNPM.
- Now move inside the client folder: `cd client` and install the dependencies using:
```bash
pnpm install
```
- We will be using  [Chakra-UI](https://chakra-ui.com/)  and  [react-ace](https://www.npmjs.com/package/react-ace)  in the client application, so install them as well.
``` bash
pnpm install @chakra-ui/react @emotion/react@^11 @emotion/styled@^11 framer-motion@^4 @chakra-ui/icons react-ace ace-builds
```
- To check if the setup is ready, run:
```bash
pnpm dev
```
It should generate the dev-build of the client folder and open it in browser.


Your final Project folder should look like this with the `node_modules` folder  `.env` file included.

%[https://github.com/nmreddy1911/CodeRunner-Tutorial]

---
### That's all for today folks. 
Let's discuss the implementation of the server application in the next article.
<br/>
**Subscribe to the newsletter for the upcoming articles. 📫**
<br/>
Stay safe everyone ❤

Until next Sunday, <br/>
Manish Reddy Nandineni.