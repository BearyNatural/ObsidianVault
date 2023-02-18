![[L11 1.png]]

1. Use timedatectl to show current time properties on your server
	1. timedatectl [local time; universal; RTC; Time zone; NTP service; clock sync;]
2. Use ntpdate to start a synchronisation with a NTP server at this moment
	1. ntpdate pool.ntp.org [unable to do this as I am unable to install on ec2]