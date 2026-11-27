# Security Policy

Work Samples is a set of three offline exercises. Each sample runs on the machine it is
written on: no network calls, no credentials, no external services, and no data leaving
the machine. The samples are demonstrations, not a deployed service, and they are not
offered for production use.

## Supported versions

| Version | Supported |
| ------- | --------- |
| `main`  | Yes — the samples are developed on `main` only. There are no release tags. |

## What is in scope

- Any code path in this repository that reaches the network, reads a credential, or
  writes outside its own sample directory.
- Anything that would cause real customer or personal data to be committed.

## Reporting a vulnerability

**Reporting contact: to be set by the owner.** There is no monitored security mailbox or
private reporting channel in this repository yet; do not send vulnerability reports to
any address guessed from this file.

Until the owner publishes a contact channel:

1. Do not open a public issue containing exploit details.
2. Do not include real client data, credentials, or personal data in any report.
3. The owner will add a private reporting channel (for example GitHub Private
   Vulnerability Reporting) and this section will name it.

## Secret handling

No credentials, tokens, or API keys belong in this tree. The samples are built to need
none: the retrieval sample's default generator is a deterministic mock, and the Ollama
adapter is optional and local. If you find a secret in the repository, treat it as
compromised and rotate it rather than relying on the commit being removed.
