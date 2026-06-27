# Event-to-Control Mapping

**Company:** NimbusLedger (fictional fintech SaaS)
**SIEM:** Splunk Cloud
**Last updated:** 2026-06-27

## How to read this table

Each row is one security event type that NimbusLedger's SIEM detects.
Each event maps to:
- The Sigma rule that detects it (to be built in /sigma-rules)
- The SOC 2 TSC criterion it satisfies
- The ISO 27001:2022 Annex A control it satisfies
- The evidence template it generates (to be built in /evidence-templates)

---

## Mapping table

| # | Event Type | Sigma Rule (planned) | SOC 2 TSC | ISO 27001 Control | Evidence Template |
|---|------------|---------------------|-----------|-------------------|-------------------|
| 1 | Failed authentication — 5+ attempts in 10 min | failed_auth_brute_force.yml | CC6.1 — Logical access controls | A.8.3 — Information access restriction | auth_failure_evidence.md |
| 2 | Privileged account login outside business hours | privileged_login_offhours.yml | CC6.3 — Role-based access | A.8.2 — Privileged access rights | privileged_login_evidence.md |
| 3 | IAM policy change / privilege escalation | iam_policy_change.yml | CC6.3 — Role-based access | A.8.2 — Privileged access rights | iam_change_evidence.md |
| 4 | Large data transfer / potential exfiltration | data_exfil_signal.yml | CC6.7 — Data transmission controls | A.8.12 — Data leakage prevention | exfil_signal_evidence.md |
| 5 | S3 bucket policy made public | s3_public_exposure.yml | CC6.7 — Data transmission controls | A.8.10 — Information deletion | s3_exposure_evidence.md |
| 6 | CloudTrail logging disabled or modified | cloudtrail_tamper.yml | CC7.2 — System monitoring | A.8.15 — Logging | cloudtrail_tamper_evidence.md |
| 7 | New admin user created outside change window | admin_user_created.yml | CC6.2 — New user provisioning | A.5.18 — Access rights | admin_creation_evidence.md |

---

## SOC 2 TSC reference (criteria used above)

| Criterion | Name | Plain meaning |
|-----------|------|---------------|
| CC6.1 | Logical Access Controls | Only authorized users can access systems |
| CC6.2 | New User Provisioning | New accounts are created through an approved process |
| CC6.3 | Role-Based Access | Access is granted based on job role, reviewed regularly |
| CC6.7 | Data Transmission | Sensitive data is protected in transit and at rest |
| CC7.2 | System Monitoring | Security events are detected and monitored |

---

## ISO 27001:2022 Annex A reference (controls used above)

| Control | Name | Plain meaning |
|---------|------|---------------|
| A.5.18 | Access Rights | Access rights are provisioned, reviewed, and revoked |
| A.8.2 | Privileged Access Rights | Admin/privileged access is tightly controlled |
| A.8.3 | Information Access Restriction | Access to systems and data is restricted by need |
| A.8.10 | Information Deletion | Data is deleted when no longer needed |
| A.8.12 | Data Leakage Prevention | Controls prevent unauthorized data egress |
| A.8.15 | Logging | Events are logged, protected, and reviewed |
