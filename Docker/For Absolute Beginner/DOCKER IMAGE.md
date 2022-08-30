[[_ Intro Docker Mumshad]]

---
[[Docker image push to DockerHub]]
[[Docker environment variables]]

---
# docker image
#docker/image 

por. [[6 - Creating Container Images]]

## How to create my own image?
### manualy
1. OS - Ubuntu   
2. update apt repo
3. intall dependencies using apt
4. intall python dependecies using pip
5. copy ource code to /opt folder
6. run the web server using `flask` command
```bash
docker run -it ubuntu bash   # run a Ubuntu container and switch on a Bash terminal

$ apt-get update
$ apt-get install python
$ apt-get install python pip
$ pip install flask
$ cat > /opt/app.py
$ FLASK_APP=/opt/app.py flask run --host=0.0.0.0
```

### using Dockerfile
#dockerfile
```dockerfile
FROM ubuntu
RUN apt-get update && apt-get -y install python
RUN pip install flask flask-mysql
COPY . /opt/source-code
ENTRYPOINT FLASK_APP=/opt/source-code/app/py flask run
```
in the terminal:
```bash
docker build . -f DockerFile -t mmumshad/my-custom-app
docker push logDOckerHub/name_of_app
```


`RUN` run particulary commands on this image
`ENTRYPOINT` what will be run when an image is runing as a container

to name the image
`docker build . -t my-simple-webapp`

to run
`docker run my-simple-webapp`


















