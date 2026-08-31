# .github

Org-wide defaults for every repository in `github.com/arklabsai`.

GitHub falls back to this repository when a repo has no file of its own at the same path.
A repo that wants something different just adds its own — `arklabsai-infrastructure` does
exactly that with a pull request template covering plans, drift and vendor changes.

## What is here

| Path | Applies to |
|---|---|
| `SECURITY.md` | How to report a vulnerability |
| `.github/PULL_REQUEST_TEMPLATE.md` | Every PR in every repo without its own |
| `.github/ISSUE_TEMPLATE/` | New issues in every repo without its own |
| `templates/CODEOWNERS` | Copy into a new repo; not inherited (see below) |
| `profile/README.md` | The organisation profile page |

## Visibility matters

**This repository is private, and that is deliberate.** GitHub matches visibility when it
resolves default community health files: a private `.github` repo supplies defaults to
*private* repos. Every ArkLabs repo is private, so this is the correct setting. Making it
public would both leak our internal process and stop the defaults applying where we need
them.

## What is not inherited

`CODEOWNERS` is **not** a community health file and does not fall back here. Each repo
needs its own, which is why one lives in `templates/` to be copied. Nor are workflows —
the reusable deploy workflow lives in
[`arklabsai-infrastructure`](https://github.com/arklabsai/arklabsai-infrastructure) and is
called by path, not inherited.

## Branching

Two protected branches, matching every other repo: `master` (default) and `develop`.
Feature work squashes into `develop`; promotions to `master` use a merge commit.

Note that GitHub reads default community health files from the **default branch** only, so
a change here is not live until it reaches `master`.

## Source of truth

The estate, its vendors and the order things get built:
[`arklabsai-infrastructure`](https://github.com/arklabsai/arklabsai-infrastructure) —
`docs/INFRA_PLAN.md` for what and why, `docs/BUILD_PLAN.md` for how and in what order.
