# HSRP (Hot Standby Router Protocol) Configuration Lab

## 1. Overview & Objectives
This lab covers First Hop Redundancy Protocol (FHRP) concepts using **HSRPv2 (Hot Standby Router Protocol version 2)**
to provide default gateway redundancy, active/standby failover, and preemption for hosts on a shared LAN subnet.

### Lab Tasks Completed:
1. Tested initial reachability from `PC1` and `PC2` to external server `8.8.8.8` and inspected each PC's configured default gateway.
2. Configured **HSRPv2** on `R1` and `R2` with a shared Virtual IP (`10.0.1.254`), making `R1` the **Active**
    router by raising its priority above the default (`100`), lowering `R2`'s priority below the default, and enabling **preemption**.
4. Set the HSRP Virtual IP (`10.0.1.254`) as the default gateway on `PC1` and `PC2`, tested pings to `8.8.8.8`,
   and inspected the PCs' ARP tables to observe the virtual MAC address mapped to the VIP.
6. Saved configurations, powered off `R1` to simulate a gateway failure, pinged `8.8.8.8` from `PC1`,
   and verified that `R2` took over as active gateway while the virtual MAC mapping in the PC's ARP table remained consistent.
8. Powered `R1` back on and verified that **preemption** allowed `R1` to reclaim the **Active** role.
