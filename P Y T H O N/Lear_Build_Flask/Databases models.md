[[_ Intro Scalable Web Applications with Python, Flask and SQLAlchemy]]


[[Blueprint]]

---

# Database model
in `app/catalog/` a new file `models.py`
```py
from app import db
from datetime import datetime


class Publication(db.Model):
    __tablename__ = 'publication'

    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(80), nullable=False)

    def __init__(self, name):
        self.name = name

    def __repr__(self):
        return 'Publisher is {}'.format(self.name)

# ...
```
klasy, które będa tabelam
ale Flask musi wiedzieć, z jakiego kontekstu wziąć dane, więc w pliku in `run.py` add:

```py
from app import create_app,db

if __name__ = '__main__':
	flask_app = create_app('dev')
	with flask_app.app_context():
		db.create_all()

	flask_app.run()

```

-------

In `app/` create `static/css`  `static/img`   `static/js` 
