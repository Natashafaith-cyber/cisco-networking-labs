### Lab 03:VLANS CONFIGURATIONS

# vlan configurations lab01

**Technical Objective**
Configured correct ip addresses in correct vlans and configured the interfaces for each vlan

**Tasks done**

1. configured the correct ip addresses and subnet masks on each pc and set the gateway address as the last usable address of the subnet.

2. made three connections between R1 and SW1
 configured one interface on R1 for each VLAN
 made sure the ip addresses are the gateway address i configured on the PCs

3. configured SW1s inerface in the proper VLANs
 named the vlans Engineering,HR,Sales

4. pinged between the PCs to check connections
sent a broadcast ping from a pc to ping the subnet to see which pcPCs devices received the broadcast

   # vlan configurations lab02

**Technical Objective**

 VLAN segmentation, 802.1Q trunking configuration, and Inter-VLAN routing using a Router-on-a-Stick (ROAS) topology.

**Tasks done**

1. configuring  the switch interfaces connected to  PCs as access ports in the correct Vlan

2. configuring the connections between SW1 and SW2  as trunk allowing only the necessary vlans
-configure an unused vlan as the native vlan
-ensured all necessarry vlans exist on each switch

3. configured the connections between SW2 and R1 using router on a stick 
assighned the last usable addresses of each subnet to R1s subinterfaces

4. Test connectivity by pinging between PCs-all PCs should be able to reach eachother

# LAB;03 Inter-VLAN Routing Migration Lab (ROAS to Layer 3 Switch)

**Objectives**

This lab demonstrates migrating an existing network from a **Router-on-a-Stick (ROAS)** configuration to an **SVI (Switched Virtual Interface)** setup on a core Multilayer Switch (SW2). 

**Tasks done**

1. Replace ROAS with a Point-to-Point Layer 3 Connection
* Remove subinterfaces on 'R1' (G0/0) and configure it as a standard Routed Port with IP `10.0.0.194/30`.
* Convert 'SW2' 's interface `G1/0/2` into a routed port (`no switchport`) and assign IP `10.0.0.193/30`.
* Configure a default route on `SW2` pointing to `R1` (`10.0.0.194`).

2. Configure SVIs on SW2
* Enable IP routing globally on `SW2`.
* Create Switched Virtual Interfaces (SVIs) for VLAN 10, 20, and 30.
* Assign the **last usable IP address** of each respective subnet to the SVI:
  * **VLAN 10 SVI:** `10.0.0.62`
  * **VLAN 20 SVI:** `10.0.0.126`
  * **VLAN 30 SVI:** `10.0.0.190`

 3. Verify Inter-VLAN Connectivity
* Ensure hosts across different VLANs can ping each other using the new SVI gateways.

4. Verify Internet Connectivity
* Test public internet reachability by pinging `1.1.1.1` from internal hosts.

