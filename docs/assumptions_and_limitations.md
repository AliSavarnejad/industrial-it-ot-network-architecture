# Assumptions and Limitations

## Assumptions

- One representative production line or machine cell
- Segmented IT/OT environment
- Example VLAN and subnet assignments
- SCADA and historian systems located in the OT production zone
- DMZ used as a controlled buffer between enterprise IT and OT
- Remote access controlled by VPN, MFA, firewall rules, and a jump server
- PLCs and machine-cell devices not directly reachable from the internet or normal office PCs

## Limitations

This architecture is simplified and does not include:

- Detailed routing configuration
- Switch configuration
- NAT rules
- Full firewall port and protocol definitions
- Redundancy and high availability design
- Detailed identity and access management
- Full industrial cybersecurity architecture
- Complete IEC 62443 zone and conduit analysis
- Safety system architecture
- Multi-site architecture
- Vendor-specific implementation details

It is not a deployable plant design without further engineering validation.
