# Configuring EIGRP (Enhanced Interior Gateway Routing Protocol) Lab 

## 1. Overview & Objectives
This lab covers the configuration and verification of **EIGRP (Autonomous System 100)** across a multi-router topology.
The primary objectives include setting up loopback interfaces, enabling EIGRP directly on individual interfaces, 
disabling automatic summarization, configuring passive interfaces, and implementing **unequal-cost load balancing**.

### Lab Tasks Completed:
1. Configured device hostnames and assigned IP addresses across all router interfaces, ensuring all links were brought up (`no shutdown`).
2. Configured loopback interfaces on each core router (`1.1.1.1/32` for R1, `2.2.2.2/32` for R2, `3.3.3.3/32` for R3, and `4.4.4.4/32` for R4).
3. Configured EIGRP under Autonomous System 100:
   * Disabled auto-summary (`no auto-summary`).
   * Enabled EIGRP directly on active physical and loopback interfaces.
   * Configured appropriate passive interfaces (including loopback interfaces).
4. Configured **R1 to perform unequal-cost load-balancing** for traffic destined for the `192.168.4.0/24` network.

   
## 2. Network Topology & Routing Architecture

* **Autonomous System:** EIGRP AS 100
* **Core Routers:** `R1`, `R2`, `R3`, and `R4` configured in a multi-path topology with redundant paths linking through `R2` and `R3`.
* **Access Layer:** Router `R4` connects directly to switch `SW1` and end client `PC1` on the `192.168.4.0/24` subnet.
* **EIGRP Concepts Applied:**
  * **Interface-Level Activation:** Running EIGRP directly on interfaces using `ip eigrp <as-number>` rather than broad network wildcard commands.
  * **Unequal-Cost Load Balancing:** Utilizing the `variance` command to allow EIGRP to install backup paths (feasible successors)
   that have a higher metric than the successor route into the routing table.
