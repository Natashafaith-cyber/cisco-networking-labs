# Extended ACLs Configuration Lab

## 1. Overview & Objectives
This lab covers granular traffic filtering using **Extended ACLs** (numbered `100–199` / `2000–2699` or named `ip access-list extended`),
which match on **protocol** (IP, TCP, UDP, ICMP), **source IP**, **destination IP**, and **source/destination ports**.
Placing extended ACLs close to the **source** avoids sending unwanted traffic across the network.

