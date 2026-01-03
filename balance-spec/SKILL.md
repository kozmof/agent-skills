---
name: Balance spec
description: Provide a specification on implementation
allowed-tools: Read, Grep, Glob
---

# Balance Spec

Balance Spec is a rule where you list what is permitted alongside what is prohibited.

Example: Login

CAN (OK):
- Users can register their email addresses.
- Users can log in using a password.
- The UI displays a notification if the user cannot log in due to an incorrect password.
- Users can change their passwords.

CAN'T (NG):
- Users cannot link multiple accounts to a single email address.
- Users cannot log in if the password and email address do not match.
- Users must not be able to identify whether the password or the email address is incorrect.
- Passwords cannot be changed other than through the email address linked to the account

## Instructions

1. Read the target files using Read tool
2. Search for patterns using Grep
3. Find related files using Glob
4. Provide detailed feedback on specification. Where a correlation exists between the "Can" and "Can't" items, report on that connection as well.
