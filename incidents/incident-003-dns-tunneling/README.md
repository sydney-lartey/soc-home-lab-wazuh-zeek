# Incident 003 — Potential DNS Tunneling Activity (Zeek + Wazuh)

## Incident Summary
Suspicious DNS activity was detected involving repeated queries with unusually long, irregular subdomain names. The behaviour deviated from normal DNS resolution patterns and is consistent with techniques commonly used for **DNS tunneling or covert command-and-control (C2)** communication.

## Alert Details
- Detection Tool: Wazuh SIEM
- Data Source: Zeek `dns.log` (JSON)
- Alert Type: Suspicious DNS behaviour
- Severity: Medium–High
- Detection Method: Behavioural analysis of DNS query structure and frequency

## Environment
- SIEM: Wazuh
- Network Monitoring: Zeek
- Log Type: `dns.log` (JSON)
- Monitored Systems:
  - Internal Linux and Windows endpoints
  - Kali Linux host (attack simulation)
- Network: Home lab with controlled outbound DNS access
- Ingestion: Zeek DNS telemetry ingested into Wazuh using native JSON decoding

## Detection Logic
The detection focused on identifying **DNS query characteristics** commonly associated with tunneling activity.

**Indicators evaluated:**
- Excessively long domain names
- High-entropy or random-looking subdomains
- Repeated queries to the same parent domain
- High query frequency over a short time window
- Lack of corresponding legitimate application behaviour

**Ration**
