
[[scalable architecture]]



## Blueprint
#python/blueprint 

>==Blueprint== 
>- set of operations registered on an application, 
>- simplifies large applications,
>-   is a class  

in `__init__.py` in a catalog folder:
```py
# app/catalog/__init.py
from flask import Blueprint

main = Blueprint('main', __name__, template_folder='templates')
```  
in that folder create a subfolder `templates`

Now

> A Blueprint object works similarly to a Flask application object, but it is not actually an application.  
> 
> Rather it is a blueprint of how to construct or extend an application.  

one package per functionality  
add more packages as needed  

reuse packages  
folder_app:

`__init__.py`:
```py
import  os, Flask, SAQAlchemy
db = SQLAlchemy

def create_app(config_type):
	app = Flask(__name__)......
    return app  
```

folder_auth  

folder_catalog  
      folder_templates
            __init__.py
```py
from flask import Blueprint

main = Blueprint('main', __name__, template_folder='templates')  
from app.catalog import routes  
```

routes.py
```py
from app.catalog import main 
#Blueprintfolder_config
```
```py
dev.py
      DEBUG = True
      SECRET_KEY = 'postgres'SQLALCHEMY_DATABASE_URI = 'postgresql://postgres:postgres@localhost/catalog_db'
      SQLALCHEMY_TRACK_MODIFICATIONS = False
```
test.py
prod.py  
run.py
```py

from app import create_app
      if __name__ == '__main__':
            flask_app = create_app('dev')
            flask_app.run()
```


### CIRCULAR REFERENCE
THis problem may occur in cases where o files or modules depend on each other.

to avoid any confilcts, we import routes at the bottom instead of importing at the top
