[[_ intro Python Docker]]

[[6 - Creating Container Images]]

---

# Manual build process

## Exercise 1:
- goal: create Jupiter Notebook image with Pytorch included
- base image: jupyter/tensorflow-notebook
- additional python libraries: torch torchvision

IN a HOST bash:
`$ docker pull jupyter/tensorflow-notebook`
`$ docker run -d --name temp jupyter/tensorflow-notebook`
`$ docker exec -it temp pip install torch torchvision`
`docker stop temp`
`$ docker commit temp myjupiter:torch` (first arg is the name of temporary image and the second one is a name of our image)
`$ docker run -it --rm -p 888:888 -v ${PWD}:/home/jovyan/notebooks myjupyter:torch`

`docker rm temp`

## Exercise 2:
- goal: create an Image with Flask based microservice
- base image: python:3
- source: s4py/section-6/manual-build/color-boxes.py
- libraries: flask

`docker run -it --name temp python:3 bash`
in an interactive bash shell of the container:
`$ pip install flask`
`$ mkdir /app`
`$ exit`

Copy a source code from the host into the container `/app` folder (in the host terminal):
`$ docker cp color-boxes.py temp:/app`
`$docker start -ai temp`
`ls -l /app`
`exit`

`$ docker commit -c "WORKDIR /app" -c "ENV FLASK_ENV=development" -c "CMD python color-boxes.py"`
`-c` changes metadata settings
and now
`$docker run -it --rm -p 5000:5000 myflask:manual`










