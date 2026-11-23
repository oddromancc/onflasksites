# Basics

Create the following:
- `static/` - a folder to store your `.css` file
- `templates/` - a folder to store your `.html` files
- `main.py` - the file where you will write your program

In `main.py`, these are the first lines of code:
```
from flask import Flask, render_template
```
You just imported flask itself to initialize it later, and you also imported `render_template` which when returned will display an HTML file.

Here is how you initialize the app. Don't worry about the value of the secret key for now, but later when you deploy you should change to something more secure.
```
app = Flask(__name__)
app.config['SECRET_KEY'] = 'key'
```

Think of a URL for the page you're creating. I'll use `home` as an example.
Here is how you create a page with this URL, `https://yourdomain.com/home`:
```
@app.route('/home')
def onhome():
    return render_template(forhome.html)
```

Let's create
