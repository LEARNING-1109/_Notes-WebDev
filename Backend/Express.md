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

### importing body-parser
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

