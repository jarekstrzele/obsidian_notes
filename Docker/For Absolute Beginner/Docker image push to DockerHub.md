[[_ Intro Docker Mumshad]]

[[DOCKER IMAGE]]

---
# HOW TO PUSH IT TO DOCKER HUB?

by default 'push' is into 'library' in dockerhub and I have no permission.
I have to change a tag of the image
`docker build . -t usernameOfDockerHub/my-simple-webapp`
next  -> log in
docker login
Username:
Password: 

`docker push my-simple-webapp`
to see
`$ docker run python:3.6 cat /etc/*release*`
```bash
PRETTY_NAME="Debian GNU/Linux 11 (bullseye)"
NAME="Debian GNU/Linux"
VERSION_ID="11"
VERSION="11 (bullseye)"
VERSION_CODENAME=bullseye
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
$
```

można odchudzić python przez zbudowanie go na alpine (FROM python:36-alpine ...) 
`docker build -t webapp-color:lite .` pamiętaj o kropce

