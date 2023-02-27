![[M21.png]]

- Configure Postfix so that it can receive messages from other servers in your network
- Answers:
	- cd /etc/postfix
		- ls
	- vi main.cf
		- /inet_interfaces [search]
			- inet_interfaces = all [uncomment this line]
			- inet_protocols = all [comment this line out and replace with the following:]
			- inet_protocals = ipv4
		- /mynetwork
			- mynetworks = 192.168.4.0/24 [new line to be entered;  use your cidr range not the cidr range given]
		- /mydestination
			- mydestination = [$]myhostname, localhost.$mydomain, localhost, $mydomain [make sure this line is uncommented and comment out any others] 