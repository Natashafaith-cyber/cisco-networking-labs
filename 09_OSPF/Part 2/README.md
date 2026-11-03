# Advanced OSPF Configuration Lab (CCNA 200-301)

## 1. Overview & Objectives
This lab covers the configuration and verification of **OSPFv2 (Open Shortest Path First)** routing within a multi-router topology,
focusing on direct interface-level OSPF activation, reference bandwidth cost tuning, passive interface design, and default route redistribution from an Autonomous System Boundary Router (ASBR).

### Lab Tasks Completed:

1.Configured device hostnames, interface IP addresses, and enabled all router interfaces (excluding ISPR1).
2. Configured loopback interfaces on each router (`1.1.1.1/32` for R1, `2.2.2.2/32` for R2, `3.3.3.3/32` for R3, and `4.4.4.4/32` for R4)
3. Enabled OSPF directly on each router interface and configured appropriate passive interfaces
4. Configured the OSPF reference bandwidth (`auto-cost reference-bandwidth 100000`) on each router so FastEthernet interfaces calculate a cost of 100
5. Configured **R1 as an ASBR** to inject and advertise a default route into the OSPF domain
6. Checked the routing tables of R4 to confirm default route injection
7. Used Simulation mode to analyze OSPF Hello messages and inspect header fields

