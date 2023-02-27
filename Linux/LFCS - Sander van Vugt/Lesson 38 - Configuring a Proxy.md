![[M22.png]]

- Configure a Squid Proxy server such that access to all sites in the rehat.com domain is denied.
- Configure your browser to verify its working
- Answers:
	- cd /etc/squid/
	- vi squid.conf
		- acl blockedsite url_regex ^http://.*.oracle.com/.*$ [replace oracle with redhat]
		- acl blockedsite url_regex ^https://.*.oracle.com/.*$ [replace oracle with redhat]
		- http_access deny !Safe_ports
		- http_access deny blockedsite
	- systemctl restart squid
	- ensure you have proxy configuration set correctly on your web browser i.e. chrome, firefox, etc
		- HTTP Proxy: 127.0.0.1 Port 3128;
	- then go to http://www.redhat.com/ [url courld not be retrieved error page - access denied - which proves that squid is doing what is has been configured to do]