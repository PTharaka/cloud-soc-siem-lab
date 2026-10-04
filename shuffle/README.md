# Shuffle

Shuffle is the automation component of the SOC lab.

## Purpose

The project used Shuffle to demonstrate webhook-driven security workflow automation.

## Workflow Concept

```text
Wazuh / Security Event
        |
        v
     Webhook
        |
        v
 Shuffle Workflow
        |
        +--> Parse
        +--> Enrich
        +--> Decide
        +--> Respond / Notify
```

## Security

Never commit webhook URLs, API tokens or credentials.

Use sanitized workflow exports or screenshots for public documentation.
