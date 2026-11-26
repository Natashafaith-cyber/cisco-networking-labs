# Standard ACLs Configuration Lab

## 1. Overview & Objectives
This lab covers **OSPF** reachability across multiple subnets and traffic filtering using **Standard Numbered ACLs** (on `R1`) 
and **Standard Named ACLs** (on `R2`). Because standard ACLs match only on **source IPv4 address**,
rules are applied outbound as close to the destination networks as possible to avoid unintended blocking.

### Lab Tasks Completed:
1. Configured OSPF across `R1` and `R2` so all PCs (`PC1`–`PC4`) and servers (`SRV1`, `SRV2`) have full IP reachability prior to applying filtering policies.
2. Enforced the policy allowing **only `PC1` (`172.16.1.1`) and `PC3` (`172.16.2.1`)** to access `192.168.1.0/24` (where `SRV1` resides).
3. Blocked hosts in `172.16.2.0/24` from accessing `192.168.2.0/24` (where `SRV2` resides).
4. Prevented bidirectional inter-VLAN/subnet access between `172.16.1.0/24` and `172.16.2.0/24` using standard ACLs on `R1`.
