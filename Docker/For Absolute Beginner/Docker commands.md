[[_ Intro Docker Mumshad]]

---
por.
[[4 - Docker containers Basics]]
[[5 - Running Docker Containers]]
[[6 - Creating Container Images]]


---
# Docker commands


## Container
### run  
#docker/run
por. [[5 Run  (and stop and create and remove) interactive container]]

`docker run nginx`  

### name container
aby nazwać contener po swojemy  
`$ docker run --name blue-app -e APP_COLOR=blue -p 38282:8080 kodekloud/simple-webapp  `


### run attach and detach
a attach mode: a terminal stops
`docker run kodekloud/simple-webapp`

a detach mode:  a container is running in the background mode  
`docker run -d kodekloud/simple-webapp`  

---
## list containers
### `ps` - list containers  
`docker ps  `
`docker ps -a  `

### `stop`  
`docker stop containerID | containerName`

### `rm` - remove a container  
`docker rm containerID | containerName  `

---

## Image
#docker/image 

### list images  
`docker images  `

### `rmi` - remove images  
`docker rmi imageID | imageName`

### `pull` - only pull a image from dockerHub  
`docker pull nginx  `

A container "lives" when does some tasks, when it is finished, then it stops itself.!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  

## others commands
==Append a command==      
e.g. Start a container ubuntu and sleep for 5 seconds  
Execute a command when we run the container!  
`docker run ubuntu sleep 5  `
  
==EXECUTING== a command on a running container!  
e.g. to see the contents of a file inside the particular container  
`docker exec nervous_spence cat /etc/release  `
  
```bash
$ docker run centos  
$ docker run -it centos bash  
[root@648c6fb58f7b /]# cat /etc/*release*  
```

==uchomienie contenera nginx i nazwanie go webapp==
`docker run -d --name webapp nginx:1.14-alpine`

---