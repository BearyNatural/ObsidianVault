During a recent security audit, the application security team of `xFusionCorp Industries` found security issues with the Apache web server on `Nautilus App Server 1` server in `Stratos DC`. They have listed several security issues that need to be fixed on this server. Please apply the security settings below:
a. On `Nautilus App Server 1` it was identified that the Apache web server is exposing the version number. Ensure this server has the appropriate settings to hide the version number of the Apache web server.
b. There is a website hosted under `/var/www/html/news` on `App Server 1`. It was detected that the directory `/news` lists all of its contents while browsing the URL. Disable the directory browser listing in Apache config.
c. Also make sure to restart the Apache service after making the changes.

stapp01
172.16.238.10
stapp01.stratos.xfusioncorp.com
tony
Ir0nM@n
Nautilus App 1

%% ssh to stapp01 %% Ir0nM@n
ssh tony@stapp01
sudo -i

%% find config file %% https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/deploying_different_types_of_servers/setting-apache-http-server_deploying-different-types-of-servers
find /etc -type f -name '*.conf' | grep http
vi /etc/httpd/conf/httpd.conf
	go to end of document:
		ServerTokens Prod
		ServerSignature Off
		find the line: Options Indexes FollowSymLinks [remove Indexes word]

%% restart webserver %%
systemctl restart httpd
systemctl status httpd

%% check the webserver %%
netstat -lnp | grep httpd [tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      653/httpd  ]
curl -I http://stapp01:8080
curl -I http://stapp01:8080/news



