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
