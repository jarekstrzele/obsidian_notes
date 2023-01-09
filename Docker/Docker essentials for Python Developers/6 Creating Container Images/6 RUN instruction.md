[[_ intro Python Docker]]

[[6 - Creating Container Images]]


----
# RUN instruction
`RUN shell command line`
- executes Shell Command Line in Temporary Container running with current state of Image Filesystem
- Only ono-interactive Commands!!
- No backgroundprocesses
- Default Shell is `/bin/sh` must exist in Image Filesystem


We use `run` to install some Python libraries:
```Dockerfile
RUN pip install -r requirements.txt
RUN pip instal django==2.2.6
RUN conda install -y pands
RUN python manage.py collectstatic
RUN iseradd kris && chown -R kris /app > /tmp/logfile
```

```Dockerfile
FROM python:3
LABEL maintainer kris@dd.net
WORKDIR /app
COPY ./app .
RUN pip install -r requirements.txt

# install Debian Linuxx System packages
RUN DEBIAN_FRONTEND=noninteractive\
	apt-get update && \
	apt-get upgradte -y && \
	apt-get install -y --no-installrecommends htop && \
	apt-get -y autoremove && \
	apte-get clean && \
	rm -rf /var/lib/apt/lists/ * /tmp/* /var/tmp/*
	
	
ENV FLASK_ENV development
EXPOSE 5000
CMD ["python", "color_boxes.py"]

```

in the terminal:
```bash
docker build -t cd:run -f Dockerfile .
```








