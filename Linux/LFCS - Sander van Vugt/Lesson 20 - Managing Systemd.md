![[M4.png]]

1. Configure the httpd service such that while loading it, it will also load the vsftpd service
	1. which http [verify that the services required are installed]
		1. for ubuntu, the package httpd is a virtual package provided by nginx-core or apache2;
			1. which nginx
				1. /usr/sbin/nginx
			2. which apache2
				1. /usr/sbin/apache2
	2. which vsftpd
		1. /usr/sbin/vsftpd
	3. systemctl disable --now vsftpd [we need it to be clean]
		1. systemctl status vsftpd [shows it is inactive & disabled]
	4. systemctl status
		1. apache2 [this has failed]
		2. nginx [this is running still, stop the service]
			1. systemctl stop nginx
	5. ps aux | grep [ensure no lingering processes are still there]
		1. apache2
		2. nginx
		3. vsftp
	6. systemctl edit apache2 or nginx [add the following lines]
		1. [Unit]
		2. Requires=vsftpd.service
		3. # system uses nano will need to use ctrl+s to save & ctrl+e to exit
	7. systemctl restart apache2 or nginx
		1. systemctl status apache2 or nginx
		2. systemctl status vsftpd
	8. both should now be running