# KB-006: DNS Resolution Troubleshooting

**Applies to:** Workstations that can reach the general internet but can't access internal shares, tools, or other internal hostnames

## Symptom

General internet browsing works fine, but internal resources like shared drives or internal web tools fail to load or time out.

## Cause

Usually a DNS misconfiguration on the affected workstation, most often the DNS server setting pointing at a public resolver instead of the internal domain controller. Public DNS servers have no knowledge of internal domain names, so internal hostnames won't resolve even though general internet access is unaffected.

## Resolution Steps

1. Confirm the split symptom with the user: general internet works, internal resources don't. This narrows the problem toward DNS or internal routing rather than a full outage.
2. On the affected machine, run nslookup (or dig) against a known internal hostname, such as the domain controller.
3. A non-existent domain (NXDOMAIN) response confirms the query reached a DNS server but that server has no record of the internal name, consistent with the wrong DNS server being configured.
4. For deeper confirmation, a packet capture (Wireshark) can show the DNS query and NXDOMAIN response at the protocol level, useful when you want to rule out the request never leaving the machine at all.
5. Check the workstation's network adapter settings and confirm which DNS server is configured. If it's pointing at a public resolver instead of the internal domain controller, correct it.
6. Rerun nslookup to confirm the internal hostname now resolves.
7. Confirm with the user that internal resources are reachable again before closing the ticket.

## Notes

If this keeps happening across multiple machines rather than a single workstation, it's worth checking DHCP settings, since a wrong DNS server being handed out automatically would affect everyone rather than just one user.
