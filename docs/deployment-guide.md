# Deployment Guide

This guide documents the deployment approach used for the lab. Exact cloud identifiers, credentials and secrets are intentionally excluded.

## 1. Prepare the OCI Network

Create a private lab network using the required OCI networking components.

The completed lab used:

`10.0.0.0/24`

Assign separate private addresses to the SIEM, sensor, Windows endpoint and automation host.

## 2. Deploy the SIEM Host

Create the Linux host used as `siem01`.

Install and configure:

- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard

Verify that the Wazuh services are running before connecting agents.

## 3. Deploy the Linux Sensor

Create the Linux sensor host.

Install:

- Wazuh Agent
- Suricata
- Zeek

The sensor should have the network visibility required by the lab design.

## 4. Connect the Wazuh Agent

Register the Linux sensor with the Wazuh server.

Verify:

- Agent registration
- Agent connectivity
- Event arrival
- Correct host identity

The completed project successfully demonstrated Wazuh agent connectivity.

## 5. Configure Suricata

Configure Suricata for network inspection.

The lab validated:

- Packet capture
- Protocol identification
- IDS rules
- JSON event output
- `eve.json` generation

Wazuh was configured to consume Suricata events from:

`/var/log/suricata/eve.json`

Do not copy credentials or environment-specific paths into public documentation unless they are intentionally public.

## 6. Configure Zeek

Deploy Zeek on the network sensor and validate network telemetry.

The completed lab produced connection telemetry including:

`conn.log`

Use Zeek logs to understand network conversations and correlate them with IDS and SIEM events.

## 7. Deploy Windows Telemetry

Connect `windows01` to the monitoring environment.

Generate controlled endpoint activity and verify that relevant telemetry reaches Wazuh.

## 8. Deploy Shuffle

Deploy Shuffle on `automation01`.

Configure a webhook-based workflow for security event automation.

Keep all webhook URLs, authentication tokens and credentials private.

## 9. Validate the Pipeline

Use a controlled test sequence:

1. Generate normal network traffic.
2. Confirm Suricata sees the traffic.
3. Confirm Zeek records network metadata.
4. Confirm Wazuh receives endpoint/security telemetry.
5. Review events in the Wazuh Dashboard.
6. Send a selected event to Shuffle.
7. Confirm the workflow executes.

## 10. Troubleshooting Checklist

### Wazuh agent not connected

Check:

- Agent registration
- Network reachability
- Wazuh Manager service
- Agent service
- Firewall/security-list rules

### Suricata has no events

Check:

- Correct network interface
- Packet capture capability
- Suricata service
- Rule loading
- `eve.json` output

### Zeek has no connection logs

Check:

- Correct monitoring interface
- Zeek process status
- Network visibility
- Log directory permissions

### Shuffle webhook fails

Check:

- Webhook endpoint
- Workflow activation
- Network connectivity
- Authentication/secrets
- Event payload format
