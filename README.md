# Work Samples

A small, honest set of working samples - reference material, not a shippable
product.

![Licence](https://img.shields.io/badge/licence-MIT-blue)

## One-line identity

Working samples kept together for reference: a proposal/estimate pack, a
retrieval-augmented generation (RAG) support-assistant sample, and Structured
Query Language (SQL) examples with expected outputs.
Each sub-directory is independent; there is no single installable package at this
level.

> **Operating principle.** These are reference samples, not a product. Treat each
> folder individually. Nothing here is production-deployed, externally audited,
> or revenue-generating - the same honest boundary as the rest of the portfolio.

## What's here

The following table summarizes each sample, what it contains, and its current
status.
The status column notes whether checks run in continuous integration (CI).

| Sample | What it is | Status |
| --- | --- | --- |
| `proposal-work-sample/` | Proposal, estimate, and client notes | Reference |
| `rag-work-sample/` | Python assistant, tests, and containers | Reference, CI-backed |
| `sql-work-sample/` | SQL examples, outputs, and check script | Reference |
| `tooling/` | Small helper scripts | Reference |

## How it fits the portfolio

These samples show how the work is done, not a shipped product. They share the
same author and evidence-first stance as the portfolio, but are independent
repositories: no shared codebase, data pipeline, or Helix Codex integration.

## Run it

Each sample runs on its own. See the README inside each sub-directory.

```bash
# RAG sample
cd rag-work-sample && python -m pip install -e '.[dev]' && pytest -q

# SQL sample
cd sql-work-sample && python run_checks.py
```

## Related work

- Portfolio and wider work: [Hatem Shalaby's portfolio on GitHub](https://github.com/Hatemshalaby15071979)

## Author

Built by Hatem Ismail Shalaby, Contact Centre Operations & AI
Implementation Lead | Workforce Management (WFM) & Customer Experience (CX)
Transformation.

Background: [Hatem Shalaby on GitHub](https://github.com/Hatemshalaby15071979)

## Licence

MIT. See `LICENSE`.
