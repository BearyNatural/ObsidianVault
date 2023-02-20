![[M17 1.png]]

1. Install a FTP server that offers anonymous file download.  Ensure that this server is accessible from other machines
2. Answers: https://www.hostinger.com/tutorials/how-to-setup-ftp-server-on-ubuntu-vps/
	1. apt install vsftpd [should already be installed]
	2. cp /etc/vsftpd.conf{,.bak} [back up your conf file]
	3. ufw status [enable if not active as it controls firewall rules and once active will list all rules here]
		1. ufw app list [lists all applications already allowed]
			1. ufw allow OpenSSH [allows all ssh]
			2. ufw allow 20/tcp [ports 20 & 21 are ftp traffic]
			3. ufw allow 21/tcp
			4. ufw allow 990/tcp [TLS uses this port]
			5. ufw allow 40000:50000/tcp [range of passive ports, conf yet to be set]
		2. ufw status [view all the rules]
	4. create user directory
		1. useradd -m hosting
		2. mkdir -p /home/hosting/ftp
		3. chown nobody:nogroup /home/hosting/ftp
		4. chmod -w /home/hosting/ftp
		5. ll /home/hosting/ftp
		6. mkdir /home/hosting/ftp/files
		7. chown hosting:hosting /home/hosting/ftp/files
		8. echo 'vsftpd sample file' > /home/hosting/ftp/files/sample.txt
	5. Configure vsftpd
		1. vi /etc/vsftpd.conf [verify the following is uncommented, otherwise add it]
			1. #Allow ananymous FTP? (Disabled by default). 
				1. anonymous_enable=NO 
			2. #Uncomment this to allow local users to log in. 
				1. local_enable=YES
				2. write_enable=YES
				3. chroot_local_user=YES
			3. user_sub_token=$USER local_root=/home/$USER/ftp
			4. pasv_min_port=40000 pasv_max_port=50000
			5. userlist_enable=YES userlist_file=/etc/vsftpd.userlist userlist_deny=NO
		2. echo 'hosting' >> /etc/vsftpd.userlist
			1. cat /etc/vsftpd.userlist
		3. systemctl restart vsftpd
		4. systemctl status vsftpd
		5. lftp localhost [may need to install this]
			1. ls 
			2. cd /pub [can see the files there]
			3. get file99 [messing around]


