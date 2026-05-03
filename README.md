<div align="center">

# TamperCheck.ai

**Document tampering detection API** — hybrid forensic analysis + AI adjudication for **KYC**, **fraud ops**, and **compliance** teams.

[![API](https://img.shields.io/badge/API-v1-6366f1?style=flat-square)](https://tampercheck.ai/docs)
[![Privacy](https://img.shields.io/badge/privacy-first-0f766e?style=flat-square)](https://tampercheck.ai/privacy)

</div>

TamperCheck.ai is **document authenticity infrastructure**: upload a PDF or image, get a **verdict**, **risk score**, and **structured findings** — built for people who need **explainable** fraud signals.

---

## Why choose TamperCheck

- **Hybrid pipeline** — classic forensic signals plus LLM reasoning where it helps
- **Privacy-first** — security and data minimization by design
- **No document storage** — files are analyzed in the processing path and are **not retained as stored document content**
- **REST API** — `POST` a file, poll or block for results, pull JSON reports
- **Forensic Report** - get a downloadable report with the findings
- **OpenAPI** — AI friendly, easy to integrate API documentation at [tampercheck.ai/docs](https://tampercheck.ai/docs)

---

## Supported file formats

`PDF` · `JPEG` / `JPG` · `PNG` · `WebP` · `BMP` · `TIFF` — up to **40 MB** per upload. Document category is **auto-detected**; you do not need to declare a type in the request.

---

## Document types we analyze

The engine is tuned for high-stakes paperwork across industries. Representative categories:

| Category | Examples |
| -------- | -------- |
| **Identity & KYC** | Passports, national ID cards, driver's licenses, residence permits, visas, voter ID, birth certificates |
| **Financial** | Bank statements, credit card statements, cheques, wire confirmations, invoices, receipts, purchase orders, utility bills |
| **Tax & income** | Tax returns and forms, payslips, salary certificates |
| **Employment** | Offer letters, employment contracts, experience and relieving letters, appointment letters |
| **Education** | Degrees, diplomas, transcripts, marksheets, admission letters |
| **Legal & property** | Contracts, affidavits, court orders, powers of attorney, deeds, leases, mortgages |
| **Insurance** | Policies, certificates, claim packets |
| **Medical** | Reports, prescriptions, lab results, discharge summaries |
| **Corporate & compliance** | Business registration, articles of incorporation, trade licenses, SOC2 / ISO-style attestations where submitted as documents |

**Full catalog (searchable):** [tampercheck.ai/documents-support](https://tampercheck.ai/documents-support) — every supported type with API slugs, descriptions, and forensic focus.

---

## Platform capabilities

- **Hybrid detection pipeline** — forensic checks + AI reasoning
- **Decision support** — confidence scoring and structured evidence
- **Privacy-first processing** — least-privilege flows and minimal retention of sensitive payloads
- **No document storage** — no long-lived copy of your file as “stored content” after analysis
- **Operational visibility** — job-level monitoring and auditability
- **Provider control** — bring your own AI model keys (BYOK) where supported
- **Usage and metering** — clear API consumption for billing and quotas

---

## Quickstart (public API)

Create an API key in the dashboard, then:

```bash
# Ingest + analyze (multipart). Use your deployment base URL.
curl -sS -X POST "https://tampercheck.ai/api/v1/documents/" \
  -H "Authorization: Bearer dt_YOUR_API_KEY" \
  -F "document=@./contract.pdf" \
  -F "mode=async"
```

- **`Authorization: Bearer dt_...`** or **`X-API-Key: dt_...`**
- **`mode=async`** — job ID immediately · **`mode=instant`** — block until complete
- Poll **`GET /api/v1/documents/<uuid>/`** for the findings when ready
- **`GET /api/v1/documents/<uuid>/report-link/`** for the PDF report with the findings and annexure.
