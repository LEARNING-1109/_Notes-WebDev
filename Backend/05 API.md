
# Installation
```js
npm i express mongoose dotenv cookie-parser
```

## nothing 

```js
import express, { json } from 'express';
const app = express();

// (3.) databse connection and ...
import mongoose from 'mongoose';    // 3
mongoose.connect("mongodb://127.0.0.1:27017", {
    dbName: "backend-api"
}).then(() => {
    console.log("Database Connected");
}).catch((e) => console.log(e))

const schema = new mongoose.Schema({
    name: String,
    email: String,
    password: String
})
const User = mongoose.model("User", schema)    // creating model

// (4.)  Using Middleware
app.use(express.json());

// creating server  (keep this below lines at the end of the code)
app.listen(4000, () => {
    console.log("Server is running at port 4000");
})

// ---------------------------

app.get('/', (req, res) => {
    res.send('Hello World'); // 👈🏻 this is the response to client request
})
```

# 2. 

```js
app.get('/users/all', async (req, res) => {
    const users = await User.find({});   // using our db created model "User"

    const keyword = req.query.college;
    
    console.log(keyword);    

    res.json({    
        success: true,
        users,
    })
})
```

# 3. 

```js
app.get("/userid/special", async (req, res) => {
    res.json({
        success: true,
        message: "Just Joking"
    })
} )

app.get("/userid/:myID", async(req, res) => {
    // const { myID } = req.body;    // postman > GET Req. > Body> raw (json file mode) >
    // const { myID } = req.query; // Params -> Query Params
    
    const { myID } = req.params; // Params -> Query Params

    const user = await User.findById(myID);   

    res.json({
        success: true,
        user
    })
} )
```

# 4. 

```js
app.post('/users/new', async(req, res) => {

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
})
```