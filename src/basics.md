# Basics

Create the following:
- `static/`
- `templates/`
- `main.py`

Here is what you write to initialize your app:
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
To create the `forhome.html` file, make sure there is a `templates` folder
