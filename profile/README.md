# ArkLabs

Internal engineering. Everything the agency runs on lives in these repositories.

| Repo | What it is |
|---|---|
| [arklabsai-infrastructure](https://github.com/arklabsai/arklabsai-infrastructure) | The estate: Terraform, Ansible, runbooks, vendor register. Start here. |
| [arklabsai-os](https://github.com/arklabsai/arklabsai-os) | ArkLabs OS — the internal operating system. Owns the Postgres schema. |
| [arklabsai-data](https://github.com/arklabsai/arklabsai-data) | Everything that reads or writes the lakehouse. |

**New here?** Read `docs/INFRA_PLAN.md` in the infrastructure repo for what exists and why,
then `RUNBOOKS/onboard-offboard-person.md` for getting your access set up.

**Two rules worth knowing before your first commit.** No secret ever goes in git — every
credential comes from Doppler at runtime. And the boundary rule decides where code lives:
infrastructure provisions, `arklabsai-os` owns the Postgres schema, `arklabsai-data` owns
the lakehouse.
