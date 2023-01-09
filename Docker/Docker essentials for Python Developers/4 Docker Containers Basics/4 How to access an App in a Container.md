[[_ intro Python Docker]]
[[4 - Docker containers Basics]]
[[4 How containers Communicate]]

---


# How to access an App in a Container?

## a text base app
```bash
docker run -it --rm python:3 bash
: python
>>
>>...
>>exit()
: exit

```

## a network service application
==port mapping==


It is implemant some sort of network service 
> apps implementing  small, well-defined network services -- ==microservices==


1. container to container (the same host machine)
	1. you can have a lot of microservices in runtime
	2. containers can "talk" to each other using their ip addresses
a network service app listens on a port - it waits for requests or data send to the container IP

> containers are designed to be shortly vived and temporary
 
2. local app on host machine to container
3. a network client external  to host machine accessing to local container 

![[container_comunication.excalidraw|600]]



## Graphical Application in Container
on linux (windows X) works great
on Windows, Mc OS you need to install X server software on host machine

On linux
```bash
docker run -it --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -v ${PWD}:/app python3 bash`
```






















