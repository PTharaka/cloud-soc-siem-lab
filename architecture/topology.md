# Network Topology

## Lab Network

The completed environment used a private:

`10.0.0.0/24`

network.

## Logical Topology

```mermaid
flowchart TB
    subgraph OCI["Oracle Cloud Infrastructure"]
      subgraph LAB["10.0.0.0/24"]
        SIEM["siem01<br/>Wazuh"]
        SENSOR["sensor01<br/>Wazuh Agent + Suricata + Zeek"]
        WIN["windows01<br/>Windows Endpoint"]
        AUTO["automation01<br/>Shuffle"]
      end
    end

    WIN -->|Endpoint telemetry| SIEM
    SENSOR -->|Security telemetry| SIEM
    SENSOR -->|Network metadata| SIEM
    SIEM -->|Automation events| AUTO
    WIN -->|Test traffic| SENSOR
```

## Host Roles

| Host | Primary Role |
|---|---|
| siem01 | Central SIEM |
| sensor01 / sensor01-zeek01 | Network security sensor |
| windows01 | Endpoint telemetry |
| automation01 | Security automation |

Keep exact public IP addresses and cloud-specific identifiers out of public documentation.
