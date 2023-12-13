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

7. 
