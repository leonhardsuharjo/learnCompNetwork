Computer Network exam prep

I. Plan

* [X] Finalize subject notes perp
* [X] recap themes and topics involved
* [X] review all books OR revised notes -- only essential chapters reviewed done
* [ ] Finish review sample questions -- total 150 sample questions
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

---

Deep review 12/01/26

Computer networks enable communication between devices through standardized protocols and infrastructure.

Chapter 1: Network fundamentals =

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

Chapter two -- network model and architecture

1. chap 2.1 **ISO/OSI Reference Model** (7 Layers) -- down to top -- sometimes can be 5 layers

   1. Physical = Transmission of raw bits over physical medium, hardware
   2. Data link = Frame formatting and delivery between adjacent nodes, Hardware addressing (MAC addresses)
   3. Network = Logical addressing (IP addresses) and routing, Routing algorithms and path selection like ipv6
   4. Transport = Process-to-process communication, like **TCP, UDP**
   5. Session (not in internet stack) = Synchronization and dialogue control, implemented in application layer if needed
   6. Presentation (not in internet stack) = Compression, encryption/decryption
   7. Application = Network services for end users and applications, example HTTP
2. Chap 2.2 **TCP IP reference model** (simplified model) -- top to down

   1. application
   2. transport
   3. Internet (network)
   4. Link
   5. physical
3. TCP ip model has less layers, more reliable/tested, and the de facto standard  with less strict boundaries. while osi layer is more theoretical, less reliable

Chapter three Network Transmission and Configuration

1. Chap 3.1 transmission mode
   1. Simplex (Unidirectional) = Communication in one direction only, One device transmits, other only receives, Examples: Keyboard-monitor
   2. Half-Duplex (Bidirectional, Not Simultaneous) = Both devices can transmit and receive, but not simultaneously, Devices take turns transmitting, example walkie talkie
   3. Full-Duplex (Bidirectional, Simultaneous) = Both devices transmit and receive simultaneously, Capacity divided between two directions, example modern phone
2. Chap 3.2 Line config -- [**skip first to key chapters]**

Chapter twelve - Transport layer overview

12.1 Transport layer functions

1. Definition of trans layer = Provides process-to-process communication
2. Key difference: network layer is host to host while transport layer is process to process

12.2 multiplexing and demultiplexing

1. multiplexing (sender side) = collecting data from sockets, one host handle multiple apps simulatenously
2. demultiplexing (reciever side) =  Delivering received segments to correct socket/application
   1. Types of demultiplexing
      1. Connectionless (UDP) =

         1. Form = Source IP, Source Port, Destination IP, Destination Port
         2. stateless, no connection setup,
      2. connection oriented (TCP) =

         1. Form = same four fields
         2. Connectionbased, can have multiple connections to same port

12.3 Sockets

1. Socket concept  = Endpoint of network communication, Identified by (IP address, Port number)
2. Socket types =
   1. Stream socket = TCP, reliable, ordered delivery
   2. Datagram socket = UDP, unreliable, unordered

Chapter 13 -- **UDP (user datagram protocol) specific**

1. main characteristic = unreliable data transfer, connectionless, min overhead, fast delivery, no congestion control
2. Segment strucutre = Source Port (16 bits) | Destination Port (16 bits) Length (16 bits) | Checksum (16 bits) [Application data]

   1. - **Source Port**: Sending process's port
   2. - **Destination Port**: Receiving process's port
   3. - **Length**: Header + data length
   4. - **Checksum**: Error detection (optional)
3. Checksum (specific) = purpose, to detect *bit errors* in segment

   1. process = sender add 16 bit words, take one's complement (flip bits), include in checksum field, if all result is 1, no error detected.
4. UDP usage =

   1. Streaming media = Audio/video where occasional loss acceptable
   2. **Online Gaming**: Low latency more important than reliability
   3. **DNS Queries**: Simple request-response
   4. **IoT Sensors**: Small data bursts, high volume
5. **Advantage**: No connection overhead, lower latency

Chapter 14 -- TCP (Transmission Control Protocol)

1. main charac = reliable data transfer, connection oriented (setup, data, teardown), Flow control (receiver controls sender), - Congestion control (sender adapts to network), - Ordered delivery, relatively complex
2. Segment format =

   1. **Port Numbers**: Source and destination process ports
   2. **Sequence Number**:
   3. - Position of first data byte in segment
   4. - Sender increments for each byte sent
   5. - Prevents duplicate/out-of-order delivery
   6. **Acknowledgement Number**:
   7. - Next expected sequence number
   8. - Receiver acknowledges reception
   9. - Cumulative ACK: Acknowledges all bytes up to this number
   10. * **Header Length**: Variable length header
   11. **Flags**:
   12. - **SYN**: Synchronize (connection setup)
   13. - **ACK**: Acknowledgement valid
   14. - **FIN**: Finish (connection close)
   15. - **RST**: Reset connection
   16. - **PSH**: Push data to application
   17. - **URG**: Urgent data
   18. **Receive Window**: Flow control
   19. - How much data receiver can accept
   20. - Sender shouldn't exceed this
   21. **Checksum**: Error detection (mandatory in TCP)
3. Connection management

   1. Three way handshake
      1. Syn = Client announces readiness to connect
      2. Syn-ack = Server confirms and sends own sequence
      3. Ack = Client confirm connection established
   2. TCP Connection termination (4-Way Handshake)
      1. * Client sends FIN (finish flag)
      2. * Server acknowledges with ACK
      3. * Server sends its FIN
      4. * Client acknowledges with ACK
      5. Connection closed gracefully
4. Reliable data transfer in TCP mechanism

   1. Sequence number = detect out of order segment and duplicate segments
   2. Acknowledgement = receiver confirm reception
   3. Retransmission = if no ack received after timeout, retransmit
5. Flow control = when receiver limit/control senders rate to not be overwhelmed, done by indicating how much data can the receiver accept in the ACK message.

Chapter 15 -- congestion control

1. Congestion = Too many sources sending too much data too fast for network to handle
2. Aproaches of cong control = endtoend (senderside), network-assisted (using router's help, used in TCP)
3. TCP congestion control -- Additive Increase, Multiplicative Decrease (AIMD) = automatically decrease or increase **throughput** depending when no packet loss detected or when congestion detected, congestion == packet loss; linear increase and **sharp decrease**
4. TCP slow start = start with small throughput, increase slowly
5. TCP fairness = muultiple flow share bandwidth fairly; UDP is not fair

---

Question review 17/01/25

Batches upload wont work, need to review individually

Whatsapp direct review with perplexity, WIT = what is true when talking about [concept] question type, WITF = what is the function, NCQ = numbers calculation question, SRA = select right answers, WH = what happens, CQ = coding question

1. Taking turns protocol on MAC protocol true statement = Master node invites other nodes to transmit in turn
2. WIT direct broadcast = direct broadcast is useful when a device in one network wants to transfer packet stream to all the devices over the other network
3. WIT Client server = client server is when computers provide resources and offer services to other computers
4. WIT direct broadcast = Direct broadcast sends packets to all devices on a different network (subnet broadcast across routers), often used for network discovery
5. in BGP (border gateway protocol), which attribute identifies the router within the AS (autonomous systems) for forwarding packet to destination = the NEXT-HOP attribute, where it specifies the IP address of the next router that should receive the packet to reach the destination.
6. WIT UDP = it is a connectionless protocol
7. which application layer protocol used to support email = SMTP
8. What is subnet mask used for (in IP addressing) = to define network and host portions of an address
9. How to send http request to create pizza = The code with r = requests.post(url, data=body, headers=headers) (the one using **POST** method with pathname='/products', JSON body {"pizza": 1, "water": 6}, and Content-Type: application/json headers)
10. Primary use of djikstra algorithm = Calculate least cost path from a source node to all other nodes
11. Application layer protocol to download an email from mailbox server to client = POP (used for retrieving/downloading mail to the client)
12. what is Throughput = rate (bits/time unit) at which bits are being sent from sender to receiver
13. What is purpose of multiplexing in **transport** layer = To handle data from multiple sockets for transmission
14. what information does an **IMCP** **message** when reporting error = Type, code, and the first 8 bytes of the IP datagram causing the error.
15. What is encapsulated within a frame at link layer = IP datagram ; At the link layer, a frame carries the network-layer packet (an IP datagram) as its payload. --- progress 19:22, 13/100 ----
16. How many **bits** is the **mac address** = 48 bits long
17. Method of socket module to assosciate host, port with socjeTo associate a host (IP) and a port with a specific socket in Python, use socket.bind((IP, PORT)) (i.e., the bind(IP,PORT) option).
18. WITF UDP's **checksum** = detect errors in transmitted segement
19. WITF tcp **3way** handshake **=** to establish connection and set the connection parameters
20. Considering ISO osi stack what is the layer numb of physical layer = 1
21. WIT slotted aloha = time is divided into equal-size slots.
22. Which technique is used for error detection = Cyclic Redundancy Check (CRC)
23. What technique is used for transition from ipv4 to ipv6 = Tunneling; carrying an IPv6 datagram as payload inside an IPv4 datagram across IPv4 routers
24. consider ISO stack what is layer number of application layer = 7
25. which method of socket module allow server socket to accept request from client socket from another host = socket.accept()
26. WIT **FDMA** (Frequency Division Multiple Access) = each station assigned fixed frequency band
27. Socket module method allow to send data to a given address = socket.sendto**(data, address)**
28. WIT http = HTTP connection can be both persistent and non-persisten
29. WIT unicast = this type of information transfer is useful when there is a participation of single sender and single recipient
30. WIT direct limited broadcast = this is useful when a device in one network wants to transfer packet stream to all the devices over the other network

    1. Types of broadcast = multicast (one/more sender to one/more receipent), unicast (one2one), direct limited (one to many)
31. what is purpose of link layer = Transferring data between adjacent nodes in a network.
32. what is TCP sequence number = byte stream number of first byte in segment’s data, sequence number counts bytes NOT segment
33. key benefit of MPLS (multiprotocol label switching) = It allows high-speed IP forwarding
34. when queue buffer fill up the packet is = dropped
35. what is NOT common intra AS (autonomous system) routing protocol = Time division multiple access. -- progress 18/01/25 01:10  32 / 100 ---
36. Bandwidth is = amount of data that can be transmitted in a fixed amount of time

    1. bandwidth != Throughput ; Throughput = ACTUAL data rate achieved in practice
37. NCQ; between two hosts H1 and H2, intended = 10 bits from H1 to router R1, timedelay = 5 sec/bit, distance or length L1 = 20 mt, propagation speed = 2 mt/sec, how long till packet arrives at router R2 = short answer 60 seconds

    1. Tranmission delay R1 to R2 = 10 bits x 5 sec = 50 sec
    2. Propagation delay = distance // speed = 20 // 2 = 10 sec
    3. Total delay or time = 50 + 10 = 60
38. correct HTTP method to delete a resource in a RESTful web service = DELETE

    1. restful web services support total client-server separation
39. What network address class reserved for multicast groups and not assignable individually = IPv4 Class D  is reserved for multicast groups and is not assignable to individual hosts
40. NCQ; intended packet length = 20 bits H2 to R1, time = 10 second / 1 bit, link distance = 20 mt, propagation speed = 10 mt / sec

    1. transdelay = 20 x 10 = 200 seconds
    2. prop delay = 20 / 10 = 2 second
    3. total = 202 seconds --- progress 13:56 pg 41 /100 ---
41. WIT client-server model = computers provide resources and offer services to other computers
42. SRA Dynamic Adaptive Streaming (DAS) =

    1. Each chunk is **encoded** at multiple different rates → server
    2. Periodically **estimates** server-to-client bandwidth → client
    3. **Divides** video file into multiple chunks → server.
43. WIT HTTP = http is stateless
44. WIT **cookies** = Websites and client browser use cookies to maintain some state between transactions
45. what information does ICMP **error message** include = ype, code, and the first 8 bytes of the IP datagram causing the error.
46. WH when switch receive frame with destination mac address not on its table = it broadcast the frame on all interfaces except the one it arrived on
47. What is hot potato routing = A routing strategy based on the lowest intra-AS cost.
48. How does ipv6 address ipv4 limitation = using a much larger 128-bit address space -- 83 / 100 --
49. WH if a frame with error is detected at link layer = it is dropped or retransmitted
50. Client wants to **send** a http request message to a website over a given port, to a pathname to receive a json body (packet) = use **POST** protocol

    1. POST /feedrss HTTP \r\n Host: replubblica.it \r\n content-type \r\n content-length \r\n
51. role of MAN = network that connects two or more computers that are apart but reside in the same or different cities,
52. [incomplete question] given transport layer scenario image with three connectionless hosts, what are the tuples required by the segments? = The required tuple for each connectionless (UDP-over-IP) segment is (source IP, source port, destination IP, destination port)
53. WIT peer to peer (p2p) = computers have both the client and server roles at the same time
54. WIT simplex = communication is unidirectional, as on a one-way street
55. MAC and ip diff = mac unique to device, ip depends on location

    1. mac address is 48 bits long, ip is 32 or 128
56. what is Cumulative acknowledgement in TCP = Acknowledging all segments up to and including a specific sequence number.
57. WIT 'Time to live' header field in IP datagram = It can be used to prevent packet looping. --progress 100/100 done --
58. --- Review 19/01/26 start 1/45--- what is function of ARP table in a host = To store a mapping of IP addresses to MAC addresses
59. Primary goal of Network address translation = Allow multiple devices to share a single public IP address
60. WIT HTTP = HTTP connection can be both persistent and non-persistent.
61. what is the **DNS server** responsible for .com and toplevel country domain = Top‑Level domain server ; other types like Root DNS servers (The “starting point” when no answer for resolver yet), Authoritative DNS servers (The final form like amazon.com), local dns or web cache (Local The DNS server your host contacts first, cache dns address)
62. which protocol to map IP address to MAC address in LAN = ARP (Address Resolution Protocol).
63. what is the goal operation of **NETCONF** protocol = Manage and configure devices network-wide
64. IPv4 format, number of networks allowed under **class C** addresses = 2^21 ; class address includes class A to E
65. VLAN acronym meaning = virtual local area network
66. Adv of **centralized control plane** = easier network management
67. WIT **half duplex** = it is used in cases where there is no need for communication in both directions at the same time.
68. SDN acronym = software defined networking
69. WIT LAN = group of comp and dev connected by switch or stack of em using a pivate addressng scheme TCP Ip protocol
70. UDP = unreliable and connectionless
71. IPv4 format, number of networks allowed under **class A** addresses = 2^7
72. CQ, send http request to /products to make pizza in shopping list = code structure protocol + hostname + pathname
73. what does DHCP provide to client device = IP address and configuration information.
74. protocol used for routing between ISP = Border Gateway Protocol (BGP)
75. In the **OSI model, the layers (top → bottom)** are: Application (7), Presentation (6), Session (5), Transport (4), Network (3), Link/Data Link (2), Physical (1) ; in the internet model its the opposite starting from application to physical (5)
76. which field in tcp header is used for **flow control** = receive window --- 145 questions review done --- 

---

########

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
    >
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
    >
    > * 12.2 Multiplexing and Demultiplexing
    >   * Multiplexing (Sender Side)
    >   * Demultiplexing (Receiver Side)
    > * 12.3 Sockets
    >
  * > **Chapter 13: UDP (User Datagram Protocol**)* 13.1 UDP Overview
    >
    > * 13.2 UDP Segment Structure
    > * 13.3 Checksum (Error Detection)
    > * 13.4 UDP Applications
    >
  * > **Chapter 14: TCP (Transmission Control Protoco**l)* 14.1 TCP Overview
    >
    > * 14.2 TCP Segment Structure
    > * 14.3 TCP Connection Management
    >   * Three-Way Handshake (Connection Setup)
    >   * TCP Connection Termination (4-Way Handshake)
    > * 14.4 Reliable Data Transfer in TCP
    > * 14.5 Flow Control
    >
  * > **Chapter 15: Congestion Control*** 15.1 Congestion Overview
    >
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
