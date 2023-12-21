Definition: Are sequential lists of entries (ACEs) that perform permit or deny packet classification based one matching statements

Packet classification starts at the top and proceeds down until a matching pattern is identified.
When a match is found, the appropriate action (permit or deny) is taken, and processing stops.
At the end of every ACL is an implicit deny ACE, which denies all packets that did not match earlier in the ACL.

Types of ACLs:
- Numbered standard ACLs: This ACL defines packets based solely on the source network. They use the numbered entries 1-99, and 1300-1999
- Numbered extended ACLs: This ACL defines packets based on source, destination, protocol, port or a combination of other packet attributes, and they use the numbered entries 100-199 and 2000-2699
- Named ACLs: Allows standard and extended ACLs to be given names instead of numbers
- Port ACLs (PACLs): use standard, extended, named, and named extended MAC ACLs to filter traffic on Layer 2 switchports
- VLAN ACLs (VACLs): use standard, extended, named, and named extended MAC ACLs to filter traffic on VLANs

Wildcard mask: It is a new concept used to define the range of IP addresses in ACL or routing purposes. 
![[Pasted image 20231219220954.png]]
![[Pasted image 20231219221100.png]]

**_ip access-list extended ACL-Example2  
deny ip host 10.0.0.5 any  
permit ip any any_**  
Trong ví dụ này, từ khóa "host" được sử dụng làm cách viết tắt cho **Wildcard mask** 0.0.0.0, chỉ định đối sánh chính xác cho địa chỉ IP 10.0.0.5. ACL từ chối lưu lượng truy cập từ máy cụ thể này đến bất kỳ đích nào trong khi cho phép tất cả lưu lượng truy cập khác.

Bạn muốn cấu hình EIGRP để chỉ bao gồm giao diện FastEthernet0/0 (mạng con 192.168.0.0/23) trong quy trình định tuyến. Bạn sẽ sử dụng cấu hình sau:    
**_router eigrp 100  
network 192.168.0.0 0.0.1.255_**    
Trong ví dụ này, quy trình EIGRP với AS số 100 được định cấu hình với câu lệnh mạng bao gồm dải địa chỉ IP 192.168.0.0 – 192.168.1.255, sử dụng **Wildcard mask** 0.0.1.255.

After applying to an interface, ACL will have its effect. But we need to define ACL first. 

Numbered ACLs:
- The process for defining this ACL (in case of standard ACL):
	- using the command access-list {number} { deny | permit } source [source-wildcard] [log]. The ACL number can be 1–99 or 1300–1999.
	- Apply the ACL to an interface by using the command ip access-group {acl-number} {in|out} under interface configuration mode. The direction (in or out) in which the ACL needs to be applied must be specified. Cisco routers allow only one inbound ACL and one outbound ACL per interface
![[Pasted image 20231220102100.png]]
![[Pasted image 20231220102616.png]]

Port ACLs:
- Access lists applied on Layer 2 ports are called port access control lists (PACLs)
- PACLs only support filtering incoming traffic on an interface (no outbound filtering support).
- PACLs cannot filter Layer 2 control packets, such as CDP, VTP, DTP, PAgP, UDLD, and STP
- PACLs are supported only in hardware. 
- PACLs do not support ACLs to filter IPv6, ARP, or Multiprotocol Label Switching (MPLS) traffic
- PACLS are only used in mode switchport (with 2 type trunk or access)
![[Pasted image 20231220110852.png]]

VLAN ACLs:
- Access lists applied to VLANs
- VACLs can filter traffic that is bridged within a VLAN or that is routed into or out of a VLAN.
- Define a VLAN access map by using the command vlan access-map name sequence
- Configure the match statement by using the command match { ip address { aclnumber | acl-name } | mac address acl-name }.
- Configure the action statement by using the command action forward|drop [log]. The action statement specifies the action to be taken when a match occurs
- Apply the VACL by using the command vlan filter vlan-access-map-name vlan-list. vlan-list can be a single VLAN, a range of VLANs (such as 5–30), or a comma-separated list of multiple VLANs (such as 1,2–4,6)
- a VLAN access map applied to VLAN 20 to drop ICMP and Telnet traffic and allow other traffic.
![[Pasted image 20231220111708.png]]
- 


