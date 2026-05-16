Date: 5/15/2026
# SSH Access via Bastion Host LAB

Secure SSH access to internal/private servers using a Bastion (Jump) Host.

---

## Overview

This document explains how to securely connect to our internal infrastructure using the **Bastion Host** as a jump server.

**Bastion Host IP : 3.138.86.32
Private Web Server IP : 10.0.3.69
VPC CIDR: 10.0.0.0/20
Public Subnet : 10.0.2.0/24
Private Subnet : 10.0.1.0/24


---

## STEPS 
- Created a VPC
- Created an Internet GW and attached it to the VPC
- Created Public and Private Subnets
- Created a Public Route table, associated it with the public subnet and to the Internet GW
- Created a NAT Gateway
- Created a Private Route table, associated it with my private subnet and to the Nat GW
- Launched an EC2 Instance for my Bastion Host , attached a security group , incbound rules allow SSH on port 22 , HTTP port 80, HTTPS port 443, on 0.0.0.0/0
- added a user data script - install httpd apache
- Launch an EC2 for Private Web server, attached security group, inbound rules allow HTTP/80 , allow SSH/22 on bastion host SG

## TEST
- test internet of public IP
- SSH bastion host on my other laptop using the public IP,
- created a file and copy the key pair,
- uses that key pair to SSH my Private Web Server and test the internet of my private IP.

---

## Main Reasons for This Design

Security – Least Privilege & Attack Surface Reduction
Your web server should never be directly reachable from the internet on SSH (port 22).
If the web server is public and gets compromised (common with web apps), attackers immediately have a foothold.
Bastion acts as a controlled gateway. You harden it heavily (fail2ban, MFA, strict security groups, logging, etc.).

Web Server Needs Inbound Traffic, But Not for Management
Web servers need to receive HTTP/HTTPS traffic (ports 80/443) from users.
They do not need to receive SSH traffic from the internet.
Best practice: Put web servers in private subnets → accessible only through an Application Load Balancer (ALB) or API Gateway.

Better Control and Auditing
All admin access is forced through the bastion → easier to monitor, log, and audit who is accessing your servers.
You can disable direct SSH on web servers completely.

Compliance & Best Practices
This follows AWS Well-Architected Framework and security standards (CIS, NIST, etc.).
Many companies and auditors require this separation.
