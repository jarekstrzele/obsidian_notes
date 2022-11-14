[[_ Intro Docker Essentials]]

[[3 Docker Images in Depth]]



---
[[Docker Images]]


---
# Docker Containers and the Docker Engine

## Container
>==a docker container== 
>is a loosely isolated environment running within a host machine's kernel that allows us to run application-specific code


__kernel__ is the software at the core od an operation system, with complete controle (the entire system)

__host machine__ an original machine's kernel


>==the Docker Engine==
>consists of:
>	- the Docker server (a lot of features),
>	- an API (to run these features),
>	- command line interface (to interacte with these feature)

__server/the Docker deamon__ 
	- background processes on an operationg system
	- it runs within the kernel of the host machine
	- it listens for requests from the user
	- it is like a construction team on the host machine

the Docker deamon has a book of blueprints (how to create various docker related object like containers) <- this is __API__


__Docker container Environments__
- the processes of one container canot affect the processes of another
- a container has limits on resource usage, like the CPU and memory
- application-specific code

---
## Images

Docker containers are created by objects in Docker called images

>==docker images==
>	- read-only templates with instructions for creating a DOcker container
>	- define the container code, libraries, environment variables, configuration files, and more...

a container is the instance or the result of executing image

>==Dockerfile==
>outlines (zarys, szkic, schemat) instructions for how an image will create a container

An image is like a class.
A container is like an instance of this class.

---
## A Ubuntu container

`docker search ubuntu`

to more information about commands:
		`docker commane --help`
		`docker create --help`


pull an image, create a container
`docker create --name=foo -it ubuntu bash`

__to start this container__
`docker start container_name`
`docker start foo`
and
`docker container ls` -> info that this container is running


to connect a standard input/output stream to this running container:
`docker attach container_name`
`docker attach foo`

```cmd
C:\Users\jstrzelecki>docker attach foo
root@952f170b080e:/
```

ESCAPE SEQUENCE
					==ctr+p + q==
-> the container is still running but stream is on the host machine

To install ping
`apt-get install uputils-ping`

`ping google.com`


__To see what was done with this container__:
`docker logs container_name`
`docker logs foo` -> all about ping


__to stop the running container__
`docker stop container_name`
`docker stop foo`

__to remove the stopped container__
`docker rm foo`
or
to stop and remove
`docker rm -f foo`

---

### DOCKER RUN
pull+create + start
`docker run --name=bar -it ubuntu bash`

---

__to see cached images__
`docker image ls`


