# Systemd Service Persistence Lab

## Objective
Understand how attackers can create malicious services to maintain persistence on Linux systems.

## Lab Scenario
A fake malicious service was created to simulate an attacker creating a service that starts automatically during system boot.

## Attack Simulation

Created a test systemd service:

- Added a service file under:
  - /etc/systemd/system/

- Reloaded systemd configuration.
- Started and enabled the service.

## Investigation Steps

Checked services using:

- systemctl status
- systemctl list-units
- systemctl list-unit-files

Reviewed:
- Service name
- Service file location
- Executed command
- Enabled status
- Creation timestamps

## Findings

Services can provide persistence because enabled services start automatically during boot.

Important investigation points:
- Unknown services
- Suspicious executable paths
- Recently created service files
- Services running with high privileges

## Lessons Learned

Learned how Linux services can be abused for persistence and how to investigate suspicious systemd services.