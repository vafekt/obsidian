Good afternoon everyone, I'll begin with my presentation: Unveiling potential Denial of Service attacks in Dual Stack Lite technology.

There are 4 main sections in my presentation related to my work. The first part is introduction about us. Followed by an explanation of why we conducted this study. The most important content is described immediately after. Finally the conclusions.

You all know about us: I am the first-year PhD student with the specialization in network security. Then it will be my supervisor who plays an important role in giving my the direction about what I need to do.

Why do we make this? First is because Dual Stack Lite is one of the most effective IPv4-IPv6 transition mechanisms. I is proved to have a lot of advantages over other technologies and is still in use today, especially in Germany.

As important as it is, deploying Dual Stack Lite requires a lot of specialized equipment with a much more complex architecture than IPv4 and IPv6-only networks. So currently there are very few automated tools to realize Dual Stack Lite on your personal computer. That's why we created a tool to help network analysts easily deploy this technology without buying special equipment and building expensive labs. But the most special reason is related to security. There is too little research about security issues in Dual Stack Lite. Some studies only addressed the security threats theoretically without realizing them.

This is the architecture that we have built and performed experimental testing. There are three main parts (IPv4 home network, IPv6 ISP core network and server network). In practice, server network is actually the internet. They are built on the GNS3 platform with all virtual devices. So you can understand everything about Dual Stack Lite through just one computer.

For the implementation, we only need to build CPE and AFTR. Other devices just work normally without any configuration. 

Frame:
