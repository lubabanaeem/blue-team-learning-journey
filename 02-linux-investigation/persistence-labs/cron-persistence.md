# Cron Persistence Lab

## Objective
Understand how attackers can use cron jobs for persistence on Linux systems and how a defender can investigate suspicious scheduled tasks.

## Lab Scenario
A suspicious cron job was created on an Ubuntu VM to simulate an attacker attempting to execute a command automatically at scheduled intervals.

## Attack Simulation
- Created a cron entry for a test user.
- Verified that the scheduled task was registered.
- Observed how cron executes commands automatically.

## Investigation Steps

Checked cron locations:

- User cron jobs:
  - crontab -l
- System-wide cron locations:
  - /etc/crontab
  - /etc/cron.

Reviewed:
- Scheduled commands
- User ownership
- Execution paths
- Suspicious entries

## Findings

Cron can be abused as a persistence mechanism because commands configured in cron execute automatically without requiring user interaction.

Important investigation points:
- Unknown scripts or binaries
- Unusual execution times
- Suspicious file locations
- Unexpected users owning cron entries

## Lessons Learned

Learned how scheduled tasks can provide persistence and how defenders investigate cron configurations and related files.