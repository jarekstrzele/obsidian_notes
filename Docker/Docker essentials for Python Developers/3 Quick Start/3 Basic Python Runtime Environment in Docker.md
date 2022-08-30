[[_intro quick start docker]]


-----
# Basic Python Runtime Environment in Docker

## Basic Python Runtime Environment in Docker

```py
# interactive container named mypython1
# using official python image 3.7 executing linux shell bash
docker run -it --name mypython1 \
-p 5000:5000 -p 8000:8000 \
-v ${PWD}: /app \
python:3.7 bash

docker start -ia mypython1

docker rm mypython1
```

`docker run` create and start a new container

`-it` interactive 

`-p host_port:container_port` localhost:5000

`-v ${PWD}:/app` maps a current  working directory in the host to /app in the container;  the container will have accese to all folders, subfolders and files in the host machine <-- ==bound mounting==

`bash` command  launches a linux bash shell

each container has its own independent file system  

---
## FLASK
`docker run -it --name myflask1 -p 5000:5000 -v ${PWD}:/app python:3.7 bash`

in the container
`pip install flask==1.1.1`
`cd /app`
`export FLASK_APP=flask_example.py`
`export FLASK_DEBUG=1`
`flask run --host=0.0.0.0`

There ia an error. You have to upgrade your flask:
`pip install flask==2.1.2`


`ctr + c  --> stop the container/flask server

---










