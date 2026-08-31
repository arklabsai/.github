# Security policy

## Reporting a vulnerability

**Please do not open a public issue.** An issue is the wrong place for an unpatched
weakness.

Use GitHub's **private vulnerability reporting**: open the Security tab on this
repository and choose *Report a vulnerability*. The report is visible only to us, and it
gives us a private thread to work in with you.

Tell us what you found, how to reproduce it, and what you believe it exposes. You will get
an acknowledgement within one Australian business day. If you do not hear back, assume the
message was missed and follow up on the same thread.

We will tell you what we intend to do and roughly when. We ask that you give us a
reasonable chance to fix the issue before disclosing it publicly.

## Scope

In scope: repositories owned by this organisation and the services they deploy.

Out of scope: systems owned by our clients that we merely deploy to. If you have found
something there, please report it to that organisation directly.

## Credentials

If you believe a credential of ours has leaked, treat it as urgent and say so in the
subject line. We would rather revoke a live credential and cause ourselves an outage than
leave it working while we deliberate.

Every secret used by our systems is held in a secrets manager and read at runtime; none
are committed. Secret scanning and push protection are enabled on every repository as a
backstop, but the rule that matters is the human one: credentials do not go in git, and a
credential that reaches a commit is treated as compromised and rotated, not tidied away.

## What happens next

1. We acknowledge and agree a severity with you.
2. We contain first — revoke, disable, or take the surface offline — and fix second.
3. We record the incident internally, including what was exposed, for how long, and the
   change that stops it recurring.
4. If anyone else's data was in scope, we tell them. The bar for that is "might have been
   exposed", not "was definitely exposed".
