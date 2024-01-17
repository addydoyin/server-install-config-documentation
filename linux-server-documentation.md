 Linux Server Installation and Configuration Documentation
  ===

 A. Introduction
 ---

 1. Purpose
The purpose of this documentation is to serve as a guide through the installation and configuration of a Linux server. The server is intended for web hosting and providing a platform for services such as websites and web applications, file hosting and database management.
 2. Scope
The server is designed for medium-scale web hosting (i.e within an organization), supporting multiple websites and services. Limitations include a focus on web-related functionalities and a lack of support for resource-intensive tasks and heavy data processing like video rendering.


 B. Hardware and Software Requirements
 ---

 1. Hardware Specifications
+ CPU: Dual-core Intel Xeon processor
+ RAM: 8 GB DDR4
+ Storage: 200 GB SSD
+ Network Interface: 1 Gbps Ethernet

 2. Software Requirements
+ Operating System: Ubuntu Server 20.04 LTS
+ Additional Software: openssh, firewall (ufw/firewalld)


 C. Installation Process
 ---

 1. Step-by-Step Installation

 + Download Ubuntu Server 20.04 LTS
Visit the official Ubuntu website (https://ubuntu.com/download/server) and download the latest LTS version.

 + Create Bootable USB
Use a tool like Rufus or dd to create a bootable USB drive with the Ubuntu Server ISO.

 + Install Ubuntu Server
Boot from the USB and follow on-screen instructions. Choose LAMP server during package selection.

3. Configuration Options

 + Partitioning
Allocate partitions for root (/), swap, and home. Use ext4 file system for root and home.

 + Network Configuration
Set a static IP address, subnet mask, and gateway during installation.


 D. Post-Installation Tasks
 ---

 1. Update and Upgrade
Once the installation is complete, run the following commands:
sudo apt update
sudo apt upgrade

 2. User and Group Management

 + Create User: add flags to create home directory for user, default shell as bash and added to sudoers group
sudo useradd -m -s /bin/bash -G sudo username

 4. Security Measures
    
 + Firewall Configuration
sudo ufw allow OpenSSH
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable

 + SSH Access Controls
Configure ssh to allow key-based authentication.

 6. Network Configuration
Edit /etc/netplan/01-network-manager-all.yaml to configure static IP, subnet mask, and gateway.


 E. System Monitoring and Maintenance
 ---

 1. Logging and Monitoring
    
 + View System Logs
execute the following command:
sudo journalctl -xe
Alternatively, configure rsyslog to centralize logs, or install and configure tools such as Prometheus, Grafana.

 3. Backup and Restore Procedures
    
 + Backup Strategy
Use tools like rsync or tar to create regular backups of important data.

 + Backup Procedure
sudo tar czvf backup.tar.gz /path/to/backup

 + Restore Procedure
sudo tar xzvf backup.tar.gz -C /


 F. Troubleshooting
 ---

 1. Common Issues
    
 + Boot Failure
Ensure correct boot device order in BIOS/UEFI settings.

 + Network Connectivity
Check network cable connections and verify static IP settings.

 3. Logs and Diagnostics
    
 + System Logs
Analyse logs by reviewing the /var/log/syslog file and /var/log/nginx/error.log for troubleshooting.

