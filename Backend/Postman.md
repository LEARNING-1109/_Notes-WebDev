# 1. Get Method 

## 1.1 Send id through body as json

```js
// app.js file
app.get("/userid", async(req, res) => {
    const { myID } = req.body;    // postman > GET Req. > Body> raw (json file mode) >
    const user = await User.findById(id);

    res.json({
        success: true,
        user
    })
} )
```

```json
// postman > GET Req. > Body> raw (json file mode) >
{
    "myID": "65155d6b97763f3086a73abc"
}
```

## 1.2 Send id through params 

`In Postman app`

Params -> Query Params

| Key | Value                    |
|-----|--------------------------|
| id  | 65155d6b97763f3086a73abc |


```js
// app.js file
app.get("/userid", async(req, res) => {
    // const { myID } = req.body;    
    const { myID } = req.query; // Params -> Query Params
    const user = await User.findById(myID);   

    res.json({
        success: true,
        user
    })
} )
```

## 1.3 Get request through params

HIT URL : 

- `http://localhost:4000/userid/65155f1d23020dc3ee9e2da3`

```js
// In app.js file 

// DYNAMIC ROUTES - hamesa last me rakho
app.get("/userid/:myID", async(req, res) => {    
    const { myID } = req.params; // Params -> Query Params

    const user = await User.findById(myID);   

    res.json({
        success: true,
        user
    })
} )
```

