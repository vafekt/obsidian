NAT (Network Address Translation) operates in Layer 3 forwarding devices (firewall, router, switch layer 3) to provide address simplification and conservation.
The most common user of NAT: Connect networks using private network addresses to the public Internet.
- NAT translates the private addresses that are used in the internal network into public addresses that can be routed across the Internet.
![[Pasted image 20231217170343.png]]
- The advantage: By using NAT, we can use only one address for the entire network to the outside world. I can also hide the internal network thus providing additional security.
![[Pasted image 20231217210931.png]]
Types of address in NAT
- Inside local address: IPv4 address that is assigned to a host on the inside network (LAN). It is likely to be the one in the reserved private IPv4 address spaces. Ex: 10.1.1.11:3333
- Inside global address: A globally routable IPv4 address that represents one or more inside local IPv4 addresses to the outside world. Ex: 10.1.1.11:3333 will be translated to 73.8.2.11:3333 (inside global address). This address still refers to a host that exists on the inside network, but this time that host appears as when viewed from the global perspective.
- Outside local address: The IPv4 address of an outside host when it appears to the inside network. Not necessarily a public address, and it is allocated from a routable address space. Ex: 82.6.4.2:80 refers to a host on the outside network, but it appears as when viewed from the local perspective.
- Outside global address: The IPv4 address that is assigned to a host on the outside network by the host owner. Ex: 82.6.4.2:80 will be translated to **`82.6.4.2:80`**, which still refers to a host that exists on the **Outside** network, but this time is what that host appears as when viewed from the **Global** perspective. Hence, this is the **Outside Global** address.

RFC 1918 Private IPv4
- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

1 important thing is translation. It is based on NAT table. If there is no matching address in the table, NAT will check if there is a rule specifying a dynamic translation. If there is a rule, a new entry will be created.

PAT (Port Address Translation), so called Hide NAT: PAT is only an extension of NAT that operates at layer 4 (because it requires port translation). It enables multiple devices to use the same public IP address simultaneously, differentiating them based on the assigned port numbers.

Deployment of NAT:
- Static NAT: maps an unregistered IPv4 address to a registered IPv4 address. One-to-one static NAT is particularly useful when a device must be accessible from outside the network. For example, static NAT is used when a server on a DMZ needs to be continuously reachable by the same predictable, translated address.
- Dynamic NAT: maps an unregistered IPv4 address to a registered IPv4 address from a pool of registered IPv4 addresses which is useful for outbound client connections when you have fewer outside global IP addresses than inside local hosts.
- Dynamic Port Address Translation PAT: maps multiple unregistered IPv4 addresses to a single registered IP address by using the source port to distinguish between translations. That single IP address may be the IP address of the NAT device itself.
- Policy NAT: uses extended criteria, such as source addresses, destination addresses, and transport layer ports to specify the translation. For example, traffic that is destined to a particular partner network may be translated to a specific address using PAT while traffic destined elsewhere is translated using a dynamic NAT pool.