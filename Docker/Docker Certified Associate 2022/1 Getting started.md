#udemy 
#Zeal_Vora


> **DOCKER** is an open platform, once we build a docker container, we can run it anywhere, say it windows, linux, mac whether on laptop, data center or in clould
> 

If follows the **build once, run anywhere** approach.

---
`docker pull nginx`
`docker run -p 8080:80 -dt nginx`
`docker ps`
`127.0.01:8080`

Windows: Docker Desktop

In this course:
- Ubuntu
- Digital Ocean as a cloud provider

```bash
docker info
```


# Images vs Containers
#docker/container 
#docker/image


>**docker image** is a file which contains all the necessary dependency and configurations which are required to run an application

```bash
docker images

nginx   latest   c316d5a335a5  4 weeks ago    142MB
```

>**docker container** is bascally a running instance an image

to run a container:
```bash
docker run -dt -p 80:80 nginx

docker ps
docker ps -a
```
// id: 30b11e528876

to stop the container:
```py
docker stop 30b11e528876
```

to start again:
```bash
docker start 30b11e528876
```

---

# Container identification
## UUID 
When you creat a Docker container, it is assigned a universally unique identifier

## Docker names
Docker alsow allows us to supply container names.
We can specify our own name to the container by adding `--name=meaningful_name` argument during  docker `run`  command.

`docker run --name my_nix -dt -p 800:80 nginx`

```bash
docker stop my_nix
docker start my_nix
docker start containerId
docker stop containerId
```

---

# Port Binding
By default Docker containers can make connections to the outside world, but the outside world cannot connect to containers.

If you want to containers to accept incoming connection from the world, you will have to __bind__ it to  a host port.

>PORTS
 0.0.0.0:80 -> 80/tcp
 (host)        -> (container)


`docker inspect containerName`:
```
...
       "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "c480abc0c6390e958c2014d7a0f4428dd5b54d4c875d2984a9a5c1b9305339d3",
                    "EndpointID": "bc8683a66899464007111b1973e9f2f12c9283714b70aa81a2b2e225023e12dd",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
```

`"IPAddress": "172.17.0.2",` is a container private IPAddress

We have to bind it to the host
`-p (a host port) : (a container port)`
`-p 8000:80`


---
# Attach and Detached mode























