# IPv6 Configuration Part 2: EUI-64, Link-Local & Static Routing

## 1. Overview & Objectives
This lab builds on IPv6 fundamentals by focusing on automatic interface ID generation using **EUI-64**, 
enabling link-local-only IPv6 interfaces (`ipv6 enable`), and configuring **IPv6 static routes** over link-local next-hop addresses.

### Lab Tasks Completed:
1. Calculated the 64-bit **EUI-64 interface IDs** from interface MAC addresses and configured global unicast IPv6 addresses using
   the `eui-64` keyword on `GigabitEthernet0/1` of `R1` and `R2`.
3. Configured static IPv6 addresses and corresponding EUI-64 default gateways on `PC1` and `PC2`.
4. Enabled IPv6 on the point-to-point link (`GigabitEthernet0/0`) between `R1` and `R2` without configuring an explicit global unicast IPv6 address (`ipv6 enable`),
 allowing communication strictly via link-local (`FE80::`) addresses.
7. Configured IPv6 static routes (`ipv6 route`) on `R1` and `R2` using the exit interface and neighbor link-local address so `PC1` can successfully ping `PC2`.

## 2. Network Topology & Subnet Layout

The topology connects two client LAN segments through a pair of routers (`R1` and `R2`) linked via an unnumbered IPv6 transit interface:

* **LAN 1 (`PC1` & `SW1`):** Connected to `R1`'s `GigabitEthernet0/1` interface on subnet `2001:DB8::/64`[cite: 9]. `PC1` is assigned `2001:DB8::2/64` and uses `R1`'s EUI-64-derived IPv6 address as its default gateway.
* **Router-to-Router Transit (`R1` `G0/0` — `R2` `G0/0`):** Operates without global unicast addresses (`ipv6 enable`), relying purely on auto-generated link-local addresses (`FE80::/10`) for neighbor reachability and static route next-hop resolution.
* **LAN 2 (`PC2` & `SW2`):** Connected to `R2`'s `GigabitEthernet0/1` interface on subnet `2001:DB8:0:1::/64`[cite: 9]. `PC2` is assigned `2001:DB8:0:1::2/64` and uses `R2`'s EUI-64-derived IPv6 address as its default gateway.
