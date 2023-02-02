# Set up Tailwind in your Project

Tailwind CSS is a utility class framework that helps you make a responsive web design. In this article, I will teach you, how to set up a tailwind in the project.

## Play CDN ( Method 1)

This is the easiest way to use Tailwind, but it is not recommended for a production application. `<script src="https://cdn.tailwindcss.com"></script>` inside the `<head>` tag.

> An Internet connection is required!

```xml
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
</body>
</html>
```

## Tailwind CLI ( Method 2 )

Tailwind CLI is a tool to quickly set up your project a generate required styling automatically. First You need to install node.js on your computer. After you have installed Node.js creates a folder (`Tailwind-Project`) and run the below command on your terminal.

> Internet connection is not required after you have done the setup once!

```bash
mkdir Tailwind-Project
cd Tailwind-Project
```

```bash
npm install -D tailwindcss
npx tailwindcss init
```

After you have run the above command you will see a `tailwind.config.js` file in your folder.\`

```bash
➜  Tailwind-Project tree
.
└── tailwind.config.js

0 directories, 1 file
```

Create a `src` folder inside `Tailwind-Project` and add your HTML, CSS, and Javascript files inside it.

```bash
➜  Tailwind-Project tree
.
├── src
│   ├── input.css
│   ├── main.html
│   └── main.js
└── tailwind.config.js

1 directory, 4 files
```

Now it is time for configuring `tailwind.config.js` you will something just like this in the code.

```javascript
module.exports = {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Replace or Rewrite the code with this ↓. Here are adding the paths to all of your template files in your `tailwind.config.js` file.

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Open the `input.css` file and paste the below lines.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Now run this command to start the Tailwind CLI build process, it will generate a file under a `/dist/output.css` , and here is the file which will contain all your CSS styling.

```bash
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch
```

Now you will see something just like this.

```bash
warn - The `content` option in your Tailwind CSS configuration is missing or empty.
warn - Configure your content sources or your generated CSS will be missing styles.
warn - https://tailwindcss.com/docs/content-configuration
Browserslist: caniuse-lite is outdated. Please run:
  npx browserslist@latest --update-db
  Why you should do it regularly: https://github.com/browserslist/browserslist#browsers-data-updating

Rebuilding...
Done in 88ms.
```

Now the project structure should see like this. Here you will see a new file under the folder `dist` the file name will be `output.css`. This is a file that we need to insert into our HTML.

```bash
➜  Tailwind-Project tree
.
├── dist
│   └── output.css
├── src
│   ├── input.css
│   ├── main.html
│   └── main.js
└── tailwind.config.js

2 directories, 5 files
```

Paste the below command into your HTML file (`main.html`). The line `<link href="/dist/output.css" rel="stylesheet">` is the line that links `output.css` to `main.html` . Now you can write class can the Tailwind CLI will automatically build the CSS file.

```xml
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="/dist/output.css" rel="stylesheet">
</head>
<body>
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
</body>
</html>
```

To learn how to use Tailwind CSS head over to [tailwindcss.com](https://tailwindcss.com).

Follow me on Twitter [Jyotirmoy Barman](https://twitter.com/jyotirmoydotdev/).