SSH Security Configuration


1. Introduction


Secure Shell (SSH) is a network protocol that allows users to securely access and manage remote computers over an encrypted connection.


In this project, SSH provides remote access to a Parrot OS Linux server from a Windows client.


The goal is to configure SSH securely and understand how authentication, access restrictions, and security logging work.


2. Environment

Component
	

Description

Server
	

Parrot OS Linux

Client
	

Windows

SSH software
	

OpenSSH

Default SSH port
	

TCP 22

Connection type
	

Local Area Network (LAN)

3. OpenSSH Installation and Configuration


The OpenSSH server was installed on the Parrot OS machine to enable remote administration.


During setup, the SSH service initially failed to start because the /run/sshd privilege separation directory was missing.


The issue was resolved by creating the directory with the appropriate ownership and permissions, then validating the SSH configuration.


Commands used:

sudo install -d -o root -g root -m 0755 /run/sshd
sudo sshd -t
sudo systemctl start ssh
sudo systemctl enable ssh

The SSH service was subsequently confirmed to be running.


4. SSH Security Settings


The SSH server configuration was backed up before changes were made.


Backup command:

sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup

The following security settings were configured:

Port 22
PermitRootLogin no
PubkeyAuthentication yes
PasswordAuthentication yes
PermitEmptyPasswords no
MaxAuthTries 3

These settings are intended to:

    Prevent direct SSH login as the root account.

    Enable public-key authentication.

    Keep password authentication available while public-key access is being tested.

    Prevent empty-password authentication.

    Limit authentication attempts per connection.


Important: Password authentication remains enabled until public-key authentication is successfully verified.


5. SSH Key Authentication


An Ed25519 SSH key pair was generated on the Windows client.


The public key was copied to the Linux server and added to the user’s ~/.ssh/authorized_keys file.


The purpose of public-key authentication is to allow secure access without sending the Linux account password for each SSH login.


Current status: The public key has been installed, but successful public-key-only login still needs to be verified.


6. SSH Connection Testing


The Windows client was used to connect to the Parrot OS server over the local network.


Testing included:

    Establishing an SSH connection using password authentication.

    Performing a controlled failed login attempt.

    Confirming that a subsequent successful login was recorded.


The SSH connection was successful using password authentication.


7. SSH Security Monitoring


SSH authentication events were inspected using the Linux system journal.


Command:

sudo journalctl -u ssh --no-pager -n 30

The logs showed authentication events, including:

    Failed password attempts.

    Accepted password authentication.

    SSH service activity.


The traditional /var/log/auth.log file was not available in this environment, so the system journal was used instead.


8. Current Security Status

Security Component
	

Status

OpenSSH server installed
	

Completed

SSH service running
	

Verified

Root SSH login disabled in configuration
	

Configured; effective setting to be verified

Public-key authentication enabled
	

Configured

Public key installed
	

Completed

Public-key-only login
	

Pending verification

Password authentication disabled
	

Not yet completed

SSH login events inspected
	

Completed

9. Planned Improvements


Future SSH security improvements include:

    Verify that public-key-only authentication works.

    Disable password authentication after successful key testing.

    Verify the effective SSH configuration.

    Test access from another authorized client.

    Continue monitoring failed and successful authentication events.


10. Security Considerations


SSH access is currently intended for the local network.


The server should not be exposed directly to the public internet without additional security controls. A VPN-based solution, such as WireGuard, may be considered for future remote access.


Private SSH keys, passwords, and sensitive server information must never be uploaded to this public repository.
