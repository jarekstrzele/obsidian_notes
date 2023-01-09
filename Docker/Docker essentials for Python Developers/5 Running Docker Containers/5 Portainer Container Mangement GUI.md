[[_ intro Python Docker]]
[[5 - Running Docker Containers]]

---

# Portainer Container Mangement GUI

https://www.portainer.io/

```bash
~$ docker volume create portainer_data
portainer_data
~$ docker run -d -p 8000:8000 -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
Unable to find image 'portainer/portainer:latest' locally
...

$ docker ps
CONTAINER ID   IMAGE                 COMMAND        CREATED          STATUS          PORTS                                                                                  NAMES
caacdbc3c1b4   portainer/portainer   "/portainer"   55 seconds ago   Up 54 seconds   0.0.0.0:8000->8000/tcp, :::8000->8000/tcp, 0.0.0.0:9000->9000/tcp, :::9000->9000/tcp   busy_mclean


```

the container is available: `http://localhost:9000/#/init/admin`

password: Filozofia2!@

localhost -> connect

