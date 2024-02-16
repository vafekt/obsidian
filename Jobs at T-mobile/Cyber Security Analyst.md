**Network and computer security**
1. Types of security
- Computer security: name for the collection of tools designed to protect data and thwart hackers
- Network security: measures to protect data during their transmission
- Internet security:  measures to protect data during the transmission over interconnected networks
2. Goals of information security
- Confidentiality: prevents unauthorized use or disclosure of information
- Integrity: safeguards the accuracy and completeness of information
- Availability: authorized users have reliable and access to information
3. Access Control
- The ability to permit or deny the use of an object by a subject
- It provides 3 essential services:
	- Authentication (who can login)
		- Person
		- Application or process
		- Machine or device
		- To prove authentication, we need identity through
			- Passwords, PIN
			- Token, Smart card,
			- Biometrics such as fingerprints, signature, voice
	- Authorization (what an authorized user can do): write, read, execute, modify
		- Roles
		- Groups
		- Location
		- Time
		- Transaction type
	- Accountability (identifies that a user did)
4. Attack sources
- Active attacks: actively involves writing data to network, disguises one's address...
	- Denial of Service attacks
		- Attempt to make a machine or network resource unavailable to its intended users. 
		- Purpose is to temporarily or indefinitely interrupt or suspend services of a host connected to the Internet
		- SYN flooding, Smurf attacks, Starvation
	- Spoofing attack
	- Man-in-the-middle attack
		- Attacker makes independent connections with victims and relays messages between them, making them believe that they are talking directly to each other
		- Usually a result of lack of end-to-end authentication
	- ARP poisoning
	- Smurf attack
	- SQL injection
	- Buffer overflow
	- Session Hijacking
		- Exploitation of a valid computer session, to gain unauthorized access to information or services in a computer system
- Passive attacks
	- Reconnaissance
		- Unauthorized users to gather information about the network or system before launching other more serious types of attacks
		- Useful information: Names, IP, email, password, token
	- Eavesdropping
	- Port scanning
5. Attacks on different layers
![[Pasted image 20231213195150.png]]
- Layer 2 attacks
	- ARP spoofing
![[Pasted image 20231213200021.png]]
	- MAC flooding (poisoning)
		- MAC is 48-bit address: FFFF.FFFF.FFFF
		- The CAM table stores information such as MAC available on physical ports with associated VLAN parameters.
		- Switch learn the way to every hosts on the link. Other clients can also learn from the CAM table of switch
![[Pasted image 20231213200200.png]]
	- DHCP attack
![[Pasted image 20231213200235.png]]
	- VLAN hopping
![[Pasted image 20231213200618.png]]
	- Spanning tree attacks
		- To maintain loop-free topologies in a redundant Layer 2 infrastructure
		- Provides path recovery services
		- A switch is elected as root
		- Attacks
			- Attacker sends BPDU (bridge protocol data unit) advertising itself with a bridge priority of zero
			- Send BPDU messages from attacker to force spanning tree recalculations => Can be DoS
				- Send another BPDU messages to become root bridge
	- Port authentication
![[Pasted image 20231213204816.png]]
- Layer 3 attacks
	- IP spoofing
	- ICMP attacks: Ping flood, Smurf attack, Ping of death
	- Fragmentation attack: Teardrop attack
		- involves inserting false offset information into fragmented packets. As a result, during reassembly, there are empty or overlapping fragments that can cause the system to be unstable
	- Routing attack: Routing table poisoning RIP, OSPF, EIGRP
		- An attacker could forge a RIP packet, claiming his host "X" has the fastest path out of the network. All packets sent out from that network would then be routed through X
- Layer 4 attacks
	- TCP attacks: SYN Flood – occurs when an attacker sends SYN requests in succession to a target.
	- TCP spoofing: When we can predict the port of server, and know the sequence number with Payload size, we can inject packet to the existing connection
	- SYN cookies is a solution
- Application layer attacks
	- DNS poisoning
	- Denial of Service with HTTP, SIP
	- SQL injection
	- Password cracking
	- Cross-Site Scripting (XSS): Malicious scripts are injected into web pages viewed by other users. These scripts can steal sensitive information, such as login credentials or session cookies, from users who view the compromised pages.
	- Session Hijacking
	- Phishing
6. TCPDUMP and Wireshark
- `tcpdump` is a command-line packet analyzer that is widely used for network troubleshooting and packet analysis. It allows users to capture and display the traffic that is traversing a network interface in real-time or to save the captured packets to a file for later analysis.
7. 
