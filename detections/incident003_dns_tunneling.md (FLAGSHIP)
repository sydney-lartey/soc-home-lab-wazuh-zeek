# Detection: DNS Tunneling / High-Entropy DNS Queries

## Related Incident
Incident 003 — DNS Tunneling Investigation

## Objective
Detect covert data transfer or command-and-control over DNS while explicitly excluding multicast name resolution traffic (mDNS / LLMNR).

## Data Sources
- Zeek `dns.log`
- Zeek `conn.log`
- DNS resolver logs (optional)

## Detection Logic (Primary)

Trigger on sustained, high-entropy DNS queries from a single host.

Conditions:
- destination_port = 53
- NOT destination_port IN (5353, 5355)
- long query length
- high query frequency

## Example Pseudocode

IF
  dest_port = 53
  AND query_length > 50
GROUP BY
  source_ip
WITHIN
  10 minutes
CALCULATE
  count(dns_queries),
  avg(query_length)
TRIGGER WHEN
  count(dns_queries) >= 30

## Optional Enhancements

- Shannon entropy scoring on query labels
- Bias toward TXT or NULL record types
- Detection of sequential or encoded subdomains

## False Positive Considerations
- CDNs
- Antivirus or EDR cloud lookups
- Some legitimate SaaS platforms

False positives are reduced by:
- Frequency thresholds
- Entropy analysis
- Per-host baselining

## Severity
High

## Triage Guidance
- Identify the dominant source host
- Block or sinkhole suspicious domains
- Isolate the host if confirmed malicious
- Pivot to endpoint analysis for process attribution
