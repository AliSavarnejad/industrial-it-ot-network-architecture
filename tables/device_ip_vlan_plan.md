# Device / IP / VLAN Plan

| Area | Device | Example Name | Example IP | Subnet | VLAN | Purpose |
|---|---|---|---|---|---:|---|
| Enterprise IT | Office PC | IT-PC-01 | 10.10.1.50 | 10.10.1.0/24 | 100 | Office work and business access |
| Enterprise IT | ERP/SAP Server | ERP-SRV-01 | 10.10.1.20 | 10.10.1.0/24 | 100 | Production planning and business data |
| Enterprise IT | Business Database | IT-DB-01 | 10.10.1.30 | 10.10.1.0/24 | 100 | Reporting and business data |
| Industrial DMZ | Jump Server | DMZ-JUMP-01 | 10.10.50.10 | 10.10.50.0/24 | 50 | Controlled remote access |
| Industrial DMZ | Data Broker | DMZ-DATA-01 | 10.10.50.20 | 10.10.50.0/24 | 50 | Controlled IT/OT data exchange |
| Industrial DMZ | Remote Access Gateway | DMZ-RA-01 | 10.10.50.30 | 10.10.50.0/24 | 50 | Remote service entry point |
| OT Production | SCADA Server | OT-SCADA-01 | 192.168.20.10 | 192.168.20.0/24 | 20 | Monitoring, alarms, and trends |
| OT Production | Historian | OT-HIST-01 | 192.168.20.20 | 192.168.20.0/24 | 20 | Process and production data storage |
| OT Production | Engineering Station | OT-ENG-01 | 192.168.20.30 | 192.168.20.0/24 | 20 | Programming, diagnostics, and commissioning |
| Machine Cell | PLC | PLC-LINE1-01 | 192.168.10.10 | 192.168.10.0/24 | 10 | Machine control |
| Machine Cell | HMI Panel | HMI-LINE1-01 | 192.168.10.20 | 192.168.10.0/24 | 10 | Operator interface |
| Machine Cell | Drive | DRV-LINE1-01 | 192.168.10.40 | 192.168.10.0/24 | 10 | Motor control |
| Machine Cell | Robot Controller | ROB-LINE1-01 | 192.168.10.50 | 192.168.10.0/24 | 10 | Robot operation |
| Machine Cell | I/O Device | IO-LINE1-01 | 192.168.10.60 | 192.168.10.0/24 | 10 | Sensor and actuator connection |
| Field Level | Sensors / Actuators | FIELD-LINE1 | Device-specific | Connected through I/O / fieldbus | 10 | Physical machine signals and actions |
