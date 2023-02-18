![[L15 1.png]]

1. Use the appropriate command to create a file /tmp/testfile five minutes from now
	1. date [Sat Feb 18 11:32:27 UTC 2023]
	2. crontab -e
		1. 37 11 18 02 06 touch /tmp/testfile.txt
	3. He suggests this way, however the 'at' package was unable to be installed on my ec2 ubuntu :'(
		1. at now +5min
		2. touch /tmp/testfile
2. Use the appropriate solution to run the fstrim command on a daily basis
	1. systemctl disable --now fstrim.timer
	2. cd /etc/cron.dailyk/
	3. vim fstrim.cron
		1. #!/bin/bash
		2. fstrim
3. Ensure that on a daily basis at 4pm the message 'hello' is written to syslog
	1. echo 'echo "hello"' > hello.sh
	2. chmod u+x hello.sh
	3. crontab -e
		1. 00 16 * * * ./hello.sh