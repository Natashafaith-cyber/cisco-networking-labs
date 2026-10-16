# Configuring EtherChannel Lab 

## 1. Overview & Objectives
This lab covers link aggregation concepts using **EtherChannel (Port-Channel)** to bundle multiple physical interfaces into a single logical high-bandwidth connection, 
providing redundancy and load balancing.

### Lab Tasks Completed:
1. Configured a Layer 2 EtherChannel between **ASW1** and **DSW1** using **LACP** (IEEE 802.3ad) and set it as a trunk.
2. Configured a Layer 2 EtherChannel between **ASW2** and **DSW2** using **PAgP** (Cisco proprietary) and set it as a trunk.
3. Configured a Layer 3 EtherChannel between **DSW1** and **DSW2** using a **static EtherChannel** (mode `on`).
4. Configured static routing to allow end hosts (`PC1`, `PC2`) to reach `SRV1`.
5. Verified the default EtherChannel load-balancing method across the switches.
6. Configured global switch load-balancing based on **source and destination IP addresses** (`src-dst-ip`).

## 2. Network Topology & Addressing Summary

The lab environment is structured into two primary access switches and two distribution switches, creating a redundant multi-tier switched network topology. 

* **Access Switch 1 (ASW1):** This switch connects directly to end clients `PC1` and `PC2` within the client subnet (`172.16.1.0/24`) on port-level access connections.
*  ASW1 hosts the VLAN 1 Switch Virtual Interface (SVI) configured with the IP address `172.16.1.254/24`.
*   It aggregates its uplinks to Distribution Switch 1 (`DSW1`) into a Layer 2 EtherChannel trunk using LACP.

* **Access Switch 2 (ASW2):** Serving the alternate user segment, ASW2 manages the local `172.16.2.0/24` subnet.
*  It features an SVI on VLAN 1 configured with the IP address `172.16.2.254/24`.
*   ASW2 connects to Distribution Switch 2 (`DSW2`) utilizing a Layer 2 EtherChannel trunk aggregated via PAgP.

* **Distribution Switch 1 (DSW1):** DSW1 acts as a layer 3 core routing boundary for ASW1.
*  It interconnects with DSW2 using a high-speed static Layer 3 EtherChannel (`Port-Channel 3`), where each switch has assigned IP addresses on the `/30` point-to-point subnet (`10.0.0.1` on DSW1 and `10.0.0.2` on DSW2).
*   IP routing is enabled with static routes pointing to the client networks.

* **Distribution Switch 2 (DSW2):** DSW2 pairs with DSW1 to form the upper distribution tier, terminating the Layer 3 backbone link on `Port-Channel 3` (`10.0.0.2/30`).
*  It includes static routing configurations to forward traffic across the core toward the server network.

* **Destination Server (SRV1):** Connected directly via `GigabitEthernet0/1` on the server edge segment, `SRV1` operates on the `172.16.2.1/24` IP address space, serving as the target destination for traffic originating from the access layer clients (`PC1` and `PC2`) across the routed EtherChannel core.

## 3. Key Protocol Details
* **LACP (Link Aggregation Control Protocol):** Open-standard protocol (IEEE 802.3ad) operating in `active` or `passive` mode. Used between ASW1 and DSW1.
* **PAgP (Port Aggregation Protocol):** Cisco-proprietary protocol operating in `desirable` or `auto` mode. Used between ASW2 and DSW2.
* **Static EtherChannel:** Forced bundling (`mode on`) without negotiation protocols. Used for the Layer 3 backbone link between DSW1 and DSW2.




   
