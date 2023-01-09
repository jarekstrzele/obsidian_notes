

# SSH
https://phoenixnap.com/kb/what-is-ssh

##### SSH -> Secure SHell
- it utilizes a client-server paradigm (client and server communicate via a secure channel)
- has three layers:
	- **the transport layer**  
		- ensures secure communication between the server and the client
		- monitors data encyption/decryption
		- protects the integrity of the connection
		- perform data caching and compression
	- **the authentication layer**
	- **the connection layer** manages communication channels after the authentication
	- the channel created by SSH uses **public-key** cryptography to authenticate the client


It was created by Tatu Ylonen



## How to use SHH?
`ssh [username]@[server_ip_or_hostname]`
