# Security policy

ArkLabs repositories are private and internal. Everything here runs the agency itself —
client records, contracts, invoices and payment credentials — so a compromise is a client
problem, not only an inconvenience.

## Reporting a vulnerability

**Do not open an issue.** Issues are visible to everyone in the org and are not the place
for an unpatched weakness.

Email an organisation owner directly at their `@arklabsai.com` address. Say what you
found, how to reproduce it, and what you think it exposes. You will get an acknowledgement
the same working day; if you do not, assume the email was missed and follow up by phone.

> **TODO:** stand up a dedicated `security@arklabsai.com` alias routed to both owners, and
> replace this paragraph with it. A single owner's inbox is a single point of failure for
> the one message that must not be missed.

If you believe a credential has leaked, do not wait for a reply. Follow
[`RUNBOOKS/rotate-secret.md`](https://github.com/arklabsai/arklabsai-infrastructure/blob/master/RUNBOOKS/rotate-secret.md):
**revoke first, ask questions after.** A live leaked token is worse than the outage that
revoking it causes.

## Scope

In scope: anything under `github.com/arklabsai`, and the services it deploys —
`os.arklabsai.com`, `deploy.`, `llm.`, `trace.`, `sign.`

Out of scope: client-owned systems we merely deploy to. Report those to the client through
your engagement contact, not here.

## What we do about credentials in git

Secret scanning and push protection are enabled on every repository, so an obvious
credential is rejected at push time. They are a backstop, not a control — they only catch
patterns providers have published. The actual rule is simpler:

**No token, key, password or connection string goes in git.** Every secret is read from
Doppler at runtime. If you need one that does not exist, ask; do not inline it "for now".

A credential that reaches a commit is compromised even after a force-push, because it was
in the reflog, in CI logs, and possibly in someone's clone. Rotate it, do not tidy it away.

## Handling a report

1. Acknowledge, and agree a severity with the reporter.
2. Contain first — revoke, disable, or take the surface offline. Fix second.
3. Record it in `docs/incidents/` in the infrastructure repo: what was exposed, for how
   long, what could reach it, and the change that stops it recurring.
4. If client data was in scope, tell the client. That decision belongs to an owner, and
   the bar for telling them is "might have been exposed", not "was definitely exposed".
