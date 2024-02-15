1. Fundamentals of computer networks/networking
- Computer network is a system that connects computing devices for transmitting and sharing information. Computing devices: Mobile, PCs, switch, router. These devices are connected using physical wires (fiber optics) or can be wireless.
	- For a standard communication, the devices must apply the communication protocols such as TCP/IP, IEEE 802, Ethernet, wireless LAN and cellular standards.
- Types of network based on geographical scale:
	- Local area network (LAN): connects devices within a limited area such as schools, offices, hospitals. These devices are connected together by a switch or stack of switches, using a private addressing scheme (local network). Routers are found at the boundary of LAN, connecting them to the larger WAN. Advantages: Fast data transfer rates, easy to set up.
	- Metropolitan area network (MAN): Covers a larger area than a LAN (connects several LANs together in a city). Advantages: Higher speed than WAN, can be used as an ISP.
	- Wide area network (WAN): Covers larger areas such as large cities, countries. Provides connectivity to the Internet, but slower speed than LAN.
	- Storage area network (SAN): It is used in storage devices such as disk arrays and tape libraries.
	- VPN: Overlay private network stretched on top of a public network.
	- Cloud network: Is an WAN whose infrastructure is delivered via cloud services.
	![[Pasted image 20240215120628.png]]
	- Wireless LANs/WANs/MANs: connects devices using wireless techniques (radio waves). There is a modem connecting from a local service provider through the fiber. Then a wireless router is connected to the modem and receives the signal from the modem. This router is also called access point, using a wireless protocol, such as 802.11 standards.
- Types of network based on organizational intent:
	- Intranet: a set of networks that is maintained and controlled by a single organization. It is secured because allowing only authorized users alone.
	- Internet: a collection of multiple networks connected by routers. Internet is actually a backbone that connects all WANs together. While WAN infrastructure consists of devices like routers, switches, access points and other end devices, the Internet includes components such as data centers, undersea cables, satellites and various interconnected elements.
	- Extranet: Similar to the intranet but with the connections to particular external networks (to share resources with partners and customers).
- Network/internet protocols:
	- Network protocols: set of procedures that enables devices to communicate back and forth across the Internet. Because two devices must support the same protocol to translate the communication.
	- 3 main types of network protocols:
		- Network management protocols: to monitor, manage and maintain a network (SNMP, FTP, POP3, Telnet).
		- Network communication protocols: to exchange data across a network (TCP, UDP, IP, HTTP, BGP, ARP).
		- Network security protocols: use security measures to protect data (SSL, HTTPS, SFTP, TLS).
- Network topology
	- Bus topology
		- A topology where all devices are connected to a single cable. It is bi-directional and multi-point connection
		![[Pasted image 20240215131306.png]]
		- It is non-robust topology because if the backbone fails the topology crashes.
		- Advantages
			- Less cost compared to other topologies.
			- CSMA is the most common method for this topology
		- Disadvantages
			- If the common cable fails, the whole system will crash
			- If the network traffic is heavy, it increases collisions in the network. To avoid, we need Pure Aloha, or CSMA/CD
			- Security is very low
	- Mesh topology
		- Every device is directly connected to each other via a dedicated channels. If we have N devices, total number of ports (endpoint of the link) is N*(N-1). 
		![[Pasted image 20240215133444.png]]
		- Advantages:
			- Very robust
			- The fault can be diagnosed easily
			- Provides security and privacy
		- Disadvantages:
			- Installation and configuration are difficult.
			- The cost is high
	- Star topology
	![[Pasted image 20240215134156.png]]
		- All devices are connected to a single hub (central node) through a cable.
		- Many Ethernet LAN protocols are used as CD, CSMA.
		- Advantages:
			- If N devices are connected, only N number of cables. Very easy.
			- Cost-effective
			- If one link fails, other will not be influenced.
		- Disadvantages:
			- If the central node fails, all crash.
			- Cost of installation is high
	- Ring topology
	![[Pasted image 20240215135934.png]]
		- Devices are connected directly with two neighboring devices, represented by a repeated. The data has to pass through several nodes to reach the destination.
		- It is less costly than star topology.
		- The failure of a single node can cause the entire network to fail.
		- Troubleshooting is difficult
	- Tree topology
		- A variation of star topology
		![[Pasted image 20240215140529.png]]
		- Error detection is very easy, also allows prioritization.
- Network elements
	- End devices (computers): device that is able to accept data as input and perform task as output
	- Transmission medium: the means through which we send out data from one place to another (signal is transmitted in the form of electromagnetic energy through air, vacuum, lights). Wired or wireless.
	- Protocols: defined rules for communication
	- Network software: the software that helps people deploy, manage and monitor a network (SDN)
- Hub, Switch, Router, Modem, Access point
	- Hub:
		- the connector that connects the wires coming from different sides. It is known as a repeater that transmits signal to every port except the port from where the signal is received.
		- Operates on layer 1 (physical layer)
	- Switch:
		- Operates at the data link layer of OSI model, uses switching table to find out the correct destination.
		- Works on the basis of MAC address and ports to filter and send packets.
	- Router:
		- Operates at network layer of OSI
		- Works on the basis of IP and ports.
		- Determines the route, performs filtering and encapsulation.
	- Modem:
		- The device that converts information to signal (modulate and demodulate). It is connected to the router. It can be ADSL modem, optic modem, GPRS modem.
		![[Pasted image 20240215175156.png]]
	- Access point: It is just a switch with WLAN, and can be connected to router or directly to modem.
		- Access point name (APN): It is the gateway between the mobile network and another computer network (Internet). 
		![[Pasted image 20240215175614.png]]
		- The APN is used to find the right IP address that the device should be identified with on the network, determine if a private network is needed, choose the correct security settings that should be used.
		- 