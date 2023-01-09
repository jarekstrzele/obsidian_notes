[[_ Intro Docker Mumshad]]
 
---
[[Volume mapping]]
[[Docker commands]]
[[Tag]]

---
# Docker run  
#docker/run 

por. [[5 - Running Docker Containers]]

T A G  (to chose a version of an image)  

`docker run redis:4.0`  tag redis:4.0  

S T D I N  
`docker run -i` kodeloud/simple-prompt-docker  
`-i` interactive mode**  

`docker run -it`  kodeloud/simple-prompt-docker  
`-it` interactive mode + terminal****  
 

uruchamiam kontener server, więc jak się z nim komunikować :  
- Running on [http://0.0.0.0:5000](http://0.0.0.0:5000 "http://0.0.0.0:5000/")  
      wiem, że jest na porcie 5000, ale jakie IP?  

- every docker container gets an IP assigned by default (this is an internal IP and is only accessible within the docker host  
    
- __I can map__:    
- `docker run -p 80:5000 kodeloud/simple-webapp`

