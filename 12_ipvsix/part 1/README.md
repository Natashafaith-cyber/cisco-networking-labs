# IPv6 Configuration & Dual-Stack Lab

## 1. Overview & Objectives
This lab focuses on deploying **IPv6** alongside an existing **IPv4** configuration to build a **dual-stack** network where devices can communicate using both address families.

### Lab Tasks Completed:
1. Enabled IPv6 unicast routing globally on router `R1` using `ipv6 unicast-routing`.
2. Configured global unicast IPv6 addresses (and link-local addresses as needed) on `R1`'s connected interfaces.
3. Verified interface IPv6 address assignments (including global unicast and `FE80::` link-local addresses) using `show ipv6 interface brief`.
4. Configured IPv6 addresses and IPv6 default gateways on `PC1`, `PC2`, and `PC3`.
5. Tested end-to-end reachability between PCs using both **IPv4** (`ping`) and **IPv6** (`ping` / `ipv6` host addressing).

   ## 2. Network Topology & Subnet Layout

The topology consists of a central router (`R1`) connected to three switches (`SW1`, `SW2`, `SW3`) and three end hosts (`PC1`, `PC2`, `PC3`), with IPv4 already in place and IPv6 added for dual-stack operation:
