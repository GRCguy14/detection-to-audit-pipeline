# Detection-to-Audit Pipeline

Security operations teams detect events. Compliance teams need evidence.
These two worlds rarely speak the same language.

This project bridges them.

The Detection-to-Audit Pipeline maps Sigma detection rules to SOC 2 TSC 
criteria and ISO 27001:2022 Annex A controls, then generates structured 
audit evidence templates for each event type. Built for a fictional fintech 
SaaS company (NimbusLedger) running Splunk Cloud.

---

## How it works
Security Event (in SIEM)
↓
Sigma Detection Rule (.yml)
↓
Event-to-Control Mapping
↓
SOC 2 TSC + ISO 27001 Control
↓
Audit Evidence Template (.md)

---

## Events covered

| Event | SOC 2 | ISO 27001 |
|-------|-------|-----------|
| Failed auth - brute force | CC6.1 | A.8.3 |
| Privileged login off-hours | CC6.3 | A.8.2 |
| IAM policy change | CC6.3 | A.8.2 |
| Large data transfer / exfil signal | CC6.7 | A.8.12 |
| S3 bucket made public | CC6.7 | A.8.10 |
| CloudTrail logging disabled | CC7.2 | A.8.15 |
| New admin user created | CC6.2 | A.5.18 |

---

## Repo structure

```
detection-to-audit-pipeline/
│
├── sigma-rules/
│   └── README.md
│
├── evidence-templates/
│   └── README.md
│
├── mappings/
│   └── README.md
│
├── docs/
│   ├── scenario.md
│   └── README.md
│
└── scripts/
    └── README.md
```
---

## Fictional company

**NimbusLedger** - B2B fintech SaaS, 80 employees, AWS-hosted, Splunk Cloud 
SIEM, SOC 2 Type II audit in progress.
Full profile: [TIRR project](https://github.com/GRCguy14/threat-informed-risk-register/blob/main/docs/company-profile.md)

---

## Frameworks

| Framework | Role |
|-----------|------|
| Sigma | Detection rule format (SIEM-agnostic) |
| SOC 2 TSC | Trust Services Criteria for compliance |
| ISO 27001:2022 | Annex A controls for information security |
| MITRE ATT&CK | Adversary technique context (where applicable) |

---

## Status

🚧 In progress - mappings complete, Sigma rules and evidence templates in development.

## Author

**Om Satam** - MS Cybersecurity, University of Delaware
[linkedin.com/in/om-satam](https://linkedin.com/in/om-satam) · [github.com/GRCguy14](https://github.com/GRCguy14)
