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

## IP Addressing Note

The IP ranges in this conceptual model are example ranges. The Enterprise IT and OT areas are shown as separate private addressing domains to reflect a common real-world situation where business networks and production networks may be planned, routed, and managed separately.

A real implementation would require a unified plant-specific IP addressing plan, routing design, firewall validation, and operational approval.

## Redundancy and Availability

This conceptual architecture shows a simplified single-path communication model. It does not include redundancy, high availability, failover concepts, redundant firewalls, redundant switches, or disaster-recovery planning.

A real production implementation would require plant-specific redundancy and availability design.
