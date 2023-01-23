The system admin team of `xFusionCorp Industries` has noticed an issue with some servers in `Stratos Datacenter` where some of the servers are not in sync w.r.t time. Because of this, several application functionalities have been impacted. To fix this issue the team has started using common/standard NTP servers. They are finished with most of the servers except `App Server 1`. Therefore, perform the following tasks on this server:

1.  Install and configure NTP server on `App Server 1`.
    
2.  Add NTP server `3.pool.ntp.org` in NTP configuration on `App Server 1`.
    
3.  Please do not try to start/restart/stop `ntp` service, as we already have a restart for this service scheduled for tonight and we don't want these changes to be applied right now.

https://dyclassroom.com/reference-server/how-to-sync-linux-server-time-with-ntp-network-time-protocol-server

stapp01
172.16.238.10
stapp01.stratos.xfusioncorp.com
tony
Ir0nM@n
Nautilus App 1

%%Login to Server - stapp02:%%
ssh tony@172.16.238.10 -i .ssh/authorized_keys
%%type password%% Ir0nM@n
pwd
sudo -i

%%NTP%%
ntpstat %%-bash: ntpstat: command not found%%
yum install -y ntp
ntpstat
rpm -qa | grep ntp %%ntp-4.2.6p5-29.el7.centos.2.x86_64 ntpdate-4.2.6p5-29.el7.centos.2.x86_64%%
systemctl status ntpd %%Active: inactive (dead)%%
ntpstat
find / -name conf | grep ntp %% find: ‘/proc/tty/driver’: Permission denied /etc/ntp.conf %%
vi /etc/ntp.conf  %% add to bottom of list 'server 3.pool.ntp.org' %%
cat /etc/ntp.conf |  grep my.pool 




