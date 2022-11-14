[[5 - Running Docker Containers]]

[[5 overview of Docker Commands]]

---
[[5 Port Mapping]]
[[5 Start a Container]]


# RUN interactive container
#docker/run


`docker run -it python:3 bash`

#docker/flag_-it
- use `it` for `--interactive --tty` option to create an INTERACTIVE CONTAINER
- interactive container is attached to current terminal window
- best way to run text-based, interactive sessions with containerized applications
- great for apps which may require input of Passwords or Secrets

#docker/flag_--rm 
__flag__ `--rm` 
- tells the Docker Deamon to clean up the container and remove the file system after the container exists
- tells docker that the container should automatically be removed after we close docker

## Stopped state
- container is stopped, when interactive session ends
- type ==exit== at Shell Prompt ot press `Contro-C` to end the interactive session
- ==disconnect== from interactive container with `Control-p` then `Control-q`
- ==recontect== to interactive conainer with `docker attach <container_name>`
- 
---
## TO STOP
`docker container stop <container>`
`docker stop <container>`

`docker kill` stop the container immediatly (send a SIGKILL)

`-t 15` defines grace period in seconds, default is 10


--------------
## Create Container without Starting
`docker container create`
`docker create ...`

> Container can be started later with [[5 Start a Container | `docker start`]]
> 

(the same options and atgs as for [[5 Run container in background | `docker run`]])

Start-up COmmand IS NOT executed

----

# Remove a Container
[[5 Pull, rename, list, delete, inspect the image#List and delete images | look at a image case]]


`docker container rm [f] <container>`
`docker rm [-f] <container>`
`docker container prune`

- Use `rm` command to delete a stopped container
- container filesystem is permanentrly deleted
- use `-f` option to force delete, a running container is killed and deleted
- use `prune` command to delete all stopped containers











