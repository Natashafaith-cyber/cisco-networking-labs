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

   
## 2. Network Topology & Policy Placement

* **Router `R1` (Access/Client Side):** Connects to `172.16.1.0/24` (`G0/0`, `.254`, hosting `PC1` at `.1` and
   `PC2` at `.2`), `172.16.2.0/24` (`G0/1`, `.254`, hosting `PC3` at `.1` and `PC4` at `.2`), and links to `R2` over `203.0.113.0/30` (`S0/0/0`, `.1`).
* **Router `R2` (Server Side):** Connects to `R1` over `203.0.113.0/30` (`S0/0/0`, `.2`), `192.168.1.0/24` (`G0/0`, `.254`, hosting `SRV1` at `.100`),
   and `192.168.2.0/24` (`G0/1`, `.254`, hosting `SRV2` at `.100`).
* **Placement Strategy:**
  * On `R2`, outbound standard named ACLs on `G0/0` (toward `192.168.1.0/24`) and `G0/1` (toward `192.168.2.0/24`) control traffic entering the server subnets.
  * On `R1`, outbound standard numbered ACLs on `G0/1` (toward `172.16.2.0/24`) and `G0/0` (toward `172.16.1.0/24`)
     block traffic between the two client subnets (`172.16.1.0/24` and `172.16.2.0/24`) without blocking traffic from `R2` (`203.0.113.0/30`).

## 3. Key Concepts & Takeaways
* **Standard ACL Filtering:** Evaluates only the **source IPv4 address** and wildcard mask; place close to the destination to prevent blocking traffic to other networks.
* **Implicit `deny any`:** Every ACL ends with an invisible `deny any` statement, so explicit `permit` entries are required for allowed traffic
  (such as `SRV1`/`SRV2` return or management traffic if needed).
* **Numbered vs. Named Standard ACLs:** Numbered standard ACLs use IDs `1–99` or `1300–1999`, while named standard ACLs use `ip access-list standard <NAME>` and allow easier line edits/removals.
