# Extended ACLs Configuration Lab

## 1. Overview & Objectives
This lab covers granular traffic filtering using **Extended ACLs** (numbered `100–199` / `2000–2699` or named `ip access-list extended`),
which match on **protocol** (IP, TCP, UDP, ICMP), **source IP**, **destination IP**, and **source/destination ports**.
Placing extended ACLs close to the **source** avoids sending unwanted traffic across the network.

### Lab Tasks & Security Policies Completed:
1. Blocked hosts in `172.16.2.0/24` from communicating with `PC1` (`172.16.1.1`).
2. Blocked hosts in `172.16.1.0/24` from accessing the **DNS** service (port 53) on `SRV1` (`192.168.1.100`).
3. Blocked hosts in `172.16.2.0/24` from accessing **HTTP** (TCP port 80) or **HTTPS** (TCP port 443) services on `SRV2` (`192.168.2.100`).
