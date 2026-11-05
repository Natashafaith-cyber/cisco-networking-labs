# Advanced OSPF Troubleshooting & Area Design Lab 

## 1. Overview & Objectives
This lab focuses on diagnosing and troubleshooting complex OSPF routing issues, 
serial link configurations, missing routes, neighbor adjacency roadblocks, and examining Link-State Databases (LSDB).

### Lab Tasks & Troubleshooting Steps Completed:
1. **Serial Link & OSPF Expansion:** Configured the newly added serial connection between `R1` and `R2`,
setting a clock rate of `128000` on the DCE interface, and enabled OSPF across `R1` and `R2`.
4. **Routing Table Diagnostics (R3 Issue):** Investigated why only `R3` possessed a route to the `10.0.2.0/24` network and resolved the routing visibility problem.
5. **Neighbor Adjacency Troubleshooting:** Fixed the adjacency issue preventing `R2` and `R4` from forming an OSPF neighbor relationship with `R5`.
6. **External Connectivity & NAT/Routing Resolution:** Fixed the issue preventing client hosts (`PC1` and `PC2`) from successfully pinging the external server (`8.8.8.8`).
7. **LSDB Inspection:** Examined the Link-State Database (`show ip ospf database`) to verify active Type-1 (Router), Type-2 (Network), and Type-5 (External) LSAs.
