# Engineering Portfolio: Infrastructure and Architecture Hardening

## Master Lab Directory
* **`labs/01_device_basics`** ◄ *Current Milestone*
* **`labs/02_cabling_interfaces`**
* **`labs/03_cli_security`**

Lab 01: Core Network Device Analysis

### Technical Objective
To evaluate the protocol behaviors, collision boundaries, and forwarding mechanics of Layer 1 and Layer 2 network architecture components within a simulated topology.

### Architectural Insights & Observations
1. **Layer 1 Hub Behavior:** Observed multi-port bit replication. The hub operates entirely on physical layer parameters, flooding data across all connected interfaces, creating a single shared collision domain.
2. **Layer 2 Switch Behavior:** Observed targeted unicast forwarding. The switch parses the Destination MAC Address, builds a hardware CAM table map, and isolates individual collision domains per port.

### Directory Artifacts
* `labs/01_device_basics/device_basics_comparison.pkt`
