# Spanning Tree Protocol (STP) - Root Bridge & Port Role Determination Lab

## Executive Summary
This hands-on laboratory demonstrates the fundamental operation of the **IEEE 802.1D Spanning Tree Protocol (STP)** in a redundant switch topology using Cisco Packet Tracer. The lab focuses on how STP prevents Layer 2 switching loops by dynamically electing a **Root Bridge**, calculating **Root Path Costs**, and assigning specific **Port Roles** (Root Port, Designated Port, Non-Designated/Blocking Port).

## Topology & Equipment
* **Simulator:** Cisco Packet Tracer
* **Devices:** 4 x Cisco Catalyst Switches (e.g., 2960 Series)
* **Interconnections:** Redundant GigabitEthernet / FastEthernet trunk links forming a loop

## Lab Objectives & Key Concepts Tested
1. **Bridge ID (BID) Structure:** Analyzed how STP uses `Priority + System ID Extension (VLAN) + MAC Address` to evaluate switch superiority.
2. **Root Bridge Election:** Verified that the switch with the lowest overall BID is selected as the central Root Bridge.
3. **Root Cost Calculation:** Calculated path costs to the Root Bridge based on standard IEEE link speeds (e.g., Gigabit Ethernet = 4, Fast Ethernet = 19).
4. **Port Role Assignment:** Identified and verified:
   - **Root Ports (R):** The single port on each non-root switch with the lowest total path cost to the Root Bridge.
   - **Designated Ports (D):** The port on a network segment that advertises the lowest cost path toward the Root. (All operational ports on the Root Bridge are DPs).
   - **Non-Designated / Alternate Ports (N):** Ports placed into a blocking state to break the Layer 2 loop.
5. **CLI State Inspection:** Utilized Cisco IOS verification commands to confirm operational states.

# Display general STP status, Root ID, Local BID, and Port Roles for VLAN 1
Switch# show spanning-tree vlan 1

# Display detailed BPDU exchange counters and timers
Switch# show spanning-tree detail

# View brief summaries of interface states and designated bridge IDs
Switch# show spanning-tree summary

Conclusion
This lab successfully demonstrates how STP maintains a loop-free Layer 2 topology while preserving link redundancy. By understanding BID prioritization and root path cost metrics, engineers can deterministically control traffic paths and Root Bridge placement across enterprise campus networks.