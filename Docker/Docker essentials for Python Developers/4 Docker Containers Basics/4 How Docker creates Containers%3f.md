[[_ intro Python Docker]]
[[4 - Docker containers Basics]]

---
[[4 DockerHub]]
[[4 Container images]]

next:
[[4 Immutable Containers Principle]]

---
# How Docker creates Containers


`docker run`:
	- `docker create`
		- filesystem - info from Local Image Cache (Unique FileSystem Object)
		- this filesystem is created with metadata 
		- there are no processes yet
		- more control atttributes are created (e.i. port mapping)
	- `docker start`
		- allocated IP Address
		- execute start-up commands in the container (i.e. shell scripts)
		- the container runs as long as the first process exists, you can rerun this container
		- `--rm` remove the container when the first process stops


---

## Image Lifecycle

![[docker image lifecycle.excalidraw|700]]


---

## Container Lifecycle
![[Container Lifecycle.excalidraw|700]]


==stopped== is like a create (new IP, new ...)

`--force` remove conainter  in any states












