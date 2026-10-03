# Lab 03: Cisco IOS CLI Configuration & Device Security Baseline

## Technical Objective
To implement an administrative hardening policy on a network edge gateway device, configuring secure system operational execution tiers and activating Layer 3 interfaces.

## Hardening Parameters Applied
1. **Host Context Mapping:** Scaled default system profile namespace to `Core-Gateway-01`.
2. **Cryptographic Authentication:** Instituted an MD5-hashed secret layer to isolate Privileged EXEC system parameters.
3. **Console Port Obscurity:** Applied local authentication rules on `line con 0` to safeguard physical configuration boundaries.
4. **Data Protection:** Enabled global password scrambling via Cisco `service password-encryption` engine to eliminate clear-text exposures.
5. **Interface Activation:** Provisioned IPv4 gateway logic on `GigabitEthernet0/0` and manually forced the interface up using the `no shutdown` protocol directive.
