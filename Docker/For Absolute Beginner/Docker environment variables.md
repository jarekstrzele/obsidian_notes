[[_ Intro Docker Mumshad]]

[[DOCKER IMAGE]]


---

# Docker environment variables

You can write in app.py :

...

color="red"

...

      return render_template('hello.html', color=color)

BUT a better practice: 
move such information put of the application code and into a  e n v i r o n m e n t    v a r i a b l e 

import os

 ....

color = os.environ.get('APP_COLOR')

...

      return render_template('hello.html', color=color)

Now you can set a value of this variable when you run the app

docker run -e APP_COLOR=blue simple-webapp-color

docker run -e APP_COLOR=pink simple-webapp-color

When an app is running:

docker inspect nameOfContainter

# in the 'Config ' section you will find "Env": [ ... "APP_COLOR=blue" ....



$ docker run --name blue-app -e APP_COLOR=blue -p 38282:8080 kodekloud/simple-webapp


