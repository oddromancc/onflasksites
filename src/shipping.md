# Shipping

Shipping, or deployment, is running your app on a server. Typically, you can deploy using your Github repo. I will show you how to do so on Railway.

Install gunicorn:
```
pip install gunicorn
```

Make sure to create a `requirements.txt` file which is essentially a list of all of the packages installed in your virtual environment. In your project folder run:
```
pip freeze > requirements.txt
```

