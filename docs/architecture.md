# Architecture

## Objective

The objective of this architecture is to demonstrate a small but realistic SOC pipeline:

**Endpoint / Network Activity → Sensors → SIEM → Investigation → Automation**

## Infrastructure

The lab was hosted on Oracle Cloud Infrastructure using multiple hosts connected through a private `10.0.0.0/24` lab network.

### Core systems

### siem01

Central Wazuh system containing:

- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard

Responsibilities:

- Receive agent telemetry
- Analyze security events
- Index events
- Provide centralized investigation and visualization

### sensor01 / sensor01-zeek01

Linux security sensor responsible for network visibility.

Components:

- Wazuh Agent
- Suricata
- Zeek

Responsibilities:

- Capture and inspect network activity
- Generate IDS events
- Generate network metadata
- Forward relevant telemetry to the central SIEM

### windows01

Windows endpoint used to generate endpoint activity and validate telemetry collection.

### automation01

Automation host running Shuffle workflows.

## Logical Data Flow

```text
Windows Endpoint
      |
      | endpoint telemetry
      v
    Wazuh Agent
      |
      v
  Wazuh Manager
      |
      v
Indexer / Dashboard
      ^
      |
Linux Sensor
  |         |
  |         +---- Zeek ----> conn.log / network metadata
  |
  +---- Suricata ----> eve.json / IDS alerts

Wazuh / security events
          |
          v
       Shuffle
          |
          v
   Automated workflows
```

## Design Principles

1. Separate centralized SIEM responsibilities from network sensing.
2. Keep monitored endpoints and security sensors logically distinct.
3. Collect both endpoint and network telemetry.
4. Preserve raw evidence where practical.
5. Automate repetitive response steps.
6. Keep secrets outside the repository.
7. Document the lab so another learner can reproduce the architecture.

## Limitations

This architecture is intentionally small. A production SOC would normally require additional redundancy, centralized identity and access management, secure secrets management, time synchronization, retention policies, high availability, asset inventory, vulnerability management and mature incident-response processes.
