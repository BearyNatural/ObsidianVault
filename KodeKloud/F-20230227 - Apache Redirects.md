The Nautilus devops team got some requirements related to some Apache config changes. They need to setup some redirects for some URLs. There might be some more changes need to be done. Below you can find more details regarding that:
1.  `httpd` is already installed on `app server 3`. Configure Apache to listen on port `6100`.    
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

%% had issues solving this one, and on a previous job I had to install epel-release prior to httpd or I couldn't sucessfully finish the job; had many issues with the terminal freezing and so would get halfway through the job and have to refresh :/ very frustrating, will copy paste from here to the terminal to make it quicker %% [--this made no difference therefore this is not an issue
yum install epel-release -y 
yum install httpd -y ]

%% now we follow the job request %%
find /etc -type f -name '.conf' | grep http
cat /etc/httpd/conf/httpd.conf | grep -i listen
vi /etc/httpd/conf/httpd.conf
	/listen 
	Listen 8080 [6100]
vi /etc/httpd/conf.d/main.conf [create this file and enter the following:]
	<VirtualHost*:6100>
	ServerName stapp03.stratos.xfusioncorp.com
	Redirect 301 / http://www.stapp03.stratos.xfusioncorp.com:6100/
	</VirtualHost>
	<VirtualHost*:6100>
	ServerName www.stapp03.stratos.xfusioncorp.com:6100/blog/ 
	Redirect 302 /blog/ http://www.stapp03.stratos.xfusioncorp.com:6100/news/
	</VirtualHost>
systemctl restart httpd [error]
systemctl status httpd [httpd: Syntax error on line 353 of /etc/httpd/conf/httpd.conf: Syntax error on line 4 of...alHost>]
vi /etc/httpd/conf/httpd.conf
	:set nu
	esc 353 shift+g [353 IncludeOptional conf.d/.conf] comment out the line
	:wq


--Given up on this activity as I have no idea why the service is having issues with line 353.  I have tried to comment it out and I fail as there is no redirect, I have tried hardcoding the main.conf in there however I can't get the service working.  I have choosen to skip this activity as I can't find anyone else who is having the same issue as me :'( therefore I am doing something incorrect