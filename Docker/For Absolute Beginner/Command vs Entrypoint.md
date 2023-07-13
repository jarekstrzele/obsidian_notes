[[_ Intro Docker Mumshad]]

[[DOCKER IMAGE]]

---
# Command  vs   Entrypoint

Containers run to aim a specific tasks. When the task is completed container stops.

CMD ["command that will be start when a container will start running"]
CMD["mysql"] 

but

CMD["bash"] - bash is not a process; it is a shell that listens for inputs from a terminal; if it cannot find a terminal it exits

`docker run ubuntu sleep 5`  'sleep 5' override  CMD["bash"]

You can write new Dockerfile
```dockerfile
FROM Ubuntu
# shell form  CMD command param1
CMD sleep5          
# or
# JSON array format CMD["command", "param1"]
# error CMD["sleep 5"] !!!!!
# CMD ["sleep", "5"]  

```
and now build image and run container:
`docker build -t ubuntu-sleeper .`
`docker run ubuntu-sleeper`
I would like to change a number of seconds:
`docker run ubuntu-sleeper sleep 10`,
but it will be better: docker run ubuntu-sleeper 10   --> ENTRYPOINT

```dockerfile
FROM Ubuntu

ENTRYPOINT["sleep"]
# default value of sleep: 
CMD["5"]  
```

`docker inspect image_name`
