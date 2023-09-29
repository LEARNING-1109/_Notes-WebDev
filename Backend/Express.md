# 1. Installation 

```js
npm i express
```

```js
import express from 'express';

const app = express();

// try to keep app.listen in the end of code
app.listen('4000', () => {
    console.log("Server is listening !");
} )
```

## GET method route
```js
app.get("/about", (req, res) => {
    res.send("<h1>About</h1>")
})
```
--- 

### importing path
`const path = require('path')`
```js


app.get("/", (req, res) => {
    // res.send("<h1>Hello World- (EXPRESS)</h1>")
    // res.sendFile('./index.html');   ❌
    res.sendFile(path.join(__dirname + '/index.html'))
})
```



## 2. POST method 

### importing body-parser i.e, req.body
`const bodyParser = require('body-parser');`

`app.use(bodyParser.urlencoded({extended: false}));`

```js
// app.post('/', (req, res) => {
app.post('/api/v1/login', (req, res) => {
    
    res.send(
        `<h1>Succes <br>Mr. ${req.body.name} <br>Email: ${req.body.email} <br>Password: ${req.body.password}`
    )
    
    console.log('POST method is executed!');
})
```

## Post request from thunder client

`app.use(express.json());`    // 🎯 post request from thunder client

```js
app.post('/api/v1/register', (req, res) => {
    const userName = req.body.name;
    const userEmail = req.body.email;
    const userPassword = req.body.password;
    
    res.json({
        success: true,
        name: userName,
        email: userEmail,
        password: userPassword
    })
    console.log("Register API working !")
})
```

# 3. Response in Express to DOM

```js
res.end('Hello World');

res.send("<h1>Data Sent to Backend successfully.</h1>");
res.sendFile(path.join(__dirname + '/contact-us.html'))

res.statusCode = 200;
res.status(400).send("message- HTML Message wit Status code in console");  
res.setHeader('Content-Type', 'text/plain');

res.render("success!")

res.redirect("/about");

res.json({
    success: true,
    name: userName,
    email: userEmail,
    password: userPassword
})
```

# 4. <%= EJS %> Embedded JavaScript templating.

## Installation

```js
npm i ejs
```

### Create Folder Structure like -

ProjectName/views/index.ejs

- i.e, Must create a `views` named folder.

public/style.css, script.js
- these public files will be directly served to the index.ejs as it don't need to mention absolute path.

```js
// 🎯 Setting Up View Engine -------------
app.set("view engine", "ejs");  // ✨ agar ye enable kr diye to .ejs niche kahi nhi use karna hoga
app.get('/ejs', (req, res) => {
    // res.render('index.ejs');
    // res.render('index');

    // 🎯 passing dynamic variable
    res.render('index', {name: "Er. Ayush"} )
} )
```
---
```js
// (Optional) Serving public folder to server
app.get('/public', (req, res) => {
    const pathLocation = path.resolve();
    console.log(pathLocation);
    res.sendFile(path.join(pathLocation, '/public/public.html'));    
})
```