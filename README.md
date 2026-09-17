# KCorp Helpdesk Support Lab

A self-hosted IT support ticketing project built around a fictional company, KCorp, to demonstrate ticket lifecycle management, troubleshooting methodology, and knowledge base documentation.

This is a companion project to my [KCorp Enterprise IAM Lab](https://github.com/kkire245/KCorp-Enterprise-Homelab), which covers identity infrastructure (Active Directory, Entra ID, hybrid identity). This repo focuses on the support side instead: how tickets get triaged, worked, and resolved, and how that work gets documented for reuse.

## What this project covers

- A working osTicket installation, self-hosted on its own Ubuntu Server VM
- Simulated support tickets against KCorp's existing 25-user roster across IT, HR, Finance, Sales, and Operations
- Full ticket lifecycle tracking (New, Assigned, In Progress, Pending, Resolved, Closed)
- Root cause analysis and resolution steps for each ticket
- A small knowledge base of reusable troubleshooting articles

## Status

Environment setup is complete. Ticket simulation is in progress.

## Structure

```
KCorp-Helpdesk-Support-Lab/
├── environment-setup.md      # VM/stack setup, install steps, troubleshooting notes
├── tickets/                  # Individual ticket write-ups
├── knowledge-base/           # Reusable KB articles referenced by tickets
└── screenshots/
    ├── setup/                # Screenshots from the environment build
    └── tickets/               # Screenshots from ticket work
```

## Environment

- Ubuntu Server 26.04.1 LTS, hosted on Hyper-V
- Apache, MySQL, PHP 8.5
- osTicket v1.18.4

See [environment-setup.md](environment-setup.md) for the full build process, including issues hit along the way and how they were resolved.

## Tickets

Ticket table will go here once all 10 are complete.
