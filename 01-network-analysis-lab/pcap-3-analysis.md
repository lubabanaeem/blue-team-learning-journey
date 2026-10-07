# Lumma Stealer — Victim Fingerprinting Investigation

## Investigation Overview

**Alert:** ET MALWARE Lumma Stealer Victim Fingerprint Activity  
**Dataset:** Malware-Traffic-Analysis.net  
**Analysis Tool:** Wireshark  
**Traffic:** HTTP/TCP  
**Suspicious Domain:** `whitepepper.su`

### Objective

Investigate the packet capture associated with a Lumma Stealer victim-fingerprinting alert, identify the affected Windows workstation, and analyze the HTTP activity responsible for the detection.

## Investigation

Traffic associated with the alert was isolated and the internal host communicating with the suspicious external infrastructure was identified.

HTTP traffic from the affected workstation was then examined in detail. Individual requests and responses were reviewed to understand the behavior occurring between the victim system and the external server.

The investigation identified HTTP GET and POST activity involving `whitepepper.su`. The contents of the HTTP communication were examined rather than relying solely on the original alert.

## Findings

### Network Environment

| Field | Value |
|---|---|
| Internal Network | `10.1.21.0/24` |
| Windows Domain | `win11office.com` |
| Active Directory Domain | `WIN11OFFICE` |
| Suspicious Domain | `whitepepper.su` |
| Protocol | HTTP |
| Destination Port | TCP/80 |

### Suspicious HTTP Activity

HTTP communication with `whitepepper.su` contained requests associated with victim fingerprinting activity.

One observed request included:

```text
GET /api/set_agent?...&agent=Chrome HTTP/1.1
Host: whitepepper.su
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ... Chrome/144.0.0.0
```

Additional HTTP POST traffic was observed, including a request containing approximately 8 KB of data.

Inspection of the HTTP streams showed that the activity extended beyond a simple connection to a suspicious domain. The request and response contents provided additional evidence of information collection and communication associated with the Lumma Stealer alert.

## Evidence

Important evidence included:

- Lumma Stealer victim-fingerprinting signature hit.
- HTTP communication with `whitepepper.su`.
- GET requests containing client-related parameters.
- HTTP POST activity containing a comparatively larger body of data.
- Browser and operating-system information visible within HTTP headers.
- Network evidence connecting the suspicious communication to the internal Windows environment.

## Assessment

The packet capture contained network behavior consistent with the Lumma Stealer victim-fingerprinting alert. Examination of the HTTP streams showed communication with `whitepepper.su` and exposed the request structure and data exchange responsible for the suspicious activity.

The investigation demonstrated the importance of validating an IDS alert by examining the underlying packet data and application-layer traffic rather than treating the alert itself as sufficient evidence.

## Skills Demonstrated

- Malware traffic analysis
- PCAP investigation with Wireshark
- HTTP request and response analysis
- IDS alert validation
- Suspicious domain investigation
- Application-layer traffic analysis
- Evidence-based security investigation