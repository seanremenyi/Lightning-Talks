### Chattin’ about OSI


We use the internet everyday from web browsing to sending emails., but have you ever taken a moment to think about how that actually happens. How does that data actually travel? How does it get from one computer to another?

The answer comes in the form of the OSI or Open Systems Interconnection model. This is a conceptual model that describes how data flows from one device to another over a network and is broken down into 7 layers. These 7 layers are the Application Layer, Presentation layer, Session Layer, Transport Layer, Network Layer, Data-Link layer and the Physical layer. 
Data travels down through the layers from the sending computer in a process known as encapsulation and is sent to the receiving computer where the data then travels back up through the layers in a process called decapsulation. 

Before we get into it, we need to describe what a protocol is. Protocols are like a common set of rules or etiquette that computers use to talk. Think of a conversation, there’s rules or etiquette to it, for example, you say “hello” and the other person replies “hello”, if you say “how are you” the other person will reply with “good” or “bad” or any word describing a feeling. Conversations have an etiquette or rules. Well protocols are the same, simple put they are the rules describing how data is being processed. When you browse the web, you’re web browser (chrome, firefox,etc.) is talking following the hypertext transfer protocol (or HTTP) rules. With this in mind lets break down all the layers of the OSI model.

#### Layer 7 - Application Layer
This is the starting layer which interacts with the data received from the user. This layer doesn’t interact directly with the user though, the OSI model doesn’t deal with Users, the OSI model explains how data is being sent between 2 devices over a network. With this in mind the application layer is where data is taken to be sent off. It’s that first step to send data on it’s way. For example when you hit send on an e-mail or click enter after entering a URL into a browser. As the data leaves an application, this will specify what protocol is to be used. If the data is leaving your mail client, ie. gmail, application layer will specify that the protocol needed will be simple mail transfer protocol or SMTP. It then sends the data down.

#### Layer 6 - Presentation Layer
This layer formats the data. The data is translated to the correct format. This can also include encryption or compression. If either is needed, it will also happen at this layer. The data is then sent down to the next layer.

#### Layer 5 - Session Layer
This layer, well, deals with the session. Here we have the opening and closing communication between the 2 machines. This layer sets up the connection, stays open long enough for the transfer of the data and can also have some extra features for error handling depending on the protocol used. Basically think of a phone call, once you’ve dialed the number and a connection is made. Wether you end up talking  to someone or leave a message if you go to your call log, you sill see that a session was established for however amount of time. This session layer creates that connection between sender and receiver. It also passes data down to the fourth layer. 

#### Layer 4 - Transport Layer
This layer will cut the data into pieces called segments, this is to ensure a good flow of data from one computer to the other as opposed to sending one giant block of data over. The segments are also numbered (for example 3 segments can be numbered 1 of 3, 2 of 3 and 3 of 3) so the segments can be reassembled back together again at the transport layer on the other receiving end. This is also good for error handling because the transport layer can see if a segment is missing and ask for retransmission. 

Remember that protocol specified in the first layer, well it is now associated with a unique number referred to as a port. Port 25 is used for SMTP, port 80 for HTTP, etc for others. Instead of listing the protocol name, a port number is used instead. The Transport layer will add the port number for the source and the destination as a header onto each segment.

The transport layer also specifies which transfer protocol is to be used UDP or TCP. Remember protocols are just rules or etiquette so they exist also for the ways in which data can travel. The 2 main ones are UDP and TCP. The segments are passed down to the next layer.

#### Layer 3 - Network Layer
The network layer adds another header to the segment transforming it into what is known  as a packet. The meta-information added in the header is the IP addresses of both the source and the destination, as well as another protocol number specifying the transfer protocol (udp is 17 and tcp is 6). And then the network layer will determine the best path for each packet to take in a process called routing. Remember that the transport layer took our original data and broke it up into segments. We added the addresses to each segment and are now sending them off to their destination. This routing process however doesn’t necessarily send all packets from the same original data via the same route. Routing determines the best route for the packets individually.

#### Layer 2 - Data - Link Layer

The data link layer adds a header with another address, this one is referred to as the physical or MAC address. To understand this address, think about browsing the internet, you want it to get a certain webpage on your browser. Based on what we’ve covered, the protocol that we specified with a port number in the header we added in the transport layer will tell us we need a web browser. IP addresses specify our address (the address of the home or office network we’re on). Well there might be a few devices on the network of that IP address, think about how many deices in your home connect ot the internet. This is where MAC addresses. The data-link layer will add a header to the segment with a source and destination MAC address which will make sure the data will arrive at the right device. Once this meta-data is added the packet is now transformed into what is called a frame. The data-link layer can also add what is called a checksum as a footer. A calculation is performed along the frame and the result is the checksum, this way when the frame is received in the data-link layer on the other side the calculation can be performed again. If the checksum doesn’t match, the data-link layer will see the data got corrupted along the way and can ask for retransmission.

The final task of the data-link layer is to transform the frame into zeros and ones and send it down to the physical layer.

#### Layer 1 - Physical Layer
The physical layer deals with the physical transfer of the data from sending device to receiving device. We now have all the data as zeros and ones and in this state they are referred to as bits. The data is sent in what is called a bitstream over a physical medium. These can be electric signals over wires, light over fibre optic cables or radiowaves over air. 

This whole process is called encapsulation and it occurs as data is being sent from a computer. Now we will be receiving the data and the process is called decapsulation.

First, the physical layer receives the physical signals and interprets them as bits and sends it to the data-link layer. Here the bits are translated into a frame and the checksum and MAC address is validated, if it’s all good the header and footers will be removed turning the frame into a packet where it will be sent to the network layer. The network layer makes sure it’s at the right IP address and determines the transfer protocol then removes this meta-data transforming the packet into a segment and sends it up to the transport layer. The transport layer will specify the ultimate protocol for the application layer from the port number and will also make transport decisions based on seeing the transport protocol, UDP will just send the data versus TCP which will collect up the segments and reassemble the data in the order specified at the transport layer on the sending side and send it as one block. The data is then sent through the session layer closing the session and the data is now at the presentation layer. Any translation, decryption or compression now occurs and data is passed to the application layer which will know how to interpret the data based on the protocol.



References,
https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/ 
https://www.networkworld.com/article/3239677/the-osi-model-explained-how-to-understand-and-remember-the-7-layer-network-model.html 
https://en.wikipedia.org/wiki/OSI_model#History
https://www.cloudflare.com/learning/network-layer/what-is-a-protocol/#:~:text=In%20networking%2C%20a%20protocol%20is%20a%20set%20of%20rules%20for,communicate%20with%20each%20other%20regardless.
