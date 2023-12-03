#udemy #Maximilian_Schwarzmuller 


[[2 Basic and CRUD]]




-----------
THe content of that note
[[#What is MongoDB?]]
[[#BSON data structure]]
[[#MongoDB Ecosytem]]
[[#Install on Window]]
[[#To install MongoDB Shell]]
[[#Drivers]]
[[#Working with MongoDB]]





----
# What is MongoDB?
- it is a database HUMONGOUS
- example:
	- database: *Shop*
	- collections: *Users*, *Orders*
	- documents: *{name: 'Max', age:29}*, *{name:'Max'}*
	- `BSON` format (*JSON* converted to a binary version)
```BSON
{
	"name":"Max",
	"age": 29,
	"address": 
	{
		"city":"Muchin"
	},
	"hobbies":[
		{"name":"Cokking"},
		{"name":"Sports"}
	]
}
```



# BSON data structure
- no schema
- no/few relations 

# MongoDB Ecosytem
- MongoDB Database
	- self-managed/enterprise
	- Altas (cloud)
	- Mobile
	- 
	- COmpasee
	- BI Connectors
	- MongoDB Charts

- Stitch
	- serverless Query API
	- Serverless Functions
	- database Triggers
	- Real-Time Sync


---------
# Install on Window
*Community Server*
https://www.mongodb.com/try/download/community

Custom installation 
- install as a service
- install Compass (GUI )

## TO STOP or START MongoDB:
- `Services`
- *cmd*: `net stop MongoDB`, `net start MongoDB`


## to start a terminal client
- path where your MongoDB is installed
- find `mongo.exe` or `mongosh.exe` -  it is the client (you will be connected to your server mongDB)
- 

# To install MongoDB Shell
#mongosh
It is a `mongosh`



# Drivers
- they are package you installed for the different programming languages your app might be written in
- they are bridges between your programming languages and the mongodb server


# Working with MongoDB


![[mongoDB_general_view.excalidraw | 700]]




