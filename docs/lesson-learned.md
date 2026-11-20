Development Journal and Lessons Learned


Introduction


This document records the practical lessons, technical challenges, troubleshooting procedures and improvements encountered while developing the secure Linux server infrastructure.


The purpose is to maintain a record of technical growth and demonstrate the ability to investigate and resolve system administration and security problems.


Learning Entry 001: Initial Linux Server Setup


Objective


Establish a working Linux server environment using Parrot OS.


Technologies

    Parrot OS

    OpenSSH

    Windows PowerShell


Implementation


Installed and configured the OpenSSH server to allow remote administration.


Established an SSH connection from a Windows client to the Parrot OS server over the local network.


Challenge Encountered


The SSH service initially failed to start because the privilege separation directory was missing.


Troubleshooting


Investigated the SSH service error and created the required directory:


/run/sshd


Verified the SSH configuration and restarted the service.


Lesson Learned


Linux services sometimes fail because required runtime directories or configuration dependencies are missing.


Understanding service errors and investigating system logs are important administration skills.

Learning Entry 002: Firewall Configuration


Objective


Establish basic network traffic controls.


Technology


UFW (Uncomplicated Firewall).


Implementation


Configured the firewall to:

    Deny incoming connections by default.

    Allow outgoing connections by default.

    Permit SSH connections.

    Enable the firewall.


Lesson Learned


A firewall should follow the principle of least privilege.


Required services should be explicitly permitted rather than allowing unnecessary incoming connections.

Learning Entry 003: SSH Intrusion Prevention


Objective


Monitor repeated unsuccessful SSH authentication attempts.


Technology


Fail2ban.


Implementation


Installed Fail2ban and enabled the SSH protection jail.


Verified the jail status and observed authentication failure statistics.


Practical Observation


A controlled unsuccessful SSH login was detected by Fail2ban.


Lesson Learned


Authentication monitoring helps administrators identify suspicious login activity.


Fail2ban can temporarily block IP addresses when configured retry thresholds are exceeded.

Learning Entry 004: PostgreSQL Database Administration


Objective


Create a database for storing sample security events.


Technology


PostgreSQL and SQL.


Implementation

    Created a database named server_security.

    Created a database role named server_admin.

    Assigned database ownership.

    Created a table named security_logs.

    Inserted a sample SSH login event.

    Retrieved the stored record using an SQL query.


Lesson Learned


Relational databases provide structured storage and querying capabilities for security-related information.

Learning Entry 005: Linux Authentication Log Investigation


Objective


Investigate SSH authentication activity.


Technology


journalctl


Implementation


Used the systemd journal to inspect SSH service logs.


Identified:

    Failed password authentication.

    Accepted password authentication.

    SSH service startup messages.


Challenge Encountered


The expected /var/log/auth.log file was not available.


Troubleshooting


Used the systemd journal instead:


sudo journalctl -u ssh --no-pager -n 20


Lesson Learned


Linux distributions may use different logging configurations.


Administrators should understand how to inspect systemd journal entries when traditional log files are unavailable.

Future Learning Entries


Additional entries will be added as the project develops.


Planned areas include:

    SSH public-key-only authentication.

    Advanced firewall configuration.

    Fail2ban ban testing.

    Automated security event collection.

    Python security automation.

    Network traffic analysis.

    Security incident investigation.


Personal Development Goal


Develop the practical technical knowledge required to work as a cybersecurity analyst, with particular emphasis on Linux administration, security monitoring, log analysis and incident investigation.
