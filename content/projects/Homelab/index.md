---
title: "Homelab"
date: 2026-01-30
featured: "featured.png"
draft: false
description: "Project documentation for my homelab"
tags: ["homelab", "networking", "docker", "proxmox", "ansible"]
showAuthor: true
---


### The Journey

My homelab has been the impetus behind my technical growth over the past 6 years. What started in 2020 as a way to push past the limits of my technical support role at a startup quickly evolved into a full-scale testing ground for enterprise grade and open source infrastructure. This homelab allows me to break, build and secure systems in a way that gives me practical and tangible real world connection and growth


### Architecture

**Network & Security**:
- **Gateway/Firewall**: OPNsense running on a Lenovo ThinkCentre M720q (24GB RAM, 256GB SSD). 
- **VLANs**:
    - Trusted
    - Guest
    - IoT
    - Management

**Compute (Virtualization & Orchestration)**:
- **Primary Proxmox Node**: 
    - **CPU**: AMD Ryzen 5 5600X (6-Core / 12-Thread)
    - **Board/RAM**: B450 Tomahawk Max | 48GB RAM
    - **Storage**: 1TB NVMe SSD for VM/LXC Boot Disks.
- **Proxmox Cluster (K8s/Automation Sandbox)**:
    - 2x Lenovo ThinkCentre M715q
    - 1x Lenovo ThinkCentre M920q
    - *Purpose-built for testing Kubernetes clusters, Ansible playbooks, and Terraform providers.*

**Data & Storage**:
- **TrueNAS Scale**: 
    - **CPU**: Intel Core i7-8700
    - **RAM**: 48GB (Optimized for ZFS ARC caching)
    - **Array**: 4x 8TB HDD in **RAID Z2** (approx. 16TB usable with double-drive parity).



    