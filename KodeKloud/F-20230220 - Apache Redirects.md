The Nautilus devops team got some requirements related to some Apache config changes. They need to setup some redirects for some URLs. There might be some more changes need to be done. Below you can find more details regarding that:

1.  `httpd` is already installed on `app server 2`. Configure Apache to listen on port `5001`.
2.  Configure Apache to add some redirects as mentioned below:
		a.) Redirect `http://stapp02.stratos.xfusioncorp.com:<Port>/` to `http://www.stapp02.stratos.xfusioncorp.com:<Port>/` i.e `non www` to `www`. This must be a permanent redirect i.e `301`
        b.) Redirect `http://www.stapp02.stratos.xfusioncorp.com:<Port>/blog/` to `http://www.stapp02.stratos.xfusioncorp.com:<Port>/news/`. This must be a temporary redirect i.e `302`.

stapp02
172.16.238.11
stapp02.stratos.xfusioncorp.com
steve
Am3ric@
Nautilus App 2

%% ssh into stapp02 %% Am3ric@
ssh steve@stapp02
sudo -i

route -n [not found, tried to install; no route package found :O]
find /etc | grep apache2 [whoops use to ubuntu]
find /etc | grep httpd
cat /etc/httpd/conf/httpd.conf | grep -i listen
[# Listen: Allows you to bind Apache to specific IP addresses and/or
#Change this to Listen on specific IP addresses as shown below to 
#Listen 12.34.56.78:80
Listen 8080]
vi /etc/httpd/conf/httpd.conf
Listen 8080 [change to 5001]
/redirect [
#Customizable error responses come in three flavors:
#1) plain text 2) local redirects 3) external redirects
] make a main.conf 
vi /etc/httpd/conf.d/main.conf
</VirtualHost*:5001>
ServerName stapp02.stratos.xfusioncorp.com
Redirect 301 / http://www.stapp02.stratos.xfusioncorp.com:5001/
Redirect 302 /blog/ http://www.stapp02.stratos.xfusioncorp.com:5001/news/
cat /etc/httpd/conf.d/main.conf
systemctl restart httpd
Job for httpd.service failed because the control process exited with error code. See "systemctl status httpd.service" and "journalctl -xe" for details.

https://www.ionos.com/digitalguide/server/configuration/apache-redirects/
%% changes to main.conf %%
Redirect 301 http://stapp02.stratos.xfusioncorp.com:8080/ http://www.stapp02.stratos.xfusioncorp.com:5001/
Redirect 302 http://www.stapp02.stratos.xfusioncorp.com:8080/blog/ http://www.stapp02.stratos.xfusioncorp.com:5001/news/
systemctl restart httpd
systemctl status httpd
%%  httpd: Syntax error on line 354 of /etc/httpd/conf/httpd.conf: Syntax error on line  %%
vi /etc/httpd/conf/httpd.conf
:set nu
354 shift+g


FAILED DUE TO INCOMPLETE WEBSITE :'(
- service 'httpd' is not running on App Server 2

![[Pasted image 20230227230052.png]]

curl http://stapp02.stratos.xfusioncorp.com:5001/
curl http://www.stapp02.stratos.xfusioncorp.com:5001/blog/




