We have a requirement where we want to password protect a directory in the Apache web server document root. We want to password protect `http://<website-url>:<apache_port>/protected` URL as per the following requirements (you can use any `website-url` for it like `localhost` since there are no such specific requirements as of now). Setup the same on `App server 3` as per below mentioned requirements:
a. We want to use basic authentication.
b. We do not want to use `htpasswd` file based authentication. Instead, we want to use `PAM` authentication, i.e `Basic Auth + PAM` so that we can authenticate with a Linux user.
c. We already have a user `ravi` with password `dCV3szSGNA` which you need to provide access to.
d. You can access the website using `APP` button on the top bar.

stapp03
172.16.238.12
stapp03.stratos.xfusioncorp.com
banner
BigGr33n
Nautilus App 3

%% ssh into stapp03 %% BigGr33n
ssh banner@stapp03
sudo -i

%% authentication for PAM %% https://osc.github.io/ood-documentation/latest/authentication/pam.html https://www.server-world.info/en/note?os=CentOS_7&p=httpd&f=10
yum install epel-release -y
yum install pwauth -y
yum install mod_authnz_external -y

find /etc -type f -name -"*.conf" | grep auth [*]
vi /etc/httpd/conf.d/authnz_external.conf
- add 1st line & uncomment the following lines:
	- <Directory /var/www/html/protected>
		- AuthType Basic
		- AuthName "PAM Authentication"
		- AuthBasic Provider external
		- AuthExternal pwauth
		- require valid-user
	- </Directory>



mkdir -p /var/www/html/protected/
vi /var/www/html/protected/index.html
- add the following:
	- # create a test page


<html>
<body>
<div style="width: 100%; font-size: 40px; font-weight: bold; text-align: center;">
Test Page for PAM Auth
</div>
</body>
</html>

systemctl status httpd
systemctl start httpd

id ravi [uid=1001(ravi) gid=1001(ravi) groups=1001(ravi)]

netstat -lnp | grep httpd [tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      1002/httpd  ]

curl -u ravi:dCV3szSGNA http://localhost:8080/protected
[<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://localhost:8080/protected/">here</a>.</p>
</body></html>]

completed [still unsure as to what it meant by access the 'app' button ???]