#docker #mysql #phpmyadmin 

## docker mysql

#docker/mysql

```console
$ docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
```
`docker run --name mysql_node --net mysql_node_network -p 8081:8080 -e MYSQL_ROOT_PASSWORD=secret -d mysql`


`docker exec -it mysql_node bash`
or in windows
`winpty docker exec -it mysql_node bash`
->
`mysql -u root -p` -> write down a password secret 


## docker phpmyadmin
#docker/phpmyadmin
If we want to access the MySQL container using phpMyAdmin, we need the host IP address and running port.
but
phpMyAdmin runs as a container, so we have to use the Docker Network

**create a new docker network**
`docker create network networkName`
attach the container to this network using `-net` option

`docker network ls` -lists avalable networks

`docker network create mysql-network`

1. ==create a new mysql container attached to the network:==
```bash
docker run -d \
-p 8081:8080 \
-e MYSQL_ROOT_PASSWORD=secret \
--name mysql_node\
--net mysql_node_network \
--v mysql_node_vol:/var/lib/mysql \
mysql
```
a host port: 8081
a container port: 8080
`-e` the environment variable

2. ==create PHPMyAdmin Container==
```bash
docker run -d -p 8082:80 \  
-e PMA_HOST=mysql_node \  
--name phpmyadmin \  
--net mysql_node_network  \  
phpmyadmin:5.1-apache
```
- phpMyAdmin runs on port 80 and is mapped to a 8082 host port ; so we can access to phpmyadmin using the 8082 port
- **PMA_HOST** :
	- is  a mandatory environment variable
	- its values is our mysql container name
	- in general it is  an IP address and port (localhost:3306)

	==so phpMyAdmin on `localhost:8082`==

---
wersja skrócona
```bash
# run mysql in the default network
docker run -d -p 3307:3306 -e MYSQL_ROOT_PASSWORD=secret --name mysqldb mysql

# run and link phpmyadmin
docker run --name myadmin -d --link mysqldb:db -p 8080:80 phpmyadmin

```



---