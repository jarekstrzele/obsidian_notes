[[_ Wprowadzenie docker]]

# 
```bash
$ docker version (Show the Docker version information)

$ docker info (Display system-wide information)

```

OLD COMMAND VERSION
`docker <command> {option}`
`docker run`


NEW VERSION
`docker <management-command> <sub-command> {option}`
`docker container run`

-----------
# Uruchamianie

`docker container run --publish 8080:80 nginx`
----> in the browser `localhost:8080`
	- pobranie obrazu `nginx` z *registry* Docker Hub
	- utworzenie nowego kontenera na podstawie pobranego obrazu
	- przekierowanie ruchu z portu 80 kontenera na port 8080 hosta

### uruchamianie kontenera w tle `--detach`
` docker container run --publish 8080:80 -detach nginx`

```bash
jarek@jarek-legion:~$ sudo docker container run --publish 8080:80 -detach nginx
834bcb7ebd1ad2fee33be5c4f9dec5e6284896e441a9b2798ba6b1220a464a3d
jarek@jarek-legion:~$ sudo docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS              PORTS                                   NAMES
834bcb7ebd1a   nginx     "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8080->80/tcp, :::8080->80/tcp   naughty_dubinsky

```








