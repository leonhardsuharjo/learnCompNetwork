Computer Network exam prep

I. Plan

* [X] Finalize subject notes perp
* [X] recap themes and topics involved
* [ ] review all books OR revised notes
* [ ] Finish review sample questions
* [ ] [optional] work on medium article

Exam first date = 19 January 2026

List of Internet Protocol layers, core of computer network

![1767972522611](image/prepexamCompNetwork/1767972522611.png)

Medium article proposal = TCP vs UDP, comparing the two

II. Course structure

* Chapter one -- introduction
  * whats internet and protocol
  * network edge
  * network core
  * performance = loss, delay, throughput
  * protocol layers, service models
  * security
  * history* (unnecessary topic)
* Chapter one part B -- introduction
  * ISO/OSI reference model
  * Transmission modes
  * Line configuration
  * unicast, broadcast, multicast
  * Topology
  * Area network types
  * IOT - networking trend*
* Chapter two -- application layer (first layer)
  * Principles of network applications
  * web and HTTP
  * email, SMTP, IMAP
  * Domain name system (DNS)
  * Video streaming and content distribution network (**CDN)**
  * Socket programming with UDP and TCP
* Chapter three -- Transport layer (second layer) -- software heavy
  * Transport layer services
  * multiplexing and demultiplexing
  * Connectionless transport -- UDP
  * Principles of reliable data transfer
  * Connection-oriented transport -- TCP
  * principles of congestion control
  * TCP congestion control
  * Evolution of transport-layer functionality
* Chapter four -- Network layer (third layer) -- soft/hardware hybrid
  * Layer overview - services and protocols
    * Data plane
    * Control plane
  * Inside a router
    * input/output ports, switching
    * buffer management
    * scheduling
  * IP - internet protocol
    * Datagram format, addressing
    * Network address translation (NAT)
    * IPv6 (difference with IPv4)
  * Generalized Forwarding
    * match+action
    * openflow
    * middleboxes
  * Internet architecture
* Chapter four part B -- Internet protocol specific
  * IPv4, IPv6,
  * Reserved address
  * Address classes
  * Subnet mask
  * Boolean algebra for IP address
* Chapter five -- network layer control plane -- router to router communication
  * introdudction
  * routing protocols
    * link state
    * distance vector
  * intra-ISP routing: OSPF
  * Routing among ISPs : BGP
  * SDN control plane
  * Internet control message protocol
  * Network management, config
    * SNMP and Netconf/YANG
* Chapter six -- Link layer and LAN
  * introduction
  * error detection and correction
  * multiple access protocols
  * LAN (Local area network)
    * addressing
    * ethernet
    * switches
    * VLAN
  * link virtualization: MPLS
  * Data center networking
  * web request recap

Deep review 12/01/26

Computer networks enable communication between devices through standardized protocols and infrastructure.

1. Chapter 1: Network fundamentals =
   1. chap 1.1 architecture
      1. Network Edge = Access Networks
         1. act as end systems like computers or mobile devices; serve as data destinations; connected through access networks to the core internet
      2. Network Core = Responsible for routing packets between networks
         1. Mesh of interconnected routers and links, uses packet switching
      3. Network comm path = direct (same subnet), routed (through router to router), multihop (mutliple routers)
   2. chap 1.2 switching
      1. packet switching == Breaking messages into packets and transmitting them individually through the network. -- publicly used network
      2. Circuit switching == End-to-end resources allocated for transmission between source and destination. -- one dedicated path
         1. connection established before transmission; resources dedicated to a single activity, no data congestion; diasdv cannot manage many simulatenous data transfer due to resource dedication
   3. Chap 1.3 network performance metrics and terms
      1. Processing delay = time to examine packet header
      2. Queueing delay = time packet waits in output queue
      3. Transmission delay = time to push packet bits onto link; formula = PacketLength / LinkRate
      4. Propagation delay = time for signal to travel physical medium
      5. Packet loss = occur when packet arrives at full buffer, loss probability increase with traffic intensity
      6. Traffic intensity = Ratio of average packet arrival rate to transmission rate
      7. Throughput = Rate at which bits are received (bits/time unit)
   4. Chap 1.4 internet terms
      1. RFC Request for Comments = Documents specifying Internet protocols and standards
      2. IETF (Internet Engineering Task Force) = Organization that develops Internet standards
2. Chapter two -- network model and architecture
   1. chap 2.1 ISO/OSI Reference Model (7 Layers) -- down to top -- sometimes can be 5 layers

      1. Physical = Transmission of raw bits over physical medium, hardware
      2. Data link = Frame formatting and delivery between adjacent nodes, Hardware addressing (MAC addresses)
      3. Network = Logical addressing (IP addresses) and routing, Routing algorithms and path selection like ipv6
      4. Transport = Process-to-process communication, like **TCP, UDP**
      5. Session (not in internet stack) = Synchronization and dialogue control, implemented in application layer if needed
      6. Presentation (not in internet stack) = Compression, encryption/decryption
      7. Application = Network services for end users and applications, example HTTP
   2. Chap 2.2 TCP IP reference model (simplified model) -- top to down

      1. application
      2. transport
      3. Internet (network)
      4. Link
      5. physical
   3. TCP ip model has less layers, more reliable/tested, and the de facto standard  with less strict boundaries. while osi layer is more theoretical, less reliable
3. Chapter three Network Transmission and Configuration
   1. Chap 3.1 transmission mode
      1. Simplex (Unidirectional) = Communication in one direction only, One device transmits, other only receives, Examples: Keyboard-monitor
      2. Half-Duplex (Bidirectional, Not Simultaneous) = Both devices can transmit and receive, but not simultaneously, Devices take turns transmitting, example walkie talkie
      3. Full-Duplex (Bidirectional, Simultaneous) = Both devices transmit and receive simultaneously, Capacity divided between two directions, example modern phone
   2. Chap 3.2 Line config

Chapter list AI PDF =

* Computer Networks: Comprehensive Study Guide
  * Introduction to Computer Networking
  * **Chapter 1: Network Fundamentals**
    * 1.1 Network Architecture Overview
      * Network Edge and Core
      * Network Communication Paths
    * 1.2 Network Switching Approaches
      * Packet Switching
      * Circuit Switching
    * 1.3 Network Performance Metrics
      * Packet Delay Components
      * Packet Loss
      * Traffic Intensity
      * Throughput
    * 1.4 Internet Standards
  * > **Chapter 2: Network Models and Architectur**e* 2.1 ISO/OSI Reference Model (7 Layers)
    > * 2.2 TCP/IP Reference Model (4-5 Layers)
    > * 2.3 OSI vs TCP/IP Comparison
    >
  * Chapter 3: Network Transmission and Configuration
    * 3.1 Transmission Modes
      * Simplex (Unidirectional)
      * Half-Duplex (Bidirectional, Not Simultaneous)
      * Full-Duplex (Bidirectional, Simultaneous)
    * 3.2 Line Configuration
      * Point-to-Point (Dedicated Link)
      * Multipoint (Multi-drop)
    * 3.3 Network Addressing and Communication
      * Unicast (One-to-One)
      * Broadcast (One-to-All)
      * Multicast (One-to-Many)
  * Chapter 4: Network Topologies
    * 4.1 Mesh Topology
    * 4.2 Star Topology
    * 4.3 Bus Topology
    * 4.4 Ring Topology
    * 4.5 Tree Topology
  * Chapter 5: Types of Networks
    * 5.1 Local Area Network (LAN)
    * 5.2 Metropolitan Area Network (MAN)
    * 5.3 Wide Area Network (WAN)
    * 5.4 Other Network Types
  * Chapter 6: The Internet and Network Access
    * 6.1 Internet Service Providers (ISPs)
    * 6.2 Access Network Technologies
      * Cable-Based Access (HFC - Hybrid Fiber-Coax)
      * Digital Subscriber Line (DSL)
      * Wireless Access
    * 6.3 Home Network Architecture
  * Chapter 7: Physical Media
    * 7.1 Directed Media (Guided)
      * Twisted-Pair Cable
      * Coaxial Cable
      * Fiber Optic Cable
    * 7.2 Undirected Media (Unguided - Wireless)
      * Terrestrial Radio
      * Characteristics of Wireless
  * **Chapter 8: Application Layer Fundamentals**
    * 8.1 Application Architecture Models
      * Client-Server Architecture
      * Peer-to-Peer (P2P) Architecture
    * 8.2 Processes and Communication
      * Processes
      * Sockets
    * 8.3 Process Addressing
      * Identifying Processes
    * 8.4 Application-Layer Protocols
  * **Chapter 9: Hypertext Transfer Protocol (HTTP)**
    * 9.1 Web Fundamentals
    * 9.2 HTTP Overview
    * 9.3 HTTP Connections
      * Non-Persistent HTTP
      * Persistent HTTP (HTTP/1.1)
    * 9.4 HTTP Request Message Structure
    * 9.5 HTTP Methods
    * 9.6 HTTP Response Message
    * 9.7 Maintaining State: Cookies
    * 9.8 Web Caching (Proxy Servers)
  * **Chapter 10: Email Systems**
    * 10.1 Email Architecture
    * 10.2 SMTP Protocol
    * 10.3 Email Retrieval: IMAP
  * **Chapter 11: Domain Name System (DNS)**
    * 11.1 DNS Overview
    * 11.2 DNS Services
    * 11.3 Why Not Centralize DNS?
    * 11.4 DNS Hierarchy
    * 11.5 DNS Query Process (Recursive Resolution)
    * 11.6 DNS Protocol Messages
    * 11.7 DNS Security Issues
  * > **Chapter 12: Transport Layer Overview*** 12.1 Transport Layer Functions
    > * 12.2 Multiplexing and Demultiplexing
    >   * Multiplexing (Sender Side)
    >   * Demultiplexing (Receiver Side)
    > * 12.3 Sockets
    >
  * > **Chapter 13: UDP (User Datagram Protocol**)* 13.1 UDP Overview
    > * 13.2 UDP Segment Structure
    > * 13.3 Checksum (Error Detection)
    > * 13.4 UDP Applications
    >
  * > **Chapter 14: TCP (Transmission Control Protoco**l)* 14.1 TCP Overview
    > * 14.2 TCP Segment Structure
    > * 14.3 TCP Connection Management
    >   * Three-Way Handshake (Connection Setup)
    >   * TCP Connection Termination (4-Way Handshake)
    > * 14.4 Reliable Data Transfer in TCP
    > * 14.5 Flow Control
    >
  * > **Chapter 15: Congestion Control*** 15.1 Congestion Overview
    > * 15.2 Congestion Control Approaches
    >   * End-to-End Congestion Control
    >   * Network-Assisted Congestion Control
    > * 15.3 TCP Congestion Control (AIMD)
    > * 15.4 TCP Slow Start
    > * 15.5 Fairness
    >
  * Chapter 16: Network Layer - Routing and Forwarding
    * 16.1 Network Layer Functions
      * Forwarding (Data Plane)
      * Routing (Control Plane)
    * 16.2 Forwarding Decision
    * 16.3 Router Architecture
    * 16.4 Input Port Processing
    * 16.5 Switching Fabrics
      * Switching via Memory
      * Switching via Bus
      * Switching via Interconnection Network
    * 16.6 Output Port Processing
  * Chapter 17: IP Protocol and Addressing
    * 17.1 IP Datagram Format
    * 17.2 IP Addressing
    * 17.3 IP Address Classes (Legacy)
    * 17.4 Subnet Mask and CIDR
  * Chapter 18: DHCP (Dynamic Host Configuration Protocol)
    * 18.1 DHCP Overview
    * 18.2 DHCP Process
    * 18.3 DHCP in Home Networks
  * Chapter 19: Network Address Translation (NAT)
    * 19.1 NAT Overview
    * 19.2 NAT Implementation
    * 19.3 NAT Advantages
    * 19.4 NAT Controversies
  * Chapter 20: IPv6
    * 20.1 IPv6 Motivation
    * 20.2 IPv6 Datagram Format
    * 20.3 IPv6 Adoption
    * 20.4 IPv6 Transition: Tunneling
  * Chapter 21: Link Layer Fundamentals
    * 21.1 Link Layer Services
    * 21.2 MAC Addresses
    * 21.3 ARP (Address Resolution Protocol)
  * Chapter 22: Securing Computer Networks
    * 22.1 Cybersecurity Threats
    * 22.2 Security Defenses
  * Conclusion
