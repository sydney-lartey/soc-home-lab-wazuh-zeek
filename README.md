# SOC Home Lab – Wazuh & Zeek

This repository documents a SOC-style home lab built to develop hands-on experience in SIEM monitoring, alert triage, and incident investigation using Wazuh and Zeek.

The focus of this lab is practical detection engineering and Tier-1 SOC workflows, including alert validation, investigation, documentation, and escalation decision-making.

---

## Lab Overview

- **SIEM:** Wazuh
- **Network Monitoring:** Zeek
- **Log Types:** conn.log, dns.log (JSON)
- **Monitored Systems:** Linux and Windows endpoints
- **Environment:** Isolated home lab

Zeek network telemetry is ingested into Wazuh using native JSON decoding, enabling field-based detection rules without custom decoders.

---

## Detection Use Cases

The following detections were developed and tested:

- Suspicious outbound UDP/NTP traffic (possible beaconing or misconfiguration)
- Network reconnaissance and port scanning behavior
- Potential DNS tunneling and covert C2 communication

Each detection was validated using Wazuh rule testing and log replay before being documented as an incident.

---

## Incident Investigations

Each incident follows a SOC-style investigation structure:
- Alert summary
- Detection logic
- Investigation steps
- Assessment and confidence
- Recommended actions

### Documented Incidents
- Incident 001: Suspicious UDP/NTP Traffic
- Incident 002: Port Scanning Detection
- Incident 003: Potential DNS Tunneling Activity

See the `/incidents` directory for full write-ups.

---

## Skills Demonstrated

- SIEM monitoring and alert triage
- Network traffic analysis using Zeek
- Detection rule development and tuning
- Incident investigation and documentation
- Linux and Windows log analysis
- False positive analysis and escalation decisions

---

## Next Improvements

Planned enhancements include:
- Time-based correlation rules
- DNS + network log correlation
- Alert severity tuning
- Dashboard visualisation

---

## About Me

I am pursuing a SOC Analyst / IT Support Analyst role, with a strong interest in security operations, monitoring, and blue-team workflows.
