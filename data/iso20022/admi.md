# admi — Administration

System-level messages, less customer-relevant but important for ops.

| Message | Purpose |
|---|---|
| admi.002 | Reject |
| admi.004 | System Event Notification |
| admi.005 | Report Query Request |
| admi.006 | Resend Request |
| admi.007 | Receipt |
| admi.011 | System Event Acknowledgement |

## Use

- CSM operator publishes admi.004 for events (cycle close, mandatory pause, holiday)
- Bank ops monitors via system event handlers
- Drives CSM availability dashboards

## Linked

[[../../03-tech-integration]]
