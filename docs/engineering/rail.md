---
title: "Rail Operations Documentation"
document_id: "RAIL-OPS-005"
description: "Network control procedures, track maintenance protocols, and signaling system documentation for enterprise rail transit."
author: "Rail Operations & Control Team"
date_created: 2026-06-06
date_updated: 2026-06-06
date_next_review: 2027-06-06
document_tier: 1
domain: "rail-transit"
asset_class: "rail-signaling-system"
tags: [rail, scada, etcs, signaling, safety]
review_status: "Approved"
---

# Rail Operations Documentation

## 1. Network Overview

The Rail Operations Documentation module governs the safe, efficient, and compliant operation of the enterprise passenger and freight rail network.

Rail infrastructure is a highly integrated cyber-physical system. Physical assets (tracks, rolling stock, points) are entirely dependent on digital control systems (SCADA, European Train Control System - ETCS). This documentation provides the Single Source of Truth (SSoT) for the Network Control Centre (NCC), Train Drivers, and Track Maintenance Technicians.

---

### Critical Safety Protocols

The foundation of rail safety is the strict separation of trains and track workers. All procedures in this section are legally binding under the National Rail Safety Act.

#### Track Occupancy Authority (TOA)

No maintenance technician may enter the rail corridor without a formally issued TOA from the Network Control Centre.

1. **Request:** Technician submits a digital TOA request via the Enterprise Field App, specifying the exact track kilometer pegs (e.g., KM 14.5 to 16.2).
2. **Isolation:** The Train Controller digitally locks the specified sector in the SCADA system, forcing all approaching signals to **DANGER (RED)**.
3. **Issuance:** A unique, time-bound alphanumeric TOA code is transmitted to the technician.
4. **Surrender:** Upon completion of work, the technician must physically clear the track and surrender the TOA code via the app before the Train Controller can unlock the sector.

---

### Standard Operating Procedure: Signal Failure Response

**Context:** This sequence must be followed immediately upon the detection of an interlocking or signal failure on the mainline network.

**Procedure Sequence:**

```mermaid
sequenceDiagram
    autonumber
    participant TC as Train Controller (NCC)
    participant SYS as SCADA / ETCS System
    participant DR as Train Driver
    participant MT as Maintenance Tech

    SYS-->>TC: Alert: Interlocking Failure (Sector 4)
    TC->>SYS: Force Signal to Danger (RED)
    SYS-->>DR: In-Cab Alert: Stop Proceeding
    DR->>TC: Radio: Acknowledge Stop. Awaiting Instructions.
    TC->>MT: Dispatch to Sector 4 Relay Room
    MT->>TC: Request Track Occupancy Authority (TOA)
    TC->>MT: TOA Granted. Proceed with manual diagnostic.
    Note over MT,SYS: Tech performs physical reset of track circuits.
    MT->>TC: Fault Cleared. TOA Surrendered.
    TC->>SYS: Clear Signals. Resume Normal Operations.
    TC->>DR: Radio: Proceed at Line Speed.
```
