![[L8 1.png]]

*NOTE: ensure you've complete lesson 7 lab before starting this one.*
1. Ensure that files created by user root cannot be accessed by group or others; files of ordinary users should be readable by the group owners
	1. umask 077 [ensures only root has access to root files]
2. Create the directories /data/sales & /data/account
	1. mkdir -p 
		1. /data/sales
		2. /data/account
3. Members of the goup sales should be able to read and write files in /data/sales, members of the group account should be able to read and write in /data/account
	1. cd /data
	2. chgrp 
		1. account /data/account
		2. sales /data/sales
4. No other users should have access to these directories
	1. chmod 
		1. g+w account sales
		2. o-rx account sales
5. Users will only be allowed to delete files they have created themselves, but user anna is the sales manager and should be able to mange all sales files
	1. chmod +t sales
	2. chown anna sales 

- SUID / SETUID
	- chmod u+s file
- SGID / SETGID
	- chmod g+s file
- +t sticky
	- chmod +t file
- chattr - for the file that you can't delete!
	- lsattr 
	- chattr -i [filename] or which ever letter lsattr shows
	- 