# .github

Org-wide defaults for every repository in `github.com/arklabsai`.

GitHub falls back to this repository when a repo has no file of its own at the same path.
A repo that wants something different just adds its own, and several do.

## What is here

| Path | Applies to |
|---|---|
| `SECURITY.md` | How to report a vulnerability |
| `.github/PULL_REQUEST_TEMPLATE.md` | Every PR in every repo without its own |
| `.github/ISSUE_TEMPLATE/` | New issues in every repo without its own |
| `templates/CODEOWNERS` | Copy into a new repo; not inherited (see below) |
| `profile/README.md` | The public organisation profile page |

## This repository is public. It is the only one that is.

It has to be: GitHub's rule is that **"the `.github` repository must be public"** for
default community health files to resolve. A private one supplies nothing — which is what
this repo did for its first half hour, until that was checked rather than assumed.

A public `.github` repo does supply defaults to private repositories: *"GitHub will use and
display default files for any repository owned by the account, regardless of the
destination repository's visibility."* So every private ArkLabs repo inherits from here.

**Everything committed here is world-readable.** Keep it generic. No hostnames, no
infrastructure detail, no repository inventory, no process that describes how we actually
operate. Anything specific belongs in a private repo. If you would not put it on the
website, it does not go here.

## What is not inherited

`CODEOWNERS` is **not** a community health file and does not fall back here. Each repo
needs its own, which is why one lives in `templates/` to be copied. Nor are workflows: a
reusable workflow is called by path from the repo that owns it, not inherited.

## Branching

Two protected branches, matching every other repo: `master` (default) and `develop`.
Feature work squashes into `develop`; promotions to `master` use a merge commit.

Note that GitHub reads default community health files from the **default branch** only, so
a change here is not live until it reaches `master`.

## Source of truth

The estate, its vendors and the order things get built are documented in a private
repository. Deliberately not named or linked from here.
