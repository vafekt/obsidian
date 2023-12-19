What we want from access control is to allow TCP from connections from the trusted network (usually the local network) to a non-trusted network (Internet), and not allow the opposite direction.

Stateful vs stateless firewall
- Stateful firewalls monitor all aspects of the traffic streams, their characteristics and communication channels. These firewalls can integrate encryption or tunnels, identify TCP connection stages, packet state and other key status updates.
- Stateless firewalls, however, only focus on individual packets, using preset rules to filter traffic. If a data packet goes outside the parameters of what is considered acceptable, the stateless firewall protocol will identify the threat and then restrict or block the data housing it.
- Pros of stateful firewalls
	- Stateful firewalls can detect when illicit (illegal) data is being used
	- A stateful inspection firewall also has the ability to log and store important aspects of network connections.
- Cons of stateful firewalls
	- Unless a stateful firewall has the latest software updates, vulnerabilities can allow it to be compromised by a hacker and then controlled.
	- In the case of some stateful firewalls, they can be fooled into allowing a harmful connection to the network.
- For a small business firewalls, companies may want to lean more toward a stateless firewall for affordability.
- For larger enterprises, stateful firewalls are the better choice. Because they offer dynamic packet filtering, they can adapt to a variety of threats