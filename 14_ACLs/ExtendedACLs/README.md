# Extended ACLs Configuration Lab

## 1. Overview & Objectives
This lab covers granular traffic filtering using **Extended ACLs** (numbered `100–199` / `2000–2699` or named `ip access-list extended`),
which match on **protocol** (IP, TCP, UDP, ICMP), **source IP**, **destination IP**, and **source/destination ports**.
Placing extended ACLs close to the **source** avoids sending unwanted traffic across the network.

### Lab Tasks & Security Policies Completed:
1. Blocked hosts in `172.16.2.0/24` from communicating with `PC1` (`172.16.1.1`).
2. Blocked hosts in `172.16.1.0/24` from accessing the **DNS** service (port 53) on `SRV1` (`192.168.1.100`).
3. Blocked hosts in `172.16.2.0/24` from accessing **HTTP** (TCP port 80) or **HTTPS** (TCP port 443) services on `SRV2` (`192.168.2.100`).

## 2. Network Topology & Policy Placement

The topology mirrors the dual-router layout with client LANs on `R1` and server LANs on `R2`:

* **Client LAN 1 (`172.16.1.0/24`):** Connected to `R1` `GigabitEthernet0/0` (`.254`) via `SW1`, hosting `PC1` (`.1`) and `PC2` (`.2`).
* **Client LAN 2 (`172.16.2.0/24`):** Connected to `R1` `GigabitEthernet0/1` (`.254`) via `SW2`, hosting `PC3` (`.1`) and `PC4` (`.2`).
* **WAN Transit (`203.0.113.0/30`):** Connects `R1` `Serial0/0/0` (`.1`) to `R2` `Serial0/0/0` (`.2`).
* **Server LAN 1 (`192.168.1.0/24`):** Connected to `R2` `GigabitEthernet0/0` (`.254`) via `SW3`, hosting `SRV1` (`.100`).
* **Server LAN 2 (`192.168.2.0/24`):** Connected to `R2` `GigabitEthernet0/1` (`.254`) via `SW4`, hosting `SRV2` (`.100`).

## 3. Key Concepts & Takeaways
* **Extended ACL Matching:** Evaluates both source and destination IP addresses along with Layer 4 protocols and port numbers (`eq domain` / `53`, `eq www` / `80`, `eq 443`).
* **Source-Based Placement:** Extended ACLs are typically applied **inbound** on the interface closest to the source traffic
  (such as `R1`'s LAN interfaces) to drop disallowed packets immediately before they traverse links.
* **Explicit `permit ip any any`:** Because every ACL ends with an implicit `deny any`, include an explicit permit rule at the end of ACLs intended to allow all other traffic.

