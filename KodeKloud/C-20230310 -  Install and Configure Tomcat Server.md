The `Nautilus` application development team recently finished the beta version of one of their Java-based applications, which they are planning to deploy on one of the app servers in `Stratos DC`. After an internal team meeting, they have decided to use the `tomcat` application server. Based on the requirements mentioned below complete the task:
a. Install `tomcat` server on `App Server 2` using `yum`.
b. Configure it to run on port `3003`.
c. There is a `ROOT.war` file on `Jump host` at location `/tmp`. Deploy it on this tomcat server and make sure the webpage works directly on base URL i.e without specifying any sub-directory anything like this `http://URL/ROOT` .

stapp02
172.16.238.11
stapp02.stratos.xfusioncorp.com
steve
Am3ric@
Nautilus App 2

%% ssh to stapp02 %% Am3ric@
ssh steve@stapp02
sudo -i

yum install tomcat -y
systemctl enable tomcat
systemctl start tomcat
systemctl status tomcat  [shows active and running]

yum install net-tools -y
netstat -lnp | grep tomcat [
[root@stapp02 ~]# netstat -lnp | grep tomcat
[root@stapp02 ~]# netstat -lnp | grep listen
[root@stapp02 ~]# netstat -lnp | grep -i tomcat
[root@stapp02 ~]# netstat -lnp | grep -i listen
tcp        0      0 127.0.0.11:33539        0.0.0.0:*               LISTEN      -                   
tcp        0      0 127.0.0.1:8005          0.0.0.0:*               LISTEN      962/java            
tcp        0      0 0.0.0.0:8009            0.0.0.0:*               LISTEN      962/java            
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      962/java            
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      372/sshd            
tcp6       0      0 :::22                   :::*                    LISTEN      372/sshd            
unix  2      [ ACC ]     STREAM     LISTENING     118897673 1/init               /run/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     118897676 1/init               /run/systemd/journal/stdout
unix  2      [ ACC ]     SEQPACKET  LISTENING     118876898 1/init               /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     118875963 1/init               /run/dbus/system_bus_socket
]

%% found the ROOT.war file! %%
ll /tmp [no root.war :O]
exit [back to jump_host]
ll /tmp [
-rw-r--r-- 1 root root 4529 Mar  9 23:11 ROOT.war]
scp /tmp/ROOT.war steve@stapp02:/tmp

%% back to stapp02 %%
ssh steve@stapp02
sudo -i
find /etc -type f | grep tomcat 
vi /etc/tomcat/tomcat.conf [no server or listening port listed]
find / -type f | grep tomcat | grep server [
/etc/tomcat/server.xml
/usr/libexec/tomcat/server]
vi /etc/tomcat/server.xml
-   Define a non-SSL HTTP/1.1 Connector on port 8080
- -->
- Connector port="3003" protocol="HTTP/1.1" [change 8080 to 3003]

find / -type d | grep tomcat | grep web 2>/dev/null [
/var/lib/tomcat/webapps]
cp /tmp/ROOT.war /var/lib/tomcat/webapps
ll /var/lib/tomcat/webapps [
drwxr-xr-x 4 tomcat tomcat 4096 Mar 10 00:16 ROOT
-rw-r--r-- 1 root   root   4529 Mar 10 00:15 ROOT.war]


systemctl restart tomcat
systemctl status tomcat [shows active and running]
curl -i http://stapp02:3003 [
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Accept-Ranges: bytes
ETag: W/"471-1580289830000"
Last-Modified: Wed, 29 Jan 2020 09:23:50 GMT
Content-Type: text/html
Content-Length: 471
Date: Fri, 10 Mar 2023 00:20:12 GMT

<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <title>SampleWebApp</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <h2>Welcome to xFusionCorp Industries!</h2>
        <br>
    
    </body>
</html>
]
