![[M3.png]]

1. On your favourite Linux distribution, configure systemd-networkd to take care of networking
	1. These work together:
		1. systemctl status systemd-networkd
		2. systemctl status systemd-resolved
	2. cat /etc/resolv.conf [currently is managed by networkmanager]
		1. this should be replaced with a symbolic link that goes to the resolve.conf that is in the run directory
		2. ll /etc/ | grep resolv.conf | awk '{print $9,$10,$11}' [resolv.conf -> ../run/systemd/resolve/stub-resolv.conf]
	3. ll /etc/systemd/network/ [file with 10-static-(name of your network card)]
		1. vi /etc/systemd/network/ [as mine is an ec2, I do not have the dedicated hardware therefore no file]
		2. it shows your network dets