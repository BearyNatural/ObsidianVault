![[M18.png]]

1. Configure a Caching-only DNS nameserver
	1. bind is what is used on ubuntu
		1. apt install bind9 bind9utils -y
		2. etc/bind/named.conf [main configuration file for bind dns]
			1. others are listed in the file
			2. /etc/bin/named.conf.options [create a backup of the default config file]
				1. cp /etc/bind/name.conf.options{,.bak}
			2. vi /etc/bind/name.conf.options
				1. acl "allowed" {172.31.16.0/20;}; [cidr range]
	2. to be continued!...