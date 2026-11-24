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
