![[L16 1.png]]

1. Find the file on your Linux distribution where errors related to authentication are written to
	1. cat /etc/rsyslog.conf [we care about what is under rules, which is apparently elsewhere file says default logging rules can be found in /etc/rsyslog.d/50-default.conf]
		1. cat /etc/rsyslog.d/50-default.conf
			1. /var/log/auth.log [this is the main one] 
			2. /var/log/syslog 