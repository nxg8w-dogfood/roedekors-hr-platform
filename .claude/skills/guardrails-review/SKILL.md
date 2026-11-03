---
name: guardrails-review
description: Review a change against this project's security requirements and guardrails before a human looks at it. Use before opening or updating a pull request.
---

# Guardrails review

Review the current diff (`git diff main...HEAD`) against every item below. For each, answer **pass**, **fail** (with file and line) or **not affected**. Finish with the fails first.


## Security requirements

- **Multi-factor authentication for all human access** — Everyone who can reach the data signs in with MFA — including administrators reaching production out of hours.
- **Encryption at rest with a managed key** — Storage, database and backups are encrypted. Key rotation is configured rather than assumed.
- **Record of processing and a lawful basis** — The processing is written into the record of processing activities with a named lawful basis, before the first real record is stored.
- **Data subject requests can actually be served** — Export and erasure work end to end, including backups and logs. A request you cannot fulfil is a breach waiting to be reported.
- **Retention period set and enforced automatically** — Personal data is deleted on a schedule, by a job, not by someone remembering.
- **Explicit consent and separated storage for special-category data** — Special-category data is held apart from ordinary personal data, with its own access control and its own audit trail.
- **Audit log of who read personal data, kept 12 months** — Read access is logged, not just writes, and the log is queryable when someone asks who looked at their record.
- **Threat model agreed before the first release** — One session, written down: what an attacker would want, how they would try, and what stops them. Revisited when the architecture changes.
- **Secrets in Key Vault, never in the repository** — Connection strings, keys and certificates live in Key Vault or environment configuration, injected at deploy time. The repository is scanned and the scan blocks the merge.
- **TLS 1.2 or better on every hop** — No plaintext anywhere, including between internal services. HTTP redirects to HTTPS and HSTS is set.
- **Authorisation enforced on the server** — Every request re-checks what the caller is allowed to do. Hiding a button in the UI is presentation, never protection.
- **Dependencies patched inside the agreed window** — Automated scanning on a schedule, with known-vulnerable versions upgraded before the window closes.

## Guardrails

- **README with run instructions** — Every repository opens with a README that states what the project is, how to run it locally, and how to deploy it. A newcomer should be productive without asking anyone.
- **Architecture decisions recorded** — Significant technical decisions are written down as short ADRs in docs/adr/, including the options rejected and why.
- **Automated tests run on every pull request** — A test suite exists and CI blocks a merge when it fails. Coverage targets are per-project; the non-negotiable part is that the suite runs unattended.
- **Protected default branch** — The default branch takes changes only through reviewed pull requests, with at least one approval and passing checks.
- **CI builds the project from a clean checkout** — The pipeline builds from nothing on every pull request. “Works on my machine” is not a build.
- **Deployment is automated per environment** — Every environment is deployed by the pipeline, with production behind an approval. Nobody deploys from a laptop.
- **No secrets in source control** — Secret scanning and push protection are on, and a leaked secret is rotated, not just deleted — git history keeps it.
- **Dependency and vulnerability scanning** — Dependabot (or equivalent) raises pull requests for vulnerable dependencies, and someone owns them.
- **Real code owners** — CODEOWNERS names people or teams who actually review, not a placeholder.
- **License and ownership declared** — The repository states its licence and the owning team, so nobody has to guess whether it may be reused.

Never approve: leave comments. A human approves.
