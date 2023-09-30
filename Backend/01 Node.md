<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [Complete-BACKEND in One Video- 6PP](#complete-backend-in-one-video--6pp)
- [0. Handling Errors :](#0-handling-errors-)
   * [1. import ](#1-import)
   * [2. Tips for fast exectuion](#2-tips-for-fast-exectuion)
   * [3. res.sendFile(path.join(`__dirname` + '/about.html'))](#3-ressendfilepathjoin__dirname--abouthtml)
- [1. How do I start with Node.js after I installed it?](#1-how-do-i-start-with-nodejs-after-i-installed-it)

<!-- TOC end -->

# Complete-BACKEND in One Video- 6PP
---

# 0. Handling Errors :
## 1. import 
```js
import mongoose from 'mongoose';    💀
```
Solution:
```js
// In package.json file add
{
    .......... ,
    "type": "module",
}
```

## 2. Tips for fast exectuion
```js
{
    // In package.json file add
    "scripts": {
    ............. ,
    "start": "node index.js",
    "dev": "nodemon index.js"
  },
}
```

## 3. res.sendFile(path.join(`__dirname` + '/about.html'))
Error: `__dirname is not defined` ❌

Soln.
```js
import { fileURLToPath } from 'url';
import { dirname } from 'path';

const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);
```



# 1. How do I start with Node.js after I installed it?

- Once we have installed Node.js, let's build our first web server. Create a file named app.js containing the following contents:

```js
const http = require('http');
 
const hostname = '127.0.0.1';
const port = 3000;
 
const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
});
 
server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

- Now, run your web server using node app.js. 
- Visit http://localhost:3000 and you will see a message saying "Hello World".

