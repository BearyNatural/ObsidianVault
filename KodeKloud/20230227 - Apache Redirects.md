The Nautilus devops team got some requirements related to some Apache config changes. They need to setup some redirects for some URLs. There might be some more changes need to be done. Below you can find more details regarding that:
1.  `httpd` is already installed on `app server 3`. Configure Apache to listen on port `8089`.    
2.  Configure Apache to add some redirects as mentioned below:    
    a.) Redirect `http://stapp03.stratos.xfusioncorp.com:<Port>/` to `http://www.stapp03.stratos.xfusioncorp.com:<Port>/` i.e `non www` to `www`. This must be a permanent redirect i.e `301` 
    b.) Redirect `http://www.stapp03.stratos.xfusioncorp.com:<Port>/blog/` to `http://www.stapp03.stratos.xfusioncorp.com:<Port>/news/`. This must be a temporary redirect i.e `302`.

stapp03
172.16.238.12
stapp03.stratos.xfusioncorp.com
banner
BigGr33n
Nautilus App 3

%% ssh into stapp03 %% BigGr33n
ssh banner@stapp03
sudo -i
find /etc -type f -name '.conf' | grep http
cat /etc/httpd/conf/httpd.conf | grep -i listen
vi /etc/httpd/conf/httpd.conf
	/listen 
	Listen 8080 [8089]
vi /etc/httpd/conf.d/main.conf [create this file and enter the following:]
	<VirtualHost*:8089>
	ServerName stapp03.stratos.xfusioncorp.com
	Redirect 301 http://stapp03.stratos.xfusioncorp.com:8089/ http://www.stapp03.stratos.xfusioncorp.com:8089/
	</VirtualHost>
	<VirtualHost*:8089>
	ServerName www.stapp03.stratos.xfusioncorp.com:8089/blog/ 
	Redirect 302 http://www.stapp03.stratos.xfusioncorp.com:/8089/blog/ http://www.stapp03.stratos.xfusioncorp.com:8089/news/
	</VirtualHost>
systemctl restart httpd [error]
systemctl status httpd [httpd: Syntax error on line 353 of /etc/httpd/conf/httpd.conf: Syntax error on line 4 of...alHost>]
vi /etc/httpd/conf/httpd.conf
	:set nu
	esc 353 shift+g [353 IncludeOptional conf.d/.conf] comment out the line
	:wq
systemctl restart httpd 
systemctl status httpd

curl http://stapp02.stratos.xfusioncorp.com:5001/
curl http://www.stapp02.stratos.xfusioncorp.com:5001/blog/
