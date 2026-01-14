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

Title = TCP & UDP, Core Transport Layer Protocols in Computer Network

Subtitle = A discussion of each

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

*Section 2 = TCP & UDP fundamental difference, in an analogy.

Now that the we know the general idea of computer network and its layers, I'd like to define TCP and UDP roles in a nutshell. Firstly, the transport layer is located between  the application and the network that routes the data. Therefore, it bears the job of providing **process-to-process communication**, meaning it ensures data gets from one running program to another. This is where the two terms differ.

Allow me to use a simple analogy to represent the core difference between udp and tcp. Given a person B who wants to send a letter to his relatives abroad. In this case, TCP is like sending a registered letter, which means that person B will need to go a post office and hand it to the official, where then he will receive a receipt confirming the office has received. Despite the process being lengthy and pricey, person B will know exactly when the letter will be delivered and if anything gets lost along the way, he will be able to track it down.

On the other hand, still on the same case, UDP is like sending a simple postcard, where person B will just need to write his letter and receipent, and drop it in the mailbox. Despite its simplicty and cheaper cost, person B won't be able to know exactly when its packet will arrive, nor will it get any confirmation of arrival. Furthermore, if the letter gets lost, then there is nothing person B can do track except accepting his fate.

The analogy above describes the core differences between the two transport protocols.  In both protocols, there will be two key actors, the sender and server, just like person B and his relative in the previous case example.

The next sections will dive deeper on the technical side of the two.

---- 

**Section 3 = TCP protocol*

* Three way handshake and why it matters
* how retransmission works
* Flow control
* Congestion control

[The Three way handshake

Upon discussing TCP, the first essential concept is the three way handshake. essentially, this is the step performed by the sender and receiver before any data is transmitted, comprised of the following steps:

a. Step 1: Syn (synchronize) = Client send a segment to server conveying its intention to connect with the server and send its number. The server then receive the message

b. Step 2: SYN-ACK (Synchronize-Acknowledge) = Server responds that it has successfully received the client's message and send a its own number to client and acknowledge the client's number.

c. Step 3: ACK (acknowledge) = Client confirms that it recieved the server's number and convey that its ready to send data, connection is then established. 

This activity shows that TCP requires a overhead process, which is why TCP is slower, alias has higher latency than UDP. Nevertheless, this process help synchronize both parties and avoid problems.

[Sequence numbers and retransmission

Another important thing to point out about TCP is that it uses sequence numbers on its packet (like the letters of person B being labeled individually). This is because packets can arrive out of order, get duplicated, or be lost entirely. This means that upon arriving to the receiver, it will acknowledge that it has received packets up to packet header ID: 99. This means that if the sender doesnt get an acknowledgement of its packet, it assumes it lost it and simply resends it.

**Section 4 = UDP protocol*

* No setup overhead or handshake
* Difference in packet structure
* Checksum for error detection
* best effort delivery

[No handshake, no connection setup

The next protocol is the UDP. Contrast with TCP, UDP doesnt establish any connetion. This means that the sender will just start sending data to the receiver immediately, without any handshake overhead procedure, saving time.

[Simpler packet structure

Compared to TCP, UDP uses a simpler packet structure, where it does not use sequence numbers, acknowledgement, and others. This means that UDP protocol will just transport the data to the receiver, and whether the receiver wants to take it or not, it doesn't matter for any side.

[Checksum for error detection

As it doesnt have packet sequence number, UDP uses a calculation called checksum that helps detect if there is bit corruption. However, an essential difference with TCP is that even in the case of corruption detection, there will be no retransmission. Instead, the bad packet will only be dropped and transmission moves on.

**Section 5 = When to use each* 

* Video streaming, online games = uses udp
* File transfer / email = uses TCP (mandatory)
* Discord, Skype, VoIP (voice over internet protocol) = uses UDP for voice, TCP for setup/control

Now that we have discussed the general characteristics of UDP and TCP, there is certainly cases when we can prefer one of the protocols over the other. 

[when to use UDP

Given UDP's characteristics of fast and simple, it is very useful in cases that doesnt require obligatory precision in data, or when loss of data is negligible due to prioritization in speed. An actual case of this would be video streaming services. When a user streams a video, the use of UDP will ensure that frames will continue to be sent continuesly. Essentially, a video is comprised of millions of frames, therefore losing frames will be negligible as video will still look smooth in the eye. Inversely, the use of TCP on video streaming may likely cause slower playback and buffer as when a frame is lost, TCP will have to perform its procedures of error detection and packet resend.

[when to use TCP

Given TCP characteristics, it is crucial in situations where data completeness is highly valued or is a must. An example use case of this will be email and file transfer applications. In an email letter, every single character matters as a corrupted file may cause misunderstanding. The case is same on file transfer, where a single corrupted bit may cause the whole file to fail, such as a single missing file could ruin an entire application. With its packet sequence features and others, TCP ensure every byte arrive in order, disregarding longer time and cost.

**Section 6 = Conclusion*

Closing this article, we have discussed the definition of the two protocols of TCP and UDP, and discuss how it works and when to use them. Hopefully, this article could help potential readers to prepare for their computer network exams, as understanding these protocols did for me. Beyond than that, I hope this article adds an extra insight on how the internet works and why it's designed the way it is.

Thanks for reading this article :) Feel free to leave a comment.

Learning Value

- Clarifies one of networking's most important distinctions
- Explains real-world engineering decisions
- Helps with exam preparation (likely on your exam!)

Hopefully, this article could help potential readers to prepare for their computer network exams, as it did for me.
