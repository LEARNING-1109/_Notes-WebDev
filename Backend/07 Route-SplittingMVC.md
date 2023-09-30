# Route Splitting MVC

`Routing refers to how an application’s endpoints (URIs) respond to client requests.`


## What is the MVC?
MVC stands for `Model, View, Controller` is an architectural pattern that separates an application into three main logical components: the model, the view, and the controller. 

Each one of these components is built to handle specific development aspects of an application.

![MVC](https://miro.medium.com/v2/resize:fit:720/format:webp/0*TgEUas3y7zXZHgeR.png)

# 1. app.js

```css
npm i express dotenv
```

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
