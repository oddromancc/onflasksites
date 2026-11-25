# Templating

Here is some stuff you can do with the Jinja templating engine besides blocks such as `{% block title %}{% endblock %}` and extending other HTML files.

## For loop

You can iterate through a list. First, in `main.py` you pass the list to the template like this:
```
return render_template('example.html', thelist=thelist)
```

Then you write this in your html:
```
{% for i in thelist %}

{% endfor %}
```

## If statement

You can also have if-else statements. I'm going to show one way to implement a message that indicates if the user is online. Let's imagine we queried our database and it showed that the user is online right now. So we set our variable `isOnline` to `'good'`. If the user wasn't online, `isOnline` would be `None`. So we pass `isOnline` to `render_template()`.

Here is the HTML part:
```
{% if isOnline %}
    <p>Online</p>
{% else %}
    <p>Away</p>
{% endif %}
```