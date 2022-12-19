During the daily standup, it was pointed out that the timezone across `Nautilus Application Servers` in `Stratos Datacenter` doesn't match with that of the local datacenter's timezone, which is `Africa/Bamako`.

	echo $TZ - blank response
	
	timedatectl -       Local time: Mon 2022-12-12 23:15:44 UTC
	  Universal time: Mon 2022-12-12 23:15:44 UTC
	        RTC time: n/a
	       Time zone: UTC (UTC, +0000)
	     NTP enabled: n/a
	NTP synchronized: yes
	 RTC in local TZ: no
	      DST active: n/a
	
	timedatectl -h
	
	ll /etc/localtime   # lrwxrwxrwx 1 root root 25 Aug  1  2019 /etc/localtime -> ../usr/share/zoneinfo/UTC
	
	timedatectl | grep -i zone   # Time zone: UTC (UTC, +0000)
	
	timedatectl list-timezones
	
	sudo timedatectl set-timezone Europe/Astrakhan  # used to correct time zone currently working on thor jumpbox
	
	timedatectl  #       Local time: Tue 2022-12-13 03:31:15 +04
	  Universal time: Mon 2022-12-12 23:31:15 UTC
	        RTC time: n/a
	       Time zone: Europe/Astrakhan (+04, +0400)
	     NTP enabled: n/a
	NTP synchronized: yes
	 RTC in local TZ: no
	      DST active: n/a


-- ssh'ing into the stratos DC
ll -a .ssh  # drwx------ 2 thor thor 4096 Dec 13 03:01 .
drwxr----- 1 thor thor 4096 Dec 13 03:01 ..
-rw------- 1 thor thor  567 Dec 13 03:01 authorized_keys

%%-- ssh into Stratos DC - Nautilus Application DB Server stdb01
ssh peter@172.16.239.10 -i .ssh/authorized_keys  # no route to host checked with Joe he said no you need to change the time zone on the webservers not on the db server.%%

-- ssh into Webservers #1 stapp01:
pwd
ll -a
ll .ssh
ssh tony@172.16.238.10 -i .ssh/authorized_keys
%%type password%% Ir0nM@n
pwd
ll -a
timedatectl
sudo timedatectl set-timezone Africa/Bamako
%%type password%% Ir0nM@n
timedatectl %%confirmed!!!!%%
exit

-- ssh into Webservers #2 stapp02:
ssh steve@172.16.238.11 -i .ssh/authorized_keys
%%type password%% Am3ric@
pwd
ll -a
timedatectl
sudo timedatectl set-timezone Africa/Bamako
%%type password%% Am3ric@
timedatectl %%confirmed!!!!%%
exit

-- ssh into Webservers #3 stapp03:
ssh banner@172.16.238.12 -i .ssh/authorized_keys
%%type password%% BigGr33n
pwd
ll -a
timedatectl
sudo timedatectl set-timezone Africa/Bamako
%%type password%% BigGr33n
timedatectl %%confirmed!!!!%%
exit

-- change the jump-box timezone also? as this is not America/Maceio....it doesn't say to...


failed! - - Make sure the timezone is set correctly on App Server 1 - didn't have the correct timezone listed and copy pasted to america/maceio rather than requested - fixed now


