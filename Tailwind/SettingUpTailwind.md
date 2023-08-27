# Tailwind CSS Installation

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
