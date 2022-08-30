[[_ intro Python Docker]]

[[6 - Creating Container Images]]

---
talend API TESTER - plugin to chrome

---
# Docker Build Command
#docker/build
Automated Imaged Creation with Dockerfile

`docker build -t <name:tag>  [-f <Dockerfile>] <build_context>`

- `-t` sets name and tag of Final Image
- `build_context` is a FOlder Path, where all Files and FOlder used by Docker Build reside
- `-f` provifdes non-standard Dockerfile name, path must be in Build Context folder. Default name is `<build_context>/Dockerfile`

## Build Context
- directory or folder, where dockerfile and all files and subfolders required to Build and Image reside
- COPY and ADD dockerfile Instructions source files are taken only from Build Context, which is a root folder of source paths
- files and/or subfolders may be excluded from Build Context, if listed in `.dockerignore` file:
`**/__pycache__` ignore all `__pycache__` from a folder and folders
`.git` ignore a folder `.git`


## example
`docker build -t mydjango:0.1 .`

- final image name - `mydjango:0.1`
- build context - `.` (dot: current working folder)
- Dockerfile - `./Dockerfile` (default)





