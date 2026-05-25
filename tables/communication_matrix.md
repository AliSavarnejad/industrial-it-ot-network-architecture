# Communication Matrix

| Source | Destination | Allowed? | Purpose | Security Note |
|---|---|---|---|---|
| HMI Panel | PLC | Yes | Operator control and machine status | Local machine communication |
| Engineering Station | PLC | Yes, controlled | Programming, diagnostics, commissioning | Authorized engineering access only |
| SCADA Server | PLC | Yes, controlled | Read tags, alarms, machine data | Restrict to required services |
| SCADA Server | Historian | Yes | Store process and production data | OT production zone communication |
| Historian / Data Broker | MES / ERP | Yes, controlled | Production reporting and analysis | Use controlled exchange through DMZ |
| Vendor Laptop | VPN Gateway | Yes, controlled | Remote maintenance entry | VPN and MFA required |
| VPN / Jump Server | Required OT System | Yes, limited | Diagnostics or support | Logged and restricted access |
| Office PC | PLC | No | Not required | Block direct office-to-PLC access |
| Internet | PLC | No | Unsafe direct access | Block by default |
| Unknown Device | OT Network | No | Untrusted access | Block by default |
