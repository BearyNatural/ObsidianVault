 ARINHow many usable hosts?
	https://jodies.de/ipcalc
	https://cidr.xyz/ - count is the answer;
	![[Pasted image 20221208161943.png]]

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









