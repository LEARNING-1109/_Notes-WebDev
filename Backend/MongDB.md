
# 1. Installation

[🔗 Download MongoDB Link](https://www.mongodb.com/try/download/community)

## 1. Installing mongoose
```js
npm i mongoose
```

```
import mongoose from 'mongoose';
```

## 2. Connect to Databse
```js
    // ❌ mongoose.connect("mongodb://localhost:27017", {
    mongoose.connect("mongodb://localhost:27017", {
    dbName: "backend",
})
```
- How find the correct connection URI link
- Open your project folder directory.
- type `cmd` in directory path
- then in cmd type `mongo`
- it will show up the link through which you can connect to your mongoDB database.

# 3. Add data to backend
```js
const msgSchema = new mongoose.Schema({
    name: String,
    email: String,
})
const msg = mongoose.model("Message", msgSchema);
```

## Add data using GET method

```js
app.get('/add', (req, res) => {
    msg.create({
        name: "Ayu",
        email: "ayu@gmail.com"
    }).then(() => {
        res.send("<h1>Data Sent to Backend successfully.</h1>");
    })
})
```
or
```js
// using async await function
app.get('/add', async (req, res) => {
    await msg.create({
        name: "Ayu",
        email: "ayu@gmail.com"
    }).then(() => {
        res.send("<h1>Data Sent to Backend successfully.</h1>");
    })
})
```

## Add data using post method

```js
app.post('/contact', (req, res) => {
    // msg.create({ name: 'youtube', email: 'subscribe@gmail.com' })    // 1
    // msg.create({ name: req.body.name, email: req.body.email })       // 2

    // destructuring data from req.body object
    const { name, email } = req.body;
    // msg.create({ name: name, email: email });
    msg.create({ name, email });    // if key value pairs have same name then write only once

    console.log('Message saved to DB successfully');
    res.redirect('/success')
})
```

