# FormBook C2 — Network Traffic Investigation

## Investigation Overview

**Alert:** ET MALWARE FormBook C2 activity  
**Dataset:** Malware-Traffic-Analysis.net  
**Analysis Tool:** Wireshark  
**Traffic:** HTTP/TCP  

### Objective

Analyze the provided packet capture to identify the affected Windows workstation and examine network activity associated with FormBook command-and-control (C2) communication.

## Investigation

The packet capture was reviewed in Wireshark to identify the internal system responsible for the suspicious traffic. Network conversations involving the affected host were isolated and HTTP traffic was examined to determine the nature of the external communication.

Repeated connections between the workstation and external infrastructure were identified. HTTP requests associated with the FormBook activity were then examined to determine the communication pattern.

## Findings

### Affected Host


| IP Address | `172.16.8.49` |
| MAC Address | `00:12:f0:28:d4:34` |
| Hostname | `DESKTOP-5NLV63K` |
| Username | `rvance` |
| User | Raymond Vance |

### Network Activity

The affected workstation established multiple HTTP connections with external systems associated with the alert.

Analysis of the HTTP traffic identified FormBook-related C2 check-in activity, including HTTP POST requests. The observed traffic used a Firefox user-agent string and communicated over TCP port 80.

An example of the suspicious request pattern included:

```text
HTTP POST /ujvq/
User-Agent: Firefox/39.0
```

The repeated outbound communication was consistent with malware maintaining contact with external C2 infrastructure.

## Evidence

Key evidence identified during the investigation included:

- Repeated outbound connections from the affected workstation.
- HTTP requests associated with the FormBook alert.
- POST communication to external infrastructure.
- Network protocol information identifying the affected Windows host and user.

## Assessment

The packet capture showed that `172.16.8.49` was the workstation involved in the FormBook-related network activity. The combination of the security alert, repeated outbound connections, and observed HTTP C2 communication provided evidence that the host was communicating with infrastructure associated with FormBook malware.

## Skills Demonstrated

- PCAP analysis with Wireshark
- HTTP traffic analysis
- Command-and-control traffic investigation
- Endpoint identification from network evidence
- Network IOC identification
- Security alert investigation