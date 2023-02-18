![[L10 1.png]]

1. Verify your current network configuration
	1. ip a
	2. ip route show
	3. cat /etc/resolv.conf
2. Check that you can ping google.com
	1. ping google.com
	2. ping microsoft.com [doesn't work they have put a stop to it]
3. Use ss to get a list of services currently offered by your server
	1. ss --help
	2. ss -tuna [to see a list of ports are open for business]
		1. grep 68 /etc/services [shows which services are using this port - why is this open???]
4. Use nmap to do the same
	1. apt install nmap -y [unable to install, possibly due to security issues surrounding this program]