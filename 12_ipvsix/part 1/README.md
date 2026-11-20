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

* **Router 1 (`R1`):** Acts as the default gateway for all three segments (`GigabitEthernet0/0`, `GigabitEthernet0/1`, and `GigabitEthernet0/2`), routing both IPv4 and IPv6 traffic across the local subnets.
* **Segment 1 (`SW1` & `PC1`):** Connected via `R1`'s `GigabitEthernet0/0` interface using IPv4 subnet `192.168.1.0/24` and IPv6 prefix `2001:DB8:0:1::/64` (e.g., `R1` gateway `2001:DB8:0:1::254/64` or `::1/64`, and `PC1` on the same `/64` prefix).
* **Segment 2 (`SW2` & `PC2`):** Connected via `R1`'s `GigabitEthernet0/1` interface using IPv4 subnet `192.168.2.0/24` and IPv6 prefix `2001:DB8:0:2::/64`.
* **Segment 3 (`SW3` & `PC3`):** Connected via `R1`'s `GigabitEthernet0/2` interface using IPv4 subnet `192.168.3.0/24` and IPv6 prefix `2001:DB8:0:3::/64`.


## 3. Key Concepts & Takeaways
* **Dual-Stack Networking:** Running IPv4 and IPv6 protocol stacks simultaneously on interfaces so hosts and routers can handle traffic for either protocol natively.
* **`ipv6 unicast-routing`:** Required on Cisco IOS routers to enable IPv6 packet forwarding between interfaces (disabled by default).
* **Global Unicast vs. Link-Local Addresses:** Every IPv6-enabled interface automatically generates a link-local address (`FE80::/10`) for local link operations (such as Neighbor Discovery), alongside its configured global unicast address (`2001:DB8::/32` documentation prefix).
