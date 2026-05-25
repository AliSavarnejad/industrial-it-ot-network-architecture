# Industrial IT/OT Network Architecture

A conceptual reference design for segmented factory connectivity, controlled production data exchange, and secure remote access in PLC-based production environments.

## Architecture Overview

```mermaid
flowchart TB
    A["Enterprise IT Zone<br/>VLAN 100<br/>Office PCs / ERP-SAP / Business systems"]
    B["Industrial DMZ<br/>VLAN 50<br/>Jump server / Data broker / Remote access gateway"]
    C["OT Production Zone<br/>VLAN 20<br/>SCADA / Historian / Engineering station"]
    D["Machine Cell Zone<br/>VLAN 10<br/>PLC / HMI / Drives / Robot controller / I/O"]
    E["Field Level<br/>Physical process<br/>Sensors / Actuators / Motors / Valves"]

    R["Secure Remote Access<br/>Vendor laptop → VPN + MFA → DMZ jump server"]
    F["Blocked Direct Paths<br/>Internet → PLC<br/>Office PC → PLC<br/>Vendor laptop → PLC direct"]

    A -->|"controlled IT/OT exchange"| B
    B -->|"approved OT exchange"| C
    C -->|"tags / alarms / diagnostics"| D
    D -->|"machine/process connection"| E

    R -->|"limited and logged access"| B
    F -. "blocked" .-> D

    classDef it fill:#ecfdf5,stroke:#059669,stroke-width:2px,color:#0f172a;
    classDef dmz fill:#fffbeb,stroke:#d97706,stroke-width:2px,color:#0f172a;
    classDef ot fill:#f5f3ff,stroke:#7c3aed,stroke-width:2px,color:#0f172a;
    classDef cell fill:#ecfeff,stroke:#0891b2,stroke-width:2px,color:#0f172a;
    classDef field fill:#f1f5f9,stroke:#64748b,stroke-width:2px,color:#0f172a;
    classDef remote fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#0f172a;
    classDef blocked fill:#fef2f2,stroke:#dc2626,stroke-width:2px,color:#991b1b;

    class A it;
    class B dmz;
    class C ot;
    class D cell;
    class E field;
    class R remote;
    class F blocked;

```

## Purpose

This project documents a simplified industrial IT/OT network architecture for a PLC-based production environment. It focuses on network segmentation, controlled communication between zones, production data flow, and secure remote access.

The design is vendor-neutral and conceptual. It can be used as a public portfolio reference for automation engineering, industrial networking, IT/OT connectivity, and production-data-related roles.

## Architecture Zones

| Zone | Example VLAN / Subnet | Typical Systems | Purpose |
|---|---:|---|---|
| Enterprise IT Zone | VLAN 100 / 10.10.1.0/24 | Office PCs, ERP/SAP, business servers, databases | Business systems, planning, and reporting |
| Industrial DMZ | VLAN 50 / 10.10.50.0/24 | Jump server, data broker, remote access gateway | Controlled buffer between IT and OT |
| OT Production Zone | VLAN 20 / 192.168.20.0/24 | SCADA, historian, engineering station | Production monitoring, engineering, and data collection |
| Machine Cell Zone | VLAN 10 / 192.168.10.0/24 | PLC, HMI, drives, robot controller, I/O devices | Direct machine control |
| Field Level | Device-specific / fieldbus | Sensors, actuators, motors, valves | Physical production process |

## Core Design Principle

Allow only required communication, document each conduit, and block direct uncontrolled access to PLCs and machine networks.

## Main Production Data Flow

```text
Field Level
Sensors / Actuators
        ↓
PLC
        ↓
HMI / SCADA
        ↓
Historian / Database
        ↓
MES
        ↓
ERP / SAP
```

## Secure Remote Access Concept

Remote access should not go directly to PLCs or machine networks.

Recommended structure:

```text
Vendor laptop
        ↓
VPN with multi-factor authentication
        ↓
Firewall
        ↓
DMZ jump server
        ↓
Firewall
        ↓
Required OT system
```

Remote access should be authenticated, limited, logged, monitored, and restricted to required systems.

## Documentation

- [Architecture Report](docs/architecture_report.md)
- [Data Flow and Remote Access](docs/data_flow_and_remote_access.md)
- [Assumptions and Limitations](docs/assumptions_and_limitations.md)
- [Device / IP / VLAN Plan](tables/device_ip_vlan_plan.md)
- [Communication Matrix](tables/communication_matrix.md)
- [Firewall Rule Examples](tables/firewall_rule_examples.md)

## Scope

This is a conceptual reference architecture, not a complete production implementation. Real projects require plant-specific network design, security review, firewall rule validation, redundancy planning, change management, and operational approval.
