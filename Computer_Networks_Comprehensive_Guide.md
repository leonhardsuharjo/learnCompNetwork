# Computer Networks: Comprehensive Study Guide

## Introduction to Computer Networking

Computer networks enable communication between devices through standardized protocols and infrastructure. Understanding networks requires knowledge of multiple layers working together in a hierarchical structure. This guide covers the fundamental principles and practical concepts essential for mastering computer networking.

---

## Chapter 1: Network Fundamentals

### 1.1 Network Architecture Overview

#### Network Edge and Core

The Internet consists of two main components:

**Network Edge (Access Networks):**

- End systems (hosts): computers, servers, mobile devices, IoT devices
- Serve as sources and destinations for data
- Connected through access networks to the core Internet
- Examples: home networks, enterprise networks, mobile networks

**Network Core:**

- Mesh of interconnected routers and links
- Responsible for routing packets between networks
- Forms the backbone of the Internet
- Uses packet switching to forward data

#### Network Communication Paths

- **Direct Connection**: Two hosts connected without intervening router (via same subnet)
- **Routed Path**: Communication between different subnets passes through routers
- **Multi-hop**: Data traverses multiple routers to reach destination

### 1.2 Network Switching Approaches

#### Packet Switching

**Definition**: Breaking messages into packets and transmitting them individually through the network.

**Process**:

1. Takes a message to be sent
2. Breaks it into smaller packets of length L bits
3. Transmits each packet at transmission rate R (bits/second)
4. Routers forward packets toward destination using forwarding tables

**Key Characteristics**:

- Resources (links) are not reserved
- Packets may take different paths to same destination
- Routers examine packet headers to determine forwarding
- Can lead to congestion when arrival rate exceeds transmission rate

**Packet Transmission Delay**:
\[ d_{trans} = \frac{L}{R} \]
where L = packet length (bits), R = link transmission rate (bits/sec)

**Packet Propagation Delay**:
\[ d_{prop} = \frac{d}{s} \]
where d = distance of physical link, s = propagation speed in medium

**Advantages**:

- Efficient use of bandwidth
- Multiple users can share bandwidth
- Simpler to implement than circuit switching

**Disadvantages**:

- Packet loss possible when buffers full
- Variable delay due to queueing
- No guaranteed service quality

#### Circuit Switching

**Definition**: End-to-end resources allocated for transmission between source and destination.

**Characteristics**:

- Resources dedicated to a single activity
- No data congestion (guaranteed capacity)
- Connection established before data transmission
- Example: Traditional telephone networks

**Drawback**: Cannot process many simultaneous data transfers due to resource dedication.

### 1.3 Network Performance Metrics

#### Packet Delay Components

**Total nodal delay** comprises four components:

1. **Processing Delay (d_proc)**

   - Time to examine packet header
   - Determine output link
   - Check for bit-level errors
   - Typically microseconds
2. **Queueing Delay (d_queue)**

   - Time packet waits in output queue
   - Depends on congestion level
   - Highly variable and unpredictable
   - Dominant component under congestion
3. **Transmission Delay (d_trans)**

   - Time to push packet bits onto link
   - Equals L/R (packet length / link rate)
   - Determined by link bandwidth
   - Microseconds to milliseconds
4. **Propagation Delay (d_prop)**

   - Time for signal to travel physical medium
   - Determined by distance and propagation speed
   - Often 5-10 microseconds per kilometer
   - Relatively constant

**Total Delay Formula**:
\[ d_{nodal} = d_{proc} + d_{queue} + d_{trans} + d_{prop} \]

#### Packet Loss

- Occurs when packet arrives at full buffer (no available memory)
- Lost packets must be retransmitted (adds delay)
- Loss probability increases with traffic intensity
- Routers employ buffer management strategies to minimize loss

#### Traffic Intensity

**Definition**: Ratio of average packet arrival rate to transmission rate

\[ a = \frac{L \cdot A}{R} \]

where:

- a = traffic intensity
- L = packet length (bits)
- A = average packet arrival rate (packets/sec)
- R = transmission rate (bits/sec)

**Interpretation**:

- a ≈ 0: negligible queueing delay
- a → 1: queueing delay grows unbounded
- a > 1: system becomes unstable, packets arrive faster than transmission

#### Throughput

- **Definition**: Rate at which bits are received (bits/time unit)
- **End-to-end throughput**: Limited by bottleneck link with minimum capacity
- **Bottleneck link**: Link in path with minimum transmission rate
- Important consideration for data transfer applications

### 1.4 Internet Standards

**RFC (Request for Comments)**

- Documents specifying Internet protocols and standards
- Published and maintained by IETF
- Example: RFC 7230 (HTTP/1.1), RFC 3261 (SIP)

**IETF (Internet Engineering Task Force)**

- Organization that develops Internet standards
- Open participation model
- Technical discussions and consensus-based decision making

---

## Chapter 2: Network Models and Architecture

### 2.1 ISO/OSI Reference Model (7 Layers)

The Open Systems Interconnection model provides a conceptual framework for network communication:

1. **Physical Layer**

   - Transmission of raw bits over physical medium
   - Hardware: cables, modems, network interface cards
   - Standards: voltage levels, timing, mechanical specifications
2. **Data Link Layer**

   - Frame formatting and delivery between adjacent nodes
   - Hardware addressing (MAC addresses)
   - Error detection and correction
   - Examples: Ethernet, WiFi (802.11), PPP
3. **Network Layer**

   - Logical addressing (IP addresses) and routing
   - Moving packets from source to destination host
   - Routing algorithms and path selection
   - Example: IP protocol (IPv4, IPv6)
4. **Transport Layer**

   - Process-to-process communication
   - Reliable delivery, flow control, congestion control
   - Examples: TCP, UDP
5. **Session Layer** *(not in Internet stack)*

   - Synchronization and dialogue control
   - Checkpoints and recovery
   - Implemented in application layer if needed
6. **Presentation Layer** *(not in Internet stack)*

   - Data format translation and encryption
   - Compression, encryption/decryption
   - Character encoding conversion
   - Implemented in application layer if needed
7. **Application Layer**

   - Network services for end users and applications
   - Examples: HTTP, SMTP, DNS, SSH, FTP

### 2.2 TCP/IP Reference Model (4-5 Layers)

The actual Internet architecture, more practical than OSI:

1. **Application Layer**

   - All user applications and services
   - Includes both traditional "Application" and "Session"/"Presentation" functions
2. **Transport Layer**

   - TCP (reliable) and UDP (unreliable)
3. **Internet (Network) Layer**

   - IP protocol and routing
4. **Link (Data Link) Layer**

   - Ethernet, WiFi, PPP
5. **Physical Layer** *(sometimes considered part of Link layer)*

   - Actual transmission medium

### 2.3 OSI vs TCP/IP Comparison

| Aspect               | TCP/IP                | OSI                        |
| -------------------- | --------------------- | -------------------------- |
| Layers               | 4-5                   | 7                          |
| Development          | Protocols then model  | Model then protocols       |
| Reliability          | More reliable, tested | Less reliable, theoretical |
| Boundaries           | Less strict           | Very strict boundaries     |
| Adoption             | De facto standard     | Teaching framework         |
| Session/Presentation | In Application layer  | Separate layers            |

---

## Chapter 3: Network Transmission and Configuration

### 3.1 Transmission Modes

Describes how data flows between two devices:

#### Simplex (Unidirectional)

- **Definition**: Communication in one direction only
- **Characteristics**:
  - One device transmits, other only receives
  - Entire channel capacity used for one direction
  - Capacity = Bandwidth
- **Examples**: Keyboard-monitor, broadcast TV, satellite download

#### Half-Duplex (Bidirectional, Not Simultaneous)

- **Definition**: Both devices can transmit and receive, but not simultaneously
- **Characteristics**:
  - Devices take turns transmitting
  - Entire capacity used for each direction
  - Capacity = Bandwidth × Propagation Delay
- **Examples**: Walkie-talkie, two-way radio, traditional telephone

#### Full-Duplex (Bidirectional, Simultaneous)

- **Definition**: Both devices transmit and receive simultaneously
- **Characteristics**:
  - Capacity divided between two directions
  - Requires separate transmission path or frequency division
  - Capacity = 2 × Bandwidth × Propagation Delay
- **Examples**: Modern telephone, video conference, TCP connections

### 3.2 Line Configuration

Describes physical connection topology:

#### Point-to-Point (Dedicated Link)

- **Definition**: Direct, exclusive link between two devices
- **Characteristics**:
  - Entire capacity reserved for two endpoints
  - Simple and reliable
  - Higher cost per connection
- **Examples**: Direct fiber link between data centers, dial-up modem connection

#### Multipoint (Multi-drop)

- **Definition**: Two or more devices share a single link
- **Sharing Methods**:
  - **Spatial Sharing**: Multiple devices simultaneously transmit (e.g., Ethernet switch)
  - **Temporal Sharing**: Devices take turns (e.g., token ring)
- **Challenge**: Coordinate access to prevent collisions
- **Examples**: LAN with multiple computers, shared bus topology

### 3.3 Network Addressing and Communication

#### Unicast (One-to-One)

- **Definition**: Data transmission from one sender to one recipient
- **Characteristics**:
  - Most common form of communication
  - Point-to-point delivery
  - Example: HTTP request/response, email to single recipient
- **Destination**: Specific IP address

#### Broadcast (One-to-All)

- **Definition**: Data transmission from one sender to all devices on network
- **Types**:
  - **Limited Broadcast**: All ones address (255.255.255.255) - stays in local network
  - **Directed Broadcast**: Host bits all ones - broadcasts to specific network
- **Characteristics**:
  - All devices on network receive message
  - Network resources heavily used
  - Examples: ARP requests, DHCP discovery
- **Use Cases**: Finding devices, network announcements

#### Multicast (One-to-Many)

- **Definition**: Data transmission to specific group of recipients
- **Characteristics**:
  - Only interested devices receive message
  - Between unicast (targeted) and broadcast (untargeted)
  - Requires multicast group membership protocol (IGMP)
  - Examples: Video streaming to multiple viewers, online gaming
- **IP Address Range**: 224.0.0.0 to 239.255.255.255

---

## Chapter 4: Network Topologies

Network topology describes physical or logical arrangement of devices and connections:

### 4.1 Mesh Topology

- **Description**: Every device connected to every other device
- **Dedicated links**: One link between each pair
- **Total links**: N(N-1)/2 for N devices
- **Ports per device**: N-1
- **Advantages**:
  - Robust (failure of one link doesn't affect others)
  - Reliable data transmission
  - High security and privacy
  - Easy fault diagnosis
- **Disadvantages**:
  - Very expensive (many cables needed)
  - Difficult installation and configuration
  - High maintenance cost
  - Not practical for large networks

### 4.2 Star Topology

- **Description**: All devices connected to central hub/switch
- **Central node**: Controls communication
- **Examples**:
  - Ethernet with central switch
  - WiFi network with access point
  - Hub-and-spoke WAN design
- **Advantages**:
  - Easy to install and expand (only N cables needed)
  - Low cable cost
  - Centralized control and monitoring
- **Disadvantages**:
  - Central hub is single point of failure
  - Hub performance limits network
  - All traffic passes through center

### 4.3 Bus Topology

- **Description**: All devices connected to single backbone cable
- **Data flow**: Linear along cable
- **Characteristics**:
  - One backbone cable with drop lines to devices
  - Simple and inexpensive
  - Non-robust (cable failure brings down entire network)
- **Advantages**:
  - Minimal cable requirement (N drop lines)
  - Low cost for small networks
- **Disadvantages**:
  - Single point of failure (backbone)
  - Collision issues with heavy traffic
  - Difficult troubleshooting
  - Limited to small local networks
  - Collision handling protocols (CSMA/CD, ALOHA) required

### 4.4 Ring Topology

- **Description**: Devices connected in circular path
- **Data flow**: Unidirectional (can be dual ring for bidirectional)
- **Token Ring**: Uses token passing for access control
- **Characteristics**:
  - Each device has exactly two neighbors
  - Repeaters needed for long distances
  - Minimal collisions
- **Advantages**:
  - Equal access opportunity for all devices
  - Cheaper than mesh
  - Minimal collisions
- **Disadvantages**:
  - Ring break disrupts entire network
  - Difficult to add/remove devices
  - Node failure can break ring
  - Troubleshooting challenges

### 4.5 Tree Topology

- **Description**: Hierarchical topology with central hub and secondary hubs
- **Structure**:
  - Root (central hub) connects to tier-2 hubs
  - Tier-2 hubs connect to devices or further hubs
  - Creates hierarchical flow: top-to-bottom or bottom-to-top
- **Examples**:
  - Data center networks (core-aggregation-access layers)
  - Large enterprise networks
- **Advantages**:
  - Allows larger networks (reduces signal degradation)
  - Hierarchical organization and priority
  - Easier to scale than star
  - Network isolation possible
- **Disadvantages**:
  - Central hub failure causes total network failure
  - Higher cable and equipment cost
  - Complex configuration and management

---

## Chapter 5: Types of Networks

### 5.1 Local Area Network (LAN)

**Definition**: Network connecting devices in limited geographical area with high-speed connections.

**Characteristics**:

- **Coverage**: Few kilometers or less (typically within building)
- **Speed**: 100 Mbps - 10 Gbps (fast)
- **Ownership**: Privately owned
- **Delay**: Very short (microseconds to milliseconds)
- **Error Rate**: Low (short distance)
- **Devices**: Switches, network adapters, Ethernet cables
- **Usage**: Office building, campus, home

**Technologies**:

- Ethernet (wired)
- WiFi/802.11 (wireless)
- Twisted-pair or coaxial cables
- High-speed connections

**Fault Tolerance**: Good (isolated network segments)

### 5.2 Metropolitan Area Network (MAN)

**Definition**: Network covering larger area than LAN but smaller than WAN.

**Characteristics**:

- **Coverage**: City or region (5-50 km)
- **Speed**: Mbps range (slower than LAN, faster than WAN)
- **Ownership**: May be privately owned or operated by service provider
- **Delay**: Moderate
- **Error Rate**: Moderate
- **Usage**: City-wide network, connecting multiple buildings
- **Examples**:
  - Cable TV network serving city
  - DSL service from telephone company
  - Municipal WiFi networks

**Fault Tolerance**: Less than LAN

### 5.3 Wide Area Network (WAN)

**Definition**: Network spanning large geographical distances, potentially across states or countries.

**Characteristics**:

- **Coverage**: City, state, country, or globe
- **Speed**: Kilobits to megabits per second (slowest)
- **Ownership**: Usually operated by service providers (public)
- **Delay**: High (potentially seconds)
- **Error Rate**: Higher (long transmission distances)
- **Transmission Medium**:
  - Satellite links
  - Microwave transmission
  - Optical fiber (long distance)
  - Leased telephone lines
- **Usage**: Internet, corporate networks spanning offices

**Types**:

- **Switched WAN**: Uses switching technology (ATM)
- **Point-to-Point WAN**: Dial-up connections, dedicated leased lines

**Fault Tolerance**: Less fault tolerant than LAN

### 5.4 Other Network Types

- **PAN (Personal Area Network)**: Device-to-device (Bluetooth, NFC)
- **CAN (Campus Area Network)**: Single campus or facility
- **SAN (Storage Area Network)**: Specialized high-speed network for storage
- **EPN (Enterprise Private Network)**: Organization's private network
- **VPN (Virtual Private Network)**: Encrypted connection over public network

---

## Chapter 6: The Internet and Network Access

### 6.1 Internet Service Providers (ISPs)

**Hierarchical Structure**:

```
End Users → Local/Regional ISP → Global Transit ISP → Internet Exchange Points
```

**Components**:

- **Local ISP**: Connects individual customers and small businesses
- **Regional ISP**: Connects multiple local ISPs
- **Global Transit ISP**: Interconnects regional networks
- **Internet Exchange Points (IXPs)**: Where ISPs peer and exchange traffic
- **Cache Data Centers**: Content servers placed closer to users

**Functions**:

- Provide Internet connectivity
- Route traffic between networks
- Manage network infrastructure
- Offer bandwidth aggregation

### 6.2 Access Network Technologies

#### Cable-Based Access (HFC - Hybrid Fiber-Coax)

- **Downstream**: Frequency division multiplexing (FDM) - different channels on different frequencies
- **Upstream**: Time division multiplexing (TDM) - time slots divided among users
- **Speed**: Asymmetric (faster download than upload)
- **Shared medium**: All users in cable segment share upstream/downstream capacity

#### Digital Subscriber Line (DSL)

- **Technology**: Uses existing copper telephone lines
- **Modems**: Separate upstream/downstream frequencies
- **Speed**: Asymmetric (faster downstream)
- **Distance Limited**: Quality decreases with distance from central office
- **Advantage**: Uses existing infrastructure

#### Wireless Access

- **WLAN (802.11/WiFi)**: Wireless LAN in building
- **Wide Area Cellular**: 4G, 5G mobile networks
- **Satellite**: Internet via satellite (high latency)
- **Bluetooth**: Personal area networks (short range)

### 6.3 Home Network Architecture

Modern home networks combine:

- **Modem**: Connects to ISP access link
- **Router**: Distributes connectivity
- **WiFi Access Point**: Wireless connectivity
- **Wired Ethernet**: Optional direct connections
- Often combined into single unit for convenience

---

## Chapter 7: Physical Media

### 7.1 Directed Media (Guided)

#### Twisted-Pair Cable

- **Description**: Two insulated copper wires twisted together
- **Specifications**:
  - Category 5 (Cat-5): 100 Mbps
  - Category 6 (Cat-6): 1 Gbps
  - Category 6A (Cat-6A): 10 Gbps
- **Advantages**: Inexpensive, widely deployed
- **Disadvantages**: Susceptible to interference, limited distance
- **Usage**: Ethernet (LAN), telephone lines

#### Coaxial Cable

- **Description**: Copper conductor surrounded by insulation, shield, and outer conductor
- **Structure**: Inner conductor | Insulation | Braided shield | Outer sheath
- **Advantages**: Better shielding than twisted pair
- **Disadvantages**: More expensive, bulkier
- **Usage**: Cable television, some older Ethernet (10BASE-2)

#### Fiber Optic Cable

- **Description**: Glass fiber carrying light pulses
- **Advantages**:
  - Very high bandwidth
  - Long distance (no repeaters needed)
  - Immune to electromagnetic interference
  - Small size and weight
  - Secure (hard to tap)
- **Disadvantages**:
  - Expensive installation and equipment
  - Requires special equipment for connections
  - Fragile compared to copper
- **Usage**: Long-distance backbone networks, undersea cables, fiber-to-home

### 7.2 Undirected Media (Unguided - Wireless)

Communication through electromagnetic radiation:

#### Terrestrial Radio

- **Wireless LAN (WiFi)**: 2.4 GHz and 5 GHz bands, up to 1+ Gbps
- **Cellular Mobile**: 4G, 5G networks
- **Terrestrial Microwave**: Point-to-point links, towers needed
- **Satellite**: Geostationary or Low-Earth-Orbit, high latency

#### Characteristics of Wireless

- **Path Loss**: Signal strength decreases with distance (inverse square law)
- **Shadowing**: Large obstacles block signal
- **Fading**: Multipath propagation causes signal variations
- **Interference**: Other transmitters on same frequency
- **Atmospheric Absorption**: Water vapor, oxygen absorption

---

## Chapter 8: Application Layer Fundamentals

### 8.1 Application Architecture Models

#### Client-Server Architecture

- **Server**:

  - Always-on host
  - Permanent IP address
  - Located in data center for scalability
  - Services many clients
  - Scaling strategies:
    - Vertical: Increase CPU/RAM (limited)
    - Horizontal: Add more servers (preferred)
- **Client**:

  - Contacts server for service
  - May be intermittently connected
  - Dynamic IP address
  - Does not communicate directly with other clients
  - Examples: HTTP, IMAP, FTP

#### Peer-to-Peer (P2P) Architecture

- **No always-on server**
- **Direct communication** between arbitrary end systems
- **Self-scalability**: New peers bring both service capacity and demand
- **Intermittent connectivity**: Peers come and go
- **Examples**: BitTorrent, P2P file sharing
- **Advantages**: No central server, scalable
- **Challenges**: Complex, difficult to manage and monitor

### 8.2 Processes and Communication

#### Processes

- **Definition**: Program running within a host
- **Inter-process Communication (IPC)**: Same host processes communicate via OS
- **Network Communication**: Different hosts communicate via messages
- **Client vs Server Process**:
  - Client: Initiates communication
  - Server: Waits for and responds to requests

#### Sockets

- **Definition**: Interface between application and transport layer
- **Analogy**: Door through which process sends/receives messages
- **Location**: Between application and transport layer
- **Function**: Application sends message to socket, transport layer delivers
- **Types**: TCP socket (stream), UDP socket (datagram)

### 8.3 Process Addressing

#### Identifying Processes

- **Host identification**: 32-bit IP address
- **Process identification**: Port number
- **Complete address**: (IP address, port number)
- **Well-known ports**:
  - HTTP: 80
  - HTTPS: 443
  - SMTP: 25
  - DNS: 53
  - SSH: 22

### 8.4 Application-Layer Protocols

**Protocol Definition**: Set of rules governing message exchange

**Protocol Components**:

- **Message Types**: Request, response, notification
- **Message Syntax**: Field names, field lengths, delimiters
- **Message Semantics**: Meaning of fields and actions
- **Rules**: When to send, how to respond
- **Standards**: Open (RFC) or proprietary

**Transport Service Requirements**:

- **Data Integrity**:
  - Reliable delivery: File transfer, email, web transactions
  - Loss-tolerant: Audio/video streaming
- **Timing**:
  - Low delay required: Interactive voice, gaming
  - Delay-tolerant: Email, file transfer
- **Throughput**:
  - Minimum bandwidth: Multimedia applications
  - Elastic: Can use available bandwidth (email, web)
- **Security**:
  - Encryption: Sensitive data
  - Authentication: Identify users
  - Integrity: Prevent tampering

---

## Chapter 9: Hypertext Transfer Protocol (HTTP)

### 9.1 Web Fundamentals

**Web Page Structure**:

- Collection of objects (files) stored on different servers
- Base HTML file with references to other objects
- Each object has unique URL

**URL Components**:

```
www.someschool.edu/someDept/pic.gif
├─ Host name: www.someschool.edu
└─ Path name: /someDept/pic.gif
```

### 9.2 HTTP Overview

**Definition**: Application-layer protocol for web communication

**Model**:

- Client-server paradigm
- Client (browser): Requests objects
- Server: Sends objects in response
- TCP connection: Port 80 (443 for HTTPS)

**Stateless Protocol**:

- Server maintains no information about past client requests
- Each request independent
- Simplifies implementation
- Limitation for multi-step transactions (solved by cookies)

### 9.3 HTTP Connections

#### Non-Persistent HTTP

- **Process per object**:
  1. Client opens TCP connection
  2. Client sends HTTP request
  3. Server sends response with one object
  4. TCP connection closes
  5. Repeat for each object
- **Delay**: 2 × RTT per object
  - 1 RTT to establish TCP connection
  - 1 RTT for request and first response bytes
  - Plus transmission time
- **Disadvantage**: Multiple connections have overhead

#### Persistent HTTP (HTTP/1.1)

- **Multiple objects** over single TCP connection
- **Server leaves connection open** after sending response
- **Client sends requests** as soon as encountering references
- **Delay**: As little as 1 RTT for all objects
- **Improvement**: Cuts response time in half compared to non-persistent

### 9.4 HTTP Request Message Structure

**Format**: ASCII text (human-readable)

```
GET /path/file.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html
Connection: keep-alive

[Entity body - optional]
```

**Components**:

1. **Request Line**:

   - Method (GET, POST, HEAD, PUT, DELETE)
   - URL (path of object)
   - HTTP version
   - Example: `GET /index.html HTTP/1.1`
2. **Header Lines**:

   - Additional information
   - Format: `HeaderFieldName: Value`
   - Examples:
     - `Host`: Identify server
     - `User-Agent`: Browser type
     - `Accept`: Acceptable file types
     - `Connection`: Keep-alive or close
3. **Entity Body**: (Optional)

   - Message payload
   - Used with POST/PUT requests
   - Contains form data or file content

### 9.5 HTTP Methods

- **GET**: Request object at specified URL

  - Data in URL query string
  - Limited data size
  - Cached by browsers
- **POST**: Create object on server

  - Data in message body
  - Larger data capacity
  - Form submissions
- **HEAD**: Same as GET but no message body in response

  - Test links, check modification times
  - Efficient bandwidth use
- **PUT**: Upload object to server

  - Replaces file at specified path
  - Complete replacement
- **DELETE**: Delete object on server

  - Remove specified resource
  - Requires authentication

### 9.6 HTTP Response Message

**Status Line**: `HTTP/1.1 [Status Code] [Status Phrase]`

**Common Status Codes**:

- **2xx Success**:

  - `200 OK`: Request succeeded
  - `201 Created`: New resource created
- **3xx Redirection**:

  - `301 Moved Permanently`: Object moved, new location in Location header
  - `304 Not Modified`: Cached copy still valid
- **4xx Client Error**:

  - `400 Bad Request`: Request malformed
  - `404 Not Found`: Requested document not found
  - `403 Forbidden`: Access denied
- **5xx Server Error**:

  - `500 Internal Server Error`: Server error
  - `503 Service Unavailable`: Server overloaded
  - `505 HTTP Version Not Supported`: Protocol version not supported

**Response Headers**:

- `Content-Type`: Type of object (HTML, image, etc.)
- `Content-Length`: Size of object
- `Server`: Server software/version
- `Last-Modified`: When object was last changed
- `Set-Cookie`: Store data on client

### 9.7 Maintaining State: Cookies

**Problem**: HTTP is stateless, but applications need persistent user state

**Cookies Solution**:

**Four Components**:

1. **Cookie Header** in HTTP response message
2. **Cookie Header** in subsequent HTTP request messages
3. **Cookie File** on user's host (managed by browser)
4. **Back-end Database** at website

**Example Flow**:

1. Client visits website first time
2. Server creates unique ID for client
3. Server includes `Set-Cookie: ID=1234` in response
4. Browser saves cookie in local file
5. Browser includes `Cookie: ID=1234` in future requests
6. Server uses cookie to identify client

**Use Cases**:

- User authentication and login
- Shopping carts
- Personalization and recommendations
- User session tracking

**Privacy Concerns**:

- **First-party cookies**: From website you chose to visit (acceptable)
- **Third-party cookies**: From ad network or tracker (privacy issue)
- Can track browsing behavior across multiple websites
- Regulations: GDPR (Europe), increasing browser restrictions

### 9.8 Web Caching (Proxy Servers)

**Definition**: Intermediary server storing copies of objects

**Function**:

- User configures browser to use cache
- Cache receives HTTP requests
- If object in cache: Returns cached copy
- If not: Requests from origin server, caches, returns

**Benefits**:

- Reduces response time (cache closer to user)
- Reduces traffic on institutional access link
- Enables better service delivery for content providers

**Conditional GET**:

- Client includes `If-Modified-Since: [date]` header
- Server responds with `304 Not Modified` if unchanged
- Saves bandwidth without re-downloading unchanged objects

---

## Chapter 10: Email Systems

### 10.1 Email Architecture

**Three Major Components**:

1. **User Agents (Mail Clients)**:

   - Programs for composing, editing, reading mail
   - Examples: Outlook, Apple Mail, Gmail, Thunderbird
   - Manages user mailbox (local or remote)
2. **Mail Servers**:

   - Permanent storage for user messages
   - Incoming mailbox for each user
   - Outgoing message queue
   - Implements SMTP and other protocols
3. **SMTP (Simple Mail Transfer Protocol)**:

   - Protocol for sending email between servers
   - Client-server model: Sender talks to receiver
   - Uses TCP port 25

### 10.2 SMTP Protocol

**Characteristics**:

- Uses TCP for reliable delivery (port 25)
- Push protocol: Client pushes messages to server
- ASCII command-response interaction
- Three phases: Handshaking, message transfer, closure

**Three Phases**:

1. **SMTP Handshaking**:

   - Client connects to server port 25
   - Exchange greeting and capabilities
2. **Message Transfer**:

   - Client specifies sender and recipients
   - Sends message header and body
3. **SMTP Closure**:

   - Connection closes

**SMTP Commands**:

- `HELO`: Identify client
- `MAIL FROM`: Specify sender
- `RCPT TO`: Specify recipient
- `DATA`: Begin message body
- `QUIT`: Close connection

**Message Format**:

- Header lines (To, From, Subject, Date)
- Blank line
- Body content

### 10.3 Email Retrieval: IMAP

**Problem**: SMTP only sends email, doesn't retrieve

**Solution**: Mail Access Protocol

**IMAP (Internet Message Access Protocol)**:

- Retrieval from remote mail server
- RFC 3501
- Keeps messages on server
- User can organize in folders
- Supports offline reading (copies downloaded)

**POP3** (Older alternative):

- Simpler than IMAP
- Downloads and deletes messages
- Stateless

**Web-based Email**:

- HTTP protocol for both sending and receiving
- Examples: Gmail, Outlook.com, Yahoo Mail
- SMTP for sending, IMAP for retrieving (backend)

---

## Chapter 11: Domain Name System (DNS)

### 11.1 DNS Overview

**Problem**: Humans use domain names; Internet uses IP addresses

- Example: `www.google.com` vs `142.251.41.14`

**Solution**: DNS (Domain Name System)

- Distributed database
- Application-layer protocol
- Translates domain names to IP addresses
- Implemented as hierarchy of DNS servers

### 11.2 DNS Services

1. **Hostname-to-IP-Address Translation**

   - Primary service
   - Example: `cs.umass.edu` → `128.119.245.12`
2. **Host Aliasing**

   - Canonical hostname and aliases
   - Example: `ibm.com` and `www-ibm.com`
3. **Mail Server Aliasing**

   - Find mail server for domain
   - `MX` record lookups
4. **Load Distribution**

   - Multiple IP addresses for same hostname
   - Different servers replicated
   - Distributes load across servers

### 11.3 Why Not Centralize DNS?

**Reasons for Distributed Architecture**:

- **Single Point of Failure**: Central server failure breaks entire Internet
- **Traffic Volume**: Massive query load (millions per second)
- **Distant Centralized Database**: High latency to distant users
- **Maintenance**: Impossible for single organization

### 11.4 DNS Hierarchy

```
Root Name Servers (13)
    ↓
Top-Level Domain (TLD) Servers (.com, .edu, .org, etc.)
    ↓
Authoritative Name Servers (company-specific)
    ↓
Local DNS Name Servers (at ISP)
```

**DNS Server Types**:

1. **Root Name Servers**:

   - 13 root servers worldwide
   - Know all TLD servers
   - Critical for Internet function
2. **Top-Level Domain (TLD) Servers**:

   - Maintain records for all domains under their TLD
   - Examples: VeriSign (`.com`, `.net`), Educause (`.edu`)
3. **Authoritative Name Servers**:

   - Maintain DNS records for organizations
   - Provide authoritative answers for their domains
   - Examples: `ns.google.com` for Google
4. **Local DNS Name Servers**:

   - At ISP or organization
   - First point of contact for hosts
   - Caches results from other servers
   - Not part of hierarchy, but important

### 11.5 DNS Query Process (Recursive Resolution)

**Scenario**: Client wants IP for `www.amazon.com`

1. **Client → Local DNS Server**:

   - Sends recursive query: "Give me IP for www.amazon.com"
   - Local server responsible for getting answer
2. **Local DNS → Root Server**:

   - Iterative query: "Where's www.amazon.com?"
   - Root server responds: "Ask TLD server for .com"
3. **Local DNS → TLD Server**:

   - Iterative query: "Where's www.amazon.com?"
   - TLD responds: "Ask amazon.com authoritative server"
4. **Local DNS → Authoritative Server**:

   - Iterative query: "Where's www.amazon.com?"
   - Authoritative responds: "IP is 205.244.81.42"
5. **Local DNS → Client**:

   - Returns IP address
   - Caches result for future queries

### 11.6 DNS Protocol Messages

**Query Message Format**:

- Identification number (to match response)
- Questions (domain names to resolve)
- Additional fields

**Response Message Format**:

- Identification number (matches query)
- Answers (resolved IP addresses)
- Authority section (authoritative servers)
- Additional section (auxiliary information)

**DNS Record Types**:

- **A**: IPv4 address
- **AAAA**: IPv6 address
- **MX**: Mail server for domain
- **CNAME**: Canonical name (alias)
- **NS**: Name server for domain
- **SOA**: Start of authority

### 11.7 DNS Security Issues

**Attacks**:

1. **DDOS Attacks**:

   - Bombard root/TLD servers with traffic
   - Attempts to make DNS unavailable
   - Mitigated by redundancy and filtering
2. **DNS Spoofing**:

   - Intercept DNS queries
   - Return false (malicious) IP addresses
   - User directed to fake website
   - Mitigation: DNSSEC (authentication)

---

## Chapter 12: Transport Layer Overview

### 12.1 Transport Layer Functions

**Definition**: Provides process-to-process communication

**Key Differences from Network Layer**:

- **Network Layer**: Host-to-host (Logical addressing with IP)
- **Transport Layer**: Process-to-process (Port numbers)

**Core Services**:

- Multiplexing: Combine data from multiple processes
- Demultiplexing: Deliver data to correct process
- Reliable delivery (TCP)
- Congestion control
- Flow control

### 12.2 Multiplexing and Demultiplexing

#### Multiplexing (Sender Side)

- **Definition**: Collecting data from multiple sockets and sending
- **Process**:
  1. Application layer delivers data to socket
  2. Transport layer adds header (port numbers, etc.)
  3. Combine into single stream for network layer
- **Purpose**: One host can run multiple applications simultaneously

#### Demultiplexing (Receiver Side)

- **Definition**: Delivering received segments to correct socket/application
- **Process**:
  1. Network layer delivers datagram to transport layer
  2. Transport layer examines destination port
  3. Delivers data to corresponding socket
- **Challenges**: Multiple sockets with same port number

**Demultiplexing Types**:

1. **Connectionless (UDP)**:

   - Uses: Source IP, Source Port, Destination IP, Destination Port
   - Stateless: No connection setup
2. **Connection-Oriented (TCP)**:

   - Uses: Same four fields as UDP
   - Connection-based: Tracks active connections
   - Can have multiple connections to same port (different source)

### 12.3 Sockets

**Socket Concept**:

- Endpoint of network communication
- Identified by (IP address, Port number)
- Applications send/receive through sockets

**Socket Types**:

- **Stream Socket (TCP)**: Reliable, ordered delivery
- **Datagram Socket (UDP)**: Unreliable, unordered delivery

---

## Chapter 13: UDP (User Datagram Protocol)

### 13.1 UDP Overview

**Characteristics**:

- Unreliable data transfer (best-effort delivery)
- Connectionless (no setup/teardown)
- Minimal overhead
- Fast delivery
- No flow or congestion control

### 13.2 UDP Segment Structure

```
Source Port (16 bits) | Destination Port (16 bits)
Length (16 bits) | Checksum (16 bits)
[Application data]
```

**Fields**:

- **Source Port**: Sending process's port
- **Destination Port**: Receiving process's port
- **Length**: Header + data length
- **Checksum**: Error detection (optional)

### 13.3 Checksum (Error Detection)

**Purpose**: Detect bit errors in segment

**Process**:

1. Sender adds all 16-bit words
2. Takes one's complement (flip bits)
3. Includes in checksum field
4. Receiver adds all words including checksum
5. If result is all 1s, no error detected

**Limitation**: Detects errors but doesn't correct them

### 13.4 UDP Applications

**Best for**:

- **Streaming Media**: Audio/video where occasional loss acceptable

  - Examples: YouTube, Netflix, Spotify
  - Loss tolerance > Delay sensitivity
- **Online Gaming**: Low latency more important than reliability

  - Action games need fast response
  - Occasional lost position update acceptable
- **DNS Queries**: Simple request-response

  - Client can retry if no response
- **IoT Sensors**: Small data bursts, high volume

  - Loss of occasional reading acceptable

**Advantage**: No connection overhead, lower latency

---

## Chapter 14: TCP (Transmission Control Protocol)

### 14.1 TCP Overview

**Characteristics**:

- Reliable data transfer (in-order, complete)
- Connection-oriented (setup, data, teardown)
- Flow control (receiver controls sender)
- Congestion control (sender adapts to network)
- Ordered delivery
- Relatively complex implementation

### 14.2 TCP Segment Structure

```
Source Port (16) | Destination Port (16)
Sequence Number (32)
Acknowledgement Number (32)
Header Len | Reserved | Flags | Receive Window (16)
Checksum (16) | Urgent Pointer (16)
[Options - variable length]
[Application data]
```

**Key Fields**:

1. **Port Numbers**: Source and destination process ports
2. **Sequence Number**:

   - Position of first data byte in segment
   - Sender increments for each byte sent
   - Prevents duplicate/out-of-order delivery
3. **Acknowledgement Number**:

   - Next expected sequence number
   - Receiver acknowledges reception
   - Cumulative ACK: Acknowledges all bytes up to this number
4. **Header Length**: Variable length header
5. **Flags**:

   - **SYN**: Synchronize (connection setup)
   - **ACK**: Acknowledgement valid
   - **FIN**: Finish (connection close)
   - **RST**: Reset connection
   - **PSH**: Push data to application
   - **URG**: Urgent data
6. **Receive Window**: Flow control

   - How much data receiver can accept
   - Sender shouldn't exceed this
7. **Checksum**: Error detection (mandatory in TCP)

### 14.3 TCP Connection Management

#### Three-Way Handshake (Connection Setup)

**Problem**: Establish reliable connection with sequence number synchronization

**Process**:

```
Client                          Server
  |                              |
  |------ SYN (seq=x) ---------->| 
  |          (1) Client initiates
  |
  |<-- SYN-ACK (seq=y, ack=x+1) --
  |          (2) Server responds
  |
  |------ ACK (seq=x+1, ack=y+1) -->
  |          (3) Client acknowledges
  |
  |======= Data Transfer =======|
```

**Steps**:

1. **SYN (Synchronization)**:

   - Client sends segment with SYN flag
   - Sequence number: Initial value x
   - No data
   - Purpose: Client announces readiness to connect
2. **SYN-ACK**:

   - Server sends segment with SYN and ACK flags
   - Sequence number: Initial value y
   - Acknowledgement number: x + 1 (acknowledges client's sequence)
   - Purpose: Server confirms and sends own sequence
3. **ACK**:

   - Client sends segment with ACK flag
   - Sequence number: x + 1
   - Acknowledgement number: y + 1 (acknowledges server's sequence)
   - May contain data
   - Purpose: Confirm connection established

**Result**: Both sides synchronized, ready for data transfer

#### TCP Connection Termination (4-Way Handshake)

```
Client                          Server
  |                              |
  |------ FIN (seq=x) --------->|
  |      (1) Client wants to close
  |
  |<------ ACK (ack=x+1) --------
  |      (2) Server acknowledges
  |
  |<------ FIN (seq=y) --------
  |      (3) Server wants to close
  |
  |------ ACK (ack=y+1) -------->|
  |      (4) Client acknowledges
  |
  |========= CLOSED ===========|
```

**Steps**:

1. Client sends FIN (finish flag)
2. Server acknowledges with ACK
3. Server sends its FIN
4. Client acknowledges with ACK

**Result**: Connection closed gracefully

### 14.4 Reliable Data Transfer in TCP

**Challenge**: Deliver data reliably over unreliable network

**Mechanisms**:

1. **Sequence Numbers**:

   - Detect out-of-order segments
   - Detect duplicate segments
   - Reorder if necessary
2. **Acknowledgements**:

   - Receiver confirms reception
   - Cumulative: ACKs all bytes received so far
3. **Retransmission**:

   - Sender maintains timer for each segment
   - If no ACK received within timeout: Retransmit
   - Can retransmit same segment or data in new segments

**TCP Timeout Calculation**:

Sender maintains estimated RTT (Round-Trip Time):

\[ EstimatedRTT = (1 - \alpha) \times EstimatedRTT + \alpha \times SampleRTT \]

where α typically = 0.125

Deviation calculation:
\[ DevRTT = (1 - \beta) \times DevRTT + \beta \times |SampleRTT - EstimatedRTT| \]

where β typically = 0.25

Timeout interval:
\[ TimeoutInterval = EstimatedRTT + 4 \times DevRTT \]

**Fast Retransmission**:

- If sender receives 3 duplicate ACKs
- Retransmit immediately (don't wait for timeout)
- Faster response to packet loss

### 14.5 Flow Control

**Problem**: Receiver might be slower than sender; sender could overwhelm receiver

**Solution**: Receiver controls sender's rate

**Mechanism**:

- Receiver includes "Receive Window" in ACK
- Indicates how much data can accept
- Sender never sends more than receive window

**Implementation**:

```
Sender's Send Buffer
├─ Acked
├─ Sent but not acked (in-flight)
├─ Ready to send (within receive window)
└─ Not ready (exceeds receive window)
```

Sender can send data up to:
\[ LastByteSent - LastByteAcked \leq ReceiveWindow \]

**Buffer Management**:

- Receiver maintains buffer for data arrival
- Receive window = Buffer size - Data in buffer
- As application reads data, window grows

---

## Chapter 15: Congestion Control

### 15.1 Congestion Overview

**Definition**: Too many sources sending too much data too fast for network to handle

**Causes of Congestion**:

- Multiple sources competing for limited bandwidth
- Routers have finite buffer capacity
- Packets arrive faster than transmission rate

**Symptoms**:

- Long queues at routers
- Packet loss due to full buffers
- Increased delay
- Wasted retransmissions (data lost then resent)

### 15.2 Congestion Control Approaches

#### End-to-End Congestion Control

- **Responsibility**: Sender's responsibility
- **Mechanism**: Sender detects congestion from packet loss, increased delay
- **Signals**: Lost packets (timeout), slow ACKs
- **Implementation**: TCP (primary approach)

#### Network-Assisted Congestion Control

- **Responsibility**: Network (routers) help
- **Mechanism**: Routers signal congestion to hosts
- **Signals**: Explicit Congestion Notification (ECN) bits in IP header
- **Implementation**: Used in conjunction with TCP

### 15.3 TCP Congestion Control (AIMD)

**Additive Increase, Multiplicative Decrease (AIMD)**:

**Additive Increase**:

- Sender increases congestion window (cwnd) by 1 segment per RTT
- When no packet loss detected
- Throughput increases linearly over time

**Multiplicative Decrease**:

- When congestion detected (packet loss):
  - Reduce cwnd by half
  - Causes sharp decrease in throughput

**Sending Rate**:
\[ Rate = \frac{cwnd}{RTT} \]

**Graphically**: Sawtooth pattern

- Linear increase followed by sharp decrease at loss event

### 15.4 TCP Slow Start

**Problem**: Start with small cwnd and increase slowly

**Slow Start**:

- Initial cwnd = 1 maximum segment size (MSS)
- Cwnd doubles each RTT (exponential growth)
- Continues until:
  - Loss event occurs → enter congestion avoidance
  - Reaches slow start threshold → enter congestion avoidance

**Timeline**:

1. **Slow Start**: Exponential growth (dangerous if uncontrolled)
2. **Congestion Avoidance**: Linear growth (AIMD)
3. **Timeout/Loss**: Halve cwnd, reset slow start threshold
4. **Duplicate ACKs**: Fast retransmit/recovery

### 15.5 Fairness

**Definition**: Multiple flows should share bandwidth fairly

**TCP Fairness**:

- Two TCP flows sharing bottleneck link: Each gets half bandwidth
- General: N flows → Each gets 1/N of bandwidth
- **Condition**: Only when RTTs are similar
- Different RTTs: Flow with shorter RTT may get more bandwidth

**Fairness Issues**:

- **UDP vs TCP**:

  - UDP not fair (no congestion control)
  - UDP flows can starve TCP flows
  - Solution: Application-level fairness, network policing
- **Network Neutrality**:

  - Should ISPs treat all traffic equally?
  - Policy debate: pricing, prioritization, blocking

---

## Chapter 16: Network Layer - Routing and Forwarding

### 16.1 Network Layer Functions

**Two Key Functions**:

#### Forwarding (Data Plane)

- **Definition**: Local process of moving packet from router input to output
- **Scope**: Single router
- **Timeframe**: Nanoseconds (hardware)
- **Implementation**: Forwarding table lookup
- **Analogy**: Passing through one intersection

#### Routing (Control Plane)

- **Definition**: Global process of determining path packets take from source to destination
- **Scope**: Entire network
- **Timeframe**: Milliseconds to seconds (software)
- **Implementation**: Routing algorithms
- **Analogy**: Planning entire trip from source to destination

### 16.2 Forwarding Decision

**Longest Prefix Matching**:

**Problem**: Multiple forwarding table entries might match destination IP

**Solution**: Use longest matching prefix

**Example**:

```
Forwarding Table:
Destination        Link
11001000 00010111 00010/22    0
11001000 00010111 00011000/23 1
11001000 00010111 00011/21    2
Otherwise                      3

Packet dest: 11001000 00010111 00011000 10101010
Matches:
- Entry 0: 11001000 00010111 00010 (20 bits) ✓
- Entry 1: 11001000 00010111 00011000 (23 bits) ✓
- Entry 2: 11001000 00010111 00011 (21 bits) ✓

Longest match: Entry 1 (23 bits) → Use Link 1
```

### 16.3 Router Architecture

**High-Level Components**:

```
        [Control Plane Software]
              (Milliseconds)
                    ↓
    ┌─────────────────────────────┐
    │   Routing Processor         │
    │   • Runs routing algorithms │
    │   • Maintains routing table │
    │   • Updates forwarding table│
    └──────────────┬──────────────┘
                   ↓
    ┌─────────────────────────────┐
    │  Switching Fabric (High-Speed)
    │      (Nanoseconds)          │
    │  • Transfers packets        │
    │  • From input to output     │
    └────────┬──────────────┬─────┘
             ↓              ↓
    ┌──────────────┐  ┌──────────────┐
    │ Input Port   │  │ Output Port   │
    │ • Physical   │  │ • Physical    │
    │ • Link layer │  │ • Link layer  │
    │ • Lookup     │  │ • Queueing    │
    │ • Queueing   │  │ • Scheduling  │
    └──────────────┘  └──────────────┘
```

### 16.4 Input Port Processing

**Functions**:

1. **Physical Layer**:

   - Receive bits from incoming link
   - Convert to electrical signals
2. **Link Layer**:

   - Implement Ethernet, WiFi, etc.
   - Frame validation
   - Check CRC (Cyclic Redundancy Check)
3. **Lookup, Forwarding, Queueing**:

   - Extract destination IP
   - Longest prefix match in forwarding table
   - Determine output port
   - If fabric is busy: Queue in input port

### 16.5 Switching Fabrics

Three main types:

#### Switching via Memory

- **Method**: CPU copies packet from input to output memory
- **Speed**: Limited by memory bandwidth
- **Limitation**: Slow (system bus bottleneck)
- **Historical**: Used in older routers

#### Switching via Bus

- **Method**: Packet transferred over shared system bus
- **Architecture**: Backplane bus
- **Speed**: Limited by bus bandwidth (e.g., 32 Gbps)
- **Usage**: Adequate for access routers
- **Issue**: Bus contention when multiple packets

#### Switching via Interconnection Network

- **Method**: Crossbar switch or multistage network
- **Advantages**:
  - Non-blocking (no interference)
  - Scalable with multiple planes
  - High throughput possible
- **Technology**: Crossbar, Clos network, banyan network
- **Usage**: High-end routers (core of Internet)

### 16.6 Output Port Processing

**Functions**:

1. **Link Layer Transmission**
2. **Queueing** (if fabric sends faster than transmission rate)
3. **Scheduling** (which packet to send next)

**Queueing**:

- Occurs when: Arriving rate > Link transmission rate
- Buffer size: RFC 3439 recommends C × RTT / N
  - C = Link capacity
  - RTT = Round trip time
  - N = Number of flows

**Scheduling Disciplines**:

1. **FCFS (First-Come-First-Served)**:

   - Send packets in arrival order
   - Fair but doesn't prioritize
2. **Priority Scheduling**:

   - Classify traffic by priority
   - Serve high priority first
   - Within priority: FCFS
3. **Round-Robin**:

   - Cycle through traffic classes
   - Send one packet from each class per cycle
   - Fair scheduling
4. **Weighted Fair Queueing (WFQ)**:

   - Each class has weight wi
   - Service proportional to weight
   - More sophisticated fair queueing

---

## Chapter 17: IP Protocol and Addressing

### 17.1 IP Datagram Format

```
Version(4) | Header Len(4) | Type of Service(8) | Total Length(16)
Identification(16) | Flags(3) | Fragment Offset(13)
Time To Live(8) | Upper Layer(8) | Header Checksum(16)
Source IP Address(32)
Destination IP Address(32)
[Options - variable length]
[Data payload - variable length]
```

**Field Descriptions**:

1. **Version** (4 bits):

   - IP version number
   - IPv4: 4
   - IPv6: 6
2. **Header Length** (4 bits):

   - Length of header in 32-bit words
   - Minimum 5 (20 bytes)
   - Maximum 15 (60 bytes) with options
3. **Type of Service (ToS)** (8 bits):

   - Priority and QoS parameters
   - Differentiated Services (DiffServ)
4. **Total Length** (16 bits):

   - Entire datagram length (header + data)
   - Maximum 65,535 bytes
   - Most links limit to 1,500 bytes (MTU)
5. **Identification** (16 bits):

   - Unique identifier for fragmented datagrams
   - Identifies fragments belonging to same datagram
6. **Flags** (3 bits):

   - **DF (Don't Fragment)**: Router shouldn't fragment
   - **MF (More Fragments)**: More fragments coming
   - **Reserved**: Unused
7. **Fragment Offset** (13 bits):

   - Position of fragment in original datagram
   - In 8-byte units
   - First fragment offset: 0
8. **Time To Live (TTL)** (8 bits):

   - Decremented by 1 at each router
   - When reaches 0: Datagram discarded
   - Prevents infinite loops
9. **Upper Layer Protocol** (8 bits):

   - Which protocol is using IP
   - 6 = TCP
   - 17 = UDP
   - 1 = ICMP
10. **Header Checksum** (16 bits):

    - Checksum of IP header only (not data)
    - Recalculated at each router (TTL changes)
    - One's complement sum
11. **Source/Destination IP Address** (32 bits each):

    - Sender and recipient IP addresses
    - Don't change (except NAT)

### 17.2 IP Addressing

**IP Address**:

- 32-bit identifier (IPv4)
- Identifies host or router interface
- Written in dotted-decimal notation: `a.b.c.d`
- Each octet (byte) in decimal: 0-255

**Interface**:

- Connection between host/router and physical link
- Router: Multiple interfaces
- Host: Typically 1-2 interfaces (Ethernet, WiFi)

**Subnet**:

- Group of device interfaces that can reach each other without passing through router
- Devices in same subnet have common high-order bits in IP address

### 17.3 IP Address Classes (Legacy)

**Class A**:

- First octet: 1-126
- Format: Network.Host.Host.Host
- Networks: 126
- Hosts per network: 16,777,214

**Class B**:

- First octet: 128-191
- Format: Network.Network.Host.Host
- Networks: 16,384
- Hosts per network: 65,534

**Class C**:

- First octet: 192-223
- Format: Network.Network.Network.Host
- Networks: 2,097,152
- Hosts per network: 254

**Class D** (Multicast):

- First octet: 224-239
- Reserved for multicast group addresses

**Class E** (Reserved):

- First octet: 240-255
- Reserved for future use

**Problem with Classes**: Wasteful allocation (Class A has 16 million addresses)

### 17.4 Subnet Mask and CIDR

**Subnet Mask**:

- 32-bit number determining network vs host portion
- 1 bits = network, 0 bits = host
- Example: 255.255.255.0 → 24 network bits

**CIDR (Classless InterDomain Routing)**:

- Notation: a.b.c.d/x
- x = number of bits in subnet portion
- Example: 200.23.16.0/23
  - 23 bits for network
  - 9 bits for hosts
  - 2^9 = 512 possible addresses

**Number of Addresses**:
\[ \text{Addresses} = 2^{(32 - x)} \]

**Subnet Calculation**:

1. AND IP address with subnet mask to get network address
2. Set host bits to 1 to get broadcast address
3. Usable addresses: Network + 1 to Broadcast - 1

---

## Chapter 18: DHCP (Dynamic Host Configuration Protocol)

### 18.1 DHCP Overview

**Problem**: Manual IP address configuration tedious

**DHCP Solution**:

- Automatic IP address assignment
- Plug-and-play networking
- Hosts dynamically obtain IP from DHCP server
- Addresses can be reused (lease system)

### 18.2 DHCP Process

**Four-Step Process**:

```
Client                          Server
  |                              |
  |--- DHCP Discover ----------->| (Broadcast)
  |    (Source: 0.0.0.0)
  |
  |<-- DHCP Offer ----------------| (Broadcast)
  |    Offers IP, subnet, gateway
  |
  |--- DHCP Request ------------>| (Broadcast)
  |    Request offered address
  |
  |<-- DHCP ACK --------| (Broadcast)
  |    Confirm allocation
```

**Messages**:

1. **DHCP Discover**: Client broadcasts "Is there a DHCP server?"
2. **DHCP Offer**: Server responds with available address
3. **DHCP Request**: Client requests specific address
4. **DHCP ACK**: Server confirms allocation

**Additional Information**:

- Subnet mask
- Default gateway (first-hop router)
- DNS server address(es)
- Lease duration (IP valid for how long)

### 18.3 DHCP in Home Networks

**Implementation**:

- DHCP server in router
- Router assigns addresses to all connected devices
- Simplifies home network setup
- Devices get IP automatically

---

## Chapter 19: Network Address Translation (NAT)

### 19.1 NAT Overview

**Motivation**:

- IPv4 address exhaustion (only 4.3 billion addresses)
- Need to connect many devices with limited addresses
- Security: Hide internal network from outside

**NAT Concept**:

- All devices in local network share one external IP
- Router translates between local and external addresses
- External world sees only router's IP

### 19.2 NAT Implementation

**Process**:

**Outgoing Datagram**:

1. Local host (10.0.0.1:3345) sends to external server (128.119.40.186:80)
2. Datagram reaches NAT router
3. Router replaces:
   - Source IP: 10.0.0.1 → 138.76.29.7 (NAT IP)
   - Source Port: 3345 → 5001 (or other port)
4. Router records in NAT translation table: (10.0.0.1:3345 ↔ 138.76.29.7:5001)
5. Modified datagram sent to external server

**Incoming Datagram**:

1. Server responds to 138.76.29.7:5001
2. Router receives response
3. Looks up translation table: 138.76.29.7:5001 ↔ 10.0.0.1:3345
4. Replaces:
   - Destination IP: 138.76.29.7 → 10.0.0.1
   - Destination Port: 5001 → 3345
5. Routes to internal host 10.0.0.1

**NAT Translation Table**:

```
WAN Side Address        LAN Side Address
138.76.29.7, 5001      10.0.0.1, 3345
138.76.29.7, 5002      10.0.0.2, 4156
```

### 19.3 NAT Advantages

- **Address Conservation**: Multiple devices share one IPv4 address
- **Privacy**: Internal IP addresses hidden from Internet
- **ISP Independence**: Can change internal addresses, only NAT IP visible
- **ISP Agility**: Change ISP without renumbering internal devices

### 19.4 NAT Controversies

**Criticisms**:

- Violates end-to-end argument (layer 3 device modifying layer 4 addresses)
- Complicates protocol design
- Breaks some applications (P2P, video conferencing)

**NAT Traversal**:

- If external host wants to initiate connection to device behind NAT
- Requires special techniques (UPnP, hole punching, relay servers)

---

## Chapter 20: IPv6

### 20.1 IPv6 Motivation

**IPv4 Limitations**:

- 32-bit address space: Only 4.3 billion addresses
- Largely exhausted (ICANN allocated last addresses in 2011)
- Header overhead (20 bytes minimum)
- Fragmentation challenges

**IPv6 Solution**:

- 128-bit address space: 3.4 × 10^38 addresses
- Vastly improved header format
- Better support for QoS and security
- Stateless address configuration

### 20.2 IPv6 Datagram Format

```
Version(4) | Traffic Class(8) | Flow Label(20)
Payload Length(16) | Next Header(8) | Hop Limit(8)
Source IP Address(128 bits)
Destination IP Address(128 bits)
[Optional Extension Headers]
[Data Payload]
```

**Improvements over IPv4**:

1. **No Header Checksum**:

   - Checksum overhead removed
   - Link-layer provides error detection
   - Speeds up router processing
2. **Simplified Fixed-Length Header**:

   - Always 40 bytes
   - No options field (options in extension headers)
   - Faster processing
3. **IPv6 Address Format**:

   - 128 bits (16 bytes)
   - Written as 8 groups of 4 hex digits: 2001:0db8:85a3:0000:0000:8a2e:0370:7334
   - Compressed notation: 2001:db8:85a3::8a2e:370:7334
4. **No Fragmentation**:

   - Routers don't fragment
   - Source fragments if needed (using Path MTU Discovery)

### 20.3 IPv6 Adoption

**Current Status** (as of 2024):

- Google: ~40% of clients use IPv6
- NIST: ~13% of US government domains IPv6-capable
- Slow deployment (25+ years and ongoing)

**Reasons for Slow Adoption**:

- No killer app driving adoption
- NAT extends IPv4 viability
- Significant deployment cost
- Application compatibility issues

### 20.4 IPv6 Transition: Tunneling

**Problem**: Mixed IPv4/IPv6 network environment

**Tunneling Solution**:

- IPv6 datagram encapsulated in IPv4 datagram
- Treated as IPv4 payload
- IPv4 routers forward transparently
- IPv6 routers decapsulate

**Process**:

```
IPv6 Host A → IPv4 Network → IPv6 Host F

A-to-B: Native IPv6
B-to-E: IPv6 inside IPv4 (tunneled)
       [IPv4 Header | IPv6 Datagram]
E-to-F: Native IPv6
```

---

## Chapter 21: Link Layer Fundamentals

### 21.1 Link Layer Services

**Definition**: Transfers datagram over single link

**Services**:

1. **Framing**: Encapsulate datagram in frame
2. **Link Access**: MAC (Media Access Control) protocol
3. **Reliable Delivery**: Detect and retransmit lost frames
4. **Error Detection**: Check for bit errors
5. **Error Correction**: Detect and correct bit errors (optional)
6. **Flow Control**: Prevent overwhelming receiver

### 21.2 MAC Addresses

**Definition**: 48-bit (6-byte) physical address

**Format**: Often written as hex: 00:1A:6B:31:FC:E8

**Scope**: Only significant on same network (not routed)

**Comparison with IP Address**:

| Aspect     | MAC                      | IP                   |  |
| ---------- | ------------------------ | -------------------- | - |
| Bits       | 48                       | 32 (IPv4)            |  |
| Scope      | Local network            | Global               |  |
| Assignment | Burned in (manufacturer) | Assigned dynamically |  |
| Changes    | Never                    | Can change with DHCP |  |
| Analogy    | Social Security Number   | Postal Address       |  |

### 21.3 ARP (Address Resolution Protocol)

**Problem**: Know IP address, need MAC address on same network

**ARP Solution**:

1. Host with IP address sends broadcast: "Who has IP X.X.X.X?"
2. Host with that IP responds: "I have IP X.X.X.X, my MAC is YY:YY:YY:YY:YY:YY"
3. Sender caches (IP, MAC) in ARP table

**ARP Table**:

```
IP Address      MAC Address        TTL
192.168.1.1     00:1A:6B:31:FC:E8  120s
192.168.1.100   A4:70:D9:20:87:A6  120s
```

**Usage**:

- Get MAC for IP before sending frame
- Periodic updates
- Broadcast sent if not in cache

---

## Chapter 22: Securing Computer Networks

### 22.1 Cybersecurity Threats

**Packet Sniffing**:

- Attacker captures network packets
- Reads sensitive data (passwords, emails, files)
- Risk: Unencrypted data transmissions
- Solution: Encryption (HTTPS, VPN)

**IP Spoofing**:

- Attacker sends packet with false source IP
- Victim thinks packet came from trusted source
- Can be used for impersonation, phishing
- Solution: Authentication, packet filtering

**Denial of Service (DoS)**:

- Attacker overwhelms resource with traffic
- Legitimate users can't access service
- Types:
  - Bandwidth flood: Saturate link
  - Connection flood: Exhaust server resources
- Amplified DoS: Use third-party servers to multiply attack traffic

**Man-in-the-Middle (MITM)**:

- Attacker intercepts communication between two parties
- Can eavesdrop or modify messages
- Example: Fake WiFi hotspot
- Solution: Encryption, authentication

### 22.2 Security Defenses

**Firewalls**:

- Software or hardware filter
- Control traffic in/out of network
- Rules: Allow/deny based on IP, port, protocol
- Limitations: Not perfect, can't stop all threats

**Access Control**:

- Authentication: Verify identity (passwords, certificates)
- Authorization: Verify permissions (what can access)
- Encryption: Scramble data so only authorized can read

**Intrusion Detection Systems (IDS)**:

- Monitor network for suspicious activity
- Alert or automatically respond to attacks
- Can be signature-based or anomaly-based

**Data Integrity Checks**:

- Checksums/hash functions detect tampering
- Message Authentication Codes (MAC) verify authenticity
- Digital signatures prove authorship

---

## Conclusion

Computer networking is a hierarchical, modular system where each layer provides specific services to the layer above it. Success requires understanding:

1. **Fundamental Concepts**: Switching, routing, protocols, addressing
2. **Protocol Stack**: How Application, Transport, Network, and Link layers interact
3. **Performance Metrics**: Delay, loss, throughput, fairness
4. **Practical Implementation**: TCP/IP, HTTP, DNS, routing algorithms
5. **Security**: Threats and defenses

The field continues to evolve with new technologies (IPv6, QUIC, SDN, 5G) and emerging challenges (IoT, security, latency requirements for real-time applications).
