# Secure-Linux-Server-Infrastructure
Project Overview  
This project focuses on building, securing, monitoring, and continuously improving a Linux server infrastructure. 
The objective is to gain practical experience in Linux system administration, network security, database management, and cybersecurity monitoring.

This repository documents the development process, technical implementations, challenges, troubleshooting procedures, and security improvement made throughout the project.
This is an ongoing hands-on learning project.

### Project Objectives

1. Build and administer a Linux server environment.
2. Configure secure remote administration using OpenSSh.
3. Implement firewall protection using UFW.
4. Configure Fail2ban to monitor suspicious SSh authentication activity.
5. Deploy PostgreSQL for security event storage.
6. Learning Linux authentication logging and system monitoring.
7. Develop automated security monitoring capabilities.
8. Document security decisions and infrastructure improvements.

   ### LAB ENVIRONMENTS
   
# Component                           Technology

Server Operating System              Parrot OS
Client Operating System              Windows
Remote Administration                OpenSSH
Firewall                             UFW
Intrusion Prevention                 Fail2ban
Database                             PoastgreSQL
Database Language                    SQL
Version Control                      Git and Github

### Implemented Components

# 1.SSH Remote Administration
.Installed OpenSSH server.
.Configured SSH service. 
.Established remote connectivity from Windows.
.Configured SSH authentication settings.

# 2 Firewall Configuration

.Installed and enabled UFW.
.Configured default incoming traffic policy.
.Configured default outgoing traffic policy.
.Added an SSH firewall allowance.

# 3.Fail2ban Protection

.Install Fail2ban
.Enabled the SSH protection jail.
.Configured SSH authentication monitoring.
.Verified detection of a failed SSH login attempt.

# 4.PostgreSQL Database

.Installed PostgreSQl.
.Created a database named server_security.
.Created a dedicated database role named server_admin.
.Created a security_logs table.
.Successfully inserted and retrieved a sample security event.

# 5.Security Log Investigation

.Used journalctl to inspect SSH service logs.
.Identified unsuccessful authentication attempts.
.Identified successful password authentication.
.Examined Fail2ban monitoring statistics.

# Planned Improvements
.Verify SSH public-key-only authentication 
.Improve SSH Security configuration.
.Review and refine firewall rules,
.Test Fail2ban banning behaviour safely.
.Develop automated security event collection.
.Integrate security monitoring with PostgreSQL.
.Introduce Python for security automation.
.Develop incident investigation and reporting procedures.


# Development Philosophy 
This project follows a continuous learning and improvement approach.
Every major implementation will include:

1 The objective of the implementation.
2.The tools and technology used.
3.The technical explanation.
4.The challenges encountered.
5.The testing and verification process.
6.Lesson learned and possible improvement.
changes to the infrastructure will be documented as the project evolves.

# Disclaimer
This project is developed in a controlled personal laboratory environment for educational purposes.
All security testing is performed on systems and networks that i own or have permission to assess.

# Project Status 

This repository represents my practical learning journey towards becoming a cybersecurity analyst.
