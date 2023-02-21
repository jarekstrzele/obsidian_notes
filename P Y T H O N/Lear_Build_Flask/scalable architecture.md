[[_ Intro Scalable Web Applications with Python, Flask and SQLAlchemy]]

[[Context]]


---

# Section 8 Scalable architecture
link do usunięcia[[Intro Flask]]

[[Blueprint]]


==scalability==:
- one package per functionality
- add more packages as needed
- reuse packages




>__packaging__ organize code into modules or packages that do a very specific task

>**package** is a folder with a file `__init__.py`

folder `app` within a file `__init__.py` inside it:
```py
import os
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()

```

folder to configurate our app:
```
config:
	dev.py
	prod.py
	test.py
```


>**scalabale**     dzielimy wszystko na moduły/package




