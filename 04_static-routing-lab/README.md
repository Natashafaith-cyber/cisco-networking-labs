This project demonstrates the configuration of basic device parameters, IP addressing, and IPv4 Static Routing across a 3-router topology in Cisco Packet Tracer.

The primary objective is to achieve end-to-end connectivity between two distinct local area networks (PC1 and PC2) by manually configuring the routing tables on each intermediate gateway.

Network Topology
The network consists of three core segments and two local networks:

PC1 Network : 192.168.1.0/24

R1 to R2 Link: 192.168.12.0/24

R2 to R3 Link: 192.168.13.0/24

PC2 Network : 192.168.3.0/24

To enable PC1 to successfully reach PC2, each router needs to know about the remote networks it is not directly connected to.
R1 needs paths to the R2-R3 link and the PC2 local network, both reachable via R2 (192.168.12.2)
R2 is in the middle; it needs to know how to reach the PC1 LAN and the PC2 LAN.

Insights

No Dynamic Protocol Overhead: By relying exclusively on static routes, no routing advertisements (like OSPF hello packets or RIP updates) are broadcasted across the links. This prevents potential network reconnaissance or malicious route injection attacks.

Strict Access Control: Traffic paths are deterministic. Maliciously added physical devices cannot redirect traffic automatically because the routing table path is fixed by the administrator.



