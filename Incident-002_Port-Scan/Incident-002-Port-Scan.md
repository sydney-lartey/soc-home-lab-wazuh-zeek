# Incident 002 — Detection of TCP Port Scanning with Service Probing
### Overview

This incident documents the detection and analysis of TCP-based port scanning activity originating from an internal host. The behavior was identified through connection-level analysis and correlated with known scanning techniques involving SYN-based probing and service/version detection.

The activity was classified as active reconnaissance, not exploitation, and was scoped to a single internal host.

## 1.0 Alert Summary

- Severity: Medium

- Detection Source: Network telemetry (Zeek)

- Data Source: Zeek conn.log and protocol logs

- Detection Type: TCP horizontal port scanning

- Source Host: 192.168.94.136 (Kali Linux)

- Target Host: 192.168.94.138 (Linux)

### Summary

A single internal host initiated a large number of short-lived TCP connections to a wide range of destination ports on a single target system. The connection pattern was consistent with horizontal port scanning and prompted further investigation.

## 2.0 Environment

- Monitoring Platform: Zeek

- Network Sensor: Zeek (Ubuntu)

- Packet Capture: tcpdump

- Attacker / Simulator: Kali Linux (192.168.94.136)

- Target Host: Linux system (192.168.94.138)

- Network Type: Internal lab network

## 3.0 Detection Logic

The activity was detected based on abnormal TCP connection patterns rather than application-layer service identification.

Rule Conditions (Conceptual)

- proto = tcp

- Short-lived connections

- Multiple destination ports

- Single source host

### Rationale

Port scanning typically manifests as:

- One-to-many connection attempts

- Minimal data transfer

- Rapid succession of TCP sessions

Service labels are not required to identify scanning behavior.

## 4.0 Investigation and Analysis
### 4.1 Connection-Level Analysis

Analysis of Zeek conn.log revealed:

- A single source host initiating connections to many destination ports

- Very short connection durations

- Low byte counts per connection

- Predominantly failed or reset connections

This behavior strongly aligns with TCP SYN-based scanning.

### 4.2 One-to-Many Port Pattern

Aggregated connection analysis demonstrated that 192.168.94.136 attempted connections to numerous distinct TCP ports on the target host within a short time window.

This pattern is a primary indicator of horizontal port scanning and is unlikely to occur during normal application behavior.

### 4.3 Service Probing Artifacts

Additional protocol logs (dns.log, http.log, ssl.log, x509.log) were generated during the scan. These artifacts are consistent with service/version probing behavior, where scanning tools briefly initiate protocol-specific handshakes to identify running services.

The presence of these logs supports reconnaissance activity but does not imply successful exploitation.

## 5.0 Assessment

Likelihood of Malicious Activity: Medium

The activity was assessed as active reconnaissance based on:

- One-to-many TCP connection pattern

- Short-lived connections with minimal payloads

- Correlation with known scanning techniques

No evidence of exploitation, privilege escalation, or lateral movement was observed.

## 6.0 Recommended Actions
### Immediate Actions

- Identify the source host responsible for the scanning activity

- Confirm whether the activity was authorized (e.g., internal testing)

### Preventive / Monitoring Actions

- Implement detection for horizontal port scanning patterns

- Alert on sustained one-to-many TCP connections

- Correlate with endpoint telemetry for process attribution

## 7.0 Lessons Learned

- Connection metadata is sufficient to identify port scanning activity

- Service identification is secondary to behavioral patterns

- Background traffic and protocol noise should be filtered during analysis

- Accurate classification prevents unnecessary escalation

### Why This Incident Matters

This investigation demonstrates the ability to detect and classify reconnaissance activity using passive network telemetry. Identifying port scanning at this stage enables defenders to respond before exploitation attempts occur.
