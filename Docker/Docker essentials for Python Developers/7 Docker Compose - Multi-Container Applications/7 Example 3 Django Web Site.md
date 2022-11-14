[[7 - Intro Docker Compose]]



[[7 Example 1 TensorFlow & TensorBoard]]
[[7 Example 2 Microservice & SQL Database]]


---
# Django Web Site

![[Docker Django Web Site Deploymentexcalidraw | 700]]

## NGINX
- It's Web, Proxy Sever & Load Balancer
- configuration:
	- main `/etc/nginx/nginx.config`
	- site `/etc/nginx/conf.d/`
- Copy or Bind Mount site configuration `mysite.conf` to `/etc/nginx/conf.d/mysite.conf`
- Copy or Bind Mount static HTML files to `/user/share/nginx/html/`



## PostgreSQL
-data stored in `/var/lib/postgresql/data`
`POSTGRES_USER`
`POSTGRES_PASSWORD`
`POSTGRES_DB`

## YAML
```yml
version: "3.7"

volumes:
  db_vol:

networks:
  frontend: # Front end Virtual Network for 'proxy', 'app1' and 'app2' Containers
  backend: # Back end Virtual Network for 'app1', 'app2', 'db' and 'pgadmin' Containers

services:

  db: # DB Engine Container
    image: postgres:12
    volumes:
      - db_vol:/var/lib/postgresql/data # Mount Volume to Postgres Data directory
    environment:
      POSTGRES_USER: "bkuser"
      POSTGRES_PASSWORD: "bkpass"
      POSTGRES_DB: "bookmarks"
    networks:
      - backend
    command: postgres -c log_destination=stderr -c log_statement=all
    restart: always

  pgadmin: # PGAdmin Container - PostgreSQL GUI Admin
    image: dpage/pgadmin4
    ports:
      - "8080:80"
    environment:
      PGADMIN_DEFAULT_EMAIL: "admin@example.com"
      PGADMIN_DEFAULT_PASSWORD: "my_secret"
    networks:
      - backend

  app1: # Bookmarks Django Application Server Container number 1
    image: mydjango:psql
    build:
      context: .
      dockerfile: Dockerfile
    networks:
      - frontend
      - backend
    restart: always

  app2: # Bookmarks Django Application Server Container number 2
    image: mydjango:psql
    build:
      context: .
      dockerfile: Dockerfile
    networks:
      - frontend
      - backend
    restart: always

  proxy: # NGINX Proxy Server Container
    image: nginx:stable
    volumes:
      - ./bookmarks_nginx.conf:/etc/nginx/conf.d/bookmarks_nginx.conf
    ports:
      - "8000:8000"
    networks:
      - frontend
    depends_on:
      - app1
      - app2
    restart: always

```



