<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [Route Splitting MVC](#route-splitting-mvc)
   * [What is the MVC?](#what-is-the-mvc)
- [0. Folder Structure](#0-folder-structure)
   * [Require module Installation](#require-module-installation)
- [1. 📜 app.js ⭐⭐](#1--appjs-)
- [2. 📜 server.js ⭐⭐](#2--serverjs-)
- [3. 📂 models > 📜 user.js ⭐⭐](#3--models---userjs-)
- [4. 📂 data > 📜 database.js ⭐⭐](#4--data---databasejs-)
- [5. config.env ⭐⭐](#5-configenv-)
- [6. 📂routes > 📜 user.js   - For Routing](#6-routes---userjs-----for-routing)
- [7. 📂 controllers > 📜 user.js](#7--controllers---userjs)

<!-- TOC end -->

# Route Splitting MVC

`Routing refers to how an application’s endpoints (URIs) respond to client requests.`


## What is the MVC?
MVC stands for `Model, View, Controller` is an architectural pattern that separates an application into three main logical components: the model, the view, and the controller. 

Each one of these components is built to handle specific development aspects of an application.

![MVC](https://miro.medium.com/v2/resize:fit:720/format:webp/0*TgEUas3y7zXZHgeR.png)

# 0. Folder Structure

`app.js` ⭐⭐

`server.js` ⭐⭐

📂 controller
- user.js

📂 data
- config.env ⭐⭐
- databse.js ⭐⭐

📂 models
- user-models.js

📂 routes
- user.js

`package.json`
- 
```js{
        "name": "05-route-splittingmvc",

        "main": "server.js",
        "type": "module",
        "scripts": {
            "test": "echo \"Error: no test specified\" && exit 1",
            "start": "node server.js",
            "dev": "nodemon server.js"
        },
        "dependencies": {
            "dotenv": "^16.3.1",
            "express": "^4.18.2",
            "mongoose": "^7.5.3"
        }
        }
```

## Require module Installation

```css
npm i express express mongoose dotenv
```

# 1. 📜 app.js ⭐⭐


```js
import express from 'express';
import userRouter from './routes/user.js'
import { config } from 'dotenv';

export const app = express();

config({
    path: "./data/config.env"
})

// Using Middleware 
app.use(express.json()); // receiving json response from POSTMAN

// app.use(userRouter);
app.use("/users", userRouter);    // adding prefix url prameter

// Home Page -----------
app.get('/', (req, res) => {
    res.send("Nice Working");
})
```

# 2. 📜 server.js ⭐⭐

```js
import {app} from './app.js';
import { dbConnect } from './data/database.js'

// Connection to database
dbConnect();


// console.log(process.env.PORT)
// Listening to server
app.listen(process.env.PORT, () => {
    console.log('Server is running on port', process.env.PORT);
})
```

# 3. 📂 models > 📜 user.js ⭐⭐
Database structure

```js
import mongoose from "mongoose";

const userSchema = new mongoose.Schema({
    name: String,
    email: String,
});

export const User = mongoose.model("User", userSchema);
```

# 4. 📂 data > 📜 database.js ⭐⭐
```js 
// npm i dotenv
import mongoose from 'mongoose';

// console.log(process.env.MONGO_URI)
// Connection to database
export const dbConnect = () => mongoose.connect(process.env.MONGO_URI, {
    dbName: "my_backend",
}).then(() => {
    console.log("Database Connected");
}).catch((e) => console.log(e))
```

# 5. config.env ⭐⭐
This file must note be uploaded on the Github. (Confidential)

```js
PORT = 4000

MONGO_URI = mongodb://127.0.0.1:27017
```

# 6. 📂routes > 📜 user.js   - For Routing

```js
import express from 'express';
import { deleteUser, getAllUsers, getUserDetails, newRegistration, specialFunc, updateUser } from '../controllers/user.js';

const router = express.Router();

// ----------------
router.get('/all', getAllUsers)

router.get("/userid/special", specialFunc)

router.post('/new', newRegistration)

// ✨ for common routes use this option ------------------------- ✨
router
    .route("/userid/:myID")
    .get(getUserDetails)
    .put(updateUser)
    .delete(deleteUser)
// or
// router.get("/userid/:myID", getUserDetails)
// router.put("/userid/:myID", updateUser)
// router.delete("/userid/:myID", deleteUser)
// ✨ ------------------------------------ ✨

export default router;
```

# 7. 📂 controllers > 📜 user.js

```js
import { User } from "../models/user-model.js";

export const getAllUsers = async(req, res) => {
    const users = await User.find({});   // using our db created model "User"

    const keyword = req.query.college;

    console.log(keyword);

    res.json({
        success: true,
        users,
    })
}

export const specialFunc = async (req, res) => {
    res.json({
        success: true,
        message: "Just Joking"
    })
}


export const newRegistration = async (req, res) => {
    
    const { name, email, password } = req.body;

    // 🎯 creating custom user manually
    // const users = User.create({
        //     name: "Ayush Kumar", 
    //     email: "ayush@gmail.com",
    //     password: "123@45",
    // })

    
    // 🎯 creating dynamic new user from dom
    const users = await User.create({
        name,
        email,
        password,
    })

    // res.json({
        res.status(201).cookie("temp-cookie", "445@22DDFT78").json({  // 201 is code for created
            success: "true",
            message: "New User Registered Successfully.",
        })
    }

export const getUserDetails = async (req, res) => {
    // const { myID } = req.body;    // postman > GET Req. > Body> raw (json file mode) >
    // const { myID } = req.query; // Params -> Query Params

    const { myID } = req.params; // Params -> Query Params

    const user = await User.findById(myID);

    res.json({
        success: true,
        user
    })
}

export const updateUser = async (req, res) => {
    const { myID } = req.params; // Params -> Query Params
    const user = await User.findById(myID);

    res.json({
        success: true,
        message: "Updated",
    })
}
export const deleteUser = async (req, res) => {
    const { myID } = req.params; // Params -> Query Params
    const user = await User.findById(myID);

    res.json({
        success: true,
        message: "Deleted",
    })
}
```