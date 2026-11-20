# Server Architecture

## 1. Architecture Overview

This project uses a small laboratory environment consisting of a Parrot OS Linux server and a Windows client computer.

The infrastructure is designed to provide secure remote administration, controlled network access, authentication monitoring and database management.

The architecture will evolve as additional security capabilities are introduced.

## 2. Infrastructure Components

### Linux Server

Operating System: Parrot OS

The Parrot OS laptop acts as the central server.

It hosts the following services:

- OpenSSH for remote administration.
- UFW for firewall management.
- Fail2ban for monitoring repeated authentication failures.
- PostgreSQL for database management and security event storage.

### Client Computer

Operating System: Windows

The Windows laptop acts as a client used to establish remote SSH connections to the Linux server.

Windows PowerShell is used to execute SSH commands.

## 3. Network Communication

The Windows client communicates with the Parrot OS server through the local network.

SSH uses TCP port 22 for remote administration.

The UFW firewall controls incoming and outgoing network traffic.

PostgreSQL uses its default port, TCP 5432, and is currently configured to listen on localhost rather than external network interfaces.

## 4. Security Controls

### OpenSSH

Provides encrypted remote administration.

### UFW

Controls network traffic and applies firewall rules.

### Fail2ban

Monitors SSH authentication failures and can temporarily block IP addresses that exceed configured retry limits.

### PostgreSQL

Provides structured storage for sample security event records.

## 5. Current Architecture Limitations

The current implementation is an initial laboratory environment.

The following improvements remain:

- Verify SSH public-key-only authentication.
- Refine network access restrictions.
- Test Fail2ban blocking behaviour safely.
- Automate security event collection.
- Integrate system security monitoring with PostgreSQL.
- Introduce remote access through a VPN in a future phase.

## 6. Future Architecture Improvements

Future development may introduce:

- Python-based security monitoring.
- Automated log analysis.
- Network traffic analysis.
- Centralized security event management.
- Incident investigation and reporting.

## 7. Architecture Development Philosophy

The architecture is designed to evolve incrementally.

Changes will be documented with their technical purpose, implementation details, security benefits and verification results.
