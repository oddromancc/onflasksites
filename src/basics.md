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

Here is how you initialize the app:
```
app = Flask(__name__)
app.config['SECRET_KEY'] = 'key'
```

Don't worry about the value of the secret key for now, but later when you deploy you should change to something more secure.

Think of a URL for the page you're creating. I'll use `home` as an example.
Here is how you create a page with this URL, `https://yourdomain.com/home`:
```
@app.route('/home')
def onhome():
    return render_template(forhome.html)
```

So far this is what we have in the `main.py` file:
```
from flask import Flask, render_template

app = Flask(__name__)
app.config['SECRET_KEY'] = 'key'

@app.route('/home')
def onhome():
    return render_template(forhome.html)
```

That is all the Python code you need for the app to run, but we still need to create the HTML files and place it in the `templates/` folder.

HTML can feel redundant which is why we're creating two HTML files. One is going to be the base titled `base.html`, and the other, titled `forhome.html`, is going to display content specific to the `/home` page.

Everything from `base.html` is carried over into `forhome.html` using Jinja.

Let's create `base.html`:
```
<!doctype html>
<html>

</html>
```
