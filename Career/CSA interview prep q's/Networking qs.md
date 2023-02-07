Networking: 
· Difference between router, switch. 
· What is a Broadcast Domain? 
· DHCP DORA process 
· DNS – detailed explanation. TCP/UDP and why? 
· Subnetting · MSS/MTU 
· Complete flow when you trigger amazon.com 
· OSI model with complete details and protocols on each layer. 
· TCP and SSL handshake · Difference between TCP/UDP, examples 
· Flow/error control 
· What is a firewall, why do you need it? 
· OSI Model 
· Subnet mask - what is it?
what if you can't ping?

 
Networking:
- What is subnet mask?
	- it defines the range of ip addresses that can be used within a network or subnet;
- Why do we use subnet? 
	- cause it is good planning, and 
	- is used to segregate departments
- how many usable ips with blah subnet i.e. 192.168.0.32/24:
	- think - 4 octets i.e. 00000000.00000000.00000000.000000000 /24 is default
	- 
		- 	![[Pasted image 20221208161943.png]]
- what is the dhcp dora process i.e. how you receive a new ip address; 
	- discover - offer - request - acknowledgement
- What is the osi model - 7 layers - 
	- 7 - Application - giving access to the network
	- 6 - Presentation - 
	- 5 - Session - 
	- 4 - Transport - from source to destination, UDP & TCP
	- 3 - Network - info about networking 
	- 2 - Data link - 
	- 1 - Physical - electrical specs/hardware
- What is DNS?
	- Domain Name System
	- default is 8.8.8.8
	- the phone book of the internet, it connects web browsers with websites;
- DNS message format
	- A - an end device ipv4 address
	- NS - an authoritative name server
	- SOA - 
	- CNAME - 
	- MX - a mail exchange record

route or ip route for all networks and local hosts
- other q's
	- ip link show - part of ip utility info for all network interfaces;
	- what is the difference between router and switch?
		- router can connect multiple network, a switch connects devices within a network
	- what is a protocol you would use for a switch
		- 
	- what is a broadcast domain
		- an area of computers that are connected by switches and will stop at the router
	- what happens when you type amazon.com into browser:
		- 1st it checks the cache if ip is cached already, in not
		- it goes to the root server, if still not known
		- it sends it to the 
 
 
 
 
 
 
 
 ARINHow many usable hosts?
	https://jodies.de/ipcalc
	https://cidr.xyz/ - count is the answer;


What ports is your local machine using for connections? 
	netstat -ano - cli command

What is DHCP?
	https://www.efficientip.com/what-is-dhcp-and-why-is-it-important/
	DHCP (Dynamic Host Configuration Protocol) is **a network management protocol used to dynamically assign an Internet Protocol (IP) address to any device, or node, on a network so they can communicate using IP**.

Why is it used?
	A DHCP client uses the DHCP protocol to acquire configuration information, such as an IP address, a default route, and one or more DNS server addresses from a DHCP server.

Who is ARIN? 
	https://search.arin.net/rdap/?query=54.240.193.130
	https://bgp.he.net/AS17719#_whois
	https://wq.apnic.net/static/search.html

What is my IP?
	https://www.whatismyip.com/

In the packet capture, why did the first ping requet not receive a reply?
	The reason the first ping usually fails is that the remote router in that LAN has to put the ping request on hold to send out an ARP broadcast to learn the MAC address of the remote device, then wait for a response, and then send the first ping through. This delay is usually too long.
	https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwiKp5fFqOn7AhVXRd4KHaISCpEQFnoECBQQAQ&url=https%3A%2F%2Flearningnetwork.cisco.com%2Fs%2Fquestion%2F0D53i00000Z9QVcCAN%2Fwhy-first-reply-is-lost-every-time-for-the-first-ping&usg=AOvVaw1c2NFvKc8O5Z2HPfu19aN2

What is PSH flag in TCP?
	The PSH flags **instruct the operating system to send (for the sending side) and receive (for the receiving side) the data immediately**. In other words, this flag instructs the operating system's network stack to send/receive the entire content of its buffers immediately.
	https://www.site24x7.com/learn/linux/tcp-flags.html

If we send a TCP SYN packet destined to port 22 to  a server who has the port open, how will the server respond? (choose 2)
	https://www.imperva.com/learn/ddos/syn-flood/
	https://nmap.org/book/man-port-scanning-techniques.html












http://ec2-reachability.amazonaws.com/
https://www.davidc.net/sites/default/subnets/subnets.html
https://blogs.mulesoft.com/api-integration/security/how-to-choose-the-cidr-block-for-your-vpc/
https://jodies.de/ipcalc
https://www.maxmind.com/en/home
https://search.arin.net/rdap/?query=54.240.193.130
https://bgp.he.net/AS17719#_whois
https://wq.apnic.net/static/search.html
https://www.whatismyip.com/
https://www.rapidtables.com/convert/number/index.html
https://miniwebtool.com/octal-calculator/
https://cidr.xyz/
https://dnschecker.org/#A/www.katya.stem.tylan.xyz









