[[_ intro Python Docker]]
[[5 - Running Docker Containers]]

---
[[5 Run  (and stop and create and remove) interactive container]]

# Start a Container
#docker/start

`docker container start <container>`
`docker start <container>`

- starts Created or Stopped Container
- new MAIN PROCESS is created to execute Start-up Command
- Use `-a` option to attach to Container STDOUT/STDERR
- use `-i` option to attach to Container STDIN
```bash
$ docker start -ai created
Python 3.10.4 (main, Apr 20 2022, 18:21:23) [GCC 10.2.1 20210110] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```







