# Tailwind CSS Setting Up 
[🔗 Tailwind CSS using PostCSS](https://tailwindcss.com/docs/installation/using-postcss)

<a href="https://tailwindcss.com/docs/installation/using-postcss" target="_blank">Tailwind CSS using PostCSS</a>

## 🪜 Step 1:

`npm init -y`


## 🪜 Step 2:

`npm install -D tailwindcss postcss autoprefixer`

`npm vite`

or

`npm install -D tailwindcss postcss autoprefixer vite`

---
## 🪜 Step 3:

`npx tailwindcss init -p`

---
## 🪜 Step 4: Create a CSS file `main.css` or `style.css`
  - Add it to your html file 
  - Paste the below content ⬇️ in your css file
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---
## 🪜 Step 5: In `tailwind.config.js` file 

- replace `content[]` with `content["*"]`

## 🪜 Step 6: In `package.json` file

- Add `"start": "vite"` to your scripts

## 🪜 Step 7: 
Run npm run start command to start a dev serve

`npm run start`
