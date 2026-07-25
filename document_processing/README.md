# Document Processing Automation
**Python automation suite for extracting and reconciling consular service data at scale**

> Built and deployed in production at the Consulate General of India, Seattle — processing hundreds of OCI and passport applicant records weekly.

---

## The Problem

Consular operations generate large volumes of structured data trapped inside unstructured documents — Word files, PDFs, and portal exports that don't talk to each other. Staff were manually:

- Opening individual OCI Detail Enquiry Word documents one by one
- Reading applicant fields and typing them into Excel tracking sheets
- Cross-referencing CSV exports against tracking workbooks to find mismatches
- Pulling applicant data from a web portal into formatted Word letters

Each of these tasks was time-consuming, error-prone, and impossible to scale during high-volume periods like passport renewal cycles or OCI backlogs.

---

## What I Built

A suite of four Python automation scripts, each targeting a specific bottleneck in the consular workflow:

---

### Script 1 — OCI Document Extractor
**`oci_extractor.py`**

Extracts structured applicant data from OCI Detail Enquiry Word documents and exports it into a formatted Excel workbook.

**How it works:**
1. Reads all `.docx` files from a target folder
2. Parses each document for key fields: File No, applicant name, DOB, address (city/state parsed separately), application type, status
3. Handles malformed documents and partial extractions with per-item error isolation — one bad file doesn't stop the batch
4. Exports all records to a structured Excel workbook with headers, formatting, and a timestamp

**Tech:** `python-docx` · `openpyxl` · `pandas` · `logging` · `re`

**Impact:** Replaced ~3 hours of manual data entry per batch with a 2-minute script run.

---

### Script 2 — Excel Reconciliation Tool
**`reconcile.py`**

Matches File Numbers between a CSV export from the consular portal and an existing Excel tracking workbook — flagging missing records, duplicates, and status mismatches.

**How it works:**
1. Loads the CSV export and the Excel tracking workbook
2. Normalizes File No formatting across both sources (handles spacing and case inconsistencies)
3. Performs a left join to identify records in the CSV not present in the tracker, and vice versa
4. Outputs a reconciliation report with match status, mismatches, and a summary count

**Tech:** `pandas` · `openpyxl` · `logging`

**Impact:** Turned a 2-hour manual cross-referencing task into a 30-second automated report.

---

### Script 3 — Selenium Portal Scraper
**`portal_scraper.py`**

Attaches to an existing authenticated Chrome session and extracts applicant data from the consular web portal, populating formatted Word output documents automatically.

**How it works:**
1. Connects to Chrome via remote debugging port (no login re-authentication required)
2. Navigates to applicant records and extracts structured fields
3. Populates a Word document template with extracted data
4. Saves output files named by File No for easy retrieval

**Tech:** `selenium` · `python-docx` · `ChromeDriver` · `logging`

**Note:** Designed for internal use only. No credentials or PII are stored in the script — the session attachment model means authentication remains in the browser, not in code.

---

### Script 4 — Passport Data Pipeline
**`passport_pipeline.py`**

End-to-end pipeline combining portal extraction and Excel export for passport renewal tracking — the highest-volume workflow at 10,000+ applicants per month.

**Tech:** `selenium` · `openpyxl` · `pandas` · `logging`

---

## Architecture Principles

Every script in this suite follows the same design pattern:

```
Config constants at top (paths, column names, field mappings)
    │
    ▼
Input validation (file exists, expected format)
    │
    ▼
Per-item processing loop with try/except isolation
    │
    ▼
Structured logging (info + error level)
    │
    ▼
Output export (Excel / Word / report)
```

**Why per-item error isolation matters:** In a batch of 200 applicant documents, one malformed file should not abort the entire run. Each script catches per-record errors, logs them with the File No, and continues processing the remaining records.

---

## What This Demonstrates (TPM Lens)

This suite wasn't built as a portfolio exercise — it was built to solve a real operational problem with real constraints:

- **Stakeholder alignment** — worked with consular operations staff to map the exact manual workflow before writing a single line of code
- **Constraint-driven design** — scripts run on Windows from `C:\Auto` with no virtual environment, no admin rights, and no internet dependency
- **Production reliability** — error isolation, logging, and graceful failure handling because real operational data is messy
- **Incremental delivery** — each script shipped and validated independently before building the next

This is the same program management approach I apply to larger engineering programs: understand the problem, define the scope, deliver incrementally, validate with users.

---

## Project Structure

```
document_processing/
│
├── oci_extractor.py          # OCI Word doc → Excel extraction
├── reconcile.py              # CSV vs Excel reconciliation
├── portal_scraper.py         # Selenium portal → Word output
├── passport_pipeline.py      # End-to-end passport tracking pipeline
├── requirements.txt
└── README.md
```

---

## Setup

```bash
# Install dependencies
pip install python-docx openpyxl pandas selenium

# For portal scraper — start Chrome with remote debugging first:
# chrome.exe --remote-debugging-port=9222

# Run individual scripts
python oci_extractor.py
python reconcile.py
```

> **Note:** Scripts reference local file paths configured at the top of each file. Update the config constants to match your environment before running.

---

*Part of the [Chetan Gupta TPM Portfolio](https://github.com/cgsalwan/chetan-gupta-tpm-portfolio)*
