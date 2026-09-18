# KB-005: Print Spooler Troubleshooting

**Applies to:** Windows workstations experiencing print jobs stuck in queue or a printer showing offline

## Symptom

Print jobs sit in the queue without processing, and the printer shows as offline even though it's powered on and other users can print to it fine.

## Cause

The print spooler service on the affected workstation has hung or crashed. This is a local issue, not usually a problem with the printer or network itself, which is why other users aren't affected.

## Resolution Steps

1. Verify the requester's identity before remoting into their machine.
2. Confirm whether other users on the same printer are affected. If not, this points to the individual workstation rather than the printer or network.
3. On the affected machine, open Services and locate Print Spooler.
4. Restart the service. If it won't restart cleanly, stop it, clear any stuck jobs from the spooler folder, then start it again.
5. Confirm with the user that printing works before closing the ticket.

## Notes

If the same user's spooler keeps hanging repeatedly, it may be worth checking for a specific stuck job or driver issue causing it, rather than just restarting the service each time.
