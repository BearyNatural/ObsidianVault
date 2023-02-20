![[M18.png]]

1. Configure a Caching-only DNS nameserver https://kifarunix.com/setup-caching-only-dns-server-using-bind9-on-ubuntu-20-04/
	1. ssh ubuntu@172.31.26.141 -i RemoteLinuxKey.pem [ssh to server]
	2. bind is what is used on ubuntu
		1. apt install bind9 bind9utils -y
		2. etc/bind/named.conf [main configuration file for bind dns]
			1. others are listed in the file
			2. /etc/bin/named.conf.options [create a backup of the default config file]
				1. cp /etc/bind/name.conf.options{,.bak}
			2. vi /etc/bind/name.conf.options
				1. #DNS server acl
					1. acl "allowed" {172.31.16.0/20;
				2. }; [cidr range]
				3. options {
					1. directory "/var/cache/bind";
					2. recursion yes;
					3. allow-recursion { localhost; allowed; };
					4. listen-on port 53 {localhost; 172.31.21.184; }; 
					5. allow-query { localhost; allowed; };
					6. allow-transfer { none; };
					7. dnssec-validation auto;
					8. listen-on-v6 { any; };
				4. };
			3. named-checkconf /etc/bind/named.conf
	3. ufw enable [y]
		1. ufw app list
		2. ufw allow from 172.31.16.0/20 to 172.31.21.184 port 53 proto udp
		3. ufw status numbered [[ 2] 172.31.21.184 53/udp       ALLOW IN    172.31.16.0/20]
	4. enable bind service
		1. systemctl enable named
		2. systemctl status named
		3. netstat -lnpau | grep 53
2. Test bind dns resolution from client side
		1. nmcli -t --fields <name> con show --active [did not include the fields section]
		2. FAILED - FUCKED THE SSH CONNECTION....

1. https://kifarunix.com/setup-caching-only-dns-server-using-bind9-on-ubuntu-20-04/
	1. install the package before stopping it