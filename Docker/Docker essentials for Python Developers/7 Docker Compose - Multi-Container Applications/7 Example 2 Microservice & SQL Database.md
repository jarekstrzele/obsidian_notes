[[7 - Intro Docker Compose]]

[[7 Example 1 TensorFlow & TensorBoard]]
[[7 Example 3 Django Web Site]]

---
# Microservice & SQL Database


![[Docker Microservice +SQL DBexcalidraw | 700]]


## MariaDB SQL
- open source clone of MySQL
- it has its official image at Docker Hub
- Data stored in `/var/lib/mysql`
- `MYSQL_ROOT_PASSWORD` mandatory!!
- `MYSQL_USER`
- `MYSQL_PASSWORD`
- `MYSQL_DATABASE`

section-7/color-boxes

```yml
version: "3.7"

volumes:
  db_vol:  # database persitent volume -uses default driver and settings

services:

  cb:
    image: cb:mysql
    build:
     context: .
     dockerfile: Dockerfile
     args:
       tag: "3.8"

    ports:
      - "5000:5000"
    environment:
      DATABASE_URL: "mysql+mysqldb://cbuser:cbpass@db:3306/cbdb"
    depends_on:
      - db
    restart: always

  db:
      image: mariadb:10.4
      volumes:
        -db_vol:/var/lib/mysql
      environment:
        MYSQL_ROOT: "my_secret"
		MYSQL_USER: "cbuser"
...
```


1. docker-compose build
2. docker-compose up -d

MariaDB needs some seconds to start up

3. `docker-compose down -v` (`-v` volume will be reomved too)
so
first:
	`docker-compose up -d db`
Wait untill "mysql: ready for connections" in `logs`
then
	`docker-compose up -d cb`

next
`docker-compose up -d phpmyadmin`
on `localhost:8080`





