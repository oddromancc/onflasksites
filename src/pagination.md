# Pagination

Let's say you have a list of data you'd like to display in batches. For example, you want to display five images per page, and you have 30 images total.

This function slices a Python list:
```
def sliceCol(aCol, perPage):
    page = request.args.get("page", 1, type=int)
    pages = len(aCol) // perPage
    if len(aCol) % perPage > 0:
        pages += 1
    offset = (page - 1) * perPage
    aColSliced = aCol[offset:offset+perPage]
    return (page, pages, aColSliced)
```

In the above example, I would have a list called `imgCol`.
```
sliced = sliceCol(imgCol, 5)
page, pages, imgColSliced = sliced[0], sliced[1], sliced[2]
```

And then passing these values to render_template:
```
return render_template('example.html', imgColSliced=imgColSliced, page=page, pages=pages)
```

Using the list in the template itself:
```
{% for img in imgColSliced %}
    <img src="{{ img }}">
{% endfor %}
```