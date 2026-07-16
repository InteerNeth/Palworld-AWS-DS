# AWS Palworld Dedicated Server Home Lab

Deploying and managing a dedicated Palworld server on Amazon EC2 using AWS networking, Linux administration, and security best practices.

---

## Project Overview

This project demonstrates how to deploy, configure, and maintain a dedicated Palworld server on AWS.

The objective was not only to host the game, but also to gain practical experience with:

- Amazon EC2
- VPC Networking
- Security Groups
- Linux Server Administration
- Remote Server Management
- Game Server Maintenance

---

## Architecture

![Architecture](Palworld-AWS-DS/System-Architecture.png)

---

## AWS Services Used

| Service | Purpose |
|----------|---------|
| Amazon EC2 | Hosts the Ubuntu server running Palworld |
| Amazon VPC | Provides network isolation |
| Public Subnet | Allows internet connectivity |
| Internet Gateway | Enables inbound/outbound internet access |
| Elastic IP | Provides a static public IP |
| Security Groups | Controls inbound/outbound traffic |

---

## System Specifications

| Component | Value |
|-----------|------|
| OS | Ubuntu Server 24.04 LTS |
| Instance Type | m7i-flex.large |
| Region | us-east-1 *(replace with your actual region)* |
| Game | Palworld Dedicated Server |

---

## Network Configuration

### Inbound Rules

| Port | Protocol | Purpose |
|------|----------|---------|
| 22 | TCP | SSH Remote Administration |
| 8211 | UDP | Palworld Game Traffic |

---

## Deployment Process

1. Launch an Ubuntu EC2 instance.
2. Allocate and associate an Elastic IP.
3. Configure Security Group rules.
4. Connect via SSH.
5. Install SteamCMD.
6. Download the Palworld Dedicated Server.
7. Configure `PalWorldSettings.ini`.
8. Start the server using `tmux`.
9. Verify client connectivity.

---

## Updating the Server

Whenever a Palworld update is released:

1. Stop the running server.
2. Update the server using SteamCMD.
3. Restart the dedicated server.
4. Verify the server version.

---

## Challenges Encountered

### Permission Issues

Some server files required elevated permissions during installation.

**Solution**

- Corrected ownership using `chown`
- Updated file permissions using `chmod`

---

### Keeping the Server Running

Closing the SSH session terminated the server process.

**Solution**

Used `tmux` to keep the server running independently of the SSH connection.

---

### Network Connectivity

Players could not connect.

**Solution**

Verified:

- Security Group rules
- Public IP
- Required UDP ports
- Palworld configuration

---

## Skills Demonstrated

- AWS EC2
- VPC Networking
- Elastic IP Management
- Security Group Configuration
- Linux Administration
- SSH
- SteamCMD
- tmux
- Server Troubleshooting
- Game Server Deployment

---

## Future Improvements

- CloudWatch Monitoring
- Automated Backups
- Terraform Deployment
- Auto Recovery
- Automated Update Script

---

## Lessons Learned

This project provided practical experience deploying and maintaining a production-like Linux server on AWS. It reinforced concepts related to networking, security, Linux administration, and operational troubleshooting while managing a live game server.
