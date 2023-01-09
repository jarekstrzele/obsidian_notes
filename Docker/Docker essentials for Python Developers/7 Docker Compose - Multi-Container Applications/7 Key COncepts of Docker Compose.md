[[7 - Intro Docker Compose]]


---
# Key Concepts of Docker Compose
#docker_compose

- Multi-container application deployment on stand-alone docker host
- `docker-compose` command
- `docker-compose.yml` file
- desired state of application deployment:
	- services
	- networks
	- volumes
- docker Sqarm extends these conceptrs to Multi-Node Docker Clusters

"service" menas in this context the same as "container"

![[Docker Compose Application Model.excalidraw | 700]]

Networks:
- Unique IP Address Ranges
- No Explicit routing between Compose Networks
- Access to Internet through DockerHost External Network
- Service Discovery via DNS Names 


## Docker Compose Desired State
- desired states is a formalized **Declaration** or description **of Apllication State** after deployment
- describes how application deployment must look like:
	- what components must be created
	- what attributes and values each component must have
- desired state is not a procedure (it is declarative programming not imperative)

Swarm
Kubernetes Service




