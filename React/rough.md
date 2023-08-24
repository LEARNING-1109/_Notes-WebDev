<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [Export and Import](#export-and-import)
- [definition](#definition)
- [Code to Run in Command Prompt](#code-to-run-in-command-prompt)
- [VS Code Terminal](#vs-code-terminal)
  * [Create React App](#create-react-app)
- [Solve Error while adding < p > tag](#solve-error-while-adding--tag)
    + [Go one folder back 👇](#go-one-folder-back-)
  * [Important Extension in VS Code for React JS :](#important-extension-in-vs-code-for-react-js-)
  * [getbootstrap.com](#getbootstrapcom)
    + [Note : ❔ Where 🤷‍♀️ to put Bootstrap JS Link 🔗](#note---where--to-put-bootstrap-js-link-)
- [To Create Subcomponents in navbar.js like file](#to-create-subcomponents-in-navbarjs-like-file)
    + [Make Some Change Then Only it will Work by Adding 👆 👇](#make-some-change-then-only-it-will-work-by-adding--)
  * [Newly Added Navbar.js will work when React is import : 👇](#newly-added-navbarjs-will-work-when-react-is-import--)
  * [Also import ✅ these all component .js files in **App.js**](#also-import--these-all-component-js-files-in-appjs)
  * [Create array object in App.js & Passing it to the Components ✅](#create-array-object-in-appjs--passing-it-to-the-components-)
- [(React Functional Component) rfc Code Snippets in Product_List.js ()](#react-functional-component-rfc-code-snippets-in-product_listjs-)
  * [Extracting the Passed value/object as Parameter Using :](#extracting-the-passed-valueobject-as-parameter-using-)
  * [Class Component Code Snippets 👇](#class-component-code-snippets-)
- [Loop in JSX](#loop-in-jsx)
- [using the State Hook](#using-the-state-hook)
  * [❔ Need of useState ?](#-need-of-usestate-)
    + [JavaScript Spread Operator (...)](#javascript-spread-operator-)
- [Important Points to keep in mind 🤯🤯 ⭐⭐](#important-points-to-keep-in-mind--)
- [Make Custom changes in jsx :](#make-custom-changes-in-jsx-)

<!-- TOC end -->

  ## [Notes 1 : Apna College 👇]

[Notes 2 Link : Tech Gun 🔗](<https://github.com/All-CODE-with-Explanation/Web-Development-Learning/tree/main/REACT%20JS%20(Learning)/Tech%20Gun%20(React%20JS)>)

[Notes 3 : Form Validation using JS](<https://github.com/All-CODE-with-Explanation/Web-Development-Learning/blob/main/REACT%20JS%20(Learning)/1.%20React%20Reusable%20Template/form_validation.md>)

# Export and Import

Named Exports :

Named exports are useful to export several values. During the import, it is mandatory to use the same name of the corresponding object.

```javascript


export class Sample {
    constructor(name) {
        this.name = name;
    }
```

```javascript
import { Sample } from "./computer.js";
```

---

---

Default Exports :

Default exports are useful to export only a single object, function, variable. During the import, we can use any name to import.

```javascript
export default class Computer {
  constructor(name) {
    this.name = name;
  }

  run() {
    console.log("The Computer is now Running");
  }
}
```

```javascript
import Computer from "./computer.js";
```

---

---

---

---

---

# definition

Module :

In Node.js, **Modules** are the blocks of encapsulated code that communicates with an external application on the basis of their functionality.

- Modules can be a single file or a collection of multiples files/folders.

- The reason programmers are heavily reliant on modules is because of their re-usability as well as the ability to break down a complex piece of code into manageable chunks.

# Code to Run in Command Prompt

npm : Node Package Manager

npx : Node Package Execute

---

**Run These Commands in CMD 👇**

```
node --version
npm --version
npx -v


```

#

#

# VS Code Terminal

## Create React App

[React JS Documentation Link 🔗](https://reactjs.org/docs/create-a-new-react-app.html)

Create React App is a comfortable environment for **learning React,** and is the best way to start building **a new single-page application** in React.

It sets up your development environment so that you can use the latest JavaScript features, provides a nice developer experience, and optimizes your app for the production.

**_To create a project, run :_**

```css
npx create-react-app my-app-name
```

```css
npm start   ❌
```

This 👆 command will not run because you have to move inside that folder where node is created

```css
ls      // This will list all the folder

cd project_name
```

```css
npm start   ✅
```

You can view namaste-world in the browser

Local : [http://localhost:3000](http://localhost:3000)

React JS has hot reloading features. (Live Server Features)

---

# Solve Error while adding < p > tag

/Project_name/src/App.js

```javascript

function App() {
  return (

    <>  ✅
    <React.Fragment> ✅

    <p>{1 + 1}</p>

    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React <br></br>
          Namaste React
        </a>
      </header>
    </div>

    </React.Fragment>   ✅
    </>     ✅

  );
}

```

### Go one folder back 👇

```css
cd ../
```

## Important Extension in VS Code for React JS :

- ES7+ React/Redux/React-Native snippets

- Prettier - Code formatter

- Simple React Snippets

- Material Icon Theme by Philipp Kief

---

## getbootstrap.com

Copy some links like 👇

**jsDelivr**

When you only need to include Bootstrap’s compiled CSS or JS, you can use jsDelivr.

and PASTE it to the index.html

project_name/public/index.html

### Note : ❔ Where 🤷‍♀️ to put Bootstrap JS Link 🔗

✅ Before the END of the Body Tag.

```html
  <!-- ✨ JavaScript Bundle with Popper ✨ -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>

</body>
</html>
```

---

# To Create Subcomponents in navbar.js like file

To write React JS Snippets.

Install Extension :

- Simple React Snippets

You will get default Output as

```javascript
class  extends Component {
    state = {  }
    render() {
        return (  ...  );
    }
}

export default ;
```

### Make Some Change Then Only it will Work by Adding 👆 👇

- Add ClassName at two positions.
- Add keyword **React.Folder_Name** i.e, **React.Component**
- 👇👇👇👇

Now Updated Code will look like :⏬

```javascript
class Navbar extends React.Component {
    state = {  }
    render() {
        return (  ...  );
    }
}

export default Navbar;
```

---

If you directly write the **_HTML_** code inside the return ( ... )

As Shown above 👆

You will Get Error! ❌❌

To Solve This Error

✅ [You can use HTML to JSX Online Compiler 🔗](https://magic.reactjs.net/htmltojsx.htm)

Then only Paste the JSX Code inside the three dot

```javascript
return ( ... );
```

---

## Newly Added Navbar.js will work when React is import : 👇

In Navbar.js file, on the top of code Add :

Shortcut (type) : " imr " in vs code

```javascript
import React from 'react';

...

```

---

## Also import ✅ these all component .js files in **App.js**

```javascript
import logo from './logo.svg';
import './App.css';
import React from 'react';

import Navbar from './components/Navbar'; ✅ ✨

function App() {
  return (

    <>
    <React.Fragment>

    <Navbar/>   ✨ ✅

    <ProductList/>

    <Footer/>

    {/* If any of the above 👆 three listed files are not Available then it will show Nothing on Screen 📵📵 */}

    </React.Fragment>
    </>

  );
}

export default App;

```

---

## Create array object in App.js & Passing it to the Components ✅

```JavaScript
function App() {

  // Create Array Object for Products before return function ✅✅

  const product = [
    {
      price : 99999,
      name : "Iphone 10S Max",
      quantity: 0,
    },

    {
      price: 10000,
      name : "Redmi Note 8",
      quantity : 0,
    }
  ]

  return (
    <>
      <Navbar />

      {/* Passing data of Product Array in the Components 👇 ✅ */}
      <ProductList product={product}/>

      {/* <Footer/> */}

      {/* If any of the above 👆 three listed files are not Available then it will show Nothing on Screen 📵📵 */}

    </>
  );
}
```

---

# (React Functional Component) rfc Code Snippets in Product_List.js ()

type rfc for React Functional Component

```javascript
import React from "react";

export default function ProductList() {
  return <div></div>;
}
```

## Extracting the Passed value/object as Parameter Using :

```javascript
export default function ProductList(y) {
  console.log(y);

  ...
}
```

OR

```javascript
/* Using props
🔷 It is an object which stores the value of attributes of a tag and work similar to the HTML attributes.

🔷 It gives a way to pass data from one component to other components.

🔷 It is similar to function arguments.

✨ Note : Jitne bhi component hote hai React ke andar wo Pure Function hote hai

Koi bhi Input pass krne pe Output Same hi rhega
*/
export default function ProductList(props) {
  console.log(props);

  ...

}
```

---

## Class Component Code Snippets 👇

type **_cc_** to get class component code snippets

```javaScript
class className extends Component {
  state = {  }
  render() {
    return ();
  }
}

export default className;
```

# Loop in JSX

🔴 For loop don't work in JSX.

🟢 It will support Map Function, ForEach

---

---

# using the State Hook

[Refer to React Hooks Documentation](https://reactjs.org/docs/hooks-state.html);

What’s a Hook?

Our new example starts by importing the useState Hook from React:

```javascript
import React, { useState } from "react";

function Example() {
  // ...
}
```

- What does calling useState do?

🟢 To make change effective we can use document.get.ElementById('');

But agar javascript hi use krna tha Then what's the use of react

To do so, we can use **_useSate_** to make changes effective.

🟢 It declares a "state variable".

- What does the useState return ?

🔷 Normally, variables "disappear" when the function exits but state variables are preserved by React.

```javaScript
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);
```

👆 Here count is our variable.

🔷 We can declare a state variable called count, and set it to 0.
React will remember its current value between re-renders, and provide the most recent one to our function.

🔷 If we want to update the current count, we can call **_setCount_**

## ❔ Need of useState ?

```javascript
// for editing title creating new variable named title
let title = props.title;
// 👆 Effective changes is not visisble by creating varible. ❌
// So Let's use useState in place of variable name

useState("");
useState("Hello School");

// 👇 here props.title is passed to the useState as a value
const [title, setTitle] = useState(props.title);
// here setTitle is the function name using which new value will be stored
```

### JavaScript Spread Operator (...)

The JavaScript spread operator (...) allows us to quickly copy all or part of an existing array or object into another array or object.

# Important Points to keep in mind 🤯🤯 ⭐⭐

- If you are using **_state_** inside the file then must create state earlier in it. Eg. this.state

- If you are using **_class component_** then create state as an **_OBJECT._** Eg. this.props

- If you are using **_functional components_** then use **_HOOKS._**

---

---

# Make Custom changes in jsx :

|class className

for= htmlFor=

- Those tags which don't have closing tags add **/** at the pre-end
