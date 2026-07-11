Lab 02: Cabling Interfaces and Link Autonegotiation

### Technical Objective
To manually manipulate Layer 1 physical line speeds and Layer 2 duplex parameters on access infrastructure, overriding default autonegotiation rules.

### Operational Observations
1. **Interface Speed Downgrading:** Verified that linking a 1000 Mbps interface to a 100 Mbps endpoint triggers standard autonegotiation constraints, forcing the link down to the lowest common capability to prevent media timing dropped frames.
2. **Manual Hardening Metrics:** Executed `speed 100` and `duplex full` rules inside the IOS command shell to guarantee fixed communication lanes, minimizing administrative errors associated with standard mismatch issues .

### Directory Artifacts(cabling validation topology)
* `labs/02_cabling_interfaces/cabling_interfaces.pkt`
