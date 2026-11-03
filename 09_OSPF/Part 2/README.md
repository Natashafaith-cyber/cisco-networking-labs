# Advanced OSPF Configuration Lab (CCNA 200-301)

## 1. Overview & Objectives
This lab covers the configuration and verification of **OSPFv2 (Open Shortest Path First)** routing within a multi-router topology,
focusing on direct interface-level OSPF activation, reference bandwidth cost tuning, passive interface design, and default route redistribution from an Autonomous System Boundary Router (ASBR).

### Lab Tasks Completed:

1.Configured device hostnames, interface IP addresses, and enabled all router interfaces (excluding ISPR1).

2. Configured loopback interfaces on each router (`1.1.1.1/32` for R1, `2.2.2.2/32` for R2, `3.3.3.3/32` for R3, and `4.4.4.4/32` for R4).
   
4. Enabled OSPF directly on each router interface and configured appropriate passive interfaces.
   
6. Configured the OSPF reference bandwidth (`auto-cost reference-bandwidth 100000`) on each router so FastEthernet interfaces calculate a cost of 100.

8. Configured **R1 as an ASBR** to inject and advertise a default route into the OSPF domain.
   
10. Checked the routing tables of R4 to confirm default route injection.
    
12. Used Simulation mode to analyze OSPF Hello messages and inspect header fields.


## 2. Network Topology & Device Layout

The network consists of an external gateway router (`ISPR1`), four internal routers (`R1`, `R2`, `R3`, `R4`), an access switch (`SW1`), and an end host (`PC1`).

* **ISPR1 & R1 Connection:** `ISPR1` links to `R1` over the public `203.0.113.0/30` subnet. OSPF is purposely omitted from this external interface.
* **Router 1 (R1):** Functions as the ASBR, connecting to `R2` (`10.0.12.0/30`), `R3` (`10.0.13.0/30`), and `ISPR1`. It originates a default route into Area 0.
* **Router 2 (R2):** Interconnects with `R1` and links downward to `R4` via the `10.0.24.0/30` subnet.
* **Router 3 (R3):** Interconnects with `R1` and links downward to `R4` via the `10.0.34.0/30` subnet.
* **Router 4 (R4):** Aggregates local traffic, connecting to switch `SW1` and client `PC1` on the `192.168.4.0/24` network.
* 


    

