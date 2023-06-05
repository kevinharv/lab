# Overview
This document holds a step by step account of the procedures followed and actions taken while building the new homelab deployment.

# Network

- Proxmox VE - 192.168.1.20
- Domain Controller - 192.168.1.10
- IPA Server - 192.168.1.12

# IPA Server
1. Provision VM
1. Install OS
1. Install IPA
1. Bind to upstream AD

# Domain Controller
1. Download Windows Server 2022 Standard ISO
1. Provision VM (4c/8GB/30GB)
1. Attach VirtIO driver ISO
1. Power On and install OS
1. Install VirtIO drivers
1. Remove VirtIO ISO
1. Hostname, IP, DNS, updates
    - Not going to install SCCM or other management software for 1-2 Windows VMs
    - Upstream DNS set to Cloudflare, Google as backup
1. Install AD DS Service
1. Restart
1. Promote to DC
1. Create forest and domain
1. Create OUs, users
1. Join to AAD

# System Configuration
- Set NTP
- Set Hostname
- Set DNS
    - Copy template /etc/resolv.conf
- Additional network configuration?
- Join Satellite server
- Set subscriptions?
- Enable repos
- Install packages
    - Common system packages
    - Packages required for configuration of system (sssd, kerberos, Puppet, Zabbix, etc.)
    - Application specific packages
- Set Message of the Day (/etc/motd)
- Set pre-auth banner (/etc/banner)
- Configure SSHD (set banner)
- Set SELinux enforcing
- Set SNMP
- Set remote syslog server
- IdM/Domain join system
- Install monitoring agent
- Install service/application

## Common Packages
- Zabbix