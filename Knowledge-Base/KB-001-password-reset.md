# KB-001: Password Reset Procedure

**Applies to:** All KCorp domain accounts (Active Directory / Entra ID)

## Symptom

User can't log in due to a forgotten or mistyped password. Account is not locked out.

## Cause

Usually just a forgotten password. Confirm the account isn't locked out first, since that's a different fix.

## Resolution Steps

1. Verify the requester's identity before touching the account (employee ID, department, or another agreed method). Never reset a password just because someone asked.
2. Confirm the account isn't locked out. If it is, follow the lockout procedure instead, a straight password reset won't fix that.
3. In Active Directory Users and Computers, find the account and select **Reset Password**.
4. Generate a temporary password and check **User must change password at next logon**.
5. Give the temporary password to the user through a verified channel, like a phone call, not by email or in the ticket itself.
6. Confirm the user can log in and sets a new permanent password.
7. Close the ticket once login is confirmed working.

## Notes

If someone needs their password reset repeatedly in a short window, it might be worth digging a little deeper, could be a forgotten password manager entry, or in rarer cases something worth escalating.
