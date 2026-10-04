# Suricata

Suricata provides network intrusion detection and network security monitoring.

## Responsibilities

- Packet inspection
- Protocol identification
- IDS rule matching
- Structured event generation

## Event Output

The lab used:

`/var/log/suricata/eve.json`

Wazuh was configured to ingest Suricata events from this output.

## Validated Protocols

The completed capture demonstrated visibility into:

- TCP
- UDP
- DNS
- HTTP
- TLS
- SSH

## Recorded Test Run

- Rules loaded: **49,691**
- Alerts recorded: **59**

These values describe the captured lab test and should not be interpreted as production performance benchmarks.
