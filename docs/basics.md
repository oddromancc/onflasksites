# Basics

Create the following:
- `static/` - a folder to store your `.css` file
- `templates/` - a folder to store your `.html` files
- `main.py` - the file where you will write your program

## Python

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

Basically, it's page URL excluding domain name, then function that does whatever and in this case finally returns a template (displays an .html file).

So far this is what we have in the `main.py` file:
```
from flask import Flask, render_template

app = Flask(__name__)
app.config['SECRET_KEY'] = 'key'

@app.route('/home')
def onhome():
    return render_template('forhome.html')
```

## HTML

That is all the Python code you need for the app to run, but we still need to create the HTML files and place them in the `templates/` folder.

HTML can feel redundant which is why we're creating two HTML files. One is going to be the base titled `base.html`, and the other, titled `forhome.html`, is going to display content specific to the `/home` page.

Everything from `base.html` is carried over into `forhome.html` using Jinja.

Let's create `base.html`:
```
<!DOCTYPE html>
<html>
    <head>
        
    </head>
    <body>
        <header>
            
        </header>
        <main>
            {% block content %}{% endblock %}
        </main>
        <footer>

        </footer>
    </body>
</html>
```

So there is a series of self-explanatory tags which you will get the hang of if seeing for the first time. But right now we're paying attention to this part:
```
{% block content %}{% endblock %}
```

This is like a bucket that we can fill using other html files. The name of the block can be anything.

Now that we have our `base.html` created, let's write the very first line of `forhome.html`:
```
{% extends 'base.html' %}
```

This means we're basically rendering `base.html` when displaying `forhome.html`, but not quite because we're also adding content unique to the `/home` page by continuing the code like this:
```
{% block content %}
    <h1>Welcome to the home page</h1>
{% endblock %}
```

Overall, this is the whole of `forhome.html`:
```
{% extends 'base.html' %}

{% block content %}
    <h1>Welcome to the home page</h1>
{% endblock %}
```

Launch your app by running this command:
```
flask --app .\main.py run
```

Navigate to the `/home` page and see the "Welcome to the home page".

Congrats! You've managed to create a simple Flask app that you can now build upon.