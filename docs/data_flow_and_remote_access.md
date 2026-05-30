# Data Flow and Remote Access

## Main Production Data Flow

The main data flow moves from the physical process toward higher-level production and business systems:

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

## Meaning of Each Step

| Step | Meaning |
|---|---|
| Field Level → PLC | Sensors provide input signals; the PLC controls actuators, motors, valves, and machine actions |
| PLC → HMI | The HMI displays machine status, alarms, setpoints, and operator controls |
| PLC → SCADA | SCADA collects tags, alarms, trends, diagnostics, and production data |
| SCADA → Historian | Process and production data are stored over time |
| Historian / Data Broker → MES | Selected production data supports orders, quality, downtime, and traceability |
| MES → ERP/SAP | Higher-level production information supports business planning and reporting |

## Remote Access Path

Direct remote access to PLCs should be avoided.

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

## Remote Access Requirements

Remote access should be:

- Authenticated
- Limited to required systems
- Logged
- Monitored
- Time-limited where possible
- Controlled by firewall rules
- Routed through a jump server
- Blocked from direct PLC access unless explicitly approved and justified

## Data Broker Role

The data broker in the Industrial DMZ is a controlled extraction point between OT and higher-level systems. It should not act as a transparent pass-through to PLCs or machine-cell networks.

Its role is to receive selected production data from approved OT systems, filter or structure the data where required, and make only approved information available to higher-level systems such as MES, reporting tools, or dashboards.
