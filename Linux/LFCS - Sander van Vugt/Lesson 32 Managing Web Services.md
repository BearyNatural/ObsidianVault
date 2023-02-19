![[M16 1.png]]

1. Install a web server.  After connecting to the web server, a client should see the message "welcome to my server"
2. Answer:
	1. apt install curl elinks [elinks won't install on ec2]
	2. vi index.html
		1. welcome to my webserver
	3. systemctl restart apache2 
	4. curl http://localhost [shows the welcome to my webserver]
	5. 