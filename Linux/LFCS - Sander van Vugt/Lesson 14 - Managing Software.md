![[L14 1.png]]

1. Request a list of all packages installed on your server.  In this list, see if an FTP server has been installed
	1. apt list
	2. apt list | grep ftp
2. Use the software manager on your server to install nmap [can't on ec2]
	1. he suggested lftp instead
	2. apt install lftp -y