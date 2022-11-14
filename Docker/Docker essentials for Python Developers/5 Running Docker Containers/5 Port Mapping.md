[[5 - Running Docker Containers]]
[[5 Run  (and stop and create and remove) interactive container]]

---

# Port Mapping
#docker/map 

> port mapping must be defined when the container is creating
> 

`docker run -it -p 8080:80 -p 8443:4333 nginx'

- `-p`  `--publish` to declare Port Mapping
- Use `-p` multple times for several Port Mappings
- Use `-P` to publish all COntainer Ports declared in Image Metadata to random Host Ports from upper range

`docker port <container_nam>` shows Port Mappings

>==Port Mapping must be declared at COntainer creation!==


>>`-p  HOST_PORT : CONTAINER_PORT`





