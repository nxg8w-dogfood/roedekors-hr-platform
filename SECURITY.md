# Security — Rødekors HR Platform

## Reporting a vulnerability

Do not open a public issue. Report it privately through GitHub's *Report a vulnerability* (Security tab) or directly to the owning team. You will get an answer within two working days.

## Security profile

Level: **Elevated**

| Question | Answer |
| --- | --- |
| Data classification | confidential |
| Personal data | sensitive |
| Exposure | internal |
| Authentication | entra |
| Compliance | GDPR |

## Requirements

- **Multi-factor authentication for all human access** (applies because of confidential data)  
  Everyone who can reach the data signs in with MFA — including administrators reaching production out of hours.
- **Encryption at rest with a managed key** (applies because of confidential data)  
  Storage, database and backups are encrypted. Key rotation is configured rather than assumed.
- **Record of processing and a lawful basis** (applies because of special-category personal data, GDPR)  
  The processing is written into the record of processing activities with a named lawful basis, before the first real record is stored.
- **Data subject requests can actually be served** (applies because of special-category personal data)  
  Export and erasure work end to end, including backups and logs. A request you cannot fulfil is a breach waiting to be reported.
- **Retention period set and enforced automatically** (applies because of special-category personal data)  
  Personal data is deleted on a schedule, by a job, not by someone remembering.
- **Explicit consent and separated storage for special-category data** (applies because of special-category personal data)  
  Special-category data is held apart from ordinary personal data, with its own access control and its own audit trail.
- **Audit log of who read personal data, kept 12 months** (applies because of special-category personal data)  
  Read access is logged, not just writes, and the log is queryable when someone asks who looked at their record.
- **Threat model agreed before the first release** (applies because of confidential data)  
  One session, written down: what an attacker would want, how they would try, and what stops them. Revisited when the architecture changes.
- **Secrets in Key Vault, never in the repository** (baseline — applies to every project)  
  Connection strings, keys and certificates live in Key Vault or environment configuration, injected at deploy time. The repository is scanned and the scan blocks the merge.
- **TLS 1.2 or better on every hop** (baseline — applies to every project)  
  No plaintext anywhere, including between internal services. HTTP redirects to HTTPS and HSTS is set.
- **Authorisation enforced on the server** (baseline — applies to every project)  
  Every request re-checks what the caller is allowed to do. Hiding a button in the UI is presentation, never protection.
- **Dependencies patched inside the agreed window** (baseline — applies to every project)  
  Automated scanning on a schedule, with known-vulnerable versions upgraded before the window closes.
