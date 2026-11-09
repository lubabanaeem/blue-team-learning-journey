# SSH Authorized Keys Persistence Lab

## Objective
Understand how attackers can maintain access to a Linux server by adding their own SSH keys.

## Lab Scenario

Simulated an attacker gaining access to a Linux user account and adding an SSH public key for future access.

Environment:
- Attacker machine: Windows
- Target machine: Ubuntu VM
- User account: testuser

## Attack Simulation

Steps performed:

1. Generated an SSH key pair on the attacker machine.
2. Added the public key to:


~/.ssh/authorized_keys

for the test user.

3. Tested SSH authentication using the created key.

## Investigation Steps

Checked:

- SSH authentication logs:
  - /var/log/auth.log

- User SSH directory:


~/.ssh/

Reviewed:
- authorized_keys content
- File ownership
- File timestamps
- Successful SSH logins

## Findings

Attackers can maintain persistent access by adding their own SSH keys.

Important investigation points:
- Unknown public keys
- Unexpected modifications to authorized_keys
- Suspicious login times
- Unknown source IP addresses

## Lessons Learned

Learned how SSH keys can be abused for persistence and how authentication logs and SSH configuration files can help invest