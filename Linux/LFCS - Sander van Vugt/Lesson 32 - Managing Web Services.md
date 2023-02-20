![[M16 1.png]]

1. Install a web server.  After connecting to the web server, a client should see the message "welcome to my server"
2. Answer:
	1. apt install curl elinks
	2. vi /var/www/html/index.html [default document root]
		1. welcome to my webserver
	1. systemctl restart apache2 
	2. curl http://localhost [shows the welcome to my webserver] 