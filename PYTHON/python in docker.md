

# Python in docker
#python  #docker 

`docker pull python`

for a single file:
```bash 
docker run -it --rm /
           --name my-running-script /
           -v "$PWD":/usr/src/myapp /
           -w /usr/src/myapp python:3/
            python your-daemon-or-script.py
```

```


for a Python project `Dockerfile`
```Dockerfile 
FROM python:3

WORKDIR /usr/src/app

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD [ "python", "./your-daemon-or-script.py" ]
```
`
and then:
`docker build -t my-python-app .`
`docker run -it --rm --name my-running-app my-python-app`






