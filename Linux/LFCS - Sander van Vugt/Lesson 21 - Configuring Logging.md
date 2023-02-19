![[M5.png]]

1. Configure rsyslog such that all messages with a priority of info are sent to /var/log/info 
2. Configure logrotate so that this file is rotated every day, and a backlog of one week is kept 
3. Ensure that messages logged by systemd-journald are stored on disk persistently
4. Answers:
	1. Start with step 3 cause it is easiest
		1. mkdir /var/log/journal
		2. will need to either restart your machine or restart the systectl systemd-journald service
			1. systemctl restart systemd-journald
	2. Next:
		1. vi /etc/rsyslog.conf [going to add a new rule on Ubuntu system it tells us - Default logging rules can be found in /etc/rsyslog.d/50-default.conf]
		2. vi /etc/rsyslog.d/50-default.conf
			1. *.=info                                                /var/log/info
		3. systemctl restart rsyslog
			1. systemctl status rsyslog
	3. Finally rotation of logs: [found in etc/logrotate.conf]
		1. vi /etc/logrotate.conf [at bottom of document]
			1. /var/log/info {
				1. daily
				2. rotate 5
			2. }
	4. Nothing else needs to be restarted as the logrotate.conf file is started by cronjob