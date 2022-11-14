#databases  #mongodb  #udemy  #stashchuk_bogdan 

[[1 - Into MongoDB Cloud]]
[[2 - GUI Tools for MongoDB Management]]



----
# Start Master MongoDB
- DigitalOcean
- Hetzner
- GoDaddy
- Amazon AWS

----
## Amazon AWS
#aws

js100code@gmail.com
Filozofia2!@
https://us-east-1.console.aws.amazon.com/console/home?nc2=h_ct&region=us-east-1&src=header-signin#

on AWS:
	- Sevices > Compute > EC2 
	- create a new instance (launch instance)
	- choose Free tier eligible Ubuntu Server
	- then choose t2.micro type
	- create shh key
	- intance state: running 
	- connect to your instance (SSH client is in Mac, in WIndows use PuTTY by converting .pem( this file is private key file) to .ppk using PuTTyGen)
	- `chmod 400 ec2.pem`   

1. create Amazon EC2 server
2. installed Ubuntu on it
3. connected to it vis SSH
	1. when server is running click on "connect" button
	2. I am connected to the sever inside the browser but I can choose 'connect by [[SSH]] client'
	3. I chose [[SSH]] and there is a instruction 

### How to install MongoDB on this server

on `www.mongodb.com` download and you can choose mongo for the ubuntu that is running on your server

next: Package Manager > instructions for installing with `apt` (this is package manger)

to start `sudo service mongod start`
to verify: `mongo`
					and `show dbs`
exit: `exit`



### MongoDB network access
##### MongoDB will accept connection from a local computer
`ubuntu@ip-172-31-91-234:~$ ifconfig`
->
```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.91.234  netmask 255.255.240.0  broadcast 172.31.95.255
```

`mongo 172.31.91.234` -> error
because MongoShell accept only
by default server accept only localhost IP (`mongo 127.0.0.1` 0k , others error)

to see all address which mongo is listing to:
```shell
ubuntu@ip-172-31-91-234:~$ sudo netstat -plant |grep mongod
tcp  0 0 127.0.0.1:27017  0.0.0.0:* LISTEN 16146/mongod  
```

so
you have to edit `/etc/mongod.conf`
	inside there is`# network interfaces net: ... bindIp: .....
	if you want to bind mongodb service to all IP Addreses of the server just type `bindIp: 0.0.0.0`

restart mongod service:
`sudo service mongod restart`

now you can write
`mongo 172.31.91.234`

----
## Allow connections to the server itself

you need to open port 27017
In Amazon > EC2 Dashboard > the running instance > Security groups section > view inbound rules (by default only `22 port` is used (this is port of `SSH`))
so we need to modify this and add a new rule
(Edit inbound rules) > `Custome TCP port 27017` (source)`anywhere` (it's not secure but you can add only your IP)

----
## Create root
```mongod
db.createUser({
	user:"admin",
	pwd: "secret",
	roles:[
		{
			role:"root",
			db: "admin"	
		}
	]

})
```

1. Connect to your server vis SSH
2. open mongo shell `mongo`
3. `cls` clear mongo shell
4. switch to admin database
5. paste this script above
6. `show users`

After creatio of MongoDB admin user you need to enable authorization of the MongoDB server, so
you need to edit MongoDB configuration file, so 
1. exit MognoDB Shell
2. `vim /etc/mongod.conf`
	1. security section and uncomment this line `#security` -> `security`

```conf
security:
  authorization: enabled

```

now you have to restart mongodb
`sudo service mongod restart`

---
## Connect to MongoDB (AWS) from your computer
You have to install mongodb on your computer

`mongo "mongodb://<username>:<password>#hostname/database>"`
`mongo "mongodb://admin:secret@hostname/database>"`

hostname -> public DNS (connect>SSH)
`ec2-107-22-71-32.compute-1.amazonaws.com`

in   your computer terminal:
`mongo "mongodb://admin:secret@ec2-107-22-71-32.compute-1.amazonaws.com/admin>"`
you will connect your computer with remote mongodb server







