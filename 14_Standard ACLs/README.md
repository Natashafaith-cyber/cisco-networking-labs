# Standard ACLs Configuration Lab

## 1. Overview & Objectives
This lab covers **OSPF** reachability across multiple subnets and traffic filtering using **Standard Numbered ACLs** (on `R1`) 
and **Standard Named ACLs** (on `R2`). Because standard ACLs match only on **source IPv4 address**,
rules are applied outbound as close to the destination networks as possible to avoid unintended blocking.
