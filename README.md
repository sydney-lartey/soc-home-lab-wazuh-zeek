# SOC Home Lab – Wazuh & Zeek Incident Investigations

This repository documents a SOC-style home lab built to develop and demonstrate hands-on experience in Security Operations, including SIEM monitoring, alert triage, and incident investigation using Wazuh and Zeek.

The focus of this lab is practical Tier-1 SOC workflows such as alert validation, log analysis, behavioural detection, incident documentation, and escalation decision-making.

---

## Lab Overview

- SIEM: Wazuh  
- Network Monitoring: Zeek  
- Log Types: conn.log, dns.log (JSON)  
- Monitored Systems: Linux and Windows endpoints  
- Environment: Isolated home lab  

Zeek network telemetry is ingested into Wazuh using native JSON decoding, enabling field-based detection rules and correlation without the use of custom decoders.

---

## Detection Use Cases

The following detection scenarios were developed, tested, and validated within this environment:

- Suspicious outbound UDP/NTP traffic (potential beaconing or misconfiguration)
- Network reconnaissance and port scanning behaviour
- Potential DNS tunneling and covert command-and-control activity

Each detection was validated using Wazuh rule testing and log replay before being documented as a full SOC-style incident investigation.

---

## Incident Investigations

Each documented incident follows a consistent SOC investigation structure, including:

- Alert summary and trigger source  
- Detection logic and context  
- Investigation steps and log analysis  
- Assessment, confidence level, and findings  
- Escalation, monitoring, or closure decision  

### Documented Incidents
- Incident 001: Suspicious UDP/NTP Traffic  
- Incident 002: Network Port Scanning Detection  
- Incident 003: Potential DNS Tunneling Activity  

See the `/incidents` directory for full write-ups and supporting evidence.

---

## Skills Demonstrated

- SIEM monitoring and alert triage  
- Network traffic analysis using Zeek  
- Detection rule development and tuning  
- Incident investigation and documentation  
- Linux and Windows log analysis  
- False positive analysis and escalation judgement  

---

## Planned Improvements

Future enhancements to the lab include:

- Time-based correlation rules  
- DNS and network log correlation  
- Alert severity tuning  
- Dashboard and visualisation improvements  

---

## About

This repository reflects practical SOC investigation work aligned with Tier-1 Security Operations and security-focused IT analyst roles.
