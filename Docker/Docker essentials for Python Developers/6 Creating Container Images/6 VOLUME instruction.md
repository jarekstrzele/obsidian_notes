t[[_ intro Python Docker]]

[[6 - Creating Container Images]]

---

# Volume instruction
#docker/volume

`VOLUME /mount/point`

- Declares Mount Point ar directory specified as an argument
- Directory is created, if necessary
- Why declare Mount Points?
	- Data Persistency - Volumes are independent of Containers
	- High Performance - Container Filesystem is slower

## VOLUME initialization with image data
```dockerfile
...
RUN mkdir /data
RUN echo text > /data/before.txt
VOLUME /data
RUN echo text > dataafter.txt
...
```


## mounting Volumes
`docker volume create data`
`docker run -v data:/data..` /before.txt

- data stored in Image is copied onto a new Volume __only at first mount__ during Container creation
- any Volume is initialized just once

Data stored in Image is NOT COPIED to a folder Bind Mounted to Mount Point
`docker run -v ${PWD}:/data`


`docker un [--rm] ...`
#docker/flag_--rm 

- if a container is created without explicit Volume Mount (or Bind Mount) to a declared Mount Point, Docker Engine creates unnamed VOlume and mounts it to Mount Point
- unnamed Volume is initialized with Data in an Image at first mount
- this volume exists after container removal, unless container is created with `--rm`. Volume is also removed in this case


---
## Docker Volume Management
`docker volume ls`
`docker volume create <name>`
`docker volume rm <name-or-id>`


---
example
```dockerfile
...
# set SQLIte3 DB file path
ENV DATABASE_URL "sqlite:////data/boxes_db.sqlite3"


# declare Mount Point
VOLUME /data
...
```



