# KCorp Helpdesk Support Lab

A self-hosted IT support ticketing project built around a fictional company, KCorp, to demonstrate ticket lifecycle management, troubleshooting methodology, and knowledge base documentation.

This is a companion project to my [KCorp Enterprise IAM Lab](https://github.com/kkire245/KCorp-Enterprise-Homelab), which covers identity infrastructure (Active Directory, Entra ID, hybrid identity). This repo focuses on the support side instead: how tickets get triaged, worked, and resolved, and how that work gets documented for reuse.

## What this demonstrates

- Full ticket lifecycle management (New → Assigned → In Progress → Resolved → Closed)
- Root cause analysis and documented troubleshooting steps
- Knowledge base article writing for recurring issues
- A working osTicket installation, self-hosted on its own Ubuntu Server VM
- A mix of fully reenacted, hands-on tickets and documented ticket write-ups against KCorp's existing 25-user roster across IT, HR, Finance, Sales, and Operations

## Environment

Self-hosted [osTicket](https://osticket.com/) running on a dedicated Ubuntu Server VM (KCorp-Helpdesk01), built on Hyper-V alongside the rest of the KCorp lab environment. Full setup process, stack details, and troubleshooting notes are in [`environment-setup.md`](./environment-setup.md).

## Tickets

10 tickets simulated against KCorp's existing employee roster. Four were worked end to end, meaning the actual fix was performed in the KCorp AD lab or on a workstation, not just written up. The other six are documented the way a real ticket would be recorded, without a live reenactment behind them.

| Ticket ID | Title | Requester | Priority | Type |
|---|---|---|---|---|
| [TICKET-001](Tickets/TICKET-001-password-reset.md) | Password Reset | Grace Liu | Normal | Full end to end |
| [TICKET-002](Tickets/TICKET-002-account-lockout.md) | Account Locked Out | Kevin Park | High | Full end to end |
| [TICKET-003](Tickets/TICKET-003-shared-drive-access.md) | Unable to Access Shared Finance Folder | Sofia Moretti | Normal | Documentation |
| [TICKET-004](Tickets/TICKET-004-software-installation.md) | PDF Reader Installation Request | Michael Kaiser | Normal | Full end to end |
| [TICKET-005](Tickets/TICKET-005-printer-not-working.md) | Printer Not Working | Daniel Osei | Normal | Documentation |
| [TICKET-006](Tickets/TICKET-006-network-connectivity.md) | Unable to Reach Internal Shares and Tools | Teddy Knight | Normal | Full end to end |
| [TICKET-007](Tickets/TICKET-007-slow-computer.md) | Computer Running Slow | Camille Fontaine | Normal | Documentation |
| [TICKET-008](Tickets/TICKET-008-outlook-not-working.md) | Outlook Not Sending or Receiving Email | Natalie Brooks | Normal | Documentation |
| [TICKET-009](Tickets/TICKET-009-vpn-connection-failure.md) | VPN Connection Failure | Hassan Ali | Normal | Documentation |
| [TICKET-010](Tickets/TICKET-010-monitor-not-detected.md) | External Monitor Not Detected | Vivian Hugo | Normal | Documentation |

## Knowledge Base

Reusable KB articles referenced by the tickets above, one per ticket type.

| KB ID | Title |
|---|---|
| [KB-001](Knowledge-Base/KB-001-password-reset.md) | Password Reset Procedure |
| [KB-002](Knowledge-Base/KB-002-account-lockout.md) | Account Lockout Procedure |
| [KB-003](Knowledge-Base/KB-003-shared-drive-access.md) | Shared Drive Access Procedure |
| [KB-004](Knowledge-Base/KB-004-software-installation.md) | Software Installation Requests |
| [KB-005](Knowledge-Base/KB-005-printer-troubleshooting.md) | Print Spooler Troubleshooting |
| [KB-006](Knowledge-Base/KB-006-dns-troubleshooting.md) | DNS Resolution Troubleshooting |
| [KB-007](Knowledge-Base/KB-007-slow-computer.md) | Slow Computer Troubleshooting |
| [KB-008](Knowledge-Base/KB-008-outlook-connection.md) | Outlook Connection Issues |
| [KB-009](Knowledge-Base/KB-009-vpn-troubleshooting.md) | VPN Connection Troubleshooting |
| [KB-010](Knowledge-Base/KB-010-monitor-not-detected.md) | External Monitor Not Detected |

## Repo Structure

```
KCorp-Helpdesk-Support-Lab/
├── README.md
├── environment-setup.md
├── Tickets/
├── Knowledge-Base/
└── Screenshots/
    ├── Setup/
    └── Tickets/
        ├── Ticket1/
        ├── Ticket2/
        └── ...
```
