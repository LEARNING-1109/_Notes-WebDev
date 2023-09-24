
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

## 