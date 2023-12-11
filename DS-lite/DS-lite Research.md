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
			- 