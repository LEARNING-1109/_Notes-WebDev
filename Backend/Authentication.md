# Authentication in Express using jwt and cookie :

-- 

# 1. Required module Installation

```js
npm i express cookie-parser mongoose body-parser jsonwebtoken
```

## 1.2 setting up  & [using Middle wares](https://expressjs.com/en/guide/writing-middleware.html)

`const app = express();`

### Using Middlewares
```js
app.use(bodyParser.urlencoded({ extended: false }));    // for req.body

app.use(cookieParser()); 
```


## 1.3 Connecting to Database
```js
// connect to db
mongoose.connect("mongodb://127.0.0.1:27017", {
    dbName: "my_backend",
})

const userSchema = new mongoose.Schema({
    name: String,
    email: String,
});

const User = mongoose.model("User", userSchema)
```

## 1.4 ejs 

### 🎯 Setting Up View Engine 
```css
npm i ejs
```
```js
app.set("view engine", "ejs");  // ✨ agar ye enable kr diye to .ejs niche kahi nhi use karna hoga
```

# 2.

## 2.1 lengthy method (❌ don't use this)
```js
app.get('/', (req, res) => {
        // res.render('login');
    
        // console.log(req.cookies);   // npm i cookie-parser
        // console.log(req.cookies.token);   // npm i cookie-parser
    
        // using destructuring for token
        const { token } = req.cookies;
        if (token) {
                res.render('logout');
            }
            else {
                    res.render('login')
                }
            
                // 🎯 passing dynamic variable
                // res.render('index', { name: "Er. Ayush" })
            })
```

## 2.1  Shorthand method- using our custom middleware
```js
// Custom middleware
const isLoggedIn = async(req, res, next) => {
    // using destructuring for token
    const { token } = req.cookies;
    if (token) {
        const decoded = jwt.verify(token, 'hbjbgroehbejodif0ds')
        console.log(decoded);
        console.log(decoded._id);        

        req.user = await User.findById(decoded._id);

        next();
    }
    else {
        res.render('login')
    }
}

app.get("/", isLoggedIn, (req, res) => {
    console.log("Value of req.user is : ", req.user);
    
    // res.render('logout');
    res.render('logout', {name: req.user.name, email: req.user.email});
})
```

# 3. if logged in then- `POST data to the backend`

## 3.1 dummy data
```js
app.post('/login', (req, res) => {
    res.cookie("token", "I_am_in2", {
        httpOnly: true,
        expires: new Date(Date.now() + (60 * 1000))
    });
    
    // res.send('<h1>Logged In Successfully.</h1>');
    res.redirect('/');

    console.log("logged in success.")
})
```

## 3.2 saving real time dom data 
```js
app.post('/login', async (req, res) => {
    console.log(req.body.name);
    console.log(req.body.email);

    const { name, email } = req.body;

    const user = await User.create({
        name, email
    })
    // console.log(`User created successfully! - with user._id: `, user._id);
    
    // 🎯 JWTs are just bits of encoded JSON data with a cryptographic signature at the end.
    // 🎯 JWT then uses the sign() method to create a JSON Web Token for that user and returns the token in the form of a JSON string.
    const token_val = jwt.sign({ _id: user._id }, "hbjbgroehbejodif0ds");
    console.log("Token Value : ", token_val);
    // console.log("Type of Token Value : ", typeof(token_val));

    res.cookie("token", token_val , {
        httpOnly: true,
        expires: new Date(Date.now() + (60 * 1000))
    });
    
    // res.send('<h1>Logged In Successfully.</h1>');
    res.redirect('/');

    console.log("logged in success.")
})
```

# 4. on clicking `Logout`

```js
// logout me hame koi login id password se matlb nhi isliye get request
app.get('/logout', (req, res) => {
    res.cookie("token", null, {
        httpOnly: true,
        expires: new Date(Date.now())
    });

    // 👇 shortcut
    // res.clearCookie("token");
    
    res.redirect('/');
} )
```

# 5. Ending

```js
app.listen(4000, () => {
    console.log('Server is running on port 4000'); // eslint-disable-line no-console
})
```