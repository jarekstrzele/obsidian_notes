**permission denied** - solved:  
`sudo groupadd docker  `
`sudo usermod -aG docker $USER ` 

 [https://hub.docker.com/](https://hub.docker.com/ "https://hub.docker.com/")   

to start container again:  
#docker/container
`docker start -i containerID` (in interactive mode)  

`docker-compose build`
`docker-compose up`


---
w windowsie błąd, to skasuj
According to Docker failed to initialize 1.3k I resolved this issue by:

C:\Users[USER]\AppData\Local\Docker
C:\Users[USER]\AppData\Roaming\Docker
C:\Users[USER]\AppData\Roaming\Docker Desktop

Once deleted, I didn’t have to do anything else, Docker Desktop started booting up as normal.

----

Po prostu spróbuj wskazać serwer WWW na właściwy adres IP kontenera. Możesz uzyskać IP kontenera za pomocą tego polecenia

docker inspect `<container-uid> | grep IPAddress`.

----

#docker/run 
`docker container run`:
- `d` run in the background
- `--name=<container-name`
- `p` map port fromhost to container
- `-e` set Environment variable
- `-v` mount volume/direcotry image-name[:image-tag]











