![[L5 1.png]]

1. Log into your server using a text-only console
	1. chvt 2 [this allows us to open a virtual terminal, exit lets you log out of this session]
2. Also log in from a SSH session
	1. ip a [local ip addr is listed under 2: inet 192.168.4.235/24, we need to remember 235]
	2. ssh 192.168.4.80 [brings us to the server that has previously been configured]
	3. ssh 192.168.4.235 [logs into server]
3. Find out which terminal names are used for both logins
	1. who [pts is sudo terminal, used when ssh & ssm]