# IPv6 Static Routes, SLAAC & Floating Backup Paths Lab

## 1. Overview & Objectives
This lab covers **IPv6 unicast routing**, **Stateless Address Autoconfiguration (SLAAC)**
for end hosts, and **IPv6 static routing with floating backup paths** across a multi-router topology with link-local-only serial links.

### Lab Tasks Completed:
1. Enabled IPv6 unicast routing globally on each router (`R1`, `R2`, and `R3`) using `ipv6 unicast-routing`.
2. Configured `PC1` and `PC2` to obtain IPv6 addresses dynamically via **SLAAC** (Router Advertisements),
    and inspected the resulting global unicast and link-local IPv6 addresses (`ipconfig /all` or `ipv6config`).
4. Configured primary and floating backup IPv6 static routes across `R1`, `R2`, and `R3` so `PC1` and `PC2` can reach each other,
    ensuring the path through `R2` acts strictly as a backup path using a higher administrative distance (e.g., `5` or `130`).

## 2. Network Topology & Path Design

* **Routers:** `R1`, `R2`, and `R3` with IPv6 addresses pre-configured on interfaces and serial links using link-local addresses only.
* **LAN 1 (`PC1` & `SW1`):** Connected to `R1` (`GigabitEthernet0/0`) on prefix `2001:DB8:0:1::/64`.
* **Direct Link (`R1` — `R3`):** Connects `R1` (`GigabitEthernet0/1`) to `R3` (`GigabitEthernet0/1`) over prefix `2001:DB8:0:13::/64`, serving as the primary path between `R1` and `R3`.
* **Backup Path via `R2`:** Connects `R1` (`Serial0/0/0`) to `R2` (`Serial0/0/0`) and `R2` (`Serial0/0/1`) to `R3` (`Serial0/0/0`), used only when the direct link fails.
* **LAN 2 (`PC2` & `SW2`):** Connected to `R3` (`GigabitEthernet0/0`) on prefix `2001:DB8:0:3::/64`.
