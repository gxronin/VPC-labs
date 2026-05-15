AWS VPC Private Lab (Intermediate Networking Project)

This project demonstrates a real-world AWS networking architecture using a custom Virtual Private Cloud (VPC) with public and private subnets, secure routing, and core AWS services integration. It is designed as an intermediate-level cloud networking lab for learning and portfolio building.


 
 --Project Overview

The goal of this lab is to build a secure and scalable AWS environment using best practices in cloud networking. It simulates a production-like architecture with isolated private resources and controlled public access.

Key focus areas:

VPC design and subnet segmentation
Route tables and internet access control
Security groups and network ACLs
Bastion host for secure SSH access
NAT Gateway for private subnet internet access
Load balancing and auto scaling
S3 integration for storage

 
 
 --Architecture Components

This lab includes the following AWS services:

Amazon VPC – Custom virtual network
Public Subnets – For internet-facing resources (ALB, Bastion Host)
Private Subnets – For application servers
Internet Gateway (IGW) – Public internet access
NAT Gateway – Outbound internet access for private instances
Route Tables – Traffic routing control
Security Groups – Instance-level firewall rules
Network ACLs (NACLs) – Subnet-level security control
Elastic Load Balancer (ALB) – Traffic distribution
Auto Scaling Group (ASG) – Automatic scaling of EC2 instances
Amazon EC2 – Application and bastion servers
Amazon S3 – Object storage for static assets or logs
Elastic IP (EIP) – Static public IP for NAT or bastion
