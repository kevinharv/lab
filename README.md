# To-Do
1. Define provision/administer/decom procedures
1. ~~~Update DNS records~~~
1. Add metadata to Ansible playbooks
1. Re-do storage allocation/assignment (iSCSI? NFS mounts?)
1. ~~~Migrate all FS01 content to desktop~~~
1. ~~~DECOM everything except prddock1~~~
1. Build new Domain Controller
    1. Create users and groups
    1. Join to free AAD environment
    1. Investigate indefinite trial workaround
1. Build IPA server?
1. Build Satellite Server
1. Build Ansible Automation Platform (Tower) Server
1. Build VPN Server
1. Rebuild Docker environment (Portainer?)
1. Build Kubernetes cluster

# New Systems
- Microsoft Active Directory Domain Controller
- Production Docker Enviornment
- Production Kubernetes environment
- VPN (probably WireGuard) Server
- Ansible Automation Platform (Tower)
- Red Hat Satellite Server
- Red Hat Identity Server (IPA)
- Red Hat Identity Server
- NGINX Proxy Manager

# New DNS Config [WIP]
Windows DC will provide local DNS. Cloudflare provides external DNS. Realistically, since I don't have authority to change DHCP DNS servers on the LAN, I'll just create public DNS entries to local IPs. It's ugly, but it works until I get a separate network.

I might be able to get a reverse proxy to help with that, but I'm not sure if it's going to overlap with my VPN services. OpenVPN wouldn't play nice with a RP, but if I go to WireGuard, I won't need a web server. TBD.

Domain:         `kevharv.com`

Lab Sub:        `lab.kevharv.com`

FQDN Format:    `[shortname].lab.kevharv.com`

AD Objects:     `[shortname].ad.lab.kevharv.com`

# New IP Organization
Home network is 192.168.1.0/24 and can't easily be changed (nor does  it need to be). I set DHCP to 192.168.1.100-192.168.1.254 and the gateway is 192.168.1.1. Anything in the 192.168.1.2-192.168.1.99 can be segmented for lab services.

- 192.168.1.20 - Hypervisor
- Others

# Code to Write
- Cloudflare DNS updater
    - Update lab.kevharv.com A record on IPv4 change
    - Dockerize and throw it in the Docker env

# Standard Server Build
High Level Outline:
1. Set Time Zone, Locale
1. Set Network Info
1. Set SELinux Enforcing
1. Configure root user
1. Create local service account
1. SSHD config
1. Bind to AD/IPA/LDAP?
1. Install applications