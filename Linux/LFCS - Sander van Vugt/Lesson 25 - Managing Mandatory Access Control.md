![[M9.png]]

1. Install an Apache webserver, and configure it to use the directory /web as the DocumentRoot.
2. Modify you Mandatory Access Cotrol to allow this non-default configuration
3. Answers: - AppArmor is ubuntu base [apparmor can be called using aa-command i.e.  aa-status]
	1. to enable
		1. systemctl enable apparmor [active & enabled]
	2. application profiles are available:
		1. /etc/apparmor.d/
		3. /sys/kernel/security/apparmor 
	3. others
		1. aa-status [all currently loaded profiles]
		2. aa-genprof [to create a profile]
4. Install and use apache web server
	1. copy the .conf file to your new directory /web
		1. cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/mynewsite.conf [it can also safely go in /mynewsite folder under sites-available]
			1. vi /web/mynewsite.conf [edit the following]
				1. ServerAdmin webmaster@localhost [change to your email address]
				2. VirtualHost * :80 [this is the listening port;  if you change this you have to change /etc/apache2/ports.conf to reflect the same change]
				3. DocumentRoot /var/www/html [for this example we want to change it to /web; this is where apache2 looks for the files that make up the site.]
				4. ServerName www.example.com [this is commented out, you want to uncomment it and change it to your domain name]
			2. a2ensite mynewsite [this enables the new virtual host using the a2ensite utility]
			3. systemctl restart apache2 [restart it so that apache2 will reflect the changes made]
	2. https://ubuntu.com/server/docs/web-servers-apache [see the website for further options and instructions]