# AWS_SAA_COURSE

Table of Contents
==================

  * [Cloud Computing Fundamentals](#Cloud-Computing-Fundamentals)
    * [Cloud Computing Definition](#Cloud-Computing-Definition)
    * [Public vs Private vs Multi vs Hybrid Cloud](#Public-vs-Private-vs-Multi-vs-Hybrid-Cloud)
    * [Cloud Service Models](#Cloud-Service-Models)
  * [Network Fundamentals](#Network-Fundamentals)
    * [Physical Layer - Layer 1](#Physical-Layer---Layer-1)
    * [Data Link Layer - Layer 2](#Data-Link-Layer---Layer-2)
    * [Network Layer - Layer 3](#Network-Layer---Layer-3)
    * [Transport Layer - Layer 4](#Transport-Layer---Layer-4)
    * [Network Address Translation](#Network-Address-Translation)
    * [DDOS - Application Layer Attack](DDOS---Application-Layer-Attack)
    * [SSL and TLS](SSL-and-TLS)
  * [AWS Fundamentals](#AWS-Fundamentals)

Cloud Computing Fundamentals
============================

Cloud Computing Definition:
------------------------------

1) On demand self service 
  - Provision and terminate using a UI/CLI without human interaction.

2) Broad Network Access
  - Capabilities are available over the network and accessed through standard mechanisms.
  - Accessed services over standard network like http, https, ssh, or vpn

3) Resource Pooling
  - There is a sense of location independence, no control or knowledge over the exact location of the resources
  - Resources are pooled to serve multiple consumers using a multi-tenant model
  - Economies of scale, cheaper service
  
4) Rapid Elasticity
  - Capabilities can be elastically provisioned and released to scale rapidly outward and inward with demand
  - To the consumer, the capabilities available for provisioning often appear to be unlimited
  - Scale UP(OUT) and DOWN(IN) automatically in response to system load

5) Measured Service
  - Resource usage can be monitored, controlled, reported and billed
  - Usage is measured. Pay for what you consume


Public vs Private vs Multi vs Hybrid Cloud
--------------------------------------------

Public cloud - A cloud environment that is accessible to the public, using 1 public cloud
Multi cloud - Using multiple cloud providers, more than 1 public cloud
Private cloud - Using a cloud provider that stores your resources offline, on prem equipmen. Using on premises real cloud
Hybrid cloud - Using private and public cloud. Hybrid cloud is **not** public cloud + legacy on-premises

Cloud Service Models
---------------------

**Infrastructure stack** or **Application stack** - collection of things which that an application needs all stack onto each other
- Facilities - Building with power, with air condition, with physical security 
- Infrastructure - storage and networking
- Servers - an app generally requires one or more physical servers. These servers run virtualization, which allows them to be carved into VMs
- Virtualization - These virtual machines run Operating Systems,
- O/S
- Container
- Runtime - Every app is written in a language such as python etc, an all have an environement that they need to run in. This is called a runtime environment
- Data - An app needs data to work on, which it creates or consumes
- Application

Parts that you manage 
Parts managed by the vendor 
Unit of consumption 

**IAAS:**
You manage:
- OS
- Container
- Runtime
- Data
- App

Vendor Manages:
- Facilities
- Infrastructure
- Servers
- Virtualization

**PAAS**
You manage:
- Runtime
- Data
- App

Vendor manages everything else

**SAAS**
Consume Application 
e.g Netflix, dropbox

Network Fundamentals
=====================

Physical Layer - Layer 1
-------------------------
Layer 1 specifications define the transmission and reception of RAW BIT STREAMS between a device and a SHARED physical medium. It defines things like voltage level, timing, rates, distances, modulation and connectors. 
- Physical medium can be copper(electrical) fibre(light) or wifi(radio frequency)
- Physical shared medium
- Standards for transmitting onto the medium
- standards for receiving from the medium
- No access control
- No uniquely identified devices
- No device => device communications

Data Link Layer - Layer 2
--------------------------
Devices at L2 have a unique hardware(MAC) address e.g. 3e:22:fb:b9:5b:75 . 48 bits, in hex, 24 bits for manufacturer. Frames can be addressed to a destination or broadcast (All Fs)
- MAC Address is uniquely attached to a specific piece of hardware.
- **Payload** is the data the frame carries from source to destination. It's generally provided by layer 3, and the Ethertype (ET) attribute defines which L3 protocol is used (e.g. IP)
- Layer 2 provides controlled acccess to the physical medium
- Provides access to machine to machine transfer where as layer 1 doesn't.  Only provides a medium to share data to everyone connected to that medium
- Identifiable devices 
- Media access control
- Collision Detection
- Unicast communication 1:1
- Broadcast communication 1:ALL
**Encapsulation**:
The process of taking some data and wrapping it in something else.  Data being wrapped inside a frame.  
- As data is passed down the osi model it is encapsulated in more and more different components.  
- Switches understand frames and MAC Addresses. They maintain a MAC Address table which starts off empty. As the swiotch receives frames on its ports, it learns which devices are connected and populates the MAC Address table

Network Layer - Layer 3
------------------------

Internet Protocol (IP) is a Layer 3 protocol which adds cross-network IP Addressing and routing to move data between Local Area Networks without direct P2P links.
IP packets are moved step by step from source to destination via intermediate networks. Encapsulated in different frames along the way. 
- Routers (L3) devices remove frame encapsulation and add new frame encapsulation at every hop.
- Every packet has a source IP and destination IP
- All IP Addresses have a **network** part. e.g 133.33.3.7 - the 133.3 is the network part - 3.7 is the **host** part
**Subnet Mask**
Its the Subnet Mask which allows a HOST to determine if an IP address it needs to communicate with is local or remote - which influences if it needs to use a gateway or can communicate locally. 
- Subnetting is used to identify which part of an ip address is the network part and which is the host part.
- As long as the network part for two different ip address is the same then we know that they are both on the same network.

**ARP Address Resolution Protocol**
- Gives you the MAC address for a given ip address
- Within a local network data is moved via L2 frames over L1. ARP discovers which MAC relates to a given IP

**Routers**
Its a routers job to move packets between networks.  Routers do this by reviewing packets checking route tables for the target addresses and adding frames allowing packets to pass through intermediate layer 2 networks. 
Router is a device that understands:
- Physcial networking 
- Data link networking
- IP networking 

**Summary**

- IP Addresses - cross network addressing
- ARP - find the MAC address for this IP
- Route - where to forward this packet
- Route tables - multiple routes
- Router - moves packets from SCR to DST - Encapsulating in L2 on the way 
- Device to Device communications over the internet
- No method for channels of communications SRC IP >=< DST IP only
- Packets can be delivered out of order. Depending on network condition there is no gauruntee that packets will take the same route from source to destination

Transport Layer - Layer 4
---------------------------
**TCP** - Segments
TCP segments arre placed inside the IP Packets. Add additional capibilities to ip packets.  
- TCP segments add source and destination ports. This gives the combined TCP-IP protocol the ability to have multiple streams of conversations at the same time between two devices
- This allows the internet to function in the flexible way that it does
- **Sequence Number** - is a way of uniquely identifying a particular segment within a particular connection so that both sides can make observations
- **Acknowledgment** - Is a way that one side can indicate that it has received up to and including a certain sequence number. Every segment which is transmitted needs to be acknowledged
- **Window** - number of bytes that your willing to receive. Lets the receiver control the rate that the which the sender sends data.  This is how flow control works.
- **Checksum** - used for error checking
- **Urgent Pointer** - Both sides can have seperate processing.  
- All these fields are known as the TCP header

**TCP Cont.**
TCP is a connection based protocol.  A connection is established between two devices using a random port on a client and a known port on the server. Once established the connection is bi-directional. The connection is a reliable connection provided via the segments encapsulated in IP packets.
- L3 packets have no error checking, no ordering, no association. 
- Segments linked to a connection, error checking, ordering, and retransmission
- Flags which can be set to alter the connection e.g. FIN can be used to close, ACK for acknowledgements, SYN to synchronise sequence numbers.

**TCP Connection 3-way Handshake**
- Client needs to inform the server of the sequence number that its going to start with. Sequence numbers are used to track and ack every segment part of that connection. 1) Client creates segment to send to server. 
- Its important both sides know the starting point by knowing the sequence number.

**Session & State**
- A network ACL(AWS) is a stateless firewall which needs two rules for tcp connection, one in both directions.
- A stateful firewall views sees one thing - Allowing the outbound implicitly allows the inbound response

**TCP Well Known Ports**
tcp/80 - http & tcp/443 https
tcp/22 ssh
tcp/25 - smtp (email)
tcp/21 - telnet
tcp/3389 - Remote Desktop Protocol
tcp/3306 - MySQL/MariaDB/Aurora
- 3 way handshake is required before every connection

Network Address Translation
----------------------------
- NAT is designed to overcome IPv4 shortages
- also provides some security benefits
- Translates private IPv4 addresses to Public
- **Static NAT** - 1 private to 1 (fixed) public address
- **Dynamic NAT** - 1 private to 1st available Public
- **Port Address Translation (PAT)** many private to 1 public - In AWS this is how the NATGateway functions - a (many:1)(PrivateIP:PublicIP) Architecture
- Ipv4 - makes no sense with IPv6

**IP Addressing and Subnetting**
- IPv4 standard created in 1981
- 0.0.0.0 -> 255.255.255.255 = 4,294,967,296
- All public IPv4 addressing is allocated
- Part of the address space is private .. can be used and reused freely 
- **Class A IPs** - typically used for huge networks, usually allocated to businesses - 0.0.0.0 - 127.255.255.255
- **Class B** - Large businesses
- **Class C** - smaller businesses

**Subnetting** 
- The process of taking a larger network, and breaking it into more smaller networks (higher prefix)
- Split the original range into two. Increment the prefix. 

DDOS - Application Layer Attack
------------------------------------
- Attackes designed to overload websites
- Compete against legitimate connections
- Distributed - hard to block individual IPs/Ranges
- Application layer - HTTP flood
- Protocol Attack - SYN Flood
- Volumetric - DNS Amplification

SSL and TLS 
------------
- Privacy and data integrity between client and server
- Privacy - communications are encypted 
- asymmetric and then symmetric
- Identity ( server or client/server) verified
- Reliable connection - protect against alteration
- **Cipher Suites** - set of protocol used by Tls. 
- **Authentication** - Ensure the server certificate is authentic, verifying the server as legitimate. The client trusts the public CA - it makes sure that the cert is valid(date, and hasn't been revoked) and that the dns name matches the name/names on the cert. Proves the server id is valif from third party CA
- **Key Exchange** - Move from Asymmetric to Symmetric keys in a secure way and begin encryption process. The client generates the pre master key, encypts it with the servers public key and sends it to the server. - The server decrypts the pre master key using its private key. Both sides use the same pre master key to generate the master secret whihc is used to generate the ongoing session keys which encrypt and decrypt data.

AWS Fundamentals
=================
