# Configuring Floating Static Routes Lab

## 1. Overview & Objectives
This lab covers the configuration and verification of **Floating Static Routes** to provide automatic backup path redundancy for static routing topologies.

### Lab Tasks Completed:
1. Checked routing tables of `R1` and `R2` to identify active dynamic routing protocols, primary paths to `SRV1`, and internet routing paths toward `1.1.1.1`.
2. Tested baseline reachability by pinging `SRV1` and the external server `1.1.1.1`.
3. Configured floating static routes on `R1` and `R2` with higher administrative distances to allow `PC1` to reach `SRV1` automatically if the primary link fails.
4. Validated link failure behavior by shutting down primary interfaces (`G0/2/0`) to confirm that traffic successfully shifts over to the backup floating static route.

## 2. Network Topology & Routing Analysis

* **Primary vs. Backup Paths:** Floating static routes serve as backup routes with an administratively modified distance (higher than the primary routing protocol,
 such as OSPF or a primary static route) so they remain dormant in the routing table until the primary link goes down.

* **Key Tasks Addressed:**
  * Identifying active dynamic protocols in use across Enterprise A.
  * Managing redundant paths between `R1`, `R2`, and ISP connections (`ISPR1`, `ISPR2`).
