<div align="center">
  
<img src="https://raw.githubusercontent.com/Hatemshalaby15071979/Helix-Solutions/main/assets/helix-solutions-logo.png" alt="Helix Solutions" width="72" height="72" style="margin-bottom:0.5rem">

# Work Samples

*Three self-contained exercises demonstrating the operations-to-software mapping.*

</div>

> Evidence before claims. Offline by default. A human is always in charge.

Each sample below is a complete, runnable unit — no dependencies, no cloud, no credentials.
The goal is to show how an operational question becomes a governed, inspectable piece of software.

## The samples

| Sample | What it shows | Run it |
|---|---|---|
| [`sql-work-sample`](sql-work-sample/) | A reconciliation query that fails closed when keys collide, with a hash-chained result pack | `cd sql-work-sample && python3 run.py` |
| [`rag-work-sample`](rag-work-sample/) | On-device retrieval with a deterministic confidence gate that escalates instead of guessing | `cd rag-work-sample && python3 run.py` |
| [`proposal-work-sample`](proposal-work-sample/) | A signed proposal builder that records every assumption before it renders | `cd proposal-work-sample && python3 run.py` |

## Operating principles

1. **Evidence before claims.** Every output carries the record that produced it. No result is trusted without its audit trail.
2. **Offline by default.** No network calls, no credentials, no external services. Everything runs on the machine it is written on.
3. **Human in the loop.** No output is final until a named human reviews and signs it.
4. **Honest about limits.** Where a sample uses synthetic data, it is labelled `simulated`. No production claim is made from a fixture.

## Licence

MIT
