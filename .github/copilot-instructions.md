# Copilot instructions — Rødekors HR Platform

No description yet.

Follow the project brief in `AGENTS.md`. In short:

- Never suggest secrets, keys or personal data in code or config.
- Enforce authorisation on the server.
- Suggest tests with every change.
- Multi-factor authentication for all human access.
- Encryption at rest with a managed key.
- Record of processing and a lawful basis.
- Data subject requests can actually be served.
- Retention period set and enforced automatically.
- Explicit consent and separated storage for special-category data.
- Audit log of who read personal data, kept 12 months.
- Threat model agreed before the first release.
- Secrets in Key Vault, never in the repository.
- TLS 1.2 or better on every hop.
- Authorisation enforced on the server.
- Dependencies patched inside the agreed window.
- README with run instructions.
- Architecture decisions recorded.
- Automated tests run on every pull request.
- Protected default branch.
- CI builds the project from a clean checkout.
- Deployment is automated per environment.
- No secrets in source control.
- Dependency and vulnerability scanning.
- Real code owners.
- License and ownership declared.
