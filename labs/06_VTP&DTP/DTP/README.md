LAB 06 Trunking, VTP Domains, and DTP Mitigation

### Technical Objective
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
# Task 1: Switchport Trunking & DTP Mitigation
Objective: Configure inter-switch links as static trunk ports and disable Dynamic Trunking Protocol (DTP) to prevent unauthorized trunk negotiation.
        ##configurations sample
SW1# configure terminal
SW1(config)# interface GigabitEthernet 0/1
SW1(config-if)# switchport mode trunk
SW1(config-if)# switchport nonegotiate
SW1# show interfaces GigabitEthernet 0/1 switchport

# Task 2: VTP Server and VLAN Propagation
Objective: Establish SW1 as the VTP Server within the domain Natalie and create production VLANs.
       ##configuration sample
SW1(config)# vtp domain Natalie
SW1(config)# vtp mode server
SW1(config)# vlan 10
SW1(config)# vlan 20
SW1(config)# vlan 30
    
