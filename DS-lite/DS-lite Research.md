This is a transition technique that enables a service provider to share IPv4 addresses among customers with 2 techniques:
- IP in IP (IPv4-in-IPv6)
- IPv4 NAPT
![[Pasted image 20231206143736.png]]

**Deployment scenarios**
The most important thing in DS-lite is: IPv4-in-IPv6 tunnel (1) 
- that is built to cross the network to reach a Carrier-grade IPv4-IPv4 NAT (2) (AFTR - Address Family Translation Router)
Benefits:
- Leveraging the large IPv6 address space. Overlapping private IPv4 address spaces are not suitable to support very large customer bases.
- Tunnels provide a direct connection between B4 and AFTR. This enable customers and applications to control how NAT function of the AFTR is performed.
- A key characteristic: Communications between end-nodes stay within their address family.
	- IPv6 only communicates with IPv6. And IPv4 only with IPv4
	- No protocol translation involved

**Key characteristics**
There are 2 key components of DS-lite
- B4 (Basic Bridging BroadBand)
- AFTR (Address Family Transition Router)
There are 2 key aspects in DS-lite to allow IPv4 clients to connect to the Internet
- Use of an IPv4-in-IPv6 tunneling mechanism between B4 and AFTR
- Use of NAPT44 (IPv4-IPv4 CGNAT) in the AFTR
NAPT44 process is centralized in AFTR (not B4).
The B4 function is located in the CPE, This CPE has IPv4 on the LAN side towards IPv4 clients.
- CPE/B4 offers IPv4 clients the DHCP service with private IPv4 addresses and DNS proxy.
- DNS proxy allows the CPE/B4 to receive DNS requests in IPv4 and resolve them using IPv6 on the operator's network.
- The WAN interface of CPE/B4 is IPv6-only and allows communicating and routing IPv6 traffic towards AFTR
- CPE/B4 encapsulates all IPv4 traffic using IPv4-in-IPv6 tunnel and forwarding to AFTR (vice versa)
- CPE/B4 must be provided with the IPv6 address of AFTR (for mapping destination). The address can be configured using manual configuration or DHCPv6 options.
The AFTR function may be located in an edge router on ISP's network. 
- It must have at least 2 interfaces:
	- 1 interface on IPv6 side of operator network for communicating with all CPEs/B4s
	- 1 WAN interface on the IPv4 Internet.
- It receives IPv6 traffic (IPv4 packet encapsulated inside), decapsulates and extracts IPv4 traffic from the tunnel. Then it proceeds to perform stateful NAPT44
	- In NAPT44, AFTR uses the pool of public IPv4 addresses assigned to the WAN interface
DS-lite supports all types of unicast traffic, but not multicast traffic.
- DS-lite defines the well-known 192.0.0.0/29 range, reserving 192.0.0.1 for AFTR and 192.0.0.2 for B4

- **B4**
	- B4 is a function implemented on a dual-stack-capable node (either a connected device or a CPE).
	- Encapsulation: Defining the multipoint-to-point IPv4-in-IPv6 tunnel that ends on the service provider AFTR.
	- Fragmentation and Reassembly: Because there is another protocol IPv6 upon the IPv4 packet, the MTU size of all links between B4 and AFTR elements reduces at least 40 bytes (the datagram part decreases to have space for IPv6 header).
		- ==Path MTU discovery is  not a reliable method to deal with this problem==  
		- Some recall about IPv4 and IPv6 fragmentation:
			- IPv4: Every IPv4 packet has the format mentioning the fragmentation (not optional like IPv6).
			![[Pasted image 20231206161345.png]]
			- IPv6: A separate header is added, it can be seen in the last fragment.
		- B4 element must perform fragmentation and reassembly if the outgoing link MTU (B4-AFTR) cannot accommodate the extra IPv6 header.
			- There can be a situation when original IPv4 packet is not oversize (it can be fragmented, but already on the local-link) but the packet is oversized after IPv6 encapsulation. Then: IPv4 must not be fragmented. 
				- Fragmentation must happen after the encapsulation of IPv6 packet.
				- Reassembly must happen before the decapsulation of IPv4 packet.
	- B4 is configured with IPv6 from the ISP. It can also learn the address of a DNS recursive server through DHCPv6 (or other methods over IPv6)
		- But the DHCPv6 server only defines option to get IPv6 address of DNS server (not IPv4 address of recursive DNS server)
		- So B4 has to perform all DNS resolution over IPv6
		- B4 can also pass this IPv6 address to downstream IPv6 nodes, but not for IPv4 nodes. So B4 should implement DNS proxy (the same function as DNS recursive server, but proxy is only a caching server).
		- If the proxy does not have the IP address, it will forward the request to a recursive DNS server.
- It is popular for B4 and AFTR to use IPv6 through DHCPv6 so security vulnerabilities for exploiting addresses can be possible.
	- Because B4 element might obtain new IPv6 address because of lease expiry, traffic forward to B4 using previous IPv6 many never reach the destination (or delivered to another B4, in this case there are more than 1 B4)
	- It also affects all mapping types
		- implicit (TCP SYN)
		- explicit (using PCP)
- 
- When there are multiple CPEs (multiple CPEs connect to one B4)