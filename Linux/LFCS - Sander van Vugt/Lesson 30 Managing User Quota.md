![[M14.png]]

1. Configure Quota to limit the amount of data user linda can write to her home directory to 1 GB
	1. ensure lindas home directory to a partitioned drive
		1. usermod -m -d /books/linda
			1. cat /etc/passwd | grep linda
		2. 