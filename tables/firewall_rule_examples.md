# Firewall Rule Examples

These rules are examples for documentation and conceptual design. Exact rules must be validated for the real plant architecture.

| Rule No. | Source Zone | Source Device | Destination Zone | Destination Device | Service / Protocol | Action | Reason |
|---:|---|---|---|---|---|---|---|
| 1 | Machine Cell VLAN 10 | HMI-LINE1-01 | Machine Cell VLAN 10 | PLC-LINE1-01 | HMI/PLC communication | Allow | Operator interface requires PLC data |
| 2 | OT VLAN 20 | OT-SCADA-01 | Machine Cell VLAN 10 | PLC-LINE1-01 | PLC tag communication | Allow controlled | SCADA requires selected machine data |
| 3 | OT VLAN 20 | OT-ENG-01 | Machine Cell VLAN 10 | PLC-LINE1-01 | Engineering / diagnostics | Allow controlled | Programming and troubleshooting |
| 4 | OT VLAN 20 | OT-SCADA-01 | OT VLAN 20 | OT-HIST-01 | Historian connection | Allow | Store process data |
| 5 | OT VLAN 20 | OT-HIST-01 | DMZ VLAN 50 | DMZ-DATA-01 | Selected data exchange | Allow controlled | Transfer selected production data |
| 6 | IT VLAN 100 | ERP-SRV-01 | DMZ VLAN 50 | DMZ-DATA-01 | Business data exchange | Allow controlled | ERP receives selected production data |
| 7 | IT VLAN 100 | IT-PC-01 | Machine Cell VLAN 10 | PLC-LINE1-01 | Any | Block | Office PCs should not directly access PLCs |
| 8 | Internet | External device | Machine Cell VLAN 10 | PLC-LINE1-01 | Any | Block | PLC must not be reachable from internet |
| 9 | External | Vendor Laptop | DMZ VLAN 50 | DMZ-JUMP-01 | VPN / remote access | Allow controlled | Remote maintenance through jump server |
| 10 | Unknown | Unknown Device | OT VLAN 20 | Any OT device | Any | Block | Block untrusted communication by default |
