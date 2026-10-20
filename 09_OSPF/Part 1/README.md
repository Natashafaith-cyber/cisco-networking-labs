# Configuring OSPF Lab 

## 1. Overview & Objectives
This lab covers the configuration and verification of **OSPFv2 (Open Shortest Path First)** routing within a multi-router topology.
The primary goals include establishing loopback interfaces, enabling single-area OSPF routing, configuring passive interfaces, and injecting a default route from an Autonomous System Boundary Router (ASBR).

### Lab Tasks Completed:
1. Configured device hostnames, interface IP addresses, and enabled all physical router interfaces (excluding ISPR1).
2. Configured loopback interfaces on each router (`1.1.1.1/32` for R1, `2.2.2.2/32` for R2, `3.3.3.3/32` for R3, and `4.4.4.4/32` for R4).
3. Configured OSPF in Area 0 across all internal router interfaces and loopbacks while ensuring proper passive interface implementation.
4. Configured **R1 as an ASBR** to advertise a default route (`default-information originate`) into the OSPF domain.
5. Verified OSPF routing tables and default route propagation on R2, R3, and R4.

## 2. Network Topology & Device Layout

The lab network consists of an external gateway router (`ISPR1`),
four core routers (`R1`, `R2`, `R3`, `R4`), an access switch (`SW1`), and an end host (`PC1`).

* **ISPR1 & R1 Connection:** `ISPR1` connects to `R1` via the public/external `203.0.113.0/30` subnet, serving as the gateway to the outside internet.
 OSPF is intentionally **not** enabled on this link.
* **Router 1 (R1):** Acts as the central router and Autonomous System Boundary Router (ASBR).
It connects to `R2` (`10.0.12.0/30`) and `R3` (`10.0.13.0/30`).
 It injects a default route into the OSPF domain[cite: 6].
* **Router 2 (R2):** Interconnects with `R1` and links downward to `R4` via the `10.0.24.0/30` subnet.
* **Router 3 (R3):** Interconnects with `R1` and links downward to `R4` via the `10.0.34.0/30` subnet.
* **Router 4 (R4):** Serves as the aggregation router for the local area network, connecting to switch `SW1` and client `PC1` on the `192.168.4.0/24` subnet.
