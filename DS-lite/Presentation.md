Good afternoon everyone, I'll begin with my presentation: Unveiling potential Denial of Service attacks in Dual Stack Lite technology.

There are 4 main sections in my presentation related to my work. The first part is introduction about us. Followed by an explanation of why we conducted this study. The most important content is described immediately after. Finally the conclusions.

You all know about us: I am the first-year PhD student with the specialization in network security. Then it will be my supervisor who plays an important role in giving my the direction about what I need to do.

Why do we make this? First is because Dual Stack Lite is one of the most effective IPv4-IPv6 transition mechanisms. I is proved to have a lot of advantages over other technologies and is still in use today, especially in Germany.

As important as it is, deploying Dual Stack Lite requires a lot of specialized equipment with a much more complex architecture than IPv4 and IPv6-only networks. So currently there are very few automated tools to realize Dual Stack Lite on your personal computer. That's why we created a tool to help network analysts easily deploy this technology without buying special equipment and building expensive labs. But the most special reason is related to security. There is too little research about security issues in Dual Stack Lite. Some studies only addressed the security threats theoretically without realizing them.

This is the architecture that we have built and performed experimental testing. There are three main parts (IPv4 home network, IPv6 ISP core network and server network). In practice, server network is actually the internet. They are built on the GNS3 platform with all virtual devices. So you can understand everything about Dual Stack Lite through just one computer.

For the implementation, we only need to build CPE and AFTR. Other devices just work normally without any configuration. 

Frame: DoS in DS-Lite
- Abstract:
	- General introduction about DS-Lite and its meaning
	- Security problems with DS-Lite
	- In this paper, we provide a broad overview of the security risks in the DS-Lite and to discuss some possible counteractions
	- To this end, after a general introduction to security, we discuss the specific security mechanisms adopted.
	- Then, we report and analyze some of the attacks against virtual devices reported in the literature, in order to point out the current security weaknesses solutions and remark the importance of considering security as an integral part in the design of the systems.
	- We conclude this article with a reasoned comparison of the considered DS-Lite with respect to a set of qualifying security attributes, namely integrity, anonymity, confidentiality, privacy, access control, authentication, authorization, resilience, self-organization.
- Introduction
	- General thing about DS-Lite
	- Again describing security problems
- Security challenges
	- Security requirements
		- Authentication
		- Integrity
		- Confidentiality
		- Access Control
		- Non-repudiation
		- Availability
	- Taxonomy of security attacks (dividing based on layers)
		- Possible approaches by attackers (in different positions)
		- Network Access Layer
		- Network Layer
		- Transport Layer
		- Application Layer
	- Main security mechanisms
		- Encryption
		- Authentication mechanisms
		- ...
- Examples of implementation in virtual devices
	- Introduction about the environment, tools
		- GNS3, Python, Designed tool
		- Virtual machines
	- Description of attacks and showing the effect
		- Every attack in different positions
		- DNS poisoning cache
		- DNS proxy
		- NAT
		- PCP
		- Neighbor Discovery
		- Application attacks
	- Applying the security (should be with graphs and images)
		- ...
		- Algorithms
- Evaluation of attacks. Which attacks are the most dangerous?
	- Checking the bandwidth to see which one is the most dangerous

For EEICT, we can do a simplified format of this article
- Name: A review of DoS attacks in DS-Lite