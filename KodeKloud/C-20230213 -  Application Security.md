We have a backup management application UI hosted on `Nautilus's` backup server in `Stratos DC`. That backup management application code is deployed under Apache on the backup server itself, and Nginx is running as a reverse proxy on the same server. Apache and Nginx ports are `8085` and `8096`, respectively. We have iptables firewall installed on this server. Make the appropriate changes to fulfill the requirements mentioned below:

We want to open all incoming connections to Nginx's port and block all incoming connections to Apache's port. Also make sure rules are permanent.

stbkp01
172.16.238.16
stbkp01.stratos.xfusioncorp.com
clint
H@wk3y3
Nautilus Backup Server

%% ssh into stbkp01 %%
ssh clint@stbkp01
sudo -i
iptables --help
iptables -S %% -P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT %%
iptables -L %% Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       %%
iptables -F %% flush all the rules %%
%% Nginx's port all all traffic %%
iptalbes -A[append] INPUT -p[set protocol] tcp --dport 8096 -j ACCEPT
%% Apache's port block incoming traffic %%
iptables -A INPUT -p tcp --dport 8085 -j DROP
iptables -L  %% Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8096
DROP       tcp  --  anywhere             anywhere             tcp dpt:8085
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      %%
find /etc iptables | grep iptables %% /etc/sysconfig/iptables
/etc/sysconfig/iptables-config %%
cat /etc/sysconfig/iptables
iptables-save > /etc/sysconfig/iptables

%% not good practice to do the following 
cat /etc/sysconfig/iptables-config
vi /etc/sysconfig/iptables-config
-- change the following line to yes
IPTABLES_SAVE_ON_STOP="no"
IPTABLES_SAVE_ON_RESTART="no" %%

exit




