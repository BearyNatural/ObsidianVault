![[M15.png]]

1. Set up SSH key-based authentication for user root between server 1 and server2
2. Write a script that synchronizes the contents of the user root home directory from server 1 to server 2, using rsync and schedule this script to run through cron one a day
3. Answers:
	1. ssh-keygen
		1. 3 x enter key
	2. ssh-copy-id server2
	3. rsync -av /root server2:/root
	4. chattr -S +i .ssh [on the server2]
	5. vi rsync.sh
		1. rsync -av /root/ server2:/root
	6. chmod +x rsync.sh
	7. cp rsync.sh /et/cron.daily/

