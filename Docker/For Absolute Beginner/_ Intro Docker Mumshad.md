[[Mumshad Mannambeth]]
#Mumshad_Mannambeth

https://billennium.udemy.com/user/mumshad-mannambeth/
#udemy 

---
[[DOCKER RUN]]
[[Volume mapping]]
[[Docker inspect]]
[[Tag]]
[[Docker commands]]
[[DOCKER IMAGE]]
[[DOCKER COMPOSE]]


---
# INTRO 
**containers**    
- completely isolated environments (own processes, services, network interfaces,...) that share the same OS  kernel  
- running instances of images that are isolated  
(por. [[4 - Docker containers Basics#Definition of Container]])


**image**   a package or a template   

**EDITIONS**
-   community      
-   enterprise


# JENKINS - web server  

`docker pull jenkins/jenkins`  
`docker run jenkins/jenkins`  

to find an IP :
`docker inspect container_Id` > Networks > IPAddress  
http://172.17.0.2:8080/  

password in terminal when you run this container  
d997e7cb36004268ad59fefa0704bb86  

but if you try to access to the server by your IP, it will be not possible --> you have to map IP  
#docker/map
`docker run -p 8080:8080 jenkins/jenkins`  
sprawdzanie własnego IP   
`linux ifconfig` 

podłączanie zewnętrznego folderu:  
`mkdir my-jenkins-data`
`docker run -p 8080:8080 -v /root/my-jenkins-data:/ver/jenkins_home -u root jenkins`  

---
