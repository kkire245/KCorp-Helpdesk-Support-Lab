# KB-002: Account Lockout Procedure

**Applies to:** All KCorp domain accounts (Active Directory)

## Symptom

User can't log in and is shown a message that the account is locked out, different from a plain incorrect-password error.

## Cause

Usually repeated failed login attempts, often from a mistyped or recently changed password. Can occasionally point to something more concerning if the pattern looks unusual (attempts outside the user's normal hours, attempts from an unfamiliar device or location).

## Resolution Steps

1. Verify the requester's identity before touching the account.
2. Ask what led up to the lockout. Most of the time it's a simple mistyped password, but this step matters for ruling out anything suspicious.
3. In Active Directory Users and Computers, open the account's Account tab and check for the "Unlock account" option, this only appears once an account is actually locked out.
4. Unlock the account.
5. Confirm the user can actually log back in. Don't close the ticket on the AD change alone, verify it worked.
6. If the user isn't confident in their current password, offer a reset at the same time rather than making them submit a second ticket.
7. Close the ticket once login is confirmed.

## Notes

If lockouts are happening repeatedly for the same user in a short window, or attempts are showing up at odd hours, it's worth escalating rather than treating it as routine.
