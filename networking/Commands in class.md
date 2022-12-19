route print [netstat -r]
ifconfig
route -n
arp -a [this showed ip 172.31.0.200 has incorrect mac address]
arp -d 172.31.0.200 [this deletes the record of above ip]
iptables --flush/-F
iptables -S
route -v -FC
ping 172.21.0.200
telnet 172.31.0.200 22 [22 is the port no]
sudo arp -s 172.31.0.200 00:00:00:00:00:00 [command to add mac address for ip in iptables]
iptables -LV [iptables are firewall for linux for in/outbound policies]
curl -v telnet://172.31.0.200:22
ec2-metadata -t -i -z -o -v -h [peering connection command to run in cli after setup]

Exercise using wireshare to test a connection
ip.addr==18.183.236.140  [filter in wireshark after selecting cisco]
[Powershell:] 
Test-NetConnection -ComputerName 18.183.236.140 -Port 22 
Test-NetConnection -ComputerName 18.183.236.140 -Port 23
192.168.24.154

DHCP = **Dynamic Host Configuration Protocol**
Used on internet protocol (IP) networks for automatically assigning IP addresses and other communication parameters to devices connected to the network using a client-server architecture.

sudo tcpdump -i eth0 "port 22"

scp tcpdump "port 67 or port 68" -w dhcp-traffic.pcap
sudo rm /var/lib/dhclient/dhclient* ; sudo dhclient -r ; sudo dhclient
ls -ltrh
scp -i dhcp-traffic.pcap ec2-user@[PIP]:/home/ec2-user/dhcp-traffic.pcap 'C:\Users\kayhowe\Documents\AWS - Docs\AWS Accounts\AWS Work Account'

traceroute google.com
traceroute -A [pip] (show the path lookups in routing registries and print results directly after the corresponding addresses)

whois AS16509 [https://lg.he.net/ or https://wq.apnic.net/]

netstat
nslookup

[https://jodies.de/ipcalc?host=10.0.0.0&mask1=16&mask2=](https://jodies.de/ipcalc?host=10.0.0.0&mask1=16&mask2=)  
HostMin:   10.0.0.1              
HostMax:   10.0.255.254
Default route below covers all IPs, including the 10/16 above
[https://jodies.de/ipcalc?host=0.0.0.0&mask1=0&mask2=](https://jodies.de/ipcalc?host=0.0.0.0&mask1=0&mask2=)  
HostMin:   0.0.0.1               
HostMax:   255.255.255.254
(https://amzn-aws.slack.com/archives/C03JPLTKDHQ/p1667344419767159)
More specific route takes preference, so IPs which fall into 10/16 are preferred over 0/0

ipconfig /displaydns
ipconfig /all


dig [www.blahblah.com] +trace
curl [webpage or ip] -v

[https://bottlenose.aws.a2z.com/d-xf1ajxcx/c-03fb2635](https://bottlenose.aws.a2z.com/d-xf1ajxcx/c-03fb2635)
curl -vvv [amazon.com](http://amazon.com/)
grubenv conf
ec2-user@ip-172-31-0-104 ~]$ find . "*http_proxy*" . ./.bash_logout ./.bash_profile ./.bashrc ./.ssh ./.ssh/authorized_keys
:D\Users\itr>curl -Lkv [amazon.com](http://amazon.com/) | more
> GET / HTTP/1.1 < HTTP/1.1 301 Moved Permanently > GET / HTTP/1.1 < HTTP/1.1 200 OK
curl -v 18.183.236.140
> GET / HTTP/1.1 < HTTP/1.1 200 OK
curl -vIkL 18.183.236.140

netstat -natup | grep 80 [checks on port to see if it is being used]
ec2-metadata -t -i -z -o -v -h








