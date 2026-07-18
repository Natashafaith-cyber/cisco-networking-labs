# LAB 06 Trunking, VTP Domains, and DTP Mitigation

## Technical Objective
configure trunk links, implement VLAN Trunking Protocol (VTP) across multiple operational modes
(Server, Client, and Transparent), enforce manual access port assignments, and mitigate security 
risks associated with Dynamic Trunking Protocol (DTP).

## Topology DiagramThe
network consists of three interconnected Cisco switches (SW1, SW2, SW3) servicing four distinct VLANs across a segmented /26 address space.
VLAN 10-10.0.0.0/26Green Zone (PC1, PC2, PC5)

VLAN 20-10.0.0.64/26Yellow Zone (PC6, PC9)

VLAN 30-10.0.0.128/26Red Zone (PC3, PC7)

VLAN 40-10.0.0.192/26Purple Zone (PC4, PC4 )

 ## Technical Tasks
### Task 1: Switchport Trunking & DTP Mitigation
Objective: Configure inter-switch links as static trunk ports and disable Dynamic Trunking Protocol (DTP) to prevent unauthorized trunk negotiation.

        #### configurations sample
        
SW1# configure terminal

SW1(config)# interface GigabitEthernet 0/1

SW1(config-if)# switchport mode trunk

SW1(config-if)# switchport nonegotiate

SW1# show interfaces GigabitEthernet 0/1 switchport

### Task 2: VTP Server and VLAN Propagation

Objective: Establish SW1 as the VTP Server within the domain Natalie and create production VLANs.

       #### configuration sample
       
SW1(config)# vtp domain Natalie

SW1(config)# vtp mode server

SW1(config)# vlan 10

SW1(config)# vlan 20

SW1(config)# vlan 30

### Task 3: VTP Transparent Mode Configuration
Objective: Configure SW2 in VTP Transparent mode to isolate its local VLAN database while permitting the forwarding of VTP advertisements to other switches.

SW2(config)# vtp mode transparent

SW2(config)# vlan 40

### Task 4: VTP Client Mode & Database Restrictions
Objective: Configure SW3 as a VTP Client to test local modification restrictions.prove VTP VLAN configuration not allowed when device is in CLIENT mode.

SW3(config)# vtp domain Natalie

SW3(config)# vtp mode client

SW3(config)# vlan 50

    ####Analysis: 
    
   1. SW3 will automatically inherit VLANs 10, 20, and 30 from the server. SW2 will not add them to its database but will pass the VTP advertisements along.
     
   2. VLAN 40 remains local to SW2. It is not added to the VLAN databases of SW1 or SW3, proving that transparent switches do not synchronize their databases with       the VTP domain.

   3. The switch correctly blocks local configuration, enforcing centralized VLAN management via the VTP Server.
