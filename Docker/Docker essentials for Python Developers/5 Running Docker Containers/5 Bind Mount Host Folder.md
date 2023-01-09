[[_ intro Python Docker]]
[[4 - Docker containers Basics]]
[[5 - Running Docker Containers]]


---

# Bind Mount Host Folder
#docker/bind

`docker run -it -v ${PWD}:/app python:3 bash`

- use `-v` to declare __Bind Mount of Host Folder__ to Container directory (MOunt Point)
- Enable Disk SHaring in Docker Desktop Settings
- Use `-v` several times for multile bind mounts
- Mount Point is automatically created, if necessary (also if the folder doesn't exist in host machin, this folder will be created by docker)
- Bind Mounting to non-empty COntainer Directory hides original files and subdirectories


`-v HOST_folder : CONTAINER_folder'
`-v Source Path :  Mount Point'

\*)  Add `:ro` at the end to enable read-only Mount


__Source Path/ Host Folder__:
- must  be an absolute path
- use ${PWD} as current folder shorthand (`-v ${PWD}/subfolder: /app`)
(in Windows, the source path must start with drive letter `-v C:\...`)

---

## Alternative option `--mount`
takes a list of argument
`docker run -it --mount type=bind, source=${PWD}, destination=/app python:$ bash`



















