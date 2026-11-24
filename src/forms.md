# Forms

This page shows basic form handling.

Here is how you create your form in HTML:
```
<form method="post">
    <input type="text" class="input" name="jobTitle" required>
</form>
```

The `name` value can be anything, and it's what you later use to save the

Here is how you save HTML form input in a variable in `main.py`:
```
@app.route('/somepage', methods=('GET', 'POST'))
def onsomepage():
    if request.method == 'POST':
        jobTitle = request.form['jobTitle']
```