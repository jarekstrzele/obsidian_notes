
[[_ Intro Scalable Web Applications with Python, Flask and SQLAlchemy]]


---
# Bootstrap and Flask
`pip3 install flask-bootstrap`


`/app/__init__.py`

```py
from flask_sqlalchemy import SQLAlchemy
from flask_bootstrap import Bootstrap

db = SQLAlchemy()
bootstrap = Bootstrap()

```

---

# jinja2 template Inheritance
#flask/inheritance

>We organize our code into re-usable html blocks.


`/app/catalog/templates/layout.html`
```html


```

We have to import this file into our `home.html` file:
```html
{% extends 'layout.html' %}
```

Delete `<head> <body>`.
Write down `{% block content %}` and at the end of the file `{% endblock %}`








