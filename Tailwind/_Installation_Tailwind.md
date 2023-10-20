Tailwidnd - a utility classes
chakra ui - Component Library

# 0. Shortcut Installation

- `Extract Here` the `MY_TEMPLATE` zip file
- To Execute the template, run the command
  - `npm run start` in the terminal of VS Code.

# 1. Tailwind CSS Installation

<a href="https://tailwindcss.com/docs/installation/using-postcss" target="_blank">🔗 Tailwind CSS using PostCSS</a>

## 🪜 Step 1:

```css
npm init -y
```

## 🪜 Step 2:
```css
npm install -D tailwindcss postcss autoprefixer
npm vite
```
or

```css
npm install -D tailwindcss postcss autoprefixer vite
```

---
## 🪜 Step 3:

```css
npx tailwindcss init -p
```

---
## 🪜 Step 4: Create a CSS file `main.css` or `style.css`
  - Add it to your html file 
```html
    <link rel="stylesheet" href="main.css">
```

  - Paste the below content ⬇️ in your `main.css` file
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---
## 🪜 Step 5: In `tailwind.config.js` file 

- replace `content[]` with `content["*"]`

```css
"*"
```

🎯 or

```js
FileName: tailwind.config.js

/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

## 🪜 Step 6: In `package.json` file

- Add `"start": "vite"` to your scripts

```css
"start": "vite"
```

## 🪜 Step 7: 
Run npm run start command to start a dev serve

```css
npm run start
```

`or`

```css
npm run start -- --host
```

  - For vite server to get host link of network.

# 2. VS Code Extension - for tailwindcss

1. Tailwind CSS IntelliSense
   - It `enhances` the Tailwind development experience by providing features such as `autocomplete, syntax highlighting, and linting.`

2. PostCSS Language Support
   - Resolve Error: `⚠️ unknown rule @apply` in css File

3. Headwind Extension
   - Tailwind CSS class sorter for Visual Studio Code. It enforces consistent ordering of classes by parsing your code and reprinting class tags to follow a given order.

```js
Headwind: `Run On Save`
⬛ A flag that controls whether or not Headwind will sort your Tailwind CSS classes on save.

Note: Remain this option as untick.
```

4. [🔗 Tailwind CSS Debug Screens- GitHub Installation Instruction](https://github.com/jorenvanhee/tailwindcss-debug-screens)
   - A Tailwind CSS component that shows the currently active screen (responsive breakpoint).

5. [🔗 Tailwindcss Brand Colors- GitHub Installation Instruction](https://github.com/praveenjuge/tailwindcss-brand-colors)
   - Tailwind plugin for adding brands colors as background, border and text colors.


# 3. Deploying a Tailwind Website to Production : Tailwind Tutorial #13

```json
FileName: package.json
{
  "scripts": {
    "build": "vite build",
    "preview": "vite preview"
  }
}
```


