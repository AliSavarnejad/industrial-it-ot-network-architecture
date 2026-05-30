# Architecture Report

## Overview

This document describes a simplified industrial IT/OT network architecture for a PLC-based production environment.

This architecture reflects communication patterns commonly found in PLC-based production environments, structured into a documented IT/OT reference model.

The architecture separates enterprise IT systems, the industrial DMZ, OT production systems, machine-cell systems, and field-level devices into distinct zones. Communication between zones is allowed only through documented and controlled paths.

## Zone Model

| Zone | Role |
|---|---|
| Enterprise IT Zone | Business systems, office systems, ERP/SAP, reporting, and planning |
| Industrial DMZ | Controlled buffer for data exchange and remote access between IT and OT |
| OT Production Zone | SCADA, historian, engineering station, diagnostics, and monitoring |
| Machine Cell Zone | PLC, HMI, drives, robot controller, industrial I/O, and local machine control |
| Field Level | Sensors, actuators, motors, valves, and the physical process |

## Segmentation Concept

Segmentation reduces unnecessary communication and limits exposure between business systems and production systems.

The design uses logical zones and example VLANs:

| Zone | Example VLAN | Example Subnet |
|---|---:|---|
| Enterprise IT Zone | 100 | 10.10.1.0/24 |
| Industrial DMZ | 50 | 10.10.50.0/24 |
| OT Production Zone | 20 | 192.168.20.0/24 |
| Machine Cell Zone | 10 | 192.168.10.0/24 |

## Communication Principle

The architecture follows a default-deny mindset:

```text
Allow required communication.
Document each conduit.
Block direct uncontrolled access.
```

Examples of controlled communication:

- SCADA reads required PLC tags, alarms, and diagnostic data.
- Historian stores process and production data.
- Data broker transfers selected production data toward business systems.
- Remote access passes through VPN, MFA, firewall rules, and a DMZ jump server.

Examples of blocked communication:

- Internet to PLC
- Office PC to PLC
- Vendor laptop directly to PLC
- Unknown device to OT network

## Main Architecture Value

The model supports a practical understanding of industrial connectivity:

- Where PLCs, HMIs, SCADA, historians, MES, and ERP/SAP systems are placed
- How production data moves upward from machines to higher-level systems
- Why IT and OT are separated by controlled boundaries
- How remote access can be structured without exposing PLCs directly
