# Changelog

All notable changes to Work Samples are recorded here.
Format follows [Keep a Changelog](https://keepachangelog.com/).

Repository history before 2026-11-27 is not reconstructed here: this file did not
exist, so the record of what changed and when lives in the git log.

## 2026-11-27

### Added

- `AGENTS.md` — agent charter and the sign-in/sign-out ledger.
- `CONSTITUTION.md` — the owner's engineering philosophy and clean-code policy, the
  same text as in every other repository in the portfolio.
- `GOVERNANCE.md` — repo map, documentation policy, sync policy and archiving rules.
- `SECURITY.md` — threat model and vulnerability reporting.
- `scripts/check_root_docs.py` — the root-document hygiene gate from `GOVERNANCE.md`
  section 2, checked in both directions (the documented root documents are present, and
  no unlisted `.md`/`.txt` sits at the root). Wired into CI, with a self-test that proves
  the gate fails closed.

### Changed

- `SHIPMENT_READINESS.md` moved to `docs/archive/SHIPMENT_READINESS.md` — a dated
  one-off report, per `GOVERNANCE.md` section 2.
