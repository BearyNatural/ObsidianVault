![[M8.png]]

1. Use iptables to build a firewall that allows the following:
	1. INCOMING: SSH, ping
	2. OUTGOING: SSH, DNS, ping, HTTP
2. Make sure these services are allowed through the firewall for future lessons
3. Answers: -
4. Ubuntu firewall is UFW - aka - uncomplicated firewall
	1. ufw status [mine is inactive]
	2. ufw enable [now firewall is active and enabled on system start]
	3. Rules [for in or out specified rules: ufw allow in ssh]
		1. Allow
			1. ufw allow port# [allows both tcp & udp on port number]
			2. ufw allow 22/tcp [allows only tcp traffic on this port]
			3. ufw allow ssh [checks /etc/services on your system for the port that ssh requires]
		2. Deny
			1. ufw reject command [like ssh]
			2. ufw deny port#
		3. Other commands:
			1. ufw delete allow/reject port#
			2. ufw reset [resets it back to default state]
			3. ufw app list
		4. 
5.  this is not applicable for Ubuntu see #4
	1. systemctl disable --now firewalld 
	2. systemctl enable --now iptables
	3. iptables -L [lists iptable configuration rules]
	4. iptables -F INPUT [to flush it]	
	5. iptables -P OUTPUT DROP [drops the output also]
	6. iptables -A INPUT -p tcp --deport 22 -j ACCEPT [incoming ssh]
	7. iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT [response to incoming ssh]
	8. iptables -A INPUT -p imcp -j ACCEPT [incoming icmp]
	9. iptables -a OUTPUT -p tcp --deport 22 -j ACCEPT [outgoing ssh]
	10. iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT [response to outgoing ssh]
	11. iptables -a OUTPUT -p icmp -j ACCEPT [outgoing icmp]
	12.  iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT [http]
	13. iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT [also for 443]
	14. iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT 
	15. iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
	16. ping 8.8.8.8 [default dns]
