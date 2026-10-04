# Detection and Monitoring

## Monitoring Layers

The project uses several complementary monitoring layers.

### Endpoint Layer

Wazuh provides centralized endpoint security telemetry.

Example sources:

- Linux host activity
- Windows endpoint activity
- Agent status
- Security-related logs

### Network IDS Layer

Suricata provides network intrusion detection and protocol-aware events.

The completed run observed:

- TCP
- UDP
- DNS
- HTTP
- TLS
- SSH

The test run loaded **49,691 rules** and recorded **59 alerts**.

### Network Metadata Layer

Zeek provides network metadata that helps analysts understand communication patterns.

A key output is:

`conn.log`

This can be used to answer questions such as:

- Which hosts communicated?
- When did the connection occur?
- Which protocol was involved?
- How long did the connection last?
- How much traffic was exchanged?

## Correlation

A useful SOC investigation should not depend on one alert.

For example:

```text
Suricata alert
      +
Zeek connection metadata
      +
Wazuh endpoint telemetry
      =
Higher-confidence investigation
```

This layered approach helps an analyst move from an alert to context.

## Detection Workflow

1. Observe an alert or suspicious event.
2. Identify the affected host.
3. Determine the source and destination.
4. Review the relevant network protocol.
5. Correlate with endpoint telemetry.
6. Determine whether the activity is expected.
7. Preserve evidence.
8. Escalate or automate the appropriate response.

## Important Distinction

An IDS alert is not automatically a confirmed compromise.

Alerts require context, validation and investigation.
