## Chattin’ about Ethernet LANs


This is a continued discussion on networks and my previous chat can be found here,



Continuing our discussion on networking and how data travels from one computer to another, let’s look at a LAN or local area network.

A network is just a grouping of multiple devices that are connected and can communicate with one another. And a local area network is a network that’s contained in one geographical location. So think about the network in your house or office, although larger scale LANs do exist, like in university campuses and enterprise buildings. To conceptualize this we are just going to think of a home network, this is what we all have at our homes where we have our computers, printer, game consoles and other devices all connected. 

And how does data travel through this network? If we have multiple devices on our home network, how does data know to go to one device and not the other. For this we need to think back to the OSI model, specifically layer 2, the data-link layer.

The data-link layer encapsulates packets into a frame by adding a source and destination MAC address (among other things) and this is how data is delivered to the right address. A MAC address or Media Access Control address specifies the device on the network. It is a unique set of characters that translates physically to your device on a NIC or network interface card. A NIC is the piece of hardware that allows devices to connect to a network. Manufacturers burn a unique MAC address into every NIC. To recap, data is encapsulated with source and destination MAC addresses at the data-link layer. These addresses are unique and burnt into a NIC which is contained in any device connecting to a network, thus ensuring data arrives at the right device (in theory no 2 MAC addresses are the same).

Continuing the discussion, relating the OSI model to LANs we will also look at how data travels at layer 1, the physical layer. For the purpose of this article, we will only discuss wired ethernet LANs as it’s easier to visualise the data travelling over a wire as opposed to wireless. 

In the past, ethernet LANs followed a Bus topology. A Topology is just the layout of devices along a network. This bus topology for example had all devices connected over a shared cable. The main problem with this however was in how often collisions would occur.

What is a collision? Well, the best analogy for these days is to think of a zoom call. When you go to speak and someone else speaks at the exact time. You immediately stop, not saying what you want to. The same can be said with a network collision. It’s when 2 devices attempt to transmit data over a network at the same time, the data “collides” and data is lost or corrupted . 

A technology was developed to handle this called CSMA/CD or Carrier Sense Multiple Access with collision detection. Remember we are still talking about a bus topology which isn’t as popular these days, I feel however it’s good to have an appreciation for how these technologies developed. These early versions of ethernet LANs also followed a half-duplex form of communication which means data can flow in either direction between 2 devices but not at the same time.

The way CSMA/CD works is a device will listen for traffic, if it senses the wire is idle, it will start transmitting data then listen again to the wire to see if any collisions occur. If none are heard, all good. However, another computer listening can hear an idle wire at the same time and if it also starts to send data then a collision will occur. Because they are listening for collisions, they will stop transmitting and send out a signal notifying all the computers on the network a collision has occurred and then wait a random amount of time and start retransmitting to avoid transmitting at the same time (knowing it will lead to a collision). Because this whole network is over a shared cable, it is referred to as a whole as a collision domain.

Think again about a zoom meeting, no ones talking so you decide to start talking but Bob also thought it was a good time to start speaking because it was quiet. You both start talking and immediately stop once you realise you’re talking at the same time. (You’re both Canadian so) You both say sorry then wait a random amount of time before trying to speak again.

The bus topology also had other disadvantages, again, being all on a shared wire, if a computer went down it disrupted the whole network. However, problems were overcome, changes made and many advancements in the technologies that lead us to our current iteration of ethernet LANs.

The most common topology we use today is the star topology, this is the one we’re familiar with in our houses. Here all computers are connected to a central point, usually a switch or a hub. All data passes through it before going to its destination device. As each device is only connected to the switch, now the collision domain is split up into multiple ones consisting of just one device, effectively stopping collisions from occurring. This was also great because If a device on the network fails it wouldn’t disrupt the entire network, they all have their own connections. The network could go down however if something were to happen to the switch and this is referred to as a single point of failure (think everyone losing their internet connection when the router is unplugged).

You may never have heard of a switch before however most modern day routers have them built in.

To summarize how devices communicate over an ethernet LAN, Data travels physically through a switch that’s built into a router, from here it knows which device to go to based on the specified MAC address which is a unique address tied to the NIC in the device.

We will take this a step further in the next Chat.


References,

https://networklessons.com/cisco/ccna-routing-switching-icnd1-100-105/collision-domains
https://www.cdw.com/content/cdw/en/articles/networking/2019/07/23/what-type-of-network-adapters-do-i-need.html
https://www.youtube.com/watch?v=zbqrNg4C98U&ab_channel=PowerCertAnimatedVideos
https://www.youtube.com/watch?v=1z0ULvg_pW8&ab_channel=PowerCertAnimatedVideos
https://www.youtube.com/watch?v=iKn0GzF5-IU&ab_channel=PowerCertAnimatedVideos
https://www.youtube.com/watch?v=UrG7RTWIJak&ab_channel=Techquickie
