## Routing

So we’ve mentioned routers quite a bit so far but what is it exactly? Well it’s a networking device that forwards data between networks. Well we’ve seen data go between devices before over a network with switches when we looked at LANs so whats the difference now. Well the routers deal with devices over separate networks. 

Let’s look at a simple example, we’re going to imagine 2  local area networks with a few devices connected to a switch and both switches connected to a router. So how does comp 1 talk to comp 2. 

Before we get too far into it lets take a step back and talk about both devices. We briefly touched on switches but they are a layer 2 device so they deal in mac addresses. They actually store a table of mac address internally of all the devices they’re connected to to ensure data reaches the right device. 

Now a router, we’ve covered some of the things it can do like DHCP and NAT and for all intents and purposes a switch would be built in to it, (i think just to conceptualize what’s going on under the hood it’s easier to visualize them as 2 different devices). So routers have an associated ip address and MAC address as well. And when a computer needs to go through this router to get to another network, we refer to this as the default gateway. It’s a gateway to get you to another network (such as the internet). Remember that ipconfig command we mentioned last time. Well when you use it you will also see a default gateway which is referring to your router’s ip. Furthermore, being that this default gateway is a gateway right so more than one entry point, there is an associated ip address and mac address for each interface.

 

Well to start we have our data which when it gets to the network level it is encapsulated into a data packet with a source and destination ip address header. From here this packet is then encapsulated into a frame with a source and destination mac address. The problem is we don’t know the mac address of our destination device. We do however know the mac address of the default gateway so this is what will go into the header. Next the frame will travel to the switch, which will look at the header see the mac address for the destination and pass it to the router. 

Now its at the router, the router looks at the macc address see its me, woo, starts decapsulating, so we’re now out of the frame  it gets chucked and now looking at the ip packet. Sees the header and looks at the destination ip. The routers says ok i know where that is, takes the packet and encapsulates it into a new frame with the correct associated destination mac address for the ip address and passes it onto the right network onto the switch. This new switch will again look at the frame and refer to its mac address table and send it off to the right device.

Well now let’s look at the internet, its what we care about, why were all here. And lets throw another device into the mix. A modem. And gain these days you can buy all this as one device but to illustrate we’ll show them separately. So a modem is the device that gets the internet into our home. It’s what’s keeping that dedicated connection with our internet service provide to allow us to connect to the internet. As we know computers read digital signals but what’s really interesting, the internet deals with analog signals (think about how we normally connect our modems to a phone jack or even fibre cable which use light as a medium). The name modem actually comes from the word modulate. A modem, modulates outgoing digital signals into analog and demodulates incoming analog into digital.

So tying everything together we’ve talked about, this is our setup when we use the internet.

As we know the internet connects, well just about everything these days. But if we think of it less as a concept and what it really is a collection of communicating computers just like the networks we’ve been discussing. And routers play such an important role, as we said they forward data between networks.  Routers make the decisions for what routes to take for your data to get where it needs to go in a process called routing. As i briefly mentioned in my first video, data is broken up into segments and when it is fully encapsulated into its frame and sent off, the frames from the same data might take different routes before all reassembling at the destination. This is routing.

Think about going out for drinks after work. You may not take the same route, maybe one person is listening to the traffic report and is avoiding certain roads, but ultimately everyone will arrive at the pub. 

On the internet routers make these logical descisions, deciding which routes to take (and similarly to our example) one of the things it looks at is network traffic. Basically routers are trying to find the most efficient path to send your data. What if driving to the pub theres road construction and you have to take a detour. Same with routers, if a route is down they account for this and take a different route.
Routers use algorithms to create routing tables to figure the best routes to send data. Just like in real life where traffic changes can occur on a dime, same with online traffic as well as other occurrences causing the most efficient path from A to B not always being the same, routers and routing will optimize the efficiency of travel.

Ya routers are the powerhouse of networks




http://www.bbc.co.uk/webwise/guides/what-is-the-internet#:~:text=The%20internet%20is%20a%20global,small%20packets%20of%20digital%20data.
https://www.youtube.com/watch?v=Mad4kQ5835Y&t=320s&ab_channel=PowerCertAnimatedVideos
https://www.freeccnastudyguide.com/study-guides/ccna/ch7/7-1-mac-address-table/#:~:text=The%20switch%20maintains%20an%20address,on%20which%20it%20was%20received.
https://www.youtube.com/watch?v=ewrBalT_eBM&ab_channel=WorldScienceFestival
https://www.youtube.com/watch?v=zhlMLRNY5-4&t=131s&ab_channel=NexGenT
https://en.wikipedia.org/wiki/Router_(computing)#:~:text=A%20router%20is%20a%20networking,the%20form%20of%20data%20packets.
