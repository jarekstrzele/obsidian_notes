#plurasight  #docker  #wahlin_dan

Docker for web developers: https://app.pluralsight.com/library/courses/docker-web-development/table-of-contents


------------
# Building and Running your first docker app

[[#Create an App Image]]
[[#Run an app container]]
[[#Comminicate between multple containers]]

To ship applications user is very usefull

==the Case for docker==:
- accelerate developer onboarding
- eliminate app conflicts
- envirenment consistency
- ship shoftware faste

==docker image==
- define the contents that are needed to run a container
- a read-only tamplate composed of layered filesystems used to share common files and create Docker container instances

==docker container==
- runs your application
- an isolated and secured shipping container created from an image that can be runm startedm stoppted, moved and deleted

Docker Desktop:
- provides image and container tools
- Win (Use the WSL2 based engine) and Mac use a hypervisor

Linux can run Docker Engine


## Create an App Image
#dockerfile 
code --> Compiler --> binary
Docker works similarly
>[!dockerfile]
>It is a text document that contains all the commands a user could call on the command line to assemble an image

Dockerfile ---> `docker build` ---> Docker image

### Dockerfile as a layered cake
> 
> Think of Dockerfile as a layered cake (a layered file system).
> Each layer is a different instruction, that's how Dockerfiles work
> 

`FROM ...` the most basic layer (e.g. `FROM node:alpine`)
`LABEL ...` metadata about the Dockerfile (e.g. `LABEL author="John Dow"`)
`ENV ...`  define environment vars (e.g. `ENV NODE_ENV=production`)
`WORKDIR /var/www`  from now you will be at this folder
`COPY [from/source] [to/target]` (copy conf files or set files or code or ...) (e.g. `COPY . .`  all from a current folder to the working directory)
`RUN ...` to run diff commands (`RUN npm install`)
`EXPOSE 3000` the container will be listening on 3000 port
`ENTRYPOINT ["node", "server.js"]` what's the first command that we're going to run to start this up (we will start `node server.js`)
https://docs.docker.com/engine

### Create a Custom app Dockerfile

in the main path of the project create a file `node.dockerfile` without any extention

`.dockerignore`
#### Dockerfile
`node.dockerfile`:
```dockerfile

FROM     node:alpine

LABEL   author="Dan Wahlin"

ENV     NODE_ENV=production
ENV     PORT=3002

WORKDIR /var/www

COPY package.json package-lock.json ./ 
RUN npm install

COPY  . ./

EXPOSE $PORT 

ENTRYPOINT  ["npm", "start"]

```


### Using `docker build`

`docker build -t <name> .`
`-t` short for `--tag`
`.` build context (where is the `Dockerfile`? In the current folder)

`docker -t nodeapp .`

==Docker Registries==:
- internal registry
- Docker Hub
- Amazon ECR
- Azure Container Registry
- Google Container Registry
- ...
`docker build -t <registry>/<name>:<tag> .`

`<registry>` docker registry name 
`<name>` image name
`<tag>` a version of the image

`docker build -t danwahlin/nodeapp:1.0 .`

#docker/image 
`docker images` list docker images
`docker rmi <imageId>` remove an image

from the course
`docker build -t nodeapp .` by default docker will be seaching a `Dockerfile`
If your docker file has different name, use this command  `$ docker build -t nodeapp -f node.dockerfile .`

### Deploy an app image to a Registry
a registry can be local or remote (e.g. DockerHub)
###### `docker push <user name>/<image name>:<tag>`

`docker login` (remember about cli-token)

### VS Code Extension
*docker* (by Microsoft)
- curson on the `Dockerfile`, right mouse button>build image
- syntax help
- run/remove/... a container from an image


## Run an app container
### `run`
`docker pull <imageName>`

`docker run -p <externalPort>:<internalPort> <imageName> `

`docker pull nginx:alpine`

```shell
$ docker run -p 8080:80 -d nginx:alpine
eced202b1e1ec598e55d175b7972883aa1fa20a72ce4d8d59dc41db2a0816a1f
$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                   NAMES
eced202b1e1e   nginx:alpine   "/docker-entrypoint.…"   28 seconds ago   Up 27 seconds   0.0.0.0:8080->80/tcp, :::8080->80/tcp   vibrant_chaplygin

```



### `log`



### volume





## Comminicate between multple containers





