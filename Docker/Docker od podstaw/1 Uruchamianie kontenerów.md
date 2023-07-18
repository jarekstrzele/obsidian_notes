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

## zatrzymanie kontenera `docker container stop`

`$ docker container stop 834`

zatrzymanie != usuwanie
```bash
$ sudo docker container ls -a
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                          PORTS     NAMES
834bcb7ebd1a   nginx         "/docker-entrypoint.…"   5 minutes ago    Exited (0) About a minute ago             naughty_dubinsky
5f321aa42b33   nginx         "/docker-entrypoint.…"   15 minutes ago   Exited (0) 12 minutes ago                 trusting_goldberg
6c304c0b1cc3   hello-world   "/hello"                 4 days ago       Exited (0) 4 days ago                     boring_wright

```

można ponownie uruchomić kontener `container start`
```bash
jarek@jarek-legion:~$ sudo docker container start 6c3
6c3
jarek@jarek-legion:~$ sudo docker container start 5f3
5f3
```

nadanie nazwy:
`docker container run --publish 8080:80 --detach --name=mynginx nginx`

usuwanie
`$ sudo docker container rm 5f32`
`docker container rm <nazwa>`
`-f` usuwanie włączonego kontenera 

```bash
$ docker container --help

Usage:  docker container COMMAND

Manage containers

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new co ...
```

`top  Display the running processes of a container`

----
# wiele kontenerów

## elasticsearch
Elasticsearch to silnik wyszukiwania oparty na bibliotece Lucene.
> Elasticsearch zapewnia rozproszony, wieloklientowy silnik wyszukiwania pełnotekstowego z interfejsem HTTP i dokumentami w formacie JSON bez schematu.

`docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -d docker.elastic.co/elasticsearch/elasticsearch:6.5.4`

sprawdzenie logów
`docker container logs <container_id> -f`

```bash
$ curl localhost:9200
{
  "name" : "BAyiEbB",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "cWNEeCUnSraVoeV55LIHxA",
  "version" : {
    "number" : "6.5.4",
    "build_flavor" : "default",
    "build_type" : "tar",
    "build_hash" : "d2ef93d",
    "build_date" : "2018-12-17T21:17:40.758843Z",
    "build_snapshot" : false,
    "lucene_version" : "7.5.0",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}

```


`$ curl -H "Content-Type: application/json" -XPOST "http://localhost:9200/docker/image/1" -d "{ \"name\" : \"elasticsearch\"}"`

*"Content-Type: application/json"* nagłówek żądania HTTP (dane przesyłane w treści żądania są w formacie JSON)

*-XPOST* żądanie będzie wysłane metoda POST

*"http://localhost:9200/docker/image/1"* wysyłane żądanie do lokalnego serwera do indeksu "docker"




