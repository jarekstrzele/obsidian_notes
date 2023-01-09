#plurasight  #poulton_nigel  #docker #kubernetes #beginner 



----
# Docker and Kubernetes - The Big Picture

#docker/container 

## What are containers? Primer
1. Older time: one server <-> one app
2. old time: one server <-> many virtual apps (MV, many virtual OS) consume many resources (hardware + software)
3. now -> CONTAINERS: one server <-> many apps (but one OS)


---
## Docker
### *Docker, Inc.* is a company.
the Company before *dotCloud* 
**docker   worker** -> docker  


### Docker is a IT technology.
> **Containers** are like fast lightweight virtual machines.
> **Docker** makes running our apps inside of containers really easy

#### Community Edition (CE)
- Open source
- lots of contributors
- quick release cycle

#### Enterprise Edition (EE)
- slower release cycle
- additional features
- official support

#### Containerizing Apps
Run and manage apps inside of containers

You are in folder with your app files. `docker image build -t name:number .` (build an image out of all of the files in this directory and below)
(image is  like a stopped container )

`docker push name_of_image` -> containerized app send to DockerHub

to run this app:
`docker container run -d -name name -p port:port name_of_image`


-----------
## Kubernetes
### History
Came from Goole (Borg > Omega > K8s)
To day:  Cloud Native computing Foundation
"Kubernetes" -> "Helsman"

### The Short & Skinny
**Docker** provides the low-level mechanics for staring and stoppinf indivudual containers.
**Kubernetes** doesn't care about low-level stuff, it cares about higher-level stuff: scheduling, scaling, healing, updating, ... (how many containers to trun in, ...)


--------------
## Prepering to Thrive in a Container World

### Individual preparedness
- in cloud (beware of cost): docker, k8s
- locally: docker k8s

Get your hands dirty!

### organization preparedness


----------
## Suitable Workloads
### Suitable Workloads
From 2018 Docker and K8s are stateless and stateful.

==stateful== :
- has to remember stuff

==stateless==
- doesn't remember stuff

Some apps can be migrated directly to containers!!

--------
## Enterprise and Production Readiness

### Docker
dotCloud > Docker
CE - Community Edition
EE - Enterprise Edition


### Kubernetes

#### Types:
==Is HUGE!!!==
- **Alpha**
	- not for production
	- off by default
	- early code
	- uncerain future
- **Beta**
	- on by default
	- becomming stable
	- promisibg future
	- some details may change
- **GA**
	- Production ready
	- solid future
	- stable


#### Where:
**On Premises**


**Cloud**:
- Hosted (canned) options:
	- AWS EKS (Elastic Kubernetes Service)
	- Azure AKS (Azure Kubernetes Service)
	- Giigke GKE (Google Kubernetes Engine)


### Ecosystem
Data, Loggin, Monitoring, Networking, ...


## A Word on Orchestration
#orchestration 
analogy: 
- players -> they play like a team, if they are organized, they are ORCHESTRATED
- a coat is orchestrating everyone

SCALE MAKES THINGS VERY COMPLEX!!

Apps comprise:
- mutiple parts (sevices)
- multiple requirements







