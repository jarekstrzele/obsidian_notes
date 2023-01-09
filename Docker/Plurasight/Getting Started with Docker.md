#docker #plurasight  #poulton_nigel

---

# Getting Started with Docker
other courses: Docker for Web Developers, Docker Deep Dive

DESKTOP DESKTOP
Windows 64, Mac 

## Play with Docker
https://labs.play-with-docker.com/

---
# Deploying a Containerized App

take some app source code 
	--->> 
	use Docker to package it as a container image 
	(`docker image build ...`) 
		--->>
		push the image to the registry
		(`docker image push ...`) (It is on dockerhub)
			--->>
			run it as a container
			(`docker containe run ...`)


## Containerizing an app
https://github.com/nigelpoulton/gsd
https://github.com/nigelpoulton/gsd.git (source code)

Docker is language agnostic!!

### DOCKERFILE
`Dockerfile` - it's a set of build instructions (app code + dependencies)

`FROM node:current-alpine` start building an image by first grabbing the node:cuurent-alpine image ([[alpine]])
Every conainer, when it is running, uses the kernel of the host it is running on.

`LABEL org.opencontainer.image.title="Hello Docker Learners!" ...`

```Dockerfile
# Create directory in container image for app code
RUN mkdir -p /usr/src/app

# Copy ap code (.) to /usr/src/app in the conainer image
COPY . /usr/src/app

#Set working directory context
WORKDIR /usr/src/app

# Install depenencies from packages.json
RUN npm install

# Command for conainer to execute
ENTRYPOINT ["node", "app.js"]

```

in the folder "first-container" where is source code and Dockerfile
`docker image build -t dockerub_ID/repoName:imageName .` period is very important (all necessary files and folders are in the current folder)

for me:
`$ docker image build -t js100code/gsd:first-ctr .`

### Hosting on a Registry
>[!container registry]
>it is a place where we store container images and we can share them and access them from different environments

`docker login -u [username]`

`docker image push dockerhub_ID/repoName:imageName`

### Running a Containerized App
Think of an image as being like a stopped container, so
a conainer is bascally a running image.
#docker/run 

`docker container run -d --name conainerName -p 8000:8080 imageName`

`-d` detached

`docker container run -it --name test aplpine sh` 
`sh` - is the main app in this container
`exit` terminate the container
`ctr+P+Q` back to the host shell, but container is still running

### Managing a Containerized App
`docker container stop containerName`

`docker container start containerName`

`docker container rm containerName`
`docker container rm containerName -f`

-------------
## Microservices and The Real World
#microservices

### Cloud-native Microservices
A **non-microservices** app has inside itself:
- frontend
- backend
- login
- logs
- reporting
- ....
and
- if you will want to change (e.g.) 
	- reporting -> you will change the whole app
	- scaling -> it will be difficult

**Microservices**:
- break this app into smaller, discrete services -> microservices
- each microservice is coded independently and often by different teams 
- microservice-db,  microservice-reporting, microservice-frontend, microservice-logs, ....

>[!Microservices design pattern]
>take the different features of an app and break them all out and code them independently 

*Cloud-native* doesn't mean that an app will be run only in a cloud, it could be:
- public cloud
- private/hybrid cloud
- on prem data center

### Multi-container Apps with Docker Compose
>[!Declarative]
>Describing the desired state of your application in a config file that you use to deploy and manage the app

##### `docker-compose`

`docker-compose.yml` this is a declarative manifest file describing an app
Docerfile:
```docker
  1 # Base image
  2 FROM python:alpine
  3 
  4 # Add app code to /code inside container image
  5 ADD . /code
  6 
  7 # Set working directory for subsequent commands
  8 WORKDIR /code
  9 
 10 # Install dependencies
 11 RUN pip install -r requirements.txt
 12 
 13 # Command to run when container starts
 14 ENTRYPOINT ["python", "app.py"]

```

docker-compose:
- two applicatiom microservices
	- `web-fe` is the Python Flask app
		- `build: .` will call that Dockerfile to build an image
		- `command: python app.py` it will be executed when the container starts
	- `redis` it just pulls a stock image from DockerHub and attaches to the same network
```yml
version: "3.8"
  2 services:
  3   web-fe:
  4     build: .
  5     command: python app.py
  6     ports:
  7       - target: 5000
  8         published: 5000
  9     networks:
 10       - counter-net
 11     volumes:
 12       - type: volume
 13         source: counter-vol
 14         target: /code
 15   redis:
 16     image: "redis:alpine"
 17     networks:
 18       counter-net:

```

To run, you must be in the folder with all files (app.py, docker-compose.yml, Dockerfile, READ.md, requirements.txt)
#docker-compose_run
`docker-compose up -d`
`-d` detached mode

#docker-compose_stop
to stop:
`docker-compose down`


### Docker Swarm
#docker/swarm
It lets you cluster multiple DOcker hosts into a secure, highly availble cluster

#### cluster
- comprises managers and workers
- a cluster is a swarm, a swarm is a cluster of one or more **manager** nodes and some **worker** nodes (together odd number)
- the managers host the control plane features (scheduling, persisting the state of the cluster ) 

#### Docker services
Swarm unlocks Docker Services!
A Docker service maps directly to an app microservice.


#### first swarm
`docker swarm init` this will make the node that you run the command on, the first manager node in the swarm or cluster

with *Play with Docker* : `docker swarm init --advertise-addr=host_IP_to_communication` (192.168.0.20)

```shell
$ docker swarm init
Swarm initialized: current node (1l5h62frdrh0rlxdzu7yjmpy9) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-3tun6jbdyoq2ovw57cr7i2tsjf5xiimx8m15lxna2rrp1o1em6-0iladk2wwukhf9q8trseppl2x 192.168.0.12:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
$ docker swarm join-token manager
To add a manager to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-3tun6jbdyoq2ovw57cr7i2tsjf5xiimx8m15lxna2rrp1o1em6-c4kbj4g7p8qqcabkwbf0l957l 192.168.0.12:2377

```

Some problems
https://docs.docker.com/get-started/overview/

---
### Microservices and Docker Services

Each of application microservices (e.g. logs, login, reporting, frontend,...) can be implemented through its own Docker service

#### imperative way
First you have to initialize a Docker swarm
`docker service create --name web -o 8080:8080 --replicas 3 nigelpoulton/gsd:first-ctr`

`docker service ls`
(a service replica is a container)
```shell
$ docker service ls
ID             NAME      MODE         REPLICAS   IMAGE                     PORTS
9c3bmar24qpu   web       replicated   3/3        js100code/gsd:first-ctr   *:8080->8080/tcp

$ docker container ls
CONTAINER ID   IMAGE                     COMMAND         CREATED              STATUS              PORTS     NAMES
c65e84ee95b5   js100code/gsd:first-ctr   "node app.js"   About a minute ago   Up About a minute             web.2.l04ajkexmsaqmkfjf4qxqvkeb
d23ca55fbec7   js100code/gsd:first-ctr   "node app.js"   About a minute ago   Up About a minute             web.3.6yvfp99ygpoeluoyzbxhy0xbp
9d4dcdd8f1ab   js100code/gsd:first-ctr   "node app.js"   About a minute ago   Up About a minute             web.1.rg2wodrb8phtz8so4xdlrjs8u

```

better command:
```shell
$ docker service ps web
ID             NAME      IMAGE                     NODE                DESIRED STATE   CURRENT STATE           ERROR     PORTS
rg2wodrb8pht   web.1     js100code/gsd:first-ctr   jarek-Lenovo-G700   Running         Running 2 minutes ago             
l04ajkexmsaq   web.2     js100code/gsd:first-ctr   jarek-Lenovo-G700   Running         Running 2 minutes ago             
6yvfp99ygpoe   web.3     js100code/gsd:first-ctr   jarek-Lenovo-G700   Running         Running 2 minutes ago  
```

You can scale the app:
`docker service scale web=10` -> 10 containers will be running; 10 is a desire state, so if you delete 3 containers, swarm restart them 

to STOP:
`docker service rm web`



#### declarative way
==yml file==
```yml
version: "3.8"
services:
	web-fe:
		image: js100code/gsd:swarm-stack
		command: python app.py
		deploy:
			replicas: 10
		ports:
			- target: 8080
			  pubished: 5000
		networks:
			- counter-net
		volumes:
			- type: volume
			- source: counter-vol
			- target: /code
		redis:
			images: "redis:alpine"
			networks:
				counter-net:
networks:
	counter-net:
volumes:
	counter-vol:
			
```

APP THAT IS RUNNING IN DOCKER SWARM MODE WE CALL THE APP ==A STACK==
stacks can't build image on fly
`docker image build js100code/gsd:swarm-stack .`

`docker stack deploy -c docker-compose.yml counter  `
`docker stack ls`
`docker stack services counter`
`docker stack ps counter`

COURSES:
Docker for web developers
Docker Deep Dive
Getting started with Kubernetes

























