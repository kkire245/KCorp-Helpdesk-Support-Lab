# KB-009: VPN Connection Troubleshooting

**Applies to:** Remote users unable to connect to the company VPN, especially with an authentication failure

## Symptom

User working remote gets an authentication failed error when trying to connect to the VPN, despite entering the correct credentials.

## Cause

A few common causes: an expired authentication certificate, a cached expired credential (especially after a recent password change), or an outdated VPN client version. Worth checking each rather than assuming the first one found.

## Resolution Steps

1. Verify the user's identity, typically by phone since they're remote and not available for in-person verification.
2. Ask when the issue started and whether anything changed recently on their end.
3. Check the VPN client's certificate status. If expired, issue a new certificate and push it to the client.
4. If the certificate is valid, check for a cached credential issue, particularly if the user changed their password recently.
5. If neither applies, confirm the VPN client is on a supported version and update if needed.
6. Confirm with the user that they can connect successfully before closing the ticket.

## Notes

If several users report VPN authentication failures around the same time, it's worth checking whether a certificate authority or VPN server-side issue is affecting multiple people at once, rather than troubleshooting each one individually as isolated cases.
