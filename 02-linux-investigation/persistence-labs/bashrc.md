# Bashrc Persistence Lab

## Objective
Understand how attackers can use shell startup files for persistence.

## Lab Scenario

A command was added to a user's .bashrc file to simulate execution when the user starts an interactive shell.

## Attack Simulation

Modified:


~/.bashrc

to include a test command.

Opened a new shell session and observed the command execution.

## Investigation Steps

Checked:


~/.bashrc

Reviewed:
- Recently added commands
- Suspicious scripts
- External commands
- File modification times

## Findings

Shell startup files can be abused because commands inside them execute automatically when a user starts a shell session.

Important investigation points:
- Unexpected commands
- Obfuscated scripts
- Network connections
- Recently modified startup files

## Lessons Learned

Learned that user startup files can be abused as a persistence technique and should be checked during Linux compromise investigations.