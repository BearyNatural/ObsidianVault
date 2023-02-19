![[M17 1.png]]

1. Install a FTP server that offers anonymous file download.  Ensure that this server is accessible from other machines
2. Answers:
	1. apt install vsftpd [should already be installed]
	2. systemctl enable vsftpd
	3. systemctl status vsftpd
	4. lftp localhost
		1. ls 
		2. cd /pub [can see the files there]
		3. get file99 [messing around]
	5. ufw [if you need to add any firewall rules]