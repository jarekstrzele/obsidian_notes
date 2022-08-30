[[_ intro Python Docker]]
[[5 - Running Docker Containers]]

---
# Environment Variables in Container
`docker run -e VAR=val [opts] image [cmd]`
`docker run -e VAR [opts] image [cmd]`
`docker run --env-file file image [cmd]`

- Image Metadat contains definition of Environment Variables for a new Container
- Variables can be added or overridden with `-e` option
- Use `--env-file` option to read Variables definitions from file in Docker Host

```bash
$ docker run --rm python:3 env
PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=916c8b68aa10
LANG=C.UTF-8
GPG_KEY=A035C8C19219BA821ECEA86B64E628F8D684696D
PYTHON_VERSION=3.10.4
PYTHON_PIP_VERSION=22.0.4
PYTHON_SETUPTOOLS_VERSION=58.1.0
PYTHON_GET_PIP_URL=https://github.com/pypa/get-pip/raw/38e54e5de07c66e875c11a1ebbdb938854625dd8/public/get-pip.py
PYTHON_GET_PIP_SHA256=e235c437e5c7d7524fbce3880ca39b917a73dc565e0c813465b7a7a329bb279a
HOME=/root

$ docker run --rm -e MY_VAR="my val" python:3 env
PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=42a29fda4ca0
MY_VAR=my val
...



```


```bash
// You have a file vars.env
$ more vars.env
VAR1 = v1
# Comment line
VAR2=v2
LANG=de_DE.UTF-8

$ docker run --rm --env-file vars.env python:3 env
docker: poorly formatted environment: variable 'VAR1 ' contains whitespaces.
See 'docker run --help'.

you have to change the file and now
$ docker run --rm --env-file vars.env python:3 env
PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=6752b37f253c
VAR1=v1
VAR2=v2
LANG=de_DE.UTF-8
GPG_KEY=A035C8C19219BA821ECEA86B64E628F8D684696D
PYTHON_VERSION=3.10.4
PYTHON_PIP_VERSION=22.0.4
PYTHON_SETUPTOOLS_VERSION=58.1.0
PYTHON_GET_PIP_URL=https://github.com/pypa/get-pip/raw/38e54e5de07c66e875c11a1ebbdb938854625dd8/public/get-pip.py
PYTHON_GET_PIP_SHA256=e235c437e5c7d7524fbce3880ca39b917a73dc565e0c813465b7a7a329bb279a
HOME=/root


```













