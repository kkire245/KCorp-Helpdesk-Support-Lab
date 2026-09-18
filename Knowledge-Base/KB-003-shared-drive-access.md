# KB-003: Shared Drive Access Procedure

**Applies to:** Department shared folders controlled by security group membership

## Symptom

User can access their normal files but gets a permissions error trying to open a specific shared folder that coworkers in the same role or team can access fine.

## Cause

Usually a missing security group membership, often from a role change, a new project assignment, or a team move where the access change wasn't part of the original request.

## Resolution Steps

1. Verify the requester's identity and current role before changing any access.
2. Confirm which folder they're trying to reach and which security group controls it.
3. Check the user's current group memberships against that group.
4. If missing, add them to the correct group.
5. Ask the user to confirm access is working before closing the ticket. Group membership changes can take a few minutes to apply, so don't close immediately without confirmation.

## Notes

If a user is missing access to several folders at once, or the same issue keeps happening after role changes, it might be worth flagging to whoever manages onboarding/role-change checklists, since it points to a step being skipped upstream rather than a one-off mistake.
