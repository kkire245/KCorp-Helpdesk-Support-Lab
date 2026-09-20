# KB-008: Outlook Connection Issues

**Applies to:** Outlook stuck on "Trying to connect" or failing to send/receive, while other network activity works normally

## Symptom

Outlook shows "Trying to connect" or similar at the bottom of the window and doesn't send or receive mail, but general internet and network access work fine.

## Cause

Often a stale cached credential, especially common right after a password change. Outlook can continue trying to authenticate with the old password without clearly prompting the user to re-enter it.

## Resolution Steps

1. Verify the user's identity before making any account changes.
2. Confirm general network and internet access are working, to rule out a broader connectivity issue.
3. Ask whether the user has changed their password recently. This is the most common trigger for this symptom.
4. Have the user sign out of Outlook completely and sign back in with their current password to refresh the cached credential.
5. Confirm email is sending and receiving normally before closing the ticket.

## Notes

If signing out and back in doesn't resolve it, the Outlook profile itself may need to be recreated, or there could be a broader account sync issue worth checking on the mail server side rather than the local client.
