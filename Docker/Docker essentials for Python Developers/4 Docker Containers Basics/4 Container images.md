[[_ intro Python Docker]]

---
[[4 Development & Production Enviroments]]
[[4 DockerHub]]

---

# Container Images

>==container== is a binary blob which has all information is necessary for a container runtime
 to create and run a container

container consists of:
- metadata
- filesystem 


In a container there are:
- application source code
- libraries & modules
- operation system utilities & files
- python interpreter & pip



## Image Build Process
- some images are base images (e.i. -> `debian:buster`),
- `python:3.8` = `debian:buster` + `install Python` 
- `flask-app:v1.0` = `debian:buster` + `install Python`  + `add source code pip flask`
- `flask-app:v1.1` = `debian:buster` + `install Python`  + `add source code pip flask` + `overwrite config files`


The actual image file system is composed of several layers related to history of image creation



### image name
consists of:
				`<registry>/<repository>:<tag>`
python:3.8
	repo: python
	tag: 3.9

d4py/myflask:v0.1
docker.io/d4y/myflask:v0.1

`:lastest` a special tag - default tag	

---

# Building own images

## Why we build Custom Images?
- simplify & shorten Deployment
- create self-contained, ready to run Container Tamplates
- Extend Official Image with:
	- our Python Source Code, Configuration and Data
	- extra Python Libraries
	- Additional Software Packages
- Set customized Start-up Command or script


## Image Build Process Overview
- Prepare Image Filesystem:
	- Base image
	- Install Required System Packages
	- Install Libraries
	- Copy Source, Configuration and Data Files
	- Execute Initialization Commands
- Define Metadata:
	- Working Directory
	- Environment Variables
	- Start-up Command
	- Mount Points
	- ...

## Ways and Tools
- manual image creation - `docker commit`
- Docker Build - `docker build`
	- automated container image build
	- dockerfile script
	- temporary containers at build phase
	- strictly non-interactive commands
	- build context
```dockerfile
FROM <base image>
WORKDIR <directory path>
COPY <build folder files> <destination path>
RUN <software & libraries installation>
VOLUME <mount point>
EXPOSE <container port>
ENTRYPOINT <start-up command>
CMD <start-up agruments&options>

```
- alternative tools:
	- Buildah
	- Orca
	- Kaniko
- CI/CD Tools:
	- GitHub/Docker Hub intergration
	- GitLab CI/CD Pipelines
	- ...






































