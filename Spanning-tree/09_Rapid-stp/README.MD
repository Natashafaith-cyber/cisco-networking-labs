# Rapid Spanning Tree Protocol (RSTP / 802.1w) Lab
## Overview & Objectives
This lab explores the implementation and rapid convergence behavior of Rapid Spanning Tree Protocol (RSTP / IEEE 802.1w) using Cisco Packet Tracer. The primary goals of this exercise are:

1. Accelerated Convergence: Replacing standard 802.1D timers with RSTP's explicit Proposal/Agreement handshake mechanism for sub-second failovers.

2. Bridge & Port Role Analysis: Identifying and verifying Root Bridges, Designated Ports (Desg), Root Ports (Root), and Alternate Ports (Alt).

3. Link Type Optimization: Configuring point-to-point link types and enabling PortFast on access interfaces connected to end devices to bypass unnecessary listening/learning delays.

## Network Topology & Device Roles
Switches: SW1 (Root Bridge), SW2, SW3, SW4

Protocol Mode: Rapid PVST+ (spanning-tree mode rapid-pvst)

# VLAN Configured: VLAN 1

 ## Configuration Summary
### Enabling Rapid PVST+ Globally
* **Plaintext**

enable

configure terminal

 spanning-tree mode rapid-pvst

end

### Configuring Edge Ports & Link Types
To ensure user-facing access ports transition instantly to the forwarding state and optimize convergence parameters:

* **Plaintext**

enable

configure terminal

 interface FastEthernet0/24

  switchport mode access

  spanning-tree portfast

  spanning-tree link-type point-to-point

 end

## Verification & Findings
Root Bridge Status (show spanning-tree)

* **Root Bridge**: SW1 was elected as the root bridge for VLAN 1, verified via bridge parameters and root status indicators.

* **Port States**: All active ports on the root bridge operate in the Designated role and Forwarding state (Desg FWD).

##  Key Differences: STP (802.1D) vs. RSTP (802.1w)

* **Port States**: RSTP consolidates traditional states into Discarding, Learning, and Forwarding.

* **Port Roles**: Introduces Alternate and Backup roles to eliminate the max-age timer dependency during link failures.

* **Convergence Time**: Reduces topology convergence from 30–50 seconds down to milliseconds.
