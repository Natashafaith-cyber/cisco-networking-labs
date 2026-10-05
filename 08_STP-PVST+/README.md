# Spanning Tree Protocol (STP) Load Balancing & Tuning Lab

## Overview

This Cisco Packet Tracer lab demonstrates the implementation, manipulation, and securing of Spanning Tree Protocol (STP / PVST+) across a multi-switch enterprise LAN network.

## Objectives

1. Per-VLAN Load Balancing: Configure active-active path utilization using primary and secondary Root Bridge designations for VLAN 1 and VLAN 2.

2. STP Path Cost Manipulation: Alter path selection for specific VLANs by tuning interface cost values.

3. STP Port Priority Tuning: Verify the criteria for Root Port selection when modifying neighbor port priority values.

4. Access Port Hardening: Secure and optimize end-host access ports using STP PortFast and BPDU Guard.

## Network Topology & Summary

* **Switches**: SW1, SW2, SW3, SW4

* **Configured VLANs**: VLAN 1, VLAN 2

* **Access Ports**:

      SW3 FastEthernet0/3 (Host Connection)

      SW4 FastEthernet0/3 (Host Connection)

# Lab Execution & Technical Analysis

### Task 1: Per-VLAN STP Load Balancing

* **Implementation**:

SW1 configured as Primary Root for VLAN 1 and Secondary Root for VLAN 2.

SW2 configured as Primary Root for VLAN 2 and Secondary Root for VLAN 1.

* **Result**: Achieved deterministic traffic distribution where VLAN 1 traffic prefers paths toward SW1 and VLAN 2 traffic prefers paths toward SW2.

### Task 2: Path Cost Tuning

* **Implementation**: Increased the STP path cost on SW4 interface FastEthernet0/2 to 102 for VLAN 1.

* **Result**: SW4 recalculated its shortest path to the Root Bridge for VLAN 1 and selected a different interface as its Root Port, placing FastEthernet0/2 into an Alternate/Blocking state.

### Task 3: Port Priority Analysis

* **Implementation**: Raised the port priority on SW1 interface FastEthernet0/1 to 240 (lowest preference).

* **Result**: As expected, this did not alter SW3's Root Port selection.

* **Key Takeaway**: Port Priority serves only as a tie-breaker between parallel links connecting directly to the same upstream switch with identical path costs.

### Task 4: PortFast & BPDU Guard Configuration

* **Implementation**: Enabled spanning-tree portfast and spanning-tree bpduguard enable on access interfaces FastEthernet0/3 on both SW3 and SW4.

* **Result**: Access ports bypassed standard Listening and Learning delays (30 seconds total) to reach Forwarding instantly. BPDU Guard protects against unexpected switches being added to user-facing ports by putting the port in err-disabled state upon receiving a BPDU.

