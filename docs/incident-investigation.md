# Incident Investigation

## Investigation Method

The lab follows a simple SOC investigation sequence:

### 1. Alert

Start with a security event from Wazuh or Suricata.

Record:

- Timestamp
- Source
- Destination
- Host
- Protocol
- Alert/signature
- Severity

### 2. Scope

Determine whether the activity affects:

- One endpoint
- Multiple endpoints
- A network segment
- An external destination

### 3. Network Context

Use Zeek data such as `conn.log` to understand the connection.

Questions:

- Was the connection established?
- Which protocol was used?
- How long did it last?
- What systems communicated?

### 4. Endpoint Context

Use Wazuh telemetry to identify related endpoint activity.

Look for:

- Process activity
- Authentication events
- Configuration changes
- Suspicious commands
- Repeated failures
- Unexpected network activity

### 5. Correlation

Correlate timestamps and hosts across:

- Wazuh
- Suricata
- Zeek
- Windows/Linux telemetry

### 6. Classification

Classify the event as one of:

- Benign
- Suspicious
- Confirmed malicious
- False positive
- Requires additional investigation

### 7. Response

Depending on the finding:

- Continue monitoring
- Collect additional evidence
- Isolate the affected endpoint in a controlled environment
- Block or contain the activity
- Trigger an automation workflow
- Document the incident

## Example Investigation Template

```text
Incident ID:
Date/Time:
Analyst:
Affected Host:
Source:
Destination:
Protocol:
Detection Source:
Alert:
Severity:

Initial Assessment:

Network Evidence:

Endpoint Evidence:

Correlated Events:

Classification:

Actions Taken:

Final Assessment:

Lessons Learned:
```

## Evidence Handling

Public repository documentation should contain sanitized screenshots and sample data only.

Never upload:

- Credentials
- API tokens
- Private keys
- Real customer information
- Sensitive production logs
