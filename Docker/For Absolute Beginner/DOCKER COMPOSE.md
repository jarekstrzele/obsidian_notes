[[_ Intro Docker Mumshad]]

[[DOCKER IMAGE]]

# DOCKER COMPOSE
#docker_compose 
In the Docker-compose we could create a configuration file in YAML format and put together different services and the options specific to this to running them in this file 



_Voting application_

Python-Container  (voting-app)      -> to vote
Redis (in-memory DB                     -> to send vote ?
.Net     (worker)                               -> to compute
Postgres   (database)                     -> to save data
NodeJS (result-app)                       -> to display result in the percentage


Without the docker-compose
```bash
docker run -d --name=redis redis # naming container is important

docker run -d --name=db  postgres
docker run -d --name=vote -p 5000:80 voting-app
docker run -d --name=result -p 5001:80 resutl-app
docker run -d --name=worker worker
# Now we have running containers but they are not linked

```

l i n k is a command line option which can be used to link two containers
e.g. voting app is dependent of the redis app
#docker/link
```bash
# in the Python file '.. host=redis'        host:container
docker run -d --name=vote -p 5000:80 --link redis:redis voting-app

# in the redis file '...postrgres://postgres@db/postgres'
docker run -d --name=result -p 5001:80 --link db:db resutl-app

# in the worker file '.. connectToRedis("redis")...connectToDB("db")
docker run -d --name=worker --link db:db --link redis:redis worker

```

## DOCKER_COMPOSE.YML
```bash
redis:
  image: redis
db:
 image: postgres:9.4
vote:
 image: voting-app
 ports:
  - 5000:80

 links:
  - redis   

result:
 image: result-app
 ports:
  - 5001:80

 links:
  -db

worker: 
 image: worker
 links:
  - redis
  - db
```
images are already built so you can write:
`docker-compose up`







