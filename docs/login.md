# Login

Install Flask-Login:
```
pip install flask-login
```

At the top of the `main.py` file, import packages from Flask-Login that you just installed:
```
from flask_login import LoginManager, login_required, UserMixin, login_user, current_user, logout_user
```

Create a LoginManager object and customize it:
```
login = LoginManager()
login.init_app(app)
login.login_view = 'onsignin'
login.login_message = 'Please sign in'
```

I'll work on this.