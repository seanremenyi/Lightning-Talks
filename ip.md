## IP Addresses

Now moving onto the Network layer. Now remember theres a source and destination MAC address added at the data-link layer in the OSI model but at the network layer a source and destination IP address is added. In both cases this is specifying to what device your data is going. This may sound a bit redundant. If we want to specify what device we want the data sent to, wouldn’t the MAC address be sufficient? It is a unique number right? Well for 2 reasons, One we are looking at addressing at 2 different level and as such we’re talking about 2 different protocols. Remember depending on which protocol you’re using, this will specify the rules devices need to communicate. At the network level, we are talking about the IP or internet protocol which require an IP address to specify devices. The other reason is whereas a MAC address is a physical address (remember burnt into the NIC) an IP address is a logical address that can change depending on what network you are connected to. You have a mac address on your phone but its ip address will change depending on whether your at home or at work. Ip address is to locate a device on a network, mac address is the device

So every device connecting to a network needs an IP address. IPv4 is the most common one and has been around since the 80s, it’s an address consisting of 4 numbers between 0 and 255 seperated by a period. Problem with this though is this combination of 4 -255 possibilities only gave a pool of about 4.2 billion possible addresses. Sounds like a lot but consider how these days most people have a computer or a device that connects to the internet and in most cases have multiple then maybe further devices at work. If each device needs its own IP address we would run out pretty fast these days. Ipv6 will take care of this which has a pool of addresses of 340 trillion trillion trillion, but before this becomes the standard and what how we deal with thi today is by having both a public and private IP address. 

So IP addresses break down into 2 categories, private and public. Analogous again to your address. Public IPs are the ones that your ISP or internet service provider give you and this specifies your network.  This is analogous to your street address. You also have a private IP address however which will specify your device on a network. And this is your house number. 

So if Our internet service provider gives us our public IP address, how do we get our private one? Theres 2 different kinds of private addresses, static or dynamic. Static addresses are ones that are assigned manually by the user. You can do this by opening your computers network configuration (can also assign subnet mask, default gateway and other things but well talk about that another time) assigns manually). Biggest disadvantage with this is imagine you’re doing this for all you’re devices and what if you have a huge network like on a school campus or large office building with a ton of devices. Anyways human errors do happen. What if you gave 2 devices the same private addresses, this leads to an error and or ip conflict. Back to our analogy, how are you going to get things delivered to the right addresses if 2 houses on the same street have the same house number.

For dynamic addresses and the other fields we just mentioned with static addressing we have DHCP which stands for dynamic host configuration protocol. This uses a client server communication where the client is your device and the server is the router (they usually have a dhcp server built-in).

How this works is a 4 step process,
Step 1. Dhcp Discover. Here the device broadcasts onto the network it connects to, “can someone give me an address?”
Step 2. Dhcp Broadcast the offer, Here the server broadcasts to everyone on the network, I can offer you an address for a certain amount of time. So like “ I can offer you 192.186.1.3 for the next 3600 seconds”
Step 3. Dhcp Request So the device will again broadcast to everyone, “i want to accept the offer”
Step 4. Dhcp ack or acknowledgement which is basically is the server saying. Perfecto  as for now, you can use this address fo this amount of time.

The time thing might be seem a bit weird. But yes dhcp leases out ip addresses instead of just giving them to a device.. This is to recycle unused addresses. Imagine you give an ip address to every device connected to a network in lets say a university campus. Giving a new address to a device each time it connects, well you can see how fast the pool of  addresses known as the scope would get used up but with DHCP as soon as the lease is up if the device is no longer on the network that address can get recycled and used again for a different address. 

If addresses are still being in use as in the device is still connected to a network, then the lease can be renewed. You can also make reservations for an address but this is usually used for devices that aren’t coming and going like a printer.

If you want to see this in practice google what is my ip address. There’s many sites that will show you. Then I kow for windows if you open the command line interface or command prompt and run the command ipconfi /all , you’ll also get your ip address. But you’ll note that these 2 addresses are different, the one you googled is your public address whereas the one you ran on the command line is your private.

So which ip address do we use when we use the internet, well both! Our public address is publicly registered and given to us by our internet service provider and is what is needed to connect to the internet, you can think of it as the external address. The private ip address is the one that DHCP configures for your device on your network. You can’t connect to the internet with this, this is just for the internal network. 

Should note though you can ask your isp for additional ip addresses for your devices but it’s more expensive and just unnecessary with how these private/public addressing work.

With that said, how does this device communicate over the internet with it’s 2 addresses. Well this is done with what is called Network address translation. Basically your router assigns every device on your network with an ip address through dhcp and when you send any data over the internet, it goes through the router which translates the address to the public one and off it goes. This works both ways and data from the internet will know your public address (remember we can google it and find it out) but won’t know the private one (we can see this with the ip config command) so the router will use NAT to translate the addresses again and make sure the data goes to the right place. 
You can compare this to delivering a package to a company. You know the address of the building so you deliver the package and drop it off at the reception. Obviously the package needs to go to the right person but you don’t know where they are bassed on the public address, they can be anywhere in the building. The receptionist however has this private information and will make sure the package gets to the right place. 

IPV6 will eventually allow for every device to have it’s own ip address but till then this is how ip addresses work.





https://networkengineering.stackexchange.com/questions/56401/private-ip-vs-mac#:~:text=While%20private%20IP%20addresses%20seemingly,LAN%20segment%20%2D%20public%20or%20private.
https://www.youtube.com/watch?v=FTUV0t6JaDA&ab_channel=PowerCertAnimatedVideos
https://www.youtube.com/watch?v=iGPXkxeOfdk&ab_channel=Computerphile
https://www.youtube.com/watch?v=e6-TaH5bkjo&ab_channel=PowerCertAnimatedVideos
https://www.youtube.com/watch?v=RUZohsAxPxQ&ab_channel=TheNetworkingDoctorsTheNetworkingDoctors 