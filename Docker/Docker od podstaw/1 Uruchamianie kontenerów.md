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




