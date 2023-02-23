We are working on hardening Apache web server on all app servers. As a part of this process we want to add some of the Apache response headers for security purpose. We are testing the settings one by one on all app servers. As per details mentioned below enable these headers for Apache:

1.  Install `httpd` package on `App Server 2` using yum and configure it to run on `8085` port, make sure to start its service.    
2.  Create an `index.html` file under Apache's default document root i.e `/var/www/html` and add below given content in it.    
    `Welcome to the xFusionCorp Industries!`    
3.  Configure Apache to enable below mentioned headers:    
    `X-XSS-Protection` header with value `1; mode=block`    
    `X-Frame-Options` header with value `SAMEORIGIN`    
    `X-Content-Type-Options` header with value `nosniff` 
`Note:` You can test using curl on the given app server as LBR URL will not work for this task.

stapp02
172.16.238.11
stapp03.stratos.xfusioncorp.com
steve
Am3ric@
Nautilus App 2

%% ssh into stapp02 %% Am3ric@
ssh steve@stapp02 
sudo -i
yum install httpd -y
yum install net-tools -y
systemctl status httpd
systemctl start httpd
netstat -lnp | grep http [tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      845/httpd]
ll /var/www/html/
echo 'Welcome to the xFusionCorp Industries!' > /var/www/html/index.html
cat /var/www/html/index.html [Welcome to the xFusionCorp Industries!]
find /etc/ -type f -name '.conf' | grep apache
find /etc/ -type f -name '.conf' | grep httpd
vi /etc/httpd/conf/httpd.conf
	/isten [change Listen 80 to 8085]
/etc/httpd/conf.d [for further config files conf.modules.d/.conf]
	:$
	#added the following into for headers:
	Header set X-XSS-Protection "1:mod=block"
	Header always append X-Frame-Options SAMEORIGIN
	Header set X-Content-Type_options nosniff
confirm it with cat /etc/httpd/conf/httpd.conf | tail -n 5
systemctl restart httpd
curl http://localhost:8085
curl -i http://localhost:8085



