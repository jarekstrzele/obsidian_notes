[[_ intro Python Docker]]
[[5 - Running Docker Containers]]

---
# Run aContainr with custom Start-up Command

`docker run  [option] image new_cmd`
`docker run [option] --entrypoint new_entry image new_cmd`

- start-up command = entrypoint +cmd
- use `--entrypoint` option to override Entrypoint as well


```bash
$ docker inspect d4py/mydjango:0.1
...
,
            "Cmd": [
                "uwsgi",
                "bookmarks_uwsgi.ini"
            ],
...},
            "WorkingDir": "/app",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": null

// if you write down docker run -it django bash
// ,cmd will be bash not uwsgi

```















