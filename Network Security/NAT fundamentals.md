NAT (Network Address Translation) operates in Layer 3 forwarding devices (firewall, router, switch layer 3) to provide address simplification and conservation.
The most common user of NAT: Connect networks using private network addresses to the public Internet.
- NAT translates the private addresses that are used in the internal network into public addresses that can be routed across the Internet.
![[Pasted image 20231217170343.png]]
- The advantage: By using NAT, we can use only one address for the entire network to the outside world. I can also hide the internal network thus providing additional security.
Types of address in NAT
- Inside local address: IPv4 address that is assigned to a host on the inside network (LAN). It is likely to be the one in the reserved private IPv4 address spaces. Ex: 10.1.1.11:3333
- 