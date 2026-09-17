# Environment Setup — KCorp Helpdesk Support Lab

## Overview
This covers the setup of the environment behind the KCorp IT Support ticketing lab: a self-hosted osTicket instance running on its own Ubuntu Server VM. It's a standalone project alongside the KCorp Enterprise IAM Lab, focused on ticket lifecycle and support methodology rather than infrastructure.

## Environment

| Component | Detail |
|---|---|
| Hypervisor | Hyper-V (host: Windows 11 Education, 32GB RAM) |
| VM Name | KCorp-Helpdesk01 |
| OS | Ubuntu Server 26.04.1 LTS |
| vCPU | 2 |
| RAM | 6144 MB static (see Troubleshooting for why) |
| Disk | 40GB |
| Web Stack | Apache2, MySQL, PHP 8.5 |
| Application | osTicket v1.18.4 |

## Stack Installed

- **Apache2** for the web server
- **MySQL** for the database backend
- **PHP 8.5** with the extensions osTicket needs: `php8.5-mysql`, `php-gd`, `php-intl`, `php-apcu`, `php-xml`, `php-mbstring`
  - `php-imap` wasn't available as a packaged build for PHP 8.5 at the time of install. This extension only supports osTicket's email piping feature (auto-creating tickets from a monitored inbox), which isn't part of this project since tickets are manually simulated. I left it out with no real impact.

## Install Steps

1. Created the KCorp-Helpdesk01 VM in Hyper-V running Ubuntu Server 26.04.1 LTS
   `![VM created in Hyper-V](Screenshots/Setup/01-hyperv-vm-created.png)`
2. Installed Ubuntu Server, enabling OpenSSH during setup for remote CLI access
   `![Network config during install](Screenshots/Setup/02a-ubuntu-network-config.png)`
   `![SSH server enabled](Screenshots/Setup/02b-ubuntu-ssh-enabled.png)`
   `![Install complete](Screenshots/Setup/02c-ubuntu-install-complete.png)`
3. SSH'd into the VM from the host machine and confirmed access
   `![Successful SSH login](Screenshots/Setup/03-ssh-login-success.png)`
4. Updated system packages and installed Apache, MySQL, and the PHP extensions above
   `![LAMP versions confirmed](Screenshots/Setup/04-lamp-versions-confirmed.png)`
5. Created a dedicated MySQL database (`osticket`) and a dedicated, least-privilege MySQL user rather than using root, scoped to localhost only
   `![MySQL database and user created](Screenshots/Setup/05-mysql-db-user-created.png)`
6. Downloaded osTicket v1.18.4 from the official GitHub releases page, extracted it, and placed it into `/var/www/html/osticket/`
   `![osTicket files placed](Screenshots/Setup/06-osticket-files-directory.png)`
7. Renamed the sample config file to `ost-config.php`, made it temporarily writable for the installer, and set ownership of the whole directory to `www-data` so Apache could serve and write to it correctly
8. Ran the osTicket web installer from a browser on the host machine, pointed at the VM's local IP. All required checks passed on the requirements screen. PHP IMAP (recommended, not required) was the only unchecked item, consistent with the omission noted above
   `![Installer requirements check](Screenshots/Setup/07a-installer-requirements-check.png)`
9. Filled out System Settings, Admin User, and Database Settings in the installer
   `![Installer system settings filled out](Screenshots/Setup/07b-installer-system-settings.png)`
10. Installer completed successfully
    `![Installer success](Screenshots/Setup/07c-installer-success.png)`
11. Reverted `ost-config.php` back to non-writable and removed the `/setup` directory so it couldn't be reached again
12. Confirmed both the staff control panel and the public ticket portal loaded and worked
    `![Staff panel dashboard](Screenshots/Setup/08a-staff-panel-dashboard.png)`
    `![Customer ticket portal](Screenshots/Setup/08b-customer-portal-landing.png)`

## Troubleshooting Findings

**Secure Boot template mismatch (VM wouldn't boot from ISO)**
On the first boot, Hyper-V threw "The signed image's hash is not allowed (DB)" and failed to load Ubuntu from the ISO. Hyper-V's default Secure Boot template ("Microsoft Windows") rejects Ubuntu's boot signature. It was fixed by switching the VM's Secure Boot template (Settings → Security) to "Microsoft UEFI Certificate Authority," which Ubuntu's installer is actually signed against.

**Out-of-memory kernel panic during package installs**
Partway through the LAMP install, the VM ran out of memory, the kernel started killing processes, and it eventually deadlocked. The VM's initial memory allocation wasn't enough for Apache, MySQL, and PHP running together. I bumped the Dynamic Memory minimum to 2048MB, which got past the install.

**A second OOM crash under live load**
Once Apache, MySQL, and PHP were all active at the same time handling a browser request to the osTicket installer, the VM ran out of memory again (systemd and mysqld got killed). 2048MB was enough for installing packages but not enough for actually running the stack under load. I fixed it by switching from Dynamic Memory to a static allocation: 6144MB startup, 4096MB minimum. This also pointed to a bigger consideration: running several KCorp lab VMs on the same host at once competes for the same physical RAM pool, so only the VM actually being worked on should stay powered on.

## Security Notes

- Used a dedicated, least-privilege MySQL user for osTicket instead of the root MySQL account
- Locked config file permissions back down (644) after install instead of leaving it world-writable
- Removed the installer's `/setup` directory after completion so it can't be reconfigured by anyone who finds the URL
- All IP addresses referenced are private/internal (Hyper-V's local network), not exposed externally

## Result

A working, self-hosted osTicket instance reachable through both the staff control panel and the public ticket-submission portal, running on its own VM inside the existing KCorp lab environment. It is ready for department and category configuration, then ticket simulation against the KCorp employee roster.
