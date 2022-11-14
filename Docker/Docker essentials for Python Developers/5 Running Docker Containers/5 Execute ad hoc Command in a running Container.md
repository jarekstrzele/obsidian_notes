[[_ intro Python Docker]]

[[5 - Running Docker Containers]]




---
# 5 Execute ad hoc Command in a running Container
to execute a new process in the container
(for running or post? container) (no in production or stopped container)
`docker container exec <container> <command>`
`docker exec <container> <command>`

- `command` (binary or script) must exist in Container Filesystem and be in `$PATH`
- use `-it` for interactive commands
- use `-w/directory` to set Working Directory for the Command 
- Use `-e VAR=VALUE` to to set Environment Variable for the Command

```bash
$ docker run -d --name bookmarks -p 8000:8000 d4py/mydjango:0.1
93be6b3a3d465ce829f861b6e879b9dc246788344b9ca201deb055ef915647d5

~$ docker exec bookmarks pwd
/app

$ docker exec bookmarks python manage.py migrate
Operations to perform:

$ docker exec -it bookmarks python manage.py createsuperuser
Username (leave blank to use 'root'): admin

```


