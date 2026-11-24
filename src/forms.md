# Forms

This page shows basic form handling.

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

Here is another code excerpt for a page, this time we save the checked boxes in a Python list:
```
@app.route('/somepage', methods=('GET', 'POST'))
def onsomepage():
    if request.method == 'POST':
        falloutCharList = request.form.getlist('falloutCharacters')
    
    print(falloutCharList)
    
    return render_template('forsomepage.html')
```

You could also have two forms on one page. For example, you're making a ranked game where a player looks for multiple potential opponents based on their rank. As a reminder, variables, such as `userRank`, that you pass to `render_template()` can be accessed in the html file by putting them in brackets like this: `{{ userRank }}`.

The HTML might look like this:
```
<form method="post">
    <input type="hidden" name="myRank" value="{{ userRank }}">
    <input type="submit" value="Find opponents">
</form>

<form method="post">
    <input type="hidden" name="opponentId" value="{{ oppId }}" required>
    <input type="submit" value="Pick opponent">
</form>
```