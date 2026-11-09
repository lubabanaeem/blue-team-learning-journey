# Sysmon Hands-on Learning

## Objective

After learning Windows telemetry and Wazuh monitoring, I practiced integrating Sysmon with Wazuh to understand how endpoint telemetry can improve investigations.

## Setup

- Installed Sysmon on Windows 11 lab machine.
- Connected the Wazuh agent to collect Sysmon Operational logs.
- Verified that Sysmon events were reaching Wazuh.

## Process Creation Investigation (Event ID 1)

I generated process activity on the Windows machine and observed how process creation events appeared in both Windows Security logs and Sysmon.

I compared:

- Windows Security Event ID 4688
- Sysmon Event ID 1

Observed that Sysmon provided additional information such as:

- Command line
- Parent process
- Process GUID
- Image path

I learned that Sysmon does not enrich existing Windows Security events. Instead, it creates separate telemetry that can be correlated during investigations.

## Registry Monitoring (Event ID 12/13)

I enabled registry monitoring through the Sysmon configuration and generated registry changes.

Through Wazuh, I observed Sysmon registry events and compared them with normal Windows logs.

I learned that registry events are useful for investigating persistence techniques because attackers commonly modify registry locations such as Run keys.

## Event Correlation Practice

During investigation practice:

1. I observed a Windows Security process creation event.
2. I searched for the corresponding Sysmon Event ID 1.
3. I compared shared attributes:
   - Timestamp
   - Process name
   - Process ID
   - User context

I learned that Process GUID is unique to Sysmon and cannot directly be used with Windows Security events because it is not present there.

## Configuration Challenges

While testing:

- Some expected events were not visible because Sysmon configuration filters telemetry.
- Later i found that most of them uses fixed specific paths for for example key registration,
  whereas i was using normal my own key paths which failed to match the configuration file's written 
  rule paths and events were not firing.

## Key Takeaways

- Sysmon provides deeper endpoint visibility than default Windows logging.
- Correlation requires understanding what fields exist in each log source.
- More telemetry does not automatically mean more detection; configuration determines what is visible.