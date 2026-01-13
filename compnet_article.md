Medium article proposal

Theme = Demonstrate learning in computer network

Target = min 5 min read, 1000 - 1500 words

photo from unsplash

Constraints =

* how to connect/frame from basic knowledge of compnetwork to tcp/udp specific because the topic is really wide

Main points

* Fundamental distinction with real-world applications
* Examples: Netflix (UDP), Gmail (TCP), Discord (hybrid)
* Decision trees and practical implementation
* **Target** : Students, developers, exam prep

#######################################################

Title = TCP & UDP, discussing the two Computer Network terms

Subtitle = When to choose each and why it matters

----

Opening words = My first article of 2026:)

Recently, I have been preparing for my one of my university exam, computer networks. During it, I encountered a topic I found interesting, the Transmission Control Protocol (TCP) and User Datagram Protocol (UDP). As this two terms are among the most crucial terms of computer network, this article will attempt to discuss and compare the two in detail, from my learning perspective.

----

**Section 1 = General idea of computer network and fundamental difference of*

* address which layer tcp and udp belongs to, some basic knowledge of computer network
* explain in analogy = registered letter vs postcard

Foremostly, lets start by understanding the context information, what is computer network? Essentially, computer network is a concept that enable communication between devices through standardized protocols and infrastructure. That being said, this field is really embedded into our everyday activity, from chatting on whatsapp to watching a video on youtube.

Computer network protocol lies around a standard called the ISO/OSI reference model, which suggest that there are 7 main layers. From the user-end side, this includes the physical, data link, network, transport, session, presentation, and application layer. Each of this layers are connected to each other with specific roles like raw bits transmission (physical), hardware addressing (data link), logical addressing (network), and more.

Now, as the two main discussed concepts in this article will be the TCP and UDP, discussing the 7 layers in detail will be out of the scope. Therefore, I will be focusing on the transport layer, the layer where TCP and UDP is located.

----

*Section 2 = TCP vs UDP in a short analogy 

Now that the we know the general idea of computer network and its layers, I'd like to define TCP and UDP in a short analogy. 

---- 

**Section 2 = TCP deep dive*

* Three way handshake and why it matters
* how retransmission works
* Flow control
* Congestion control

**Section 3 = UDP deep dive*

* No setup overhead or handshake
* Difference in packet structure
* Checksum for error detection
* best effort delivery

The opposite 

**Section 4 = Real world implementation*

* Video streaming, online games = uses udp
* File transfer / email = uses TCP (mandatory)
* Discord, Skype, VoIP (voice over internet protocol) = uses UDP for voice, TCP for setup/control

**Section 5 = When to use each of them*

* make decision tree of individually when to use TCP and UDP
* when its a complex choice
* QUIC usage (what is QUIC)

**Section 6 = Conclusion*

Learning Value

- Clarifies one of networking's most important distinctions
- Explains real-world engineering decisions
- Helps with exam preparation (likely on your exam!)

Hopefully, this article could help potential readers to prepare for their computer network exams, as it did for me.
