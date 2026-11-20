# Work Samples - GitHub shipment readiness

**Assessment date:** 2026-11-20
**Branch:** `main`
**Verified commit:** `fbd9eaa2348e4781a5b5dbeb248dcf2d6963fbd6` (`fbd9eaa`)
**Remote:** `https://github.com/Hatemshalaby15071979/work-samples.git`
**Pushed:** 2026-11-20, `c10955a939a1c5918cb2ada57273654051535e4c` (`c10955a`),
after Hatem's explicit authorization. `main` tracks `origin/main`.
**Working tree:** clean.

This records local repository, CI-equivalent, evaluation, container, and secret
checks, plus the completed push. No release, deployment, or external write beyond
the push was performed.

## Weak results and open gaps (read first)

1. **SSH authentication to GitHub does not work here.** Both local keys were
   rejected with `Permission denied (publickey)`. The push was made over HTTPS
   using the authenticated `gh` credential helper, and `origin` was switched from
   SSH to HTTPS (a reversible local config change). To restore SSH pushes, add a
   public key to the GitHub account.
2. **GitHub-hosted CI was not observed.** Every check below was run locally with
   the same versions the workflow pins. A hosted run cannot be claimed from a
   local result.
3. **The Ollama adapter remains unverified end to end.** Its error and timeout
   paths are covered by tests; no generation was observed to complete. The default
   mock generator is the only one used by the committed evaluation report.
4. **The project's own stated limits still apply:** thresholds were fitted on the
   test set, there is no held-out set, no authentication or rate limiting, no
   load test, and no external audit. These are documented in
   `rag-work-sample/README.md` and are not shipment gates being waived here.
5. **The secret scan is pattern-based.** A clean scan of 23 commits and 69 tracked
   files is evidence, not proof that no credential ever existed.

## Verification

| Check | Command (from `rag-work-sample/` unless noted) | Result |
| --- | --- | --- |
| Format | `ruff format --check --diff .` | PASS - 23 files already formatted |
| Lint | `ruff check .` | PASS - no findings |
| Types | `mypy src --ignore-missing-imports` | PASS - 10 source files |
| Tests | `pytest` | **106 passed** |
| Evaluation | `python run_eval.py` | PASS - report matches `expected/eval_report.txt`, latency excluded |
| Container build | `docker build -t support-assistant-work-sample:ci .` | PASS |
| Container health | `docker run -p 8080:8080 ...` + `curl /health` | PASS - `{"status":"ok"}` |
| SQL checks (from `sql-work-sample/`) | `python run_checks.py` | **8/8 PASS** |
| Local CI runner | `python scripts/ci.py` | **6/6 steps passed** |

**CI-version fidelity.** The checks above were re-run in a clean Python 3.13.16
virtual environment with the workflow's pins (`ruff==0.16.1`, `pytest>=8`,
`anyio>=4`, `mypy>=1.10`, `requirements.txt`): format, lint, typecheck, tests,
and evaluation all passed (5/5 non-Docker steps). The evaluation job was also run
in a second clean environment with **only** `requirements.txt` installed, matching
that job's dependency step: PASS. The same checks passed on Python 3.14.4 with
ruff 0.16.1 and 0.17.3.

## Secret and hygiene scan

- `git ls-files` filtered for `.env`, `*.pem`, `*.key`, `*credentials*`,
  `*secret*`, `*token*`: **0 files** among 69 tracked files.
- `git grep` over the working tree for AWS keys, OpenAI/GitHub tokens, and private
  key headers: **0 hits**.
- Same pattern set over all commits reachable from `git rev-list --all` (23
  commits): **0 files**.
- Caches (`__pycache__/`, `.pytest_cache/`, `.mypy_cache/`, `.ruff_cache/`) and
  generated databases are ignored and were not staged.

## CI workflow review

`.github/workflows/ci.yml` is mirrored by `scripts/ci.py`: format, lint, typecheck,
tests, evaluation, container build. The workflow has `contents: read` only, no
registry login, no secret, and no deploy step. The container job builds and runs a
local health check, then removes the container with `if: always()`.

## Shipment report

- **DID:** Completed and committed the pending hardening pass at `fbd9eaa` - safe
  local bind default, generator-failure escalation, HTTP body-drain guard, pinned
  dev tools, accurate test counts, filled MIT holders, screen-reader-friendly docs.
  Added this readiness record, then pushed `main` to `origin` with Hatem's explicit
  authorization and corrected this file to match the shipped state.
- **PROVED:** 6/6 local CI steps, 8/8 SQL checks, 106 tests, zero secret-pattern
  hits in 69 tracked files across 23 commits. Remote `refs/heads/main` and local
  `HEAD` both read `c10955a939a1c5918cb2ada57273654051535e4c`.
- **NOT DONE:** No hosted CI result confirmed; no cloud deployment; no external
  audit; no end-to-end Ollama generation. SSH push remains unavailable.
- **RISK:** Hidden CI-only failure is unlikely but not disproven; the adapter is
  unproven end to end; the evaluation's fitted thresholds limit how far the numbers
  generalise.
- **DECIDE:** No push decision is pending - it was authorized and completed. The
  only optional decision is whether to register an SSH key with GitHub.
- **NEXT:** Check the hosted CI run on GitHub for commit `c10955a`. If SSH pushes
  are wanted, add the public key from `~/.ssh/id_ed25519.pub` to the GitHub account
  and restore the SSH remote URL.
