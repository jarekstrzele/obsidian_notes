[[_ Intro Docker Mumshad]]

---
# VOLUME   MAPPING  
#docker/volume 
docker > run > stop > rm  --> all data will be deleted  

`docker run -v /opt/datadir:/var/lib/mysql mysql`  
__volumne in docker host__: /opt/datadir  
__folder in mysql__:      /var/lib/mysql  

`docker run -v /opt/datadir:/var/lib/mysql mysql`  

it will implicitly mount the external directory to a folder inside the docker container  

__if I delete a docker container, data will be safe !!!!__

