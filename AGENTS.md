# AGENTS.md — Agent Charter & Ledger for Work Samples

> **Read order (mandatory, every landing):** `AGENTS.md` → `CONSTITUTION.md` →
> `GOVERNANCE.md` → `README.md`. Then **sign in** to the ledger below, do the work,
> **sign out**. No entry, no trust: an unlogged session's work is treated as unverified
> until someone checks it.

## 1. Who agents are here

An "agent" is any entity that reads or writes this repository — an AI model, an
automation script, or a human acting as operator. There is exactly **one supreme
authority**: the repository owner (**Hatem Shalaby**). An agent acts only on the
owner's instruction and records every landing.

## 2. The mandatory sign-in / sign-out rule

Every agent, on **every landing** (a landing = one session that ends with the agent
stopping, whether the task is finished or not), must:

1. **SIGN IN** before any write action — who, why, what will be touched, sensitive or
   network actions planned, and the **date and time from the system clock**.
2. **SIGN OUT** when the landing's work is complete or stopped — what changed, why,
   the files touched, evidence of verification, and **the current status when leaving**,
   written so the next agent can continue without re-discovery.

Fail closed: if a task cannot be completed, still sign out and state exactly what is
incomplete. Never claim verification that did not happen.

### Entry format

```
## [YYYY-MM-DD HH:MM TZ] — <agent name / model>
Task: <what was assigned>
Touched: <files created / modified / deleted / moved>
Why: <the reasoning, not just the diff>
Verification: <what was actually checked and the observed result>
Left undone: <what is incomplete, needs review, or is deferred — or "nothing">
Sensitive: <any remote writes, secrets, or destructive actions, or "none">
```

## 3. Environment facts

- **Repo:** Work Samples — three self-contained exercises that show how an operational
  question becomes a governed, inspectable piece of software. There are no release tags.
- **Owner account:** https://github.com/Hatemshalaby15071979
- **Default branch:** main
- **Where it runs:** fully local. The samples make no network calls and hold no
  credentials; the retrieval sample's default generator is a deterministic mock, and the
  optional Ollama adapter is local. CI runs on GitHub Actions.
- **Verification commands:** the root-document gate is `python3 scripts/check_root_docs.py`
  (add `--self-test` to prove it fails closed). Per sample: `cd rag-work-sample && pytest -q`,
  `cd sql-work-sample && python3 run_checks.py`, and `cd rag-work-sample && python3 scripts/ci.py`
  for the CI-equivalent sweep.

## 4. Rules this agent must follow

- Read and obey **CONSTITUTION.md** (philosophy + clean-code policy). On conflict, it
  wins over this file.
- Follow **GOVERNANCE.md** for the repo map, documentation policy, and archiving rules.
- Keep `README.md` the single source of truth; landing pages and dashboards mirror it.
- Keep local and remote in harmony: after a sanctioned change, commit and push so the
  GitHub copy matches the working copy.
- Sign in and sign out every landing, with the real clock time.
- The samples are evidence, not marketing: no published number that this repository
  cannot re-run.

## 5. Ledger (sign-in / sign-out)

## [2026-11-27 04:55 EET] — sami (OpenMausBot), owner-authorised governance landing

STATUS: SIGN-IN (work in progress)

Task: Bring this repository onto the portfolio governance standard, as the owner approved in chat on 2026-11-27 ("bring the remaining eleven onto the same governance standard"). Add the missing root documents (AGENTS.md, CONSTITUTION.md, GOVERNANCE.md, CHANGELOG.md, SECURITY.md), move the one-off report out of the root, land the shared root-document gate and wire it into CI.

Touched: Will add `AGENTS.md`, `CHANGELOG.md`, `CONSTITUTION.md`, `GOVERNANCE.md`, `SECURITY.md`, `scripts/check_root_docs.py`; move `SHIPMENT_READINESS.md` to `docs/archive/`; add one job to `.github/workflows/ci.yml`. Nothing is deleted.

Why: This repository had a logo, a README and a product, but no written policy: no CONSTITUTION.md, no GOVERNANCE.md, no agent ledger, and no SECURITY.md, and a dated shipment report sat at the root. The other five governance repositories now enforce one rule — root holds only the documented set — through one shared gate; this repository had neither the rule nor the gate.

Verification: Planned — `python3 scripts/check_root_docs.py` and `--self-test` locally, then the three samples' own checks, then the GitHub Actions run on the landing commit.

Left undone: Nothing at sign-in.

Sensitive: `git push origin main` (owner's instruction in chat, 2026-11-27). No force push, no history rewrite, no secrets.
