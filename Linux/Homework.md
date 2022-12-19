https://www.tecmint.com/

A.) What is OSI model & it's purpose? 
- Open System Interconnection OSI model is **a reference model that provides a convenient representation of data transmitted across a network**. It splits the network communication tasks into seven manageable bits performed on each abstract layer. [https://linuxhint.com/network-osi-layers-explained/] Layers:
	- Application
	- Presentation
	- Session
	- Transport
	- Network
	- Data Link
	- Physical
- The purpose of the OSI reference model is to guide vendors and developers so the digital communication products and software programs they create will interoperate, and to facilitate clear comparisons among communications tools. [https://www.networkworld.com/article/3239677/the-osi-model-explained-and-how-to-easily-remember-its-7-layers.html]
B.) How OSI model is different from TCP/IP model?
- OSI Model - ##The OSI Model is a logical and conceptual model that defines network communication used by systems open to interconnection and communication with other systems. The Open System Interconnection (OSI Model) also defines a logical network and effectively describes computer packet transfer by using various layers of protocols.
- TCP/IP Model - ##TCP/IP helps you to determine how a specific computer should be connected to the internet and how you can transmit data between them. It helps you to create a virtual network when multiple computer networks are connected together.  TCP/IP stands for Transmission Control Protocol/ Internet Protocol. It is specifically designed as a model to offer highly reliable and end-to-end byte stream over an unreliable internetwork.
- KEY DIFFERENCE [https://www.guru99.com/difference-tcp-ip-vs-osi-model.html]
-   OSI has 7 layers whereas TCP/IP has 4 layers.
-   The OSI Model is a logical and conceptual model that defines network communication used by systems open to interconnection and communication with other systems. On the other hand, TCP/IP helps you to determine how a specific computer should be connected to the internet and how you can be transmitted between them.
-   OSI header is 5 bytes whereas TCP/IP header size is 20 bytes.
-   OSI refers to Open Systems Interconnection whereas TCP/IP refers to Transmission Control Protocol.
-   OSI follows a vertical approach whereas TCP/IP follows a horizontal approach.
-   OSI model, the transport layer, is only connection-oriented whereas the TCP/IP model is both connection-oriented and connectionless.
-   OSI model is developed by ISO (International Standard Organization), whereas TCP Model is developed by ARPANET (Advanced Research Project Agency Network).
-   OSI model helps you to standardize router, switch, motherboard, and other hardware whereas TCP/IP helps you to establish a connection between different types of computers.
C.) What are different classes of IP Address & their purpose? https://study-ccna.com/classes-of-ip-addresses/ 
- There are 5 IP address classes, each one defined by a letter: A, B, C, D and E and classified depending on the first octet range.
D.) What are the key difference between IPv4 & IPv6? 
-   IPv4 is a 32-Bit IP address, whereas IPv6 is a 128-Bit IP address.
-   IPv4 is a numeric addressing method, whereas IPv6 is an alphanumeric addressing method.
-   IPv4 binary bits are separated by a dot(.), whereas IPv6 binary bits are separated by a colon(:).
-   IPv4 offers 12 header fields, whereas IPv6 offers 8 header fields.
-   IPv4 supports broadcast, whereas IPv6 doesn’t support broadcast.
-   IPv4 has checksum fields while IPv6 doesn’t have checksum fields
-   When we compare IPv4 and IPv6, IPv4 supports VLSM (Variable Length Subnet Mask), whereas IPv6 doesn’t support VLSM.
-   IPv4 uses ARP (Address Resolution Protocol) to map to MAC address, whereas IPv6 uses NDP (Neighbour Discovery Protocol) to map to MAC address.
E.) How many IP addresses can be created using CIDR /27? 
-    30
F.) What are the main difference between TCP & UDP protocol? 
-   TCP is a connection-oriented protocol, whereas UDP is a connectionless protocol.
-   The speed for TCP is slower while the speed of UDP is faster
-   TCP uses handshake protocol like SYN, SYN-ACK, ACK while UDP uses no handshake protocols
-   TCP does error checking and also makes error recovery, on the other hand, UDP performs error checking, but it discards erroneous packets.
-   TCP has acknowledgment segments, but UDP does not have any acknowledgment segment.
-   When we compare TCP vs UDP protocol, TCP is heavy-weight, and UDP is lightweight.
G.) How DNS & DHCP works?
- https://www.tutorialspoint.com/difference-between-dns-and-dhcp
- DNS is a directory of names that correspond to specific IP addresses, however it is not a single directory. Just like the Internet, the DNS is also You can think of DNS as the contact list on your smartphone, where each contact corresponds to a particular mobile number.
- DHCP is a network management protocol that automates the process of configuring the devices on IP networks, thus allowing them to use the various network services. A DHCP server dynamically assigns an IP address and other network configuration parameters to each device on a network so that they can communicate with other IP networks.
H.) What happens when you type 'www.amazon.com' in browser?
- The browser sends an HTTP request to the webserver. Once the TCP connection is established, it is time to start transferring data! The browser will send a GET request asking for maps.google.com web page.

![:tv:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/google-medium/1f4fa@2x.png) **Reference/Study material:**  
{+} [https://www.youtube.com/watch?v=vv4y_uOneC0](https://www.youtube.com/watch?v=vv4y_uOneC0)  
{+} [https://www.youtube.com/watch?v=OTwp3xtd4dg](https://www.youtube.com/watch?v=OTwp3xtd4dg)  
{+} [https://www.youtube.com/watch?v=OqsXzkXfwRw](https://www.youtube.com/watch?v=OqsXzkXfwRw)  
{+} [https://www.youtube.com/watch?v=Qs2Nu7nJpO4](https://www.youtube.com/watch?v=Qs2Nu7nJpO4)

