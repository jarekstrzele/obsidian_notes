

----
# MongoDB installation

DOCKER
`$ docker run --name some-mongo -d mongo:tag`

`docker run --name mymongo -p 27017:27017 -d mongo`

to run MongoDB Shell:
`docker exec -it mymongo mongosh`


----

https://www.mongodb.com/docs/manual/installation/

- `http mongodb> resource > server > installation` choose *Community Edition*
- and install `mongosh` - mongodb shell
- mongdb extension in VS Code


------------
## docker
### Mongo
- Obraz `mongo` to oficjalny obraz Docker zawierający serwer MongoDB. Pozwala na uruchomienie instancji bazy danych MongoDB w kontenerze.
##### `docker run -d -p 27017:27017 --name moja-baza-danych mongo`

##### `docker ps` pokaże aktualnie działające kontenery

#### uruchomienie konsolowego interfejsu do komunikacji z `mongodb`
##### `docker exec -it moja-baza-danych mongosh`

> Ponowne uruchomienie kontenera już istniejącego:
>   1. `docker start <container_id>`
>   2. `docker exec -it <container_id> mongosh`



--------------
### Mongo-express
- Obraz `mongo-express` to narzędzie do zarządzania bazą danych MongoDB za pomocą interfejsu graficznego. Pozwala na przeglądanie, dodawanie, usuwanie i edytowanie danych w bazie MongoDB za pomocą przeglądarki internetowej.
##### `docker run -d -p 8081:8081 --link moja-baza-danych:mongo mongo-express`
> wyjaśnienie: `moja-baza-danych:mongo`
> wewnątrz kontenera `mongo-express`  kontener `moja-baza-danych` będzie dostępny za pomocą aliasu `mongo` (kontener `mongo-express`  potrzebuje tego aliasu, aby łatwo się komunikować z bazą)


> - obraz `mongo` dostarcza silnik bazy danych MongoDB, natomiast 
> - obraz `mongo-express` dostarcza interfejs użytkownika do zarządzania bazą danych MongoDB, wykorzystując dostęp do serwera MongoDB. 
> - 
> Oba obrazy mogą współpracować, co pozwala na skorzystanie z interfejsu graficznego do zarządzania bazą danych MongoDB uruchomioną w kontenerze `mongo`.


> ` docker logs <idkontenera>`
```
No custom config.js found, loading config.default.js
Welcome to mongo-express
------------------------


Mongo Express server listening at http://0.0.0.0:8081
Server is open to allow connections from anyone (0.0.0.0)
basicAuth credentials are "admin:pass", it is recommended you change this in your config.js!
```

###### `admin:pass`

---
## MongoDB Atlas
is a service offered by MongoDB Company

https://www.mongodb.com/

Cloud -> Atlas
https://www.mongodb.com/cloud/atlas/register
js100code@gmail.com

----
## GUI
### STUDIO 3T ROBOT 3T
https://studio3t.com/download-studio3t-free

### Compass MongoDB

### mogno-express in docker
docker








