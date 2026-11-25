# CSS

CSS is styling your HTML elements so they look nice.

### DaisyUI

One of your options is [DaisyUI](https://github.com/saadeghi/daisyui), I'm going to walk you through installing it.

First, make sure you have Node installed. Then in your project folder run this to create a new npm project:
```
npm init -y
```

Install Tailwind and DaisyUI by running this in the terminal:
```
npm install tailwindcss@latest @tailwindcss/cli@latest daisyui@latest
```

In the `package.json` file, under "scripts" create a new script by adding this entry:
```
"build:css": "npx @tailwindcss/cli -i app.css -o static/output.css"
```

Create .css file by running the script in the terminal:
```
npm run build:css
```

Make sure `url_for` is imported from `flask` and include this in the head section of your base HTML template:
```
<link href="{{ url_for('static', filename='output.css') }}" rel="stylesheet">
```

Run your app.

### Bootstrap

Another CSS option is Bootstrap.

