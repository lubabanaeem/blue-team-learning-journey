# NetSupport Manager RAT — Network Traffic Investigation

## Investigation Overview

**Alert:** ET MALWARE NetSupport Manager RAT activity  
**Dataset:** Malware-Traffic-Analysis.net  
**Analysis Tool:** Wireshark  
**Traffic:** TCP  

### Objective

Analyze the supplied packet capture to identify the Windows workstation associated with the NetSupport Manager RAT alert and determine the network evidence connecting the endpoint to the suspicious activity.

## Investigation

The traffic associated with the security alert was isolated in Wireshark and the communication between the external system and the internal network was examined.

After identifying the internal IP involved in the suspicious connection, additional Windows network traffic was analyzed to determine the identity of the affected workstation.

Information from multiple network protocols was correlated to identify the host, MAC address, username, and associated user.

## Findings

### Affected Host

| Field | Value |
|---|---|
| IP Address | `10.2.28.88` |
| MAC Address | `00:19:d1:b2:4d:ad` |
| Hostname | `DESKTOP-TEYQ2NR` |
| Username | `brolf` |
| User | Beck Rolf |

### Suspicious Network Activity

The workstation was observed communicating with external infrastructure associated with the NetSupport Manager RAT alert.

Analysis of the network traffic established that the internal host `10.2.28.88` was responsible for the communication that triggered the detection.

Windows network protocol information was then used to correlate the IP address with the affected workstation and user account.

## Evidence

The investigation relied on several pieces of network evidence:

- Security alert identifying NetSupport Manager RAT activity.
- Communication between an external system and `10.2.28.88`.
- MAC address associated with the affected endpoint.
- Windows network traffic exposing the workstation hostname.
- Protocol information allowing the username and user identity to be correlated with the host.

Rather than relying on a single packet, information from multiple network conversations was correlated to build the affected-host profile.

## Assessment

Network evidence identified `DESKTOP-TEYQ2NR` (`10.2.28.88`) as the Windows workstation associated with the NetSupport Manager RAT alert.

The investigation demonstrated how information distributed across different network protocols can be correlated to move from a security alert to identification of the affected endpoint and user.

## Skills Demonstrated

- PCAP investigation
- Wireshark traffic filtering
- Security alert analysis
- Windows host identification from network traffic
- Network protocol correlation
- Endpoint and user attribution from packet data