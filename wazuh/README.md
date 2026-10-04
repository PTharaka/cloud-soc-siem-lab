# Wazuh

Wazuh is the central SIEM and endpoint monitoring component in this project.

## Responsibilities

- Centralized event collection
- Endpoint monitoring
- Security event analysis
- Event indexing
- Dashboard visualization
- Agent management

## Deployment

The central server is:

`siem01`

It hosts:

- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard

The Linux sensor and Windows endpoint provide telemetry to the central system.

## Validation

The project successfully demonstrated Wazuh agent connectivity and centralized telemetry.

## Public Repository Rule

Do not commit:

- Wazuh passwords
- Agent keys
- Private certificates
- Production configuration containing secrets
