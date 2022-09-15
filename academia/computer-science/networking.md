# Networking

## Ports and Protocols

### Protocols

TCP (Transmission Control Protocol): Is a connection oriented protocol. TCP is a reliable mode of communication meaning when data is send, we expect to receive an acknowledgement. TCP also numbers the data so that it can request retransmissions of lost data.

UDP (User Datagram Protocol): Does not have a formal call setup, meaning it sends data whenever it is available and hopes the device on the other end is ready to receive. It is an unreliable form of delivery, meaning it has no way of recovering data. Since it receives no feedback from receiving devices, there's no way to provide any type of flow control.

### Ports

#### Basic Information

Information is transferred from one IP address to another and is delivered to specific ports. Port numbers are described as one of two types: non-ephemeral and ephemeral ports. 

Ephemeral: are temporary port numbers that the client usually decides to use randomly as it’s sending this information back to the server.

Non-ephemeral: This would be permanent port numbers that are used and they’re commonly used by applications or services that are running on a server. Those port numbers are usually defined as port 0 through 1,023.

Our server IP address would commonly use a non-ephemeral port and the client IP address is commonly going to use an ephemeral port number.

#### Common Ports

ICMP (Internet Control Message Protocol): You'd send an ICMP request to see if a device is there and active. It may send a ICMP request to let the original sender that it is able to communicate.

##### TCP

1. Telnet - Telecommunication Network: TCP/23
	* TCP/23
	* Login to devices remotely
	* Console access
	* In-the-clear communication
	* Not the best choice for production systems
2. SSH (Secure Shell)
	* TCP/22
	* Encrypted communication link
	* Looks and acts like Telnet
3. SMTP (Simple Mail Transfer Protocol)
	* TCP/25
	* Server to server email transfer and to send mail from a device to a mail server
	* IMAP and POP3 are protocols used to receive mail
4. SFTP (Secure FTP)	
	* TCP/22
	* Uses the SSH File Transfer Protocol
	* Provides file system functionality
	* Encrypted communication using SSH
5. FTP (File Transfer Protocol)
	* TCP/20 (active mode data), TCP/21 (control)
	* Transfers files between systems
	* Authenticates with a username and password
	* Full-featured functionality (list, add, delete, etc)
6. HTTP (Hypertext Transfer Protocol)
	* TCP/80 
	* Web server communication
7. HTTPS ( Hypertext Transfer Protocol Secure )
	* TCP/443 
	* Web server communication encrypted
8. RDP (Remote Desktop Protocol)
	* TCP/3389
	* Share a desktop from a remote location
	* Remote Desktop Services on many Windows versions
	* Can connect to an entire desktop or just an application
	* Clients for Windows, MacOS, Linux, Unix, iPhone, and others
9. SIP (Session Initiation Protocol)
	* TCP/5060 and TCP/5061 
	* Voice over IP (VoIP) signaling
	* Setup and manage VoIP sessions
	* Extend voice communication
10. SMB (Server Message Block)
	* TCP/445
	* Protocol used by Windows
	* File sharing, printer sharing
11. POP3 (Post office protocol version 3)
	* TCP/110
	* Basic mail transfer functionality
12. IMAP4 (Internet Message Access Protocol v4)
	* TCP/143
	* Includes management of email inbox from multiple clients
13. LDAP (Lightweight Directory Access Protocol)
	* TCP/389
	* Store and retrieve information in a network directory
14. LDAPS (LDAP Secure)
	* TCP/636
	* A non-standard implementation of LDAP over SSL
15. Voice over IP (VoIP) signaling
	* TCP/1720
	* ITU Telecommunication H.32x protocol series
##### UDP

1. DNS (Domain Name System)
	* UDP/53
	* Converts names to IP addresses
2. TFTP (Trivial File Transfer Protocol)	
	* UDP/69
	* Very simple file transfer application (read and write files)
	* No authentication
	* Not used on production systems
3. DHCP (Dynamic Host Configuration Protocol)
	* Automated configuration of IP address, subnet mask, and other options
	* UDP/67, UDP/68
	* Requires a DHCP server
4. SNMP (Simple Network Management Protocol)
	* UDP/161
	* Gather statistics from network devices
5. NTP (Network Time Protocol)
	* UDP/123
	* Switches, routers, firewalls, servers, workstations
	* Synchronizing clocks

## OSI Model

Open Systems Interconnection Reference Model

##### Layer 1 (Physical)

* The physics of the network
	* Signaling, cabling, connectors
	* This layer isn't about protocols

##### Layer 2 (Data Link Layer)

* The basic network "language"
	* The foundation of communication at the data link layer
* Data Link Control (DLC) protocols
	* MAC (Media Access Control) address on Ethernet
* The "switching" layer
##### Layer 3 (Network Layer)

* The "routing" layer
* Internet Protocol (IP)
* Fragments frames to traverse different networks

##### Layer 4 (Transport Layer)

* The "post office" layer
* TCP and UDP

##### Layer 5 (Session Layer)

* Communication management between devices
	* Start, stop, restart
* Control protocols, tunneling protocols

##### Layer 6 (Presentation Layer)

* Character encoding
* Application encryption
* Often combined with the Application layer 

##### Layer 7 (Application Layer)

* The layer we see
* HTTP, FTP, DNS, POP3

## Ethernet

### MAC Address

* Ethernet Media Access Control address
	* The "physical" address of a network adapter 
	* Unique to a device
* 48 bits / 6 bytes long
	* Displayed in hexidecimal (e.x., 8c:2d:aa:4b:98:a7)
		* First 3 bytes are Organizationally Unique Identifier (OUI) (the manufacturer)
		* Last 3 bytes are Network Interface Controller-Specific (the serial number)

### Duplex

#### Half-duplex

* A device  cannot send and receive simultaneously
* All LAN hubs are half-duplex devices
* Switches can be configured as half-duplex
* Traffic received on one interface is repeated to all other interfaces
* If two devices communicate simultaneously, you have a collision

#### Full-duplex

* Data can be sent and received at the same time
* A properly configured switch interface will be set to full-duplex

### Devices

#### The Switch

* Forward or drop frames
	* Based on the destination MAC address
* Gather a constantly updating list of MAC addresses
* Maintain a loop free environment
	* Using Spanning Tree Protocol (STP)

### Unicast, Broadcasts, and Multicasts

#### Unicast

* One station sending information to another station
* Send information between two systems
* Web surfing, file transfers
* Does not scale optimally for real-time streaming media

#### Broadcasts

* Send information to everyone at once
* One packet, received by everyone
* Limited scope
	* The broadcast domain
* Routing updates ARP requests
* Not used in IPv6
	* Focus on multicast

#### Multicast

* Delivery of information to interested systems
	* One to many
*	Multimedia delivery, stock exchanges
* Very specialized

### Protocol Data Units

* A unit of transmission
	* A different group of data at different OSI layers
* Ethernet operates on a frame of data
	* It has no idea what's inside
* TCP or UDP PDU
	* TCP segment
	* UDP datagram

#### Headers

* Each layer of the OSI model contains layers
	* Layer 5, 6, and 7
		* Application Data
	* Layer 4
		* Application Data, TCP Header
	* Layer 3
		* Application Data, TCP Header, IP Header
	* Layer 2
		* Application Data, TCP Header, IP Header, Frame Header
	* Layer 1
		* Application Data, TCP Header, IP Header, Frame Header, Frame Trailer 

#### Maximum Transmission Unit (MTU)

* Maximum IP packet to transmit
* Fragmentation slows things down
* Difficult to know the MTU all the way through the path
* MTU sizes are usually configured once
* What if you send packets with Don't Fragment (DF) set?
	* Routers will respond back and tell you to fragment
* Ping with DF and force a maximum size of 1472 bytes
	* 1500 bytes - 8 bytes ICMP header - 20 bytes IP address = 1472
		* Windows: ping -f -l 1472 8.8.8.8
		* Linux: 


##### Fragmentation 

* IP fragmentation is an Internet Protocol (IP) process that breaks packets into smaller pieces (fragments), so that the resulting pieces can pass through a link with a smaller maximum transmission unit (MTU) than the original packet size. The fragments are reassembled by the receiving host.
