# Forms

This page shows basic form handling. Not using WTForms, at least not yet.

Here is how you create your form in HTML:
```
<form method="post">
    <input type="text" name="jobTitle" required>
    <input type="submit" value="Send form">
</form>
```

The `name` value can be anything. It's how you get the contents of that specific input in Python code.

Here is an excerpt showing code for a page that saves HTML form input in a variable and prints it later:
```
@app.route('/somepage', methods=('GET', 'POST'))
def onsomepage():
    if request.method == 'POST':
        jTitle = request.form['jobTitle']
    
    print(jTitle)
    
    return render_template('forsomepage.html')
```

You write `methods=('GET', 'POST')` to allow GET and POST requests, which means the form submit button is functional.

Here is a form of checkboxes, which has only one `name` value, but multiple actual "inputs":
```
<form method="post">
    <input type="checkbox" name="falloutCharacters" aria-label="Maximus" value="Maximus">
    <input type="checkbox" name="falloutCharacters" aria-label="Lucy" value="Lucy">
    <input type="checkbox" name="falloutCharacters" aria-label="Ghoul" value="Ghoul">
    <input type="checkbox" name="falloutCharacters" aria-label="Hank" value="Hank">
    <input type="submit" value="Send form">
</form>
```

Here is how you then save the checked boxes in a Python list:
```
@app.route('/somepage', methods=('GET', 'POST'))
def onsomepage():
    if request.method == 'POST':
        falloutCharList = request.form.getlist('falloutCharacters')
    
    print(falloutCharList)
    
    return render_template('forsomepage.html')
```

You could also have two forms on one page. 

The HTML might look like this:
```
<form method="post">
    <input type="text" name="fullName" required>
    <input type="submit" value="Send form #2">
</form>

<form method="post">
    <input type="text" name="someInfo" required>
    <input type="submit" value="Send form #2">
</form>
```

Python code:
```
@app.route('/somepage', methods=('GET', 'POST'))
def onsomepage():
    if request.method == 'POST':
        if 'fullName' in request.form:
            fullName = request.form['fullName']
        
        if 'someInfo' in request.form:
            someInfo = request.form['someInfo']
        
    return render_template('forsomepage.html')
```