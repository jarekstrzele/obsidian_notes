[[_ intro Python Docker]]

[[6 - Creating Container Images]]

[[6 Docker Build Command]]

----
# FROM instruction

`FROM python`
`FROM python:3.8`
`FROM localhost:5001/mypython:3-slim`

- one argument - Base Image name, interpreted by Docker Engine at Build Host
- Name reference muyst render expected Base Image (python version, libraries, etx)


## ARG instruction
`ARG base=python`
`ARG tag=3`
`FROM $base:$tag`

this command override :
`docker build -t myinage:3.9 --build-arg tag=3.9 .`


after `FROM` you have to repeat `ARG`

```dockerfile
ARG base=pytho
ARG tag=3
FROM $base:$tag

ARG base
ARG tag
LABEL baseimage=$base:$tag
ENV BASE_IMAGE=$base:$tag
RUN echo $base:$tag > /tmp/base_img

LABEL maintainer=kirs@oo.ee
WORKDIR app
COPY ./app .
RUN pip install -r requirements.txt
ENV FlASK_ENV development
EXPOSE 5000
CMD ["python", "color_boxes.py"]



```


