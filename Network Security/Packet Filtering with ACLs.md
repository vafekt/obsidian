ACL (Access Control List) is an essential part of maintained network. They help controlling traffic and protecting data.
- Packet filtering. Can be implemented on routers, multi-layer switches, and firewalls.
- Traffic direction
- QoS
It includes the mechanism to permit, deny, classify, and mark traffic to secure, optimize and protect the network.
- QoS can be configured by using Cisco modular QoS configuration (MQC).
	- Class Maps: Define the traffic
	- Policy Maps: Apply the rules
	- Service Policy: Activate them on an interface
![[Pasted image 20231217223053.png]]

DMZ and firewall
- A DMZ is a network segment that is isolated from both the internal network and the external (untrusted) network. (usually between). The DMZ acts as a buffer zone between the trusted internal network and the untrusted external network, providing an additional layer of security.
- Systems in the DMZ are typically more exposed to potential threats from the internet, but they are separated from the critical internal network, helping to contain and mitigate security risks.
- A firewall is a network security device or software that monitors and controls incoming and outgoing network traffic based on predetermined security rules.
![[Pasted image 20231217223531.png]]

Option for packet filtering
- Source and destination IP addresses at the network layer.
- Protocol differentiation at the transport layer: TCP, UDP, ICMP, OSPF, and so on 
- When the transport layer is TCP or UDP, source and destination ports can be specified. 
- When the transport layer is ICMP, types and codes can be specified.
- When the traffic is TCP, the presence of the ACK bit or the RST bit can be verified. Under normal TCP connection flow, neither of these bits is ever set in the first packet of a new TCP connection.

Example (shown in the image above):
- Clients on the user subnet are permitted to send packets to TCP ports 80 and 443 on the two web servers on the server subnet.
- Clients on the user subnet are permitted to send packets to TCP ports 20 and 21 on the FTP server on the server subnet.
- The administrator can use the show access-list 100 command to view the ACL and each entry’s hit count. Without the explicit deny, there would be no record of the number of packets that were denied by the ACL. Also, the explicit deny uses the log argument, which will cause the generation of syslog messages that are associated with the denies, which can facilitate central audit trails of rejected traffic.
- eq means: equal to
- Explicit vs implicit: Explicit is when you define the rule in access list. Implicit Denies are Automatically set by the System, and does not generate a message. So when we want to deny the rest, we need to define with the log.
- 